<template>
  <div>
    <!-- Login Screen -->
    <div v-if="currentPage === 'login'">
      <h1>Login Screen</h1>
      <form>
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" />
        <br />
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" />
        <br />
        <button type="submit" @click.prevent="login">Login</button>
      </form>
    </div>

    <!-- Map Page -->
    <div color="#778DA9" v-else-if="currentPage === 'map'">
      <html class="boddy">
        <body class="boddy">
          <div color="#778DA9">
            <h1>Map Page</h1>
            <div>
              <logout-button>Logout</logout-button>
            </div>
            <div>
              <va-button color="#778DA9" @click="switchPage('map')"
                >Map</va-button
              >
              <button @click="switchPage('mission')">Mission</button>
              <button @click="switchPage('settings')">Settings</button>
            </div>
            <div>
              <img src="src/assets/map_1.jpg" alt="Map" />
              <p>This is the Map page.</p>
            </div>
          </div>
        </body>
      </html>
    </div>

    <!-- Mission Page -->
    <div v-else-if="currentPage === 'mission'">
      <h1>Mission Page</h1>
      <logout-button @click="switchPage('logout')">Logout</logout-button>
      <div>
        <button @click="switchPage('map')">Map</button>
        <button @click="switchPage('mission')">Mission</button>
        <button @click="switchPage('settings')">Settings</button>
      </div>
      <img src="src/assets/mission_board.jpg" alt="MB" />
      <p>This is the Mission page.</p>
    </div>

    <!-- Settings Page -->
    <div v-else-if="currentPage === 'settings'">
      <h1>Settings Page</h1>
      <div>
        <logout-button @click="switchPage('logout')">Logout</logout-button>
      </div>
      <div>
        <button @click="switchPage('map')">Map</button>
        <button @click="switchPage('mission')">Mission</button>
        <button @click="switchPage('settings')">Settings</button>
      </div>
      <img src="src/assets/settings.jpg" alt="Settings" />
      <p>This is the Settings page.</p>
    </div>
  </div>
  <footer>
    <p>T.R.E Productions</p>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      currentPage: 'login',
      username: '',
      password: '',
      currentTab: 'MapTab',
    };
  },
  methods: {
    login() {
      // Perform login logic here
      // If successful, switch to the map page
      this.currentPage = 'map';
    },
    switchPage(page) {
      // Switch to the selected page
      switch (page) {
        case 'map':
          this.currentPage = 'map';
          this.currentTab = 'MapTab';
          break;
        case 'mission':
          this.currentPage = 'mission';
          break;
        case 'settings':
          this.currentPage = 'settings';
          break;
        case 'logout':
          this.currentPage = 'login';
          break;
      }
    },
  },
  components: {
    MapTab: {
      template: `
        <div>
          <h2>Map Tab</h2>
          <p>This is the Map tab.</p>
        </div>
      `,
    },
  },
};
</script>
