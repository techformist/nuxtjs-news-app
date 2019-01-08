<template>
  <div>
    <v-container>
      <v-flex xs12 pb-5>
        <h2>News</h2>
      </v-flex>

      <v-flex>
        <!-- News !-->
        <v-flex xs12 pb-3 sm6 offset-sm3 v-for="(article, index) in articles" :key="index">
          <v-card>
            <img :src="article.urlToImage" width="100%" height="200px">

            <v-card-title primary-title>
              <div>
                <div class="headline">{{article.title}}</div>
              </div>
            </v-card-title>

            <v-card-text>{{article.content}}</v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn flat :href="article.url" target="_blank">Open</v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      "https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=dbccf410f7cc4a22a178086ed6cffc83"
    );
    return { articles };
  }
};
</script>
