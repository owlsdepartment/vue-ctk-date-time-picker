<template>
  <div
    role="row"
    class="week-days flex"
    :class="{'is-dark': dark}"
  >
    <div
      v-for="(weekDay, index) in weekDays"
      :key="index"
      class="flex-1 text-muted lm-fs-12 flex justify-content-center align-center week-days-container"
      aria-sort="none"
      role="columnheader"
      :aria-label="getFullWeekdayName(weekDay)"
    >
      <span aria-hidden="true">
        {{ weekDay }}
      </span>
    </div>
  </div>
</template>

<script>
  import moment from 'moment'

  export default {
    name: 'WeekDays',
    props: {
      weekDays: { type: Array, default: () => ([]), required: true },
      dark: { type: Boolean, default: null }
    },
    methods: {
      getFullWeekdayName (day) {
        return moment(day, 'dd').format('dddd')
      }
    }
  }
</script>

<style lang="scss" scoped>
  .week-days {
    height: 41px;
    text-transform: capitalize;
    &.is-dark .week-days-container {
      color: #a8a8a8 !important;
    }
  }
  @media screen and (max-width: 415px) {
    &:not(.inline) {
      .datepicker-week {
        height: 21px !important;
      }
    }
  }
</style>
