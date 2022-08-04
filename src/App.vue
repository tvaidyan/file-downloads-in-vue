<script setup>
import axios from 'axios';

async function downloadFile() {
  const http = axios.create({
    baseURL: 'https://dummyimage.com/600x400/000/fff',
    timeout: 10000,
    responseType: 'blob'
  });

  let responseFile = await http.get();

  const blob = new Blob([responseFile.data]);
  const url = window.URL.createObjectURL(blob);
  var docUrl = document.createElement('a');
  docUrl.href = url;
  docUrl.setAttribute(
    'download',
    'example.png'
  );
  document.body.appendChild(docUrl);
  docUrl.click();
}
</script>

<template>
  <div>
    <h3>File Download Demo</h3>
    <button @click="downloadFile()">Download File</button>
  </div>
</template>
