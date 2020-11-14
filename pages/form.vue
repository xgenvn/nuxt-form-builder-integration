<template>
  <div>
    <form-builder :form="form" :config="formConfig"></form-builder>
  </div>
</template>

<script>
import { useForm } from '@fext/vue-use'
import { FormBuilder } from '@fext/vue-form-builder'

export default {
  name: 'AwesomeForm',

  components: {
    FormBuilder,
  },

  setup() {
    // Form Composition API
    const form = useForm()
    const { formValues, updateFormValues } = form

    return {
      form,

      /* 表单数据模型 */
      formValues,

      /* 手动更新表单数据模型 */
      updateFormValues,
    }
  },

  data() {
    return {
      formConfig: [
        {
          component: 'el-card',
          props: {
            header: 'Basic Group',
          },
          fields: [
            {
              name: 'comment',
              component: 'ElFormAdaptor',
              label: 'Description',
              rules: {
                required: true,
              },
              props: {
                type: 'textarea',
                rows: 5,
                placeholder:
                  'Use adaptor and render with default(el-input) component',
              },
            },
          ],
        },
      ],
    }
  },
}
</script>
