<template>
<div class="container-fluid" style="padding-top:100px;">
        <div class="col-sm-6 col-md-4 col-md-offset-4">
            <h1 class="text-center text-primary login-title">Enter your email address</h1>
            <div class="account-wall">
                <form class="form-signin">
                <input type="email" class="form-control" placeholder="Email" id="email" v-model="form.email" required autofocus>
                <br/>
                <button class="btn btn-lg btn-success btn-block" type="button" @click="login()">

                    Request reset</button>

                </form>
            </div>
        </div>
    </div>

</template>

<script>
import firebase from 'firebase'

export default {
  data () {
    return {
      btcbalance: 0,
      ltcbalance: 0,
      form: {
        email: '',
        walletaddress: '',
        prefferedcoin: 'btc',
        amount: 0
      },
      error: null
    }
  },
  methods: {
    ToRegister () {
      this.$router.push('/register')
    },
    login: function () {
      firebase.auth().sendPasswordResetEmail(this.form.email)
      this.$vs.notify({title: 'Password reset Successfully', text: 'A password reset link has been sent to your email address', color: 'red', position: 'top-center'})
    }
  }
}
</script>
<style scoped>
.form-signin
{
    max-width: 330px;
    padding: 15px;
    margin: 0 auto;
}
.form-signin .form-signin-heading, .form-signin .checkbox
{
    margin-bottom: 10px;
}
.form-signin .checkbox
{
    font-weight: normal;
}
.form-signin .form-control
{
    position: relative;
    font-size: 16px;
    height: auto;
    padding: 10px;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}
.form-signin .form-control:focus
{
    z-index: 2;
}
.form-signin input[type="text"]
{
    margin-bottom: -1px;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
}
.form-signin input[type="password"]
{
    margin-bottom: 10px;
    border-top-left-radius: 0;
    border-top-right-radius: 0;
}
.account-wall
{
    margin-top: 20px;
    padding: 40px 0px 20px 0px;
    background-color: #f7f7f7;
    -moz-box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
    -webkit-box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
    box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
}
.login-title
{
    color: #555;
    font-size: 18px;
    font-weight: 400;
    display: block;
}
.profile-img
{
    width: 96px;
    height: 96px;
    margin: 0 auto 10px;
    display: block;
    -moz-border-radius: 50%;
    -webkit-border-radius: 50%;
    border-radius: 50%;
}
.need-help
{
    margin-top: 10px;
}
.new-account
{
    display: block;
    margin-top: 10px;
}

</style>
