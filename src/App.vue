<script lang="ts">
import { applyReactInVue } from "veaury";
import { StiggProvider, Paywall } from "@stigg/react-sdk";
import type { Plan } from "@stigg/js-client-sdk";

export default {
  components: {
    StiggProvider: applyReactInVue(StiggProvider),
    Paywall: applyReactInVue(Paywall),
  },
  methods: {
    onPlanSelected: ({ plan }: { plan: Plan }) => {
      console.log(`Selected plan: ${plan.displayName}`);
    },
  },
  setup() {
    return {
      apiKey:
        "YOUR-CLIENT-API-KEY",
      theme: {
        layout: {
          planMinWidth: "320px",
        },
      },
    };
  },
};
</script>

<template>
  <StiggProvider :apiKey="apiKey" :theme="theme">
    <Paywall :onPlanSelected="onPlanSelected" />
  </StiggProvider>
</template>
