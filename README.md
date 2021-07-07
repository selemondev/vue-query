[![Vue Query logo](./media/vue-query.png)](https://damianosipiuk.github.io/vue-query/)

[![npm version](https://img.shields.io/npm/v/vue-query)](https://www.npmjs.com/package/vue-query)
[![npm license](https://img.shields.io/npm/l/vue-query)](https://github.com/DamianOsipiuk/vue-query/blob/main/LICENSE)
[![bundle size](https://img.shields.io/bundlephobia/minzip/vue-query)](https://bundlephobia.com/result?p=vue-query)
[![npm](https://img.shields.io/npm/dm/vue-query)](https://www.npmjs.com/package/vue-query)

[![build status](https://img.shields.io/github/workflow/status/DamianOsipiuk/vue-query/CI/main)](https://github.com/DamianOsipiuk/vue-query/actions/workflows/ci.yml?query=branch%3Amain)
[![codecov](https://codecov.io/gh/DamianOsipiuk/vue-query/branch/main/graph/badge.svg?token=X8FK0O5CTG)](https://codecov.io/gh/DamianOsipiuk/vue-query)

# Vue Query

Hooks for fetching, caching and updating asynchronous data in Vue.

Support for Vue 2.x via [vue-demi](https://github.com/vueuse/vue-demi)

Based on [react-query](https://github.com/tannerlinsley/react-query)

# Documentation

Visit https://vue-query.vercel.app

# Quick Features

- Transport/protocol/backend agnostic data fetching (REST, GraphQL, promises, whatever!)
- Auto Caching + Refetching (stale-while-revalidate, Window Refocus, Polling/Realtime)
- Parallel + Dependent Queries
- Mutations + Reactive Query Refetching
- Multi-layer Cache + Automatic Garbage Collection
- Paginated + Cursor-based Queries
- Load-More + Infinite Scroll Queries w/ Scroll Recovery
- Request Cancellation
- (experimental) [Suspense](https://v3.vuejs.org/guide/migration/suspense.html#introduction) + Fetch-As-You-Render Query Prefetching
- (experimental) SSR support
- Dedicated Devtools
- [![npm bundle size](https://img.shields.io/bundlephobia/minzip/vue-query)](https://bundlephobia.com/result?p=vue-query) (depending on features imported)

# Quick Start

1. Attach **Vue Query** to the root component of your Vue application

   ```ts
   import { defineComponent } from "vue";
   import { useQueryProvider } from "vue-query";

   export default defineComponent({
     name: "App",
     setup() {
       useQueryProvider();
     },
   });
   ```

2. Use query

   ```ts
   import { defineComponent } from "vue";
   import { useQuery } from "vue-query";

   export default defineComponent({
     name: "MyComponent",
     setup() {
       const query = useQuery("todos", getTodos);

       return {
         query,
       };
     },
   });
   ```

3. If you need to update options on your query dynamically, make sure to pass it as reactive property

   ```ts
   const id = ref(1);
   const queryKey = reactive(["todos", { id }]);
   const queryFunction = () => getTodos(id);
   const options = reactive({
     enabled: false,
   });

   const query = useQuery(queryKey, queryFunction, options);
   ```
