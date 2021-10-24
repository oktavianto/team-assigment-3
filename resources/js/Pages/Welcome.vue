<template>
    <Head title="Perhitungan Nilai" />

    <div class="min-h-screen bg-no-repeat bg-cover bg-center" style="background-image: url('https://images.unsplash.com/photo-1486520299386-6d106b22014b?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80')">
        <div class="flex justify-end">
            <div class="bg-white min-h-screen w-1/2 flex justify-center items-center">
                <!-- Jika Belum Mempunyai Hasil -->
                <div class="w-3/4" v-if="!result">
                    <div>
                        <span class="text-sm text-gray-900">Tugas Kelompok 3 - Team 4</span>
                        <h1 class="text-2xl font-bold">Perhitungan nilai</h1>
                    </div>
                    <div class="mt-3">
                        <label class="block text-md mb-2" for="quis">Quis</label>
                        <input class="px-4 w-full border-2 py-2 rounded-md text-sm outline-none" type="number" min="0" max="100" v-model="quis" name="quis" placeholder="Quis">
                    </div>
                    <div class="mt-2">
                        <label class="block text-md mb-2" for="tugas">Tugas</label>
                        <input class="px-4 w-full border-2 py-2 rounded-md text-sm outline-none" type="number" min="0" max="100" v-model="tugas" name="tugas" placeholder="Tugas">
                    </div>
                    <div class="mt-2">
                        <label class="block text-md mb-2" for="absensi">Absensi</label>
                        <input class="px-4 w-full border-2 py-2 rounded-md text-sm outline-none" type="number" min="0" max="100" v-model="absensi" name="absensi" placeholder="Absensi">
                    </div>
                    <div class="mt-2">
                        <label class="block text-md mb-2" for="praktek">Praktek</label>
                        <input class="px-4 w-full border-2 py-2 rounded-md text-sm outline-none" type="number" min="0" max="100" v-model="praktek" name="praktek" placeholder="Praktek">
                    </div>
                    <div class="mt-2">
                        <label class="block text-md mb-2" for="uas">UAS</label>
                        <input class="px-4 w-full border-2 py-2 rounded-md text-sm outline-none" type="number" min="0" max="100" v-model="uas" name="uas" placeholder="UAS">
                    </div>
                    <div class="mt-2">
                        <button class="mt-4 mb-3 w-full bg-green-500 hover:bg-green-400 text-white py-2 rounded-md transition duration-100" @click="hitung">Hitung</button>
                    </div>
                </div>
                <!-- Jika Sudah Mempunyai Hasil -->
                <div class="w-3/4" v-else>
                    <div>
                        <span class="text-sm text-gray-900">Tugas Kelompok 3 - Team 4</span>
                        <h1 class="text-2xl font-bold">Perhitungan nilai</h1>
                    </div>
                    <div class="bg-blue-200 border border-blue-500 rounded p-3 text-blue-500 mt-4">
                        <span class="font-bold">Quis: </span><span>{{ quis }}</span><br/>
                        <span class="font-bold">Tugas: </span><span>{{ tugas }}</span><br/>
                        <span class="font-bold">Absensi: </span><span>{{ absensi }}</span><br/>
                        <span class="font-bold">Praktek: </span><span>{{ praktek }}</span><br/>
                        <span class="font-bold">UAS: </span><span>{{ uas }}</span><br/><br/>
                        <span class="font-bold">Rumus: </span><span>{{ quis+"+"+tugas+"+"+absensi+"+"+praktek+"+"+uas+"/"+"5" }}</span><br/>
                        <span class="font-bold">Hasil: </span><span>{{ hasil }}</span><br/>
                        <span class="font-bold">Grade: </span><span>{{ grade }}</span>
                    </div>
                    <div class="mt-2">
                        <button class="mt-4 mb-3 w-full bg-gray-500 hover:bg-gray-400 text-white py-2 rounded-md transition duration-100" @click="result=false;hasil=0;quis=0;absensi=0;tugas=0;praktek=0;uas=0;">Kembali</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import { Head, Link } from '@inertiajs/inertia-vue3';
    export default {
        components: {
            Head,
            Link,
        },
        data() {
            return {  
                quis: 0,
                tugas: 0,
                absensi: 0,
                praktek: 0,
                uas: 0,
                result: false,
                hasil: null,
                grade: null
            }
        },

        methods: {
            hitung() {
                let jumlah = this.quis+this.tugas+this.absensi+this.praktek+this.uas;
                this.hasil = jumlah/5;
                if (this.hasil < 0) {
                    return alert('Nilai tidak bisa kurang dari 0');
                }
                if (this.hasil > 100) {
                    return alert('Nilai tidak bisa lebih dari 100');
                }
                this.result = true;
                if (this.hasil <= 65) {
                    this.grade = "D";
                } else if (this.hasil <= 75) {
                    this.grade = "C";
                } else if (this.hasil <= 85) {
                    this.grade = "B";
                } else if (this.hasil <= 100) {
                    this.grade = "A";
                }
            }
        }
    }
</script>