
<template>
  <!--
  <div id="buffet">
    <h3>Buffet Name: {{ buffet.description }}</h3>
    <p>Location: {{buffet.location}}</p>
    <p>Is food halal: {{buffet.halal}}</p>
    <p>Amount of food left (0-1): {{buffet.foodremaining}}</p>
    <p>Buffet still available: {{buffet.open}}</p>

    <p>Clearing time: {{buffet.time.toLocaleString()}}</p>

  </div>
  -->

      <div id="buffet">
        <!--Panel-->
        <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
          <div class="card" style="max-width: 500px; max-height: 690px;">
            <div class="card-header deep-orange lighten-1 white-text" style="padding-left: 7px;
            padding-right: 5px;">

            <h1 class="text-center" style="font-family: lobster, monospace;">Buffet @ {{buffet.location}},<br>
               {{this.toDateDisplayString(buffet.time)}}</h1>
          </div>
          <div class="card-body" style="padding: 10px 10px 10px 10px;">
            <p class="card-title" style="font-family: raleway, monospace;">Description: {{ buffet.description }}</p>
            <p style="font-family: raleway, monospace;">Food Halal? {{this.tfConverter(buffet.halal)}}</p>
            <p style="font-family: raleway, monospace;">Cultery Available? {{this.tfConverter(buffet.cutlery)}}</p>
            <p style="font-family: raleway, monospace;">Amount of food left: {{buffet.foodremaining}}%</p>
            <p style="font-family: raleway, monospace;">Buffet still available: {{this.tfConverter(buffet.open)}}</p>
            <p style="font-family: raleway, monospace;">Clearing time: {{this.toDateDisplayString(buffet.expirytiming)}}</p>
            <button v-on:click="deleteBuffet">Delete</button>
          </div>
        </div>
      </div>
      <!--/.Panel-->

    </div>   <!-- End buffet -->



</template>



<script>
import db from "./datab";

export default {
  name: "buffet-detail",
  props: ["buffet", "buffetId", "displayDate"],
  methods: {
    tfConverter(bool) {
      return bool ? "✔" : "✖";
    },
    toDateDisplayString(date) {
      return this.displayDate
        ? date.toLocaleString()
        : date.toLocaleTimeString();
    },
    deleteBuffet() {
      db
        .collection("Buffets")
        .doc(this.buffetId)
        .delete();
    }
  }
};
</script>
