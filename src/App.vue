<template>
  <div id="app">
    <img class="clayton-image" src="./assets/clayton-sucks-at-halo.gif">
    <h1 class="title">Welcome to claytonsucksathalo.com :)</h1>
    <img class="clayton-image" src="./assets/clayton.jpg">

    <label v-if="messageSent" class="sent-label">
      Message Sent!
    </label>

    <form v-else class="form" @submit.prevent="sendTextToClayton">
      <div class="encouragement-label">
        <label>
          Clayton could use your encouragement!
        </label>
        <label>
          Use the form below to text Clayton some
          encouragement to not suck so bad at Halo
        </label>
      </div>
      <textarea
        v-model="message"
        class="message-input"
        placeholder="Get well soon!... etc."
      >
      </textarea>
      <button class="submit-button" type="submit" :disabled="isSending">
        {{ isSending ? 'Sending...' : 'Send' }}
      </button>
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    status: '',
    message: null,
    messageSent: false,
  }),

  computed: {
    hasError() {
      return this.status === 'error';
    },
    isSending() {
      return this.status === 'sending';
    },
  },

  methods: {
    sendTextToClayton() {
      this.status = 'sending';

      setTimeout(() => {
        this.messageSent = true;
        this.resetForm();
      }, 1000);
    },

    resetForm() {
      this.status = '';
      this.message = '';
    },
  },
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: purple;
}

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.encouragement-label {
  display: flex;
  flex-direction: column;
  margin-bottom: 1vw;
}

.form {
  display: flex;
  flex-direction: column;
  align-content: center;
  padding: 1vw;
}

.clayton-image {
  max-width: 100%;
}

.sent-label {
  border: 3px solid red;
  color: red;
  padding: 20px;
  margin-top: 10px;
}

.message-input {
  height: 10vw;
  margin-bottom: 1vw;
}

.submit-button {
  padding: 10px;
  cursor: pointer;
}
</style>
