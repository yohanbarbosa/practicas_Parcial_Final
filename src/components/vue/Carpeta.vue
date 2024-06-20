<script setup>
import { ref } from 'vue';

const selectedIndex = ref('');
const selectedIndexHijo = ref('');


const localC = ref([
  { name: 'Home' },
  { name: 'Galeria' },
  {
    name: 'OnDrive - personal',
    hijo: [
      {
        name: 'Documentos',
        hijo: [
          { name: 'Anvsoft' },
          { name: 'Captura' },
          { name: 'ClickCharts' }, 
          { name: 'Custom Office Template' }, 
          { name: 'OneNote Notebooks'},
          { name: 'Sound Recordings'},
          { name: 'Zoom'},
          { name: 'Pictures'},
          { name: 'TWC'},
          { name: 'HOLA MUNDO'},

        ]
      }
    ]
  }
]);

function showInfo(i) {
    if (i == selectedIndex.value) {
        selectedIndex.value = -1;
    } else {
        selectedIndex.value = i
    }
}

function showInfoHijo(j) {
    if (j == selectedIndexHijo.value) {
        selectedIndexHijo.value = -1;
    } else {
        selectedIndexHijo.value = j
    }

}

</script>

<template>
    <div class="flex items-center w-full h-screen bg-black">
      <div class="mx-auto w-2/4 h-96 bg-slate-400">
        <div class="bg-slate-200 w-[200px]">
          <div v-for="(carpeta, i) in localC" :key="i" class="px-2 cursor-pointer">
            <span  @click="showInfo(i)"> 
                <span class="">{{ selectedIndex == i ? 'v' : '>' }}</span>
                {{ carpeta.name }}</span>
            <div v-if="i === 2" class="px-2">
                
                <div v-show="selectedIndex == i" class="">

                    <div v-for="(hijo, j) in carpeta.hijo" :key="j" class="ml-4">
                        <span @click="showInfoHijo(j)" >
                            <span class="">{{ selectedIndexHijo == j ? 'v' : '>' }}</span>
                            {{ hijo.name  }}
                        </span>

                        <div v-show="selectedIndexHijo == j" class="">
                        <div v-for="subHijo in hijo.hijo" :key="subHijo.name" class="px-2">
                            {{ subHijo.name }}
                        </div>
                    </div>
                    </div>
                </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>

