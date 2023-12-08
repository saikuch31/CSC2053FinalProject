<template>
  <header class="sticky top-0 bg-indigo-900 shadow-lg">
    <nav
      class="container flex flex-col sm:flex-row items-center gap-4 text-black py-6"
    >
      <RouterLink :to="{ name: 'home' }">
        <div class="hover:text-white flex items-center gap-3">
          <i
            class="motion-reduce:hidden animate-bounce h-6 w-6 mr-10 fa-solid fa-cloud text-2xl"
          ></i>
          <p class="text-2xl">Weather App</p>
        </div>
      </RouterLink>

      <div class="flex gap-3 flex-1 justify-end">
        <i
          class="fa-solid fa-circle-info text-xl hover:text-weather-secondary duration-150 cursor-pointer"
          @click="toggleModal"
        ></i>
      </div>

      <BaseModal :modalActive="modalActive" @close-modal="toggleModal">
        <div class="text-black">
          <h1 class="text-2xl mb-1">About:</h1>
          <p class="mb-4">
            The Weather App allows you to track the current and future weather
            of cities of your choosing.
          </p>
          <h2 class="text-2xl">How it works:</h2>
          <ol class="list-decimal list-inside mb-4">
            <li>
              Search for your city by entering the name into the search bar.
            </li>
            <li>
              Select a city within the results, this will take you to the
              current weather for your selection.
            </li>
          </ol>
        </div>
      </BaseModal>
    </nav>
  </header>
</template>

<script setup>
import { RouterLink, useRoute, useRouter } from "vue-router";
import { ref } from "vue";
import BaseModal from "./BaseModal.vue";

const route = useRoute();
const router = useRouter();

const modalActive = ref(null);
const toggleModal = () => {
  modalActive.value = !modalActive.value;
};
</script>
