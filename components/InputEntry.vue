<script setup lang="ts">
// import { useTypedRouter } from '~/generated/typed-router'

const { router, routes } = useTypedRouter()
const name = ref('')

const go = (): void => {
  if (name.value) {
    void router.push({
      name: routes.hiId,
      params: { id: encodeURIComponent(name.value as string) },
    })
  }
}
</script>

<template>
  <div>
    <input
      id="input"
      v-model="name"
      :placeholder="$t('input-name')"
      type="text"
      autocomplete="off"
      p="x-4 y-2"
      m="t-5"
      w="250px"
      text="center"
      bg="transparent"
      border="~ rounded gray-200 dark:gray-700"
      outline="none active:none"
      @keydown.enter="go"
    />
    <div>
      <button m-3 text-sm btn :disabled="!name" @click="go">
        {{ $t('go') }}
      </button>
    </div>
  </div>
</template>
