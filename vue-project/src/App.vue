<script setup>
import { ref } from "vue";

const email = ref("");
const emails = ref([]);
const showSuccess = ref(false);

const addEmail = () => {
  if (email.value && !emails.value.includes(email.value)) {
    emails.value.push(email.value);
    showSuccess.value = true;
    email.value = "";

    setTimeout(() => {
      showSuccess.value = false;
    }, 3000);

    console.log("All emails:", emails.value);
  }
};
</script>

<template>
  <div
    class="min-h-dvh bg-white flex flex-col items-center justify-between pt-6 md:pt-12 lg:pt-16 pb-6 md:pb-10 px-4 relative"
  >
    <!-- Top Section: Logo and Subtitle -->
    <div class="w-full flex flex-col items-center">
      <div class="flex justify-center mb-4 md:mb-6">
        <img
          src="/images/smarthomes-logo-coffee.png"
          alt=""
          class="w-[80%] md:w-[60%] lg:w-[500px] h-auto"
        />
      </div>
      <div class="max-w-3xl w-full text-center">
        <p
          class="text-base md:text-xl lg:text-2xl text-black font-normal italic px-4"
        >
          There's Nothing Quite Like What We're Building
        </p>
      </div>
    </div>

    <!-- Middle Section: Main Content -->
    <div
      class="w-full flex flex-col items-center space-y-8 md:space-y-12 lg:space-y-16"
    >
      <div class="max-w-2xl w-full text-center">
        <p
          class="text-base md:text-xl lg:text-2xl font-normal text-black tracking-tight"
        >
          Check back soon to find out more
        </p>
        <p
          class="text-base md:text-xl lg:text-2xl font-normal text-[#432818] tracking-wide mt-2"
        >
          Garuka vuba urebe uko bimeze
        </p>
      </div>

      <!-- Email Input Form -->
      <div class="max-w-md w-full px-4">
        <p class="text-black mb-4 text-sm md:text-base lg:text-lg text-center">
          Get <span class="font-bold">SMARTHOMES</span> updates
        </p>

        <!-- Form - Hidden when success message shows -->
        <form
          v-if="!showSuccess"
          @submit.prevent="addEmail"
          class="flex flex-col sm:flex-row gap-2 sm:gap-3"
        >
          <input
            v-model="email"
            type="email"
            placeholder="Enter your email"
            required
            class="flex-1 px-4 py-2.5 md:py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-[#432818] text-black text-sm md:text-base"
          />
          <button
            type="submit"
            class="px-6 py-2.5 md:py-3 bg-[#432818] text-white rounded-lg hover:bg-[#5a3622] transition text-sm md:text-base whitespace-nowrap"
          >
            Update Me
          </button>
        </form>

        <!-- Success Message - Shows when form is hidden -->
        <p
          v-if="showSuccess"
          class="text-green-600 text-sm md:text-base lg:text-lg text-center py-3"
        >
          Thank you! We'll update you.
        </p>
      </div>
    </div>

    <!-- Footer Section -->
    <div class="flex flex-col items-center w-full">
      <a
        class="text-sm md:text-base lg:text-xl font-normal text-black cursor-pointer tracking-[0.2em] md:tracking-[0.3em]"
      >
        www.smarthomes.rw
      </a>

      <p
        class="text-sm md:text-base lg:text-xl font-normal text-black mt-1 md:mt-2 tracking-tight"
      >
        Kigali | Bugesera | Musanze
      </p>
      <p
        class="text-sm md:text-base lg:text-xl decoration-none font-normal text-black mt-1 md:mt-2"
      >
        Tel: +250795878484
      </p>
    </div>
  </div>
</template>
