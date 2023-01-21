<template>
<div class="main-container">
  <p class="id">Advice #{{ num }}</p>
  <p class="quote">
    {{ advice }}
  </p>
  <img src="./assets/images/pattern-divider-mobile.svg">
  <!-- <br>
  <img src="./assets/images/pattern-divider-desktop.svg"> -->
<div class="move">
  <div class="dice-container" @click="getAdvice">
    <img src="./assets/images/icon-dice.svg">
  </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      num: 0,
      advice: ''
    }
  },
  methods: {
    async getAdvice() {
      const response = await axios.get('https://api.adviceslip.com/advice')
      this.num = response.data.slip.id
      this.advice = response.data.slip.advice
      console.log(this.num)
      console.log(this.advice)
    }
    // getAdvice() {
    //   axios
    //     .get('https://api.adviceslip.com/advice')
    //     .then(response => (this.advice = response))
    //     console.log(this.advice)
  // }

},
mounted() {
  this.getAdvice()
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 28px;
}
.main-container {
  /* height: 100%;
  width: 80%; */
  /* min-width: 400px; */
  border: 1px solid #000;
  border-radius: .7rem;
  margin: 0 auto;
}
.id {
  color: hsl(150, 100%, 66%);
  font-weight: 800;
}
.quote {
  margin: 15px 10px;
  font-weight: 800;
}
.dice-container {
  background-color: hsl(150, 100%, 66%);
  width: 70px;
  height: 70px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  cursor: pointer;
}
.main-container>.move {
  position: relative;
  top: 40px;
}
@media screen and (max-width: 375px) {
  #app {
    font-size: 16px;
  }
  .main-container {
    width: 90%;
    /* margin: 10px; */
    border-color: red;
  }


}
</style>
