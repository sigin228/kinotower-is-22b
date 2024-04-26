<script lang="ts" setup>
const filmsStore = useFilmsStore();
const categoriesStore = useCategoriesStore();
const countriesStore = useCountriesStore();

filmsStore.fetchFilms();
categoriesStore.fetchCategories();
countriesStore.fetchCountries();
</script>

<template>
  <div class="row mb-4">
    <div class="col-md-4">
      <select class="form-select" aria-label="Default select example">
        <option selected :value="null">Select genre...</option>
        <option v-for="category in categoriesStore.categories" :key="category.id" :value="category.id">{{ category.name }}</option>
      </select>
    </div>
    <div class="col-md-4">
      <select class="form-select" aria-label="Default select example">
        <option selected :value="null">Select genre...</option>
        <option v-for="country in countriesStore.countries" :key="country.id" :value="country.id">{{ country.name }}</option>
      </select>
    </div>
    <div class="col-md-3">
      <select class="form-select" aria-label="Default select example">
        <option value="1">name</option>
        <option value="2">year</option>
        <option value="3">reting</option>
      </select>
    </div>
    <div class="col-md-1">
      <button class="btn btn-warning">Reset</button>
    </div>
  </div>
    <div class="row row-cols-1 row-cols-md-3 g-4">
  <div class="col" v-for="film in filmsStore.films" :key="filmsStore.id">
    <div class="card h-100">
      <img :src="film.link_img" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ film.name }}</h5>
        <p class="card-text">Rating:{{ Number(film.ratingAvg).toFixed(1) }}</p>
        <p class="card-text">{{ film.duration }}</p>
        <p class="card-text">{{ film.name }}</p>
        <p class="card-text">
  <template v-for="(category, index) in film.categories" :key="category.id">
    {{ category.name }}
    <span v-if="index < film.categories.length - 1">,</span>
  </template>
</p>


      </div>
      <div class="card-footer">
        <small class="text-body-secondary"><button type="button" class="btn btn-primary">Primary</button>
</small>      </div>
    </div>
  </div>
  

</div>

<nav class="mt-3 d-flex justify-content-center" aria-label="Page navigation example">
  <ul class="pagination">
    <li class="page-item">
      <a class="page-link" href="#" aria-label="Previous">
        <span aria-hidden="true">&laquo;</span>
      </a>
    </li>
    <li class="page-item"><a class="page-link" href="#">1</a></li>
    <li class="page-item"><a class="page-link" href="#">2</a></li>
    <li class="page-item"><a class="page-link" href="#">3</a></li>
    <li class="page-item">
      <a class="page-link" href="#" aria-label="Next">
        <span aria-hidden="true">&raquo;</span>
      </a>
    </li>
  </ul>
</nav>
  
</template>


<style></style>