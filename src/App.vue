<template>
	<a-locale-provider :locale="zh_CN">
		<div id="app">
			<div>
				<a-form :form="form">

					<a-form-item label="加了placeholder" :labelCol="labelCol" :wrapperCol="wrapperCol">
						<a-input placeholder="请输入用户账号" v-decorator="[ 'username', validatorRules.username]" />
					</a-form-item>


					<a-form-item label="加了prefix,suffix" :labelCol="labelCol" :wrapperCol="wrapperCol">
						<a-input type="password" placeholder="请输入登录密码" v-decorator="[ 'password', validatorRules.password]">
							<a-icon slot="prefix" type="user" />
							<a-tooltip slot="suffix" title="Extra information">
								<a-icon type="info-circle" style="color: rgba(0,0,0,.45)" />
							</a-tooltip>
						</a-input>
						当加了prefix,从上面个Input按tab键切换下来需要按两次，
						加了suffix从这个Input按tab键切换到下个input需要按两次
					</a-form-item>
					<a-form-item label="Note" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
						<a-input v-decorator="['note', { rules: [{ required: true, message: 'Please input your note!' }] }]" />
					</a-form-item>





				</a-form>
			</div>
		</div>
	</a-locale-provider>
</template>

<script>
	import zh_CN from 'ant-design-vue/lib/locale-provider/zh_CN'

	export default {
		name: 'app',
		data() {
			return {
				zh_CN,
				labelCol: {
					xs: {
						span: 24
					},
					sm: {
						span: 5
					}
				},
				wrapperCol: {
					xs: {
						span: 24
					},
					sm: {
						span: 16
					}
				},
				form: this.$form.createForm(this),
				validatorRules: {
					username: {
						rules: [{
							required: true,
							message: '请输入用户账号!'
						}, {
							validator: this.validateUsername,
						}]
					},
					password: {
						rules: [{
							required: true,
							message: '请输入密码!'
						}]
					}

				}
			}
		},
		components: {}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
