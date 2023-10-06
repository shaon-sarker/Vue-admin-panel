<template>
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <div class="card">
            <div class="card-body">
              <div>
                <input placeholder="Search..." class="form-control mb-2 w-auto form-control-sm" type="text" v-model="searchValue">
                <EasyDataTable buttons-pagination alternating :headers="Header" :items="Item" :rows-per-page="10" :search-field="searchField"  :search-value="searchValue">
                    
                  <template #item-image="{image}">
                    <img :src="image" alt="" style="width: 100px;">
                  </template>
                  <template #item-number="{ number,productname,price }">
                    <button class="btn btn-info btn-sm" @click="itemClick(number,productname,price)">View Details</button>
                  </template>
                </EasyDataTable>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script setup>

import {ref} from "vue";


const searchField = ["productname","price","stock"];
const searchValue = ref();


const Header = [
  { text: "Product Name", value: "productname" },
  { text: "Unit Price", value: "price"},
  { text: "Number of Items", value: "stock"},
  { text: "Product Image", value: "image"},
  { text: "Product Details", value: "number"},
];

const Item = ref([
  { productname: "iPhone 9", price: "549", number: 1, stock: '94', image:'https://i.dummyjson.com/data/products/1/thumbnail.jpg'},
  { productname: "iPhone 9", price: "549", number: 2, stock: '94', image:'https://i.dummyjson.com/data/products/2/thumbnail.jpg'},
  
  { productname: "Samsung Universe 9", price: "12549", number: 3, stock: '36', image: 'https://i.dummyjson.com/data/products/3/thumbnail.jpg'},
  { productname: "OPPOF19", price: "280", number: 4, stock: '123', image: 'https://i.dummyjson.com/data/products/4/thumbnail.jpg'},
  { productname: "Huawei P30", price: "4549", number: 5, stock: '32', image: 'https://i.dummyjson.com/data/products/5/thumbnail.jpg'},
  { productname: "MacBook Pro", price: "1549", number: 6, stock: '83', image: 'https://i.dummyjson.com/data/products/6/1.png'},
  { productname: "Samsung Galaxy Book", price: "3549", number: 7, stock: '56', image: 'https://i.dummyjson.com/data/products/7/thumbnail.jpg'},
  { productname: "Microsoft Surface Laptop 4", price: "1549", number: 8, stock: '454', image: 'https://i.dummyjson.com/data/products/8/thumbnail.jpg'},
])


const itemClick = (number,productname,price) => {
  alert(`Product Id is=${number} & Product Name is=${productname} & Price =${price}`)
}
</script>
