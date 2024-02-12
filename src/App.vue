<script setup>
import { ref } from 'vue';

const searchQuery = ref('');
const items = ['Daddy Yankee', 'Bad Bunny', 'Maluma', 'Ozuna', 'J Balvin'];
const counter = ref(0);
const bgColor = ref('blanco');

const incrementarContador = () => {
  counter.value++;
  document.getElementById('counterDisplay').innerText = counter.value;
};

const cambiarColorFondo = () => {
  if (bgColor.value === 'blue') {
    bgColor.value = 'black';
  } else {
    bgColor.value = 'blue';
  }
};

const elementosFiltrados = () => {
  return items.filter(item =>
    item.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
};
</script>

<template>
<body>

<div id="app">
  <!-- V-Model -->
  <input type="text" v-model="searchQuery" placeholder="Buscar...">
  
  <!-- V-If, V-Else-If, V-Else -->
  <div v-if="searchQuery === 'vue'">
    ¡Vue.js es impresionante!
  </div>
  <div v-else-if="searchQuery === 'react'">
    ¡React también es genial!
  </div>
  <div v-else>
    Tu búsqueda no se ha encontrado.
  </div>
  
  <!-- V-For -->
  <ul>
      <li v-for="(elemento, index) in elementosFiltrados()" :key="index">{{ elemento }}</li>
  </ul>
  <!-- Dos directivas V-On -->
  <button v-on:click="incrementarContador">Haz clic para incrementar el contador</button>
  <button v-on:mouseover="cambiarColorFondo">Pasa el ratón para cambiar el fondo</button>
  
  <!-- V-Bind -->
  <div v-bind:style="{ backgroundColor: bgColor }">
    Este color de fondo está vinculado dinámicamente.
  </div>

   <!-- Elemento para mostrar el contador -->
   <div>Valor del contador: <span id="counterDisplay">{{ counter }}</span></div>
</div>
</body>
</template>

<style scoped>/* Estilos para el contenedor principal */
#app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

/* Estilos para el campo de búsqueda */
input[type="text"] {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 2px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
}

/* Estilos para la lista de elementos */
ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

/* Estilos para los botones */
button {
  padding: 10px 20px;
  margin-right: 10px;
  border: none;
  border-radius: 5px;
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
  font-size: 16px;
  margin: 1%;
}

button:hover {
  background-color: #0056b3;
}

/* Estilos para el contenedor del contador */
#counterDisplay {
  font-size: 18px;
  font-weight: bold;
  color: #007bff;
}

/* Estilos para el contenedor del color de fondo */
div[style] {
  margin-top: 20px;
  padding: 20px;
  border-radius: 5px;
  color: #fff;
}

/* Estilos específicos para el color de fondo */
div[style="background-color: lightblue;"] {
  background-color: lightblue;
}

</style>
