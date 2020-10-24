<template>
 <div class="app-container">
   @{{user.username}} - {{ fullName }}
   <strong>Followers: </strong>{{ followers }}
   <button v-on:click="followUser"> Follow </button>
 </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '_vikrant',
        firstname: 'vikrant',
        lastname: 'singh',
        email: 'vikrantsingh47@gmail.com',
        isAdmin: true
      }
    }
  },
  computed: {
    fullName(){
      return `${this.user.firstname} ${this.user.lastname}`;
    }
  },
  watch:{
    followers(newValue, oldValue){
      if(oldValue < newValue){
        console.log(`${this.user.username} has gained a follower!`);
      }
    }
  },
  methods:{
    followUser(){
      this.followers++;
    }
  },
  mounted(){
    this.followUser();
  }
}
</script>

<style scoped>
.app-container {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
