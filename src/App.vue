<template>
	<div class="container">
		<form>
			<div class="row">
				<div class="col-md-8 col-md-offset-2">
					<h1>Application Form</h1>
					<hr>
					<div class="form-group">
						<label for="email">Mail</label>
						<input type="text" id="email" name="" class="form-control" v-model="userData.email">
					</div>
					<div class="form-group">
						<label for="password">Password</label>
						<input type="password" id="password" class="form-control" v-model="userData.password">
					</div>
					<div class="form-group">
						<label for="age">Age</label>
						<input type="number" id="age" class="form-control" v-model="userData.age">
					</div>
					<div class="form-group">
						<label for="age">Message</label>
						<textarea id="message" rows="5" class="form-control" v-model="userData.message">
							
						</textarea>
					</div>
					<div class="row">
						<div class="col-md-12">
							<div class="form-group">
								<label for="sendmail">
									<input type="checkbox" id="sendmail" value="SendEmail" name="" v-model="sendMail">
								Send mail </label>
						 
								<label for="sendinfomail">
								<input type="checkbox" id="sendinfomail" value="SendInfoEmail" name="" v-model="sendMail">
								Send infomail </label>
							</div>
						</div>
					</div>

					<div class="row">
						<div class="col-md-12">
							<div class="form-group">
								<label for="sendmail">
									<input type="radio" id="male" value="Male" name="" v-model="gender">
								Male </label>
						 
								<label for="sendinfomail">
									<input type="radio" id="female" value="Female" name="" v-model="gender">
								Female </label>
							</div>
						</div>
					</div>

					<div class="row">
						<div class="col-md-12">
							<div class="form-group">
								<label for="priority"> priority </label>
								<select 
									id="priority" 
									class="form-control"
									v-model="selectedPriority">
									<option v-for="priority in priorities"> {{ priority }}</option>
								</select>
							</div>
						</div>
					</div>

					<div class="row">
						<div class="col-md-12">
							<button @click.prevent="submitted" class="btn btn-primary">Submit</button>
						</div>
					</div>

				</div>
			</div>
		</form>
		<hr>
		<div class="row" v-if="isSubmitted">
			<div class="col-md-8 col-md-offset-2">
				<div class="panel panel-default">
					<div class="panel-heading">
						<h4>Your data</h4>
					</div>
					<div class="panel-body">
						<p>Mail: {{ userData.email }}</p>
						<p>Password: {{ userData.password }}</p>
						<p>Age: {{ userData.age }}</p>
						<p style="white-space: pre">Message: {{ userData.message }}</p>
						<p><strong>Send mail</strong></p>
						<ul>
							<li v-for="item in sendMail"> {{ item }}</li>
						</ul>
						<p>Gender: {{ gender }}</p>
						<p>Priority: {{ selectedPriority }}</p>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				userData: {
					email: '',
					password: '',
					age: '',
					message: '',
				},
				sendMail: [],
				gender: 'Male',
				selectedPriority: 'Medium',
				priorities: ['High', 'Medium', 'Low'],
				isSubmitted: false
			}
		},
		methods: {
			submitted() {
				this.isSubmitted = true;
			}
		}  
	}
</script>

<style scoped>

</style>
