<template>
  <div>
    <h3>{{ title }}</h3>
    <div class="productContainer">
      <div class="product" v-for="(product, i) in data" :key="i">
        <RouterLink :to="`/details/${product.id}`">
          <div>
            {{  product.title  }}
          </div>
        </RouterLink>
        <div>{{ product.description }}</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const data = await fetch('https://dummyjson.com/products')
                .then(res => res.json())
                .then(data => data.products)

const title = 'Example E-Commerce Website'
const description = 'Just a simple SEO example'
const image = 'https://cdn.oddinpay.com/og.webp'

useServerSeoMeta({
  description,
  title,
  ogTitle: title,
  ogDescription: description,
  ogImage: image,
  ogImageUrl: image,
  twitterCard: 'summary_large_image',
  
})
</script>

<style>
.product {
  margin-bottom: 20px;
  padding: 10px;
  background-color: antiquewhite;
}
</style>
