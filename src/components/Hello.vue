<template>

  <!-- Main content -->
  
  <div class="container">
        <div class="box-header with-border">
          <h3 class="box-title"></h3>
          <div class="box-body">
            <div >
              <p class="text-center">
                <strong>Sample Temperature Gauge</strong>
              </p>
               </div>
              <IEcharts :option="gauge"  style="width: 600px; height: 450px;" ></IEcharts>
           
        </div>
        <small class="space"><b>Tip</b> This is sample graph!</small>
      </div>
    </div>
 
  <!-- /.content -->
 
</template>

<script>
// import Chart from 'chart.js'
import IEcharts from 'vue-echarts-v3/src/full.vue'
//var Client = require('ibmiotf')

export default {
   name: 'hello',
  components: { IEcharts },
  props: { },
  data () {
    return {
      loading: true,
      temp: 0,

      gauge: {
        tooltip: {
          formatter: '{a} <br/>{b} : {c}'
        },
        toolbox: {
          show: true,
          feature: {
            mark: {show: true},
            restore: {show: false},
            saveAsImage: {show: false}
          }
        },
        series: [
          {
            name: 'Temp',
            type: 'gauge',
            detail: {formatter: '{value}°C'},
            data: [{value: 50, name: 'Temperature'}]
          }
        ]
      },

    }
  },
  methods: {  
      refreshData () {
    this.gauge.series[0].data[0].value = (Math.random() * 100).toFixed(2) - 0;
       }
  },

  mounted () 
  {
      this.refreshData()
      setInterval(function () {
          this.refreshData();
        }.bind(this), 3000); 
   
  }

}
</script>
<style>
</style>
