<template>
  <Page>
    <ActionBar>
      <Label text="Home" class="font-bold text-lg" />
    </ActionBar>

    <GridLayout>
      <Label
        class="text-xl align-middle text-center text-gray-500"
        :text="message"
        @tap="buttonTap"
      />
    </GridLayout>
  </Page>
</template>

<script lang="ts">
import Vue from 'nativescript-vue';
import { Http } from '@nativescript/core';

export default Vue.extend({
  computed: {
    message() {
      return 'Blank {N}-Vue app';
    },
  },

  methods: {
    buttonTap() {
      Http.getJSON('http://localhost:8090/forecast?freetext=chicago').then(
        (result: any) => {
          console.log(result);
        },
        (e) => {
          console.log(e);
        }
      );
      console.log('You have tapped the message!');
    },
  },
});
</script>

<style>
/* .info {
    font-size: 20;
  } */
</style>
