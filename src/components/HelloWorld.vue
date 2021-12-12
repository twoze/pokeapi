<template>
  <div>
    <h1 id="idh1"></h1>
  <!-- <img id="id2" src="../assets/logo.png">
    <button v-on:click="clicked">click</button>
    <button v-on:click="hide">hide</button>
    <button v-on:click="show">show</button>-->

    <div id="create"></div>
    <input type="number" id="name" name="name" size="15">
    <button v-on:click="create">search</button>

    <div>{{this.nom}}</div>
    <div>{{this.poids}}</div>
    <div>{{this.url}}</div>
    <img id="src">

  </div>

</template>

<script>
import axios from 'axios'
export default {
  name: 'PokemonAPI',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      info: null,
      nom: null,
      poids: null,
      url: null
    }
  },
  methods: {
    clicked: function () {
      console.log('click')
    },
    hide: function () {
      console.log('hide')
      document.getElementById('idh1').style.display = 'none'
    },
    show: function () {
      console.log('show')
      document.getElementById('idh1').style.display = 'block'
    },
    create: function () {
      axios
        .get('https://pokeapi.co/api/v2/pokemon/' + document.getElementById('name').value)
        .then(response => {
          this.info = response.data
          this.nom = this.info.name
          this.poids = this.info.height
          this.url = this.info.sprites.front_default
          var image = document.getElementById('src')
          image.src = this.url
        })

      // var txt = JSON.stringify(this.info)
      // var h = document.createElement('p')
      // var t = document.createTextNode(txt)
      // h.appendChild(t)
      // var currentDiv = document.getElementById('create')
      // currentDiv.appendChild(h)
    }
  }
  // mounted () {
  //   axios
  //     .get('https://pokeapi.co/api/v2/pokemon/1')
  //     .then(response => (this.info = response.data.name))
  // }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

button {
  color: white;
  border: none;
  background-color: rgb(129, 166, 209);
  border-radius: 30px;
}
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

input {
  border: none;
  background-color: rgb(240, 240, 240);
}
#create {
  border: none;
  border-radius: 8px;
}
#src {}

</style>
