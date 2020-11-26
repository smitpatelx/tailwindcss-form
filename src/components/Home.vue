<template>
  <div :class="night ? 'dark' : ''" class="dark-box-transition" :map-keydown="handlers">
    <div class="w-full antialiased min-h-screen flex flex-wrap justify-center items-center dark:bg-gray-900 bg-gray-100">
      <div tabindex="0" @click="night = !night" class="transform focus:outline-none focus:ring-2 focus:ring-teal-400 h-7 flex flex-wrap items-center justify-start w-16 top-0 absolute dark:bg-gray-700 bg-gray-400 rounded-full py-1.5 px-2 mt-3 dark:text-gray-400 text-sm font-medium leading-none">
        <span class="inline-block w-5 h-5 absolute rounded-full bg-gradient-to-r from-teal-400 to-teal-900 leading-none transition-all duration-600 ease-in shadow" :class="night ? 'from-teal-400 to-teal-900 left-1.5' : 'from-gray-100 to-gray-50 left-9'"></span>
      </div>
      <form ref="form" @submit.prevent="submit_form()" class="w-auto md:w-full absolute md:max-w-lg mx-4 md:mx-0 lg:max-w-lg bg-gray-200 bg-opacity-40 ring-1 ring-gray-200 dark:ring-0 dark:ring-transparent dark:bg-gray-800 flex flex-wrap border-t-8 border-teal-400 flex-col py-12 px-8 rounded-xl shadow-xl space-y-4">
        <span class="text-4xl mb-6 dark:text-gray-300 font-semibold w-full text-center">Login</span>
        <div class="w-full flex flex-wrap flex-col">
          <label class="w-full text-sm font-medium text-gray-600 dark:text-teal-400" for="login">Email or Username</label>
          <input class="border-0 focus:outline-none focus:ring-2 focus:ring-teal-400 transition-shadow ease-out duration-200 w-full text-lg dark:text-gray-100 placeholder-gray-500 px-3 py-1 mt-2 rounded dark:bg-gray-700" type="text" id="login" placeholder="Email or Username" />
        </div>
        <div class="w-full flex flex-wrap flex-col">
          <label class="w-full text-sm font-medium text-gray-600 dark:text-teal-400" for="password">Password</label>
          <input class="border-0 focus:outline-none focus:ring-2 focus:ring-teal-400 transition-shadow ease-out duration-200 w-full text-lg dark:text-gray-100 placeholder-gray-500 px-3 py-1 mt-2 rounded dark:bg-gray-700" type="password" id="password" placeholder="Password" />
        </div>
        <div class="w-full flex flex-wrap flex-row">
          <span class="w-full flex flex-wrap mt-2">
            <input class="border-0 w-5 h-5 rounded cursor-pointer focus:outline-none focus:ring-2 focus:ring-offset-0 focus:ring-teal-400 text-teal-500 transition-shadow ease-out duration-200 dark:bg-gray-700" id="remember_me" type="checkbox" />
            <label class="text-lg ml-3 my-auto leading-none text-gray-600 dark:text-gray-200 select-none cursor-pointer" for="remember_me">Remember me</label>
          </span>
        </div>
        <div class="flex items-center justify-center pt-6 space-x-4">
          <button class="focus:outline-none cursor-pointer focus:bg-opacity-70 hover:bg-opacity-70 focus:ring-2 focus:ring-teal-400 transition-shadow ease-out duration-200 py-2 px-6 bg-teal-400 text-gray-800 rounded-md text-base font-medium" type="submit">Login</button>
          <button class="focus:outline-none cursor-pointer hover:bg-opacity-75 focus:ring-2 focus:ring-teal-400 transition-shadow ease-out duration-200 py-2 px-6 bg-gray-600 text-gray-100 rounded-md text-base font-medium" type="reset">Reset</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      night: true,
    };
  },
  methods: {
    submit_form() {
      alert("Form submited");
    },
    handlers(e) {
      if (e.which === 191) {
        e.preventDefault();
        this.night = !this.night;
      }

      if (e.which === 27) {
        e.preventDefault();
        this.$refs["form"].reset();
      }
    },
  },
  created() {
    window.addEventListener("keyup", this.handlers);
  },
};
</script>
