<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    
    <div v-for= "(post, index) in posts"
      :key="index"
    >
      {{ post.title +"," + post.author }}
     
    </div>
    <HelloWorld>
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data() {
    return {
      posts: null
    }
  },
  mounted: function() {
    fetch('https://desolate-meadow-70423.herokuapp.com/posts', {
      method: 'get'
    })

      .then((response) => {
        return response.json()
      })

      .then((jsonData) => {
        this.posts = jsonData
      })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
