<template>
    <div>
        <form>
        <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label">Email address</label>
            <input v-model="data.email" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
        </div>
        <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label">Password</label>
            <input v-model="data.password" type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3 form-check">
            <input type="checkbox" class="form-check-input" id="exampleCheck1">
            <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary" @click.prevent="methods.login">Submit</button>
        </form>
    </div>
</template>

<script setup>
import { ref } from "vue";
import { authStore } from '../stores/auth'

const auth = authStore();

const data = ref({
    email: ref(null),
    password: ref(null)
})

const methods = {
    login: async () => {
        console.log(data.value);

        await auth.login(data.value.email, data.value.password).then((response) => {
            console.log(response);
        }).catch((err) => {
            console.log(err);
        })
    }
}

</script>