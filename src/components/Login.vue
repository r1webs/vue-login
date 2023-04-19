<script setup>
import { ref, onMounted } from 'vue';

const username = ref('');
const password = ref('');
const params = ref('');
onMounted(() => {
  if (window.location.search) {
    params.value = new URLSearchParams(window.location.search).toString()
  }
})

function updateUsername(event) {
  username.value = event.target.value;
}

function updatePassword(event) {
  password.value = event.target.value;
}

async function onSubmit() {
    window.location.href = `postlogin.html?code=${window.crypto.randomUUID()}&${params.value}`;
}
</script>

<template>
    <div class="card m-3">
        <h4 class="card-header">Login</h4>
        <div class="card-body">
                <div class="form-group">
                    <label>Username</label>
                    <input name="username" type="text" class="form-control" :value="username" @change="updateUsername" />
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input name="password" type="password" class="form-control" :value="password" @change="updatePassword"/>
                </div>
                <div class="form-group">
                    <button class="btn btn-primary" @click="onSubmit">
                        Login
                    </button>
                </div>
        </div>
    </div>
</template>
