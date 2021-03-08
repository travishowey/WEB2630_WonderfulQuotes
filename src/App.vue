<template>
  <div class="container">
    <app-header :quote-count="quotes.length" :max-quotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <br>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <br>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import QuoteGrid from './components/QuoteGrid'
import NewQuote from './components/NewQuote'

export default {
  data () {
    return {
      quotes: [
        "One string by default"
      ],
      maxQuotes: 10
    }
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Delete a quote")
      }
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  },
  components: {
    'app-quote-grid': QuoteGrid,
    'app-new-quote': NewQuote,
    'app-header': Header,
  }

}
</script>

<style></style>
