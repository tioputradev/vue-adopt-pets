<template>
  <div>
    <h1>{{ animal.name }} ({{ $route.params.species}})</h1>
    <p>Age : {{animal.age}}</p>
    <p>Breed : {{animal.breed}}</p>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  data() {
    return {
      animal: {}
    };
  },
  computed: {
    ...mapState(["cats", "dogs"])
  },
  mounted() {
    const animal = this[this.$route.params.species][this.$route.params.id];
    return (this.animal = animal);
  }
};
</script>