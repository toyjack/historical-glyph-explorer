<script setup lang="ts">
const route = useRoute()
const selected = ref("")

selected.value = route.params.source as string || ""

function changeSelected() {
  return navigateTo({
    path: '/list/' + selected.value,
  })
}
</script>

<template>
  <div class="container mx-auto">
    <div class="form-control w-full max-w-xs p-1 md:p-3">
      <label class="label">
        <span class="label-text">表示する内容</span>
      </label>
      <select class="select select-primary max-w-xs" v-model="selected" @change="changeSelected()">
        <option disabled selected value=''>APIソースを選ぶ</option>
        <option value="hng">HNG</option>
        <option value="uthi">電子くずし字字典</option>
        <option value="nijil">国文研字形検索β</option>
      </select>
    </div>

    <NuxtPage />
  </div>
</template>