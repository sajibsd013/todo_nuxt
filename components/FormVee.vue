<template>
  <div>
    <div>
      <input v-model="name" />
      <div v-for="error of v$.name.$silentErrors" :key="error.$message">
        <div>{{ error.$message }}</div>
      </div>
    </div>
    <div>
      <input v-model="contact.email" />
      <div
        v-for="error of v$.contact.email.$silentErrors"
        :key="error.$message"
      >
        <div>{{ error.$message }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required, email } from "@vuelidate/validators";

export default {
  name: "App",
  setup() {
    return { v$: useVuelidate() };
  },
  data() {
    return {
      name: "",
      contact: {
        email: "",
      },
    };
  },
  validations() {
    return {
      name: { required },
      contact: {
        email: { required, email },
      },
    };
  },
};
</script>
