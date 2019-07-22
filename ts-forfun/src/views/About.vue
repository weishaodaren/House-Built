<template>
<div>
  <v-card
    class="hide-overflow"
    height="200px"
  >
    <v-card-text class="text-xs-center">
      <v-btn
        flat
        color="#126"
        @click="showNav = !showNav"
      >
        Toggle Nav
      </v-btn>
    </v-card-text>

    <v-bottom-nav
      :active.sync="activeBtn"
      :value="showNav"
      absolute
      color="transparent"
    >
      <v-btn flat color="teal">
        <span>Recents</span>
        <v-icon>history</v-icon>
      </v-btn>

      <v-btn flat color="orange">
        <span>Favorites</span>
        <v-icon>favorite</v-icon>
      </v-btn>

      <v-btn flat color="purple">
        <span>Nearby</span>
        <v-icon>place</v-icon>
      </v-btn>
    </v-bottom-nav>
  </v-card>
<!--  -->
  <v-layout justify-center>
    <v-flex xs12 sm6>
      <v-toolbar color="indigo" dark>
        <v-toolbar-side-icon></v-toolbar-side-icon>
        <v-toolbar-title>Discover</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn icon>
          <v-icon>search</v-icon>
        </v-btn>
      </v-toolbar>

      <v-card>
        <v-container
          fluid
          grid-list-md
        >
          <v-layout row wrap>
            <v-flex
              v-for="card in cards"
              :key="card.title"
              v-bind="{ [`xs${card.flex}`]: true }"
            >
              <v-card>
                <v-img
                  :src="card.src"
                  height="200px"
                >
                  <v-container
                    fill-height
                    fluid
                    pa-2
                  >
                    <v-layout fill-height>
                      <v-flex xs12 align-end flexbox>
                        <span class="headline white--text" v-text="card.title"></span>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-img>

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn icon>
                    <v-icon>favorite</v-icon>
                  </v-btn>
                  <v-btn icon>
                    <v-icon>bookmark</v-icon>
                  </v-btn>
                  <v-btn icon>
                    <v-icon>share</v-icon>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card>
    </v-flex>
  </v-layout>
  <!--  -->
  <v-footer
    dark
    height="auto"
  >
    <v-card
      flat
      tile
      class="indigo lighten-1 white--text text-xs-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-3 white--text"
          icon
        >
          <v-icon size="24px">{{ icon }}</v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text pt-0">
        Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        &copy;2018 — <strong>Vuetify</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</div>
</template>

<script lang="ts">
import {Component ,Vue, Provide} from 'vue-property-decorator'

@Component
export default class About extends Vue{
  @Provide() activeBtn: Number=1
  @Provide() showNav: Boolean=true
  @Provide() cards: Array<any>=[
        { title: 'Pre-fab homes', src: 'https://cdn.vuetifyjs.com/images/cards/house.jpg', flex: 12 },
        { title: 'Favorite road trips', src: 'https://cdn.vuetifyjs.com/images/cards/road.jpg', flex: 6 },
        { title: 'Best airlines', src: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg', flex: 6 }
  ]
  @Provide() icons: Array<String>=[
        'fab fa-facebook',
        'fab fa-twitter',
        'fab fa-google-plus',
        'fab fa-linkedin',
        'fab fa-instagram'
  ]
}


</script>
<style lang="scss" scoped>
 i{
   font-style: normal
 }
</style>

