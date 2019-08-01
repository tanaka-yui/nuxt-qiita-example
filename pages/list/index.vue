<template>
  <ul class="list">
    <li v-for="item in data" :key="item.id" class="listItem">
      {{ item.title }}
    </li>
  </ul>
</template>

<style>
.list {
  padding: 0;
}

.listItem {
  list-style: none;
  border-bottom: 1px solid #999;
  padding: 1rem 16px;
  box-sizing: border-box;
}
</style>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({})
export default class List extends Vue {
  async asyncData(context) {
    const res = await context.$axios.get('https://qiita.com/api/v2/items', {
      headers: {
        Authorization: 'Bearer xxxxxxxx'
      }
    })
    return {
      data: res.data
    }
  }
}
</script>
