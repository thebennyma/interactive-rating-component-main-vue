<template>
  <div class="container" v-show="showMainContainer">
    <img src="@/images/icon-star.svg" alt="" />
    <h1>How did we do?</h1>
    <p>
      Please let us know how we did with your support request. All feedback is
      appreciated to help us improve our offering!
    </p>
    <ul>
      <li v-for="i in 5" :key="i">
        <button
          class="btn"
          :class="{ active: rating === i }"
          @click="handleRatingClick(i)"
        >
          {{ i }}
        </button>
      </li>
    </ul>
    <button
      class="btn-submit"
      v-show="showMainContainer"
      @click="handleRatingButtonClick()"
    >
      Submit
    </button>
  </div>

  <div class="thank-you" v-show="showThanksContainer">
    <img src="@/images/illustration-thank-you.svg" alt="" />
    <p class="gray">
      You selected
      <span id="rating" style="display: inline-block; margin: 0 0.3rem">{{
        rating
      }}</span>
      out of 5
    </p>
    <h2>Thank you!</h2>
    <p>
      We appreciate you taking the time to give a rating. If you ever need more
      support, don’t hesitate to get in touch!
    </p>
    <button class="btn-submit" id="rate-again" @click="handleRateAgainClick()">
      Rate Again
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rating: 0,
      showMainContainer: true,
      showThanksContainer: false,
    };
  },
  methods: {
    handleRatingClick(rating) {
      this.rating = rating;
      const buttons = document.querySelectorAll(".btn");
      buttons.forEach((button, index) => {
        if (index + 1 !== rating) {
          button.classList.remove("active");
        }
      });
    },
    handleRatingButtonClick() {
      this.showMainContainer = false;
      this.showThanksContainer = true;
    },
    handleRateAgainClick() {
      this.rating = 0;
      this.showMainContainer = true;
      this.showThanksContainer = false;
    },
  },
};
</script>

<style>
:root {
  --color-dark-blue: hsl(212, 18%, 14%);
  --color-darker-blue: hsl(220, 16%, 11%);
  --color-light-blue: hsl(217, 12%, 63%);
  --color-gold: hsl(25, 97%, 53%);
  --font-family: "Overpass", sans-serif;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-family);
  font-size: 15px;
  background-color: hsl(216, 12%, 8%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

h1,
h2 {
  color: #fff;
}

p {
  line-height: 1.8;
  color: var(--color-light-blue);
}

img {
  max-width: 100%;
}

ul {
  list-style-type: none;
}

ul,
li,
button {
  font-family: inherit;
  font-size: 1rem;
}

button {
  user-select: none;
  cursor: pointer;
}

.btn {
  background-color: var(--color-darker-blue);
  width: 3rem;
  height: 3rem;
  color: #ffffff;
  border: none;
  outline: none;
  border-radius: 50%;
  padding-top: 0.3rem;
  transition: 0.3s;
}

.btn:hover {
  background-color: var(--color-light-blue);
}

.btn:focus {
  background-color: var(--color-gold);
}

.btn.active {
  background-color: var(--color-gold);
}

.btn-submit {
  background-color: var(--color-gold);
  padding: 0.625rem 2rem 0.5rem;
  width: 100%;
  border: none;
  border-radius: 30px;
  color: #fff;
  margin-top: 2rem;
  transition: 0.3s;
  text-transform: uppercase;
  letter-spacing: 0.2rem;
  font-size: 0.9rem;
}

.btn-submit:hover {
  background-color: #fff;
  color: var(--color-gold);
}

.container,
.thank-you {
  background-image: linear-gradient(
    to bottom,
    var(--color-dark-blue),
    var(--color-darker-blue)
  );
  max-width: 400px;
  padding: 2rem 1.5rem;
  border-radius: 0.625rem;
}

.container img {
  padding: 0.8rem;
  border-radius: 50%;
  background-color: var(--color-darker-blue);
  margin-bottom: 2rem;
}

.container h1,
.thank-you h2 {
  margin-bottom: 1rem;
}

.container p,
.thank-you p {
  margin-bottom: 1rem;
}

.container ul {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
}

.container ul li {
  margin: 0.5rem;
}

.thank-you {
  text-align: center;
}

.thank-you.hidden {
  display: none;
}

.thank-you h2 {
  margin-top: 2rem;
}

.thank-you img {
  display: block;
  margin: 0 auto 1rem;
}

p.gray {
  display: inline-block;
  background-color: var(--color-darker-blue);
  color: var(--color-gold);
  padding: 0.3rem 1rem 0;
  border-radius: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>