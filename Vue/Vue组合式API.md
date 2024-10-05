## 概述

> - 组合式 API 是 Vue 3 引入的一种全新方式，用于构建组件，旨在提高代码的可重用性和可读性。
> - 通过组合式 API，开发者可以在一个函数中定义响应式状态、计算属性和生命周期钩子，便于逻辑的组织和复用。



## 核心概念



### setup函数

> - 组合式 API 的入口，在组件实例化之前执行，返回的对象会成为组件的响应式状态。



### 响应式状态

> - 使用 `ref` 和 `reactive` 创建响应式数据。

```javascript
import { ref, reactive } from 'vue';

setup() {
  const count = ref(0);
  const state = reactive({ message: 'Hello' });
  return { count, state };
}

```

### 计算属性

> - 使用 `computed` 创建基于响应式状态的计算属性。

```javascript
import { computed } from 'vue';

setup() {
  const count = ref(0);
  const doubleCount = computed(() => count.value * 2);
  return { count, doubleCount };
}

```

### 生命周期钩子

> - 使用 `onMounted`、`onUpdated` 等函数来定义生命周期钩子。

```javascript
import { onMounted } from 'vue';

setup() {
  onMounted(() => {
    console.log('Component is mounted');
  });
}

```

### 示例

```javascript
<template>
  <div>
    <p>{{ state.message }}: {{ count }}</p>
    <button @click="count++">Increment</button>
    <p>Double: {{ doubleCount }}</p>
  </div>
</template>

<script>
import { ref, reactive, computed, onMounted } from 'vue';

export default {
  setup() {
    const count = ref(0);
    const state = reactive({ message: 'Hello' });
    const doubleCount = computed(() => count.value * 2);

    onMounted(() => {
      console.log('Component is mounted');
    });

    return { count, state, doubleCount };
  },
};
</script>

```



































