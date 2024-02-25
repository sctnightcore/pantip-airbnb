<script setup lang="ts">
import rooms from "~/data/rooms";
import hightlights from "~/data/highlights";
import topics from "~/data/topics";
</script>

<template>
  <VApp>
    <VAppBar elevation="0" color="#302c4c">
      <VContainer>
        <VAppBarTitle class="text-h5 font-weight-black"> PANTIP </VAppBarTitle>
      </VContainer>
      <template #append>
        <VBtn icon="mdi-bell-outline" size="x-large" />
        <VBtn icon="mdi-web" size="x-large" />
        <VBtn icon="mdi-account" size="x-large" />
      </template>
    </VAppBar>
    <VMain>
      <VContainer fluid>
        <VRow>
          <VCol cols="12" md="8">
            <VTabs stacked color="#302c4c" height="100">
              <VTab v-for="i in rooms.data">
                <p>
                  {{ i.name }}
                </p>
              </VTab>
            </VTabs>

            <VTab value="1">
              <VRow>
                <VCol cols="12" md="4" v-for="i in topics.data[0].topics">
                  <VCard variant="text">
                    <VImg
                      width="400px"
                      height="400px"
                      :src="i.thumbnail_url!"
                      cover
                    ></VImg>
                    <VCardTitle class="text-start">
                      {{ i.title }}
                    </VCardTitle>
                    <VCardSubtitle class="text-start">
                      <VAvatar size="60" color="black">
                        <VImg :src="i.author.avatar.original" />
                      </VAvatar>
                      <span class="ml-2 font-weight-bold">{{
                        i.author.name
                      }}</span>
                    </VCardSubtitle>
                    <VCardText>
                      <VChip v-for="j in i.tags">
                        {{ j.name }}
                      </VChip>
                    </VCardText>
                  </VCard>
                </VCol>
              </VRow>
            </VTab>
          </VCol>

          <VCol cols="12" md="4">
            <VCard variant="text">
              <VCardText>
                <VSlideGroup show-arrows>
                  <VSlideGroupItem v-for="i in hightlights">
                    <VRow>
                      <vCol cols="12">
                        <VImg
                          height="600px"
                          width="600px"
                          :src="i.image_url[0]"
                        />
                      </vCol>
                      <VCol cols="12">
                        <VCardTitle>{{ i.name }}</VCardTitle>
                      </VCol>
                    </VRow>
                  </VSlideGroupItem>
                </VSlideGroup>
              </VCardText>
            </VCard>

            <VCard>
              <VCardTitle>แท็กฮิต</VCardTitle>
              <VCardText>
                <VList>
                  <VListItem v-for="i in topics.data[0].topics[0].tags">
                    <VListItemTitle>{{ i.name }}</VListItemTitle>
                  </VListItem>
                </VList>
              </VCardText>
            </VCard>
          </VCol>
        </VRow>
      </VContainer>
    </VMain>
  </VApp>
</template>

<style>
@import "https://fonts.googleapis.com/css?family=Sarabun";
* {
  font-family: "Sarabun", sans-serif !important;
}
</style>
