<script setup>
    import useSkills from '../../composables/skills';
    import { onMounted } from 'vue';

    const {skills, getSkills} = useSkills();

    onMounted(() => getSkills());

</script>
<template>
    <div class="mt-12">
        <div class="flex justify-end m2 p-2">
            <RouterLink 
                :to="{name: 'SkillCreate'}"
                class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 text-white rounded"
            >New Skill</RouterLink>
        </div>
        <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
            <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            Name
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Slug
                        </th>
                        <th scope="col" class="px-6 py-3">
                            <span class="sr-only">Edit</span>
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="skill in skills" :key="skill.id" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                            {{skill.name}}
                        </th>
                        <td class="px-6 py-4">
                            {{skill.slug}}
                        </td>
                        <td class="px-6 py-4 text-right">
                            <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>