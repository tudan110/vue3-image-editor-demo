<script setup>
import 'tui-color-picker/dist/tui-color-picker.css';
import 'tui-image-editor/dist/tui-image-editor.css';
import TuiImageEditor from '@tudan110/vue3-image-editor';
import {localeZh, myTheme} from './editor-config'

import {ref} from 'vue';

// 控制是否使用默认 UI
const useDefaultUI = ref(true);

// 配置选项
const options = {
  includeUI: {
    loadImage: {
      path: new URL("/src/assets/test.png", import.meta.url).href, //图片地址,
      name: 'image'
    },
    menu: ['resize', 'crop', 'rotate', 'draw', 'shape', 'icon', 'text', 'filter'], // 底部菜单按钮列表 隐藏镜像flip和遮罩mask
    initMenu: 'draw', // 默认打开的菜单项
    menuBarPosition: 'bottom', // 菜单所在的位置
    locale: localeZh, // 本地化语言为中文
    theme: myTheme // 自定义样式
  },
  cssMaxWidth: 700, // canvas 最大宽度
  cssMaxHeight: 500 // canvas 最大高度
};
</script>

<template>
  <div class="editor">
    <tui-image-editor
        :use-default-ui="useDefaultUI"
        :options="options"
    />
  </div>
</template>

<style scoped>
.editor {
  width: 100vh;
  height: 80vh;
}
</style>
