<template>
  <v-container>
        <v-row>
          <v-col
            v-for="film in filmovi"
            :key="film.display_title"
            cols="4"
          >
            <v-card height="200"><h2>{{film.display_title}}</h2></v-card>
          </v-col>
        </v-row>
      </v-container>
</template>

<script>


export default {
  name: 'HomeView',

  data(){
    return{
      filmovi:[],
      page:1,
    }
  },
  created(){
    console.log('created')
    this.getData();
  },
  methods:{
    getData(){
      let api="https://api.nytimes.com/svc/movies/v2/reviews/search.json"
      this.axios.get(api,{
        params:{
          'api-key':'74KMMSifsWPAWcgO1PV826Ac0p31SUfy'
        }
      }).then((response) => {
      console.log(response.data)
      this.filmovi=response.data.results
      })
    }
  }
  
}
</script>
