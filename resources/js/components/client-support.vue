<template>
    <!-- Your template code here -->
</template>

<script>
import axios from 'axios'; // Import axios if not already imported

export default {
    /*
     * The component's data.
     */
    data() {
        return {
            clients: [],
            clientSecret: null,
            createForm: {
                errors: [],
                name: '',
                redirect: '',
                confidential: true
            },
            editForm: {
                errors: [],
                name: '',
                redirect: ''
            }
        };
    },

    /**
     * Prepare the component.
     */
    mounted() {
        this.prepareComponent();
    },

    methods: {
        /**
         * Prepare the component.
         */
        prepareComponent() {
            this.getClients();

            $('#modal-create-client').on('shown.bs.modal', () => {
                $('#create-client-name').focus();
            });

            $('#modal-edit-client').on('shown.bs.modal', () => {
                $('#edit-client-name').focus();
            });
        },

        /**
         * Get all of the OAuth clients for the user.
         */
        getClients() {
            axios.get('/oauth/clients')
                .then(response => {
                    this.clients = response.data;
                });
        },

        // Rest of your methods...
    }
};
</script>

<style scoped>
/* Your scoped styles here */
</style>
