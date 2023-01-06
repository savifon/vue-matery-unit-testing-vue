<template>
  <div>
    <p v-if="error" data-testid="message-error">{{ error }}</p>
    <p v-else-if="message.text" data-testid="message">{{ message.text }}</p>
  </div>
</template>

<script>
import { getMessage } from "@/services/axios.js";

export default {
  data() {
    return {
      message: {
        text: "",
      },
      error: null,
    };
  },

  async created() {
    try {
      this.message = await getMessage();
    } catch (err) {
      this.error = "Oops! Something went wrong.";
    }
  },
};
</script>
