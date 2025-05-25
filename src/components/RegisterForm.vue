<script setup>
import { ref, computed } from 'vue'

// State
const name = ref('')
const age = ref(null)
const alamat = ref('')
const isRegistered = ref(false)
const showError = ref(false)


const statusColor = computed(() => {
  return age.value >= 17 ? 'green' : 'orange'
})

const alamatStyle = computed(() => {
  return {
    border: alamat.value.length < 5 ? '2px solid red' : '2px solid green'
  }
})

// Fungsi Submit
function submitForm() {
  if (name.value && age.value >= 17 && alamat.value.length >= 5) {
    isRegistered.value = true
    showError.value = false
  } else {
    isRegistered.value = false
    showError.value = true
  }
}
</script>

<template>
  <div class="container">
    <h1>Formulir</h1>

    <input v-model="name" placeholder="Nama" />
    <input v-model.number="age" placeholder="Umur" type="number" />
    <input
      v-model="alamat"
      placeholder="Alamat (minimal 5 karakter)"
      :style="alamatStyle"
    />

    <button @click="submitForm">Daftar</button>

    <p v-if="isRegistered" :style="{ color: statusColor }">
      Terima kasih {{ name }}, kamu berhasil mendaftar!
    </p>


    <p>Nama saat ini: {{ name }}</p>
    <p>Umur saat ini: {{ age }}</p>
    <p>Alamat saya di: {{ alamat }}</p>
  </div>
</template>

<style scoped>
/* Buat CSS Nya Di Sini Dan Di File Style.css ( Cek Folder ) */
</style>