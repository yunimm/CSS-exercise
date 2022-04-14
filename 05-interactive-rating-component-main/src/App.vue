<script setup>
import { ref, reactive } from 'vue'

const itemB = reactive([
  { id: 1, item: 1, isActive: false },
  { id: 2, item: 2, isActive: false },
  { id: 3, item: 3, isActive: false },
  { id: 4, item: 4, isActive: false },
  { id: 5, item: 5, isActive: false },
])
const isHidden = ref(false)
const num = ref('')
function toggleActive(key) {
  itemB[key].isActive = !itemB[key].isActive
  num.value = itemB[key].item
}
function handleSubmitted() {
  isHidden.value = !isHidden.value
}
</script>

<template>
  <div class="container">
    <div class="card vote" :class="{ hidden: isHidden }">
      <div class="img-star-container">
        <img
          class="card-star"
          src="./assets/images/icon-star.svg"
          alt="star on screen"
        />
      </div>
      <div class="card-title">How did we do?</div>
      <p class="card-p">
        Please let us know how we did with your support request. All feedback is
        appreciated to help us improve our offering!
      </p>
      <ul class="items">
        <li
          v-for="({ id, item, isActive }, index) in itemB"
          :key="id"
          @click="toggleActive(index)"
          :class="{ active: isActive }"
        >
          {{ item }}
        </li>
      </ul>
      <button type="button" class="btn" @click="handleSubmitted">Submit</button>
    </div>
    <div class="card thx" :class="{ hidden: !isHidden }">
      <div class="img-container">
        <img
          class="card-thx"
          src="./assets/images/illustration-thank-you.svg"
          alt="img on screen"
        />
      </div>
      <span>You selected {{ num }} out of 5</span>
      <div class="card-title">Thank you!</div>
      <p class="card-p">
        We appreciate you taking the time to give a rating. If you ever need
        more support, don’t hesitate to get in touch!
      </p>
    </div>
  </div>
</template>

<style lang="scss" src="./assets/scss/all.scss"></style>
