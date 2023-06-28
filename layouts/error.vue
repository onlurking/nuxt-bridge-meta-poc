<template>
    <div id="ErrorView" class="d-flex justify-center">
      Fehlercode {{ error.statusCode }}
      Ö OE Ä AE Ü UE ä ae ö oe ü ue
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import { NuxtError } from '@nuxt/types'

export default defineComponent({
    name: 'ErrorView',
    props: { error: { required: true, type: Object as PropType<NuxtError> } },
    setup(props) {
        return {
            getText: () => {
                let text

                switch (props.error.statusCode) {
                    case 404:
                        text = 'Diese Seite existiert nicht.'
                        break
                    case 500:
                        text = 'Ein unbekannter Serverfehler trat auf.'
                        break
                    default:
                        text = 'Ein unbekannter Fehler trat auf.'
                }

                return text
            },
        }
    },
})
</script>

<style lang="scss" scoped />
