<template>
  <v-app
    :dark="dark"
  >

    <v-toolbar
      :clipped-left="clipped"
      fixed
      dense
      app
    >
      <v-toolbar-side-icon @click="drawer = !drawer" />
      <v-toolbar-title v-text="'cheat-sheeter'" />
      <v-spacer />
      <v-btn
        @click.stop="dark = !dark"
        icon
      >
        <v-icon>brightness_3</v-icon>
      </v-btn>
      <v-menu offset-y>
          <template v-slot:activator="{ on }">
            <v-btn
              v-on="on"
              flat
            >
              <v-icon>translate</v-icon>
            </v-btn>
          </template>
        <v-list>
          <v-list-tile
            v-for="lang in laguages"
            :key="lang.title"
            :to="lang.to"
          >
            <v-list-tile-title>{{ lang.title }}</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>
    </v-toolbar>

    <v-navigation-drawer
      v-model="drawer"
      :clipped=true
      fixed
      app
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <nuxt />
    </v-content>

    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      dark: false,
      drawer: false,
      items: [
        {
          icon: 'apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'bubble_chart',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      laguages: [
        {
          title: 'English',
          to: 'en'
        },
        {
          title: '日本語',
          to: 'ja'
        }
      ]
    }
  }
}
</script>
