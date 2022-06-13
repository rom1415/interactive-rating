<template>
    <div class="c-rating">
        <div class="c-rating__container" v-show="!this.selected">
            <div class="c-rating__star">
                <img src="../assets/rating.svg" alt="Rating Star">
            </div>
            <div class="c-rating__question">
                <h1>How did we do?</h1>
            </div>
            <div class="c-rating__description">
                <p>Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!</p>
            </div>
            <div class="c-rating__numbers">
                <div v-for="number in this.numbers" v-bind:key="number"
                v-on:click="setAsActive(number)"
                :class="{ 
                    'c-rating__numbers__item': true,
                    'c-rating__numbers__item--active' : number.active,
                }"
                >{{ number.label }}</div>
            </div>
            <div class="c-rating__submit" v-on:click="submit()">
                <a>Submit</a>
            </div>
        </div>
        <div class="c-rating__finished--container" v-show="this.selected">
            <div class="c-rating__finished">
                <img src="../assets//finished.svg">
            </div>
            <div class="c-rating__selected">
                You selected {{ this.selected }} out of {{ this.numbers.length }}
            </div>
            <div class="c-rating__thankyou">
                <h1>Thank you!</h1>
            </div>
            <div class="c-rating__thankyou__description">
                <p>We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!</p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "RatingComponent",
    data() {
        return { 
            selected: 0,
            numbers: [
                {
                    label: 1,
                    active: true,
                },
                {
                    label: 2,
                    active: false
                },
                {
                    label: 3,
                    active: false
                },
                {
                    label: 4,
                    active: false
                },
                {
                    label: 5,
                    active: false
                }
            ]
         }
    },
    methods: {
        setAsActive: function(number) {
            this.numbers.forEach(item => item.active = false);
            number.active = true;
        },
        submit: function() {
            let current = this.numbers.filter(item => item.active === true)[0];
            this.selected = current.label;
        }
    }
}

</script>