<script>
import { mapState, mapStores } from 'pinia'
import { useMainStore } from '@/store/store'

export default {
  props: {
    msg: String
  },
  data: () => ({
    store: useMainStore()
  }),
  computed: {
    ...mapState(useMainStore, ['count'])
  },
  mounted() {
    this.store.count = 12;
  }
  // computed: {
  //   ...mapState(useMainStore, ['count']),
  //   //...mapStores(useMainStore)
  // },
  
}

</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <p>
      Recommended IDE setup:
      <a href="https://code.visualstudio.com/" target="_blank">VS Code</a>
      +
      <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    </p>
    <p>
      <a href="https://vitejs.dev/guide/features.html" target="_blank">
        Vite Documentation
      </a>
      |
      <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</a>
    </p>
    <button type="button" @click="store.$patch({ count: store.count + 1 })">count is: {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test hot module replacement.
    </p>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
