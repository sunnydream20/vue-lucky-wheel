<template>
  <div>
    <LuckyWheel
      ref="myLucky"
      width="300px"
      height="300px"
      :prizes="prizes"
      :blocks="blocks"
      :buttons="buttons"
      @start="startCallback"
      @end="endCallback"
    />
  </div>
</template>

<script>
import lightningImage from './assets/lightning.png';
import wheelBg from './assets/turnplate-bg.png';
import wheelPointer from "./assets/pointer.png";

export default {
  data () {
    return {
      blocks: [{ padding: '13px', imgs:[{src: wheelBg, width: '300px' }] }],
      prizes: [
        { fonts: [{ text: 'Yellow', top: '10%', fontColor: "white" }], 
          background: '#ccc', 
          imgs: [{ src: lightningImage, width: '20px', height: '20px',  top: '50px'}]
        },
        { fonts: [{ text: 'Red', top: '10%', fontColor: "white" }], 
          background: '#aaa', 
          imgs: [{ src: lightningImage, width: '20px', height: '20px',  top: '50px'}]
        },
        { fonts: [{ text: 'Red', top: '10%', fontColor: "white" }], 
          background: '#aaa', 
          imgs: [{ src: lightningImage, width: '20px', height: '20px',  top: '50px'}]
        },
        { fonts: [{ text: 'Red', top: '10%', fontColor: "white" }], 
          background: '#aaa', 
          imgs: [{ src: lightningImage, width: '20px', height: '20px',  top: '50px'}]
        },
        { fonts: [{ text: 'Red', top: '10%', fontColor: "white" , borderColor: 'black'}], 
          background: '#aaa', 
          imgs: [{ src: lightningImage, width: '20px', height: '20px',  top: '50px'}]
        },
      ],
      buttons: [{
        radius: '35%',
        background: '#ffbe04',
        // pointer: true,
        imgs: [{src: wheelPointer, top: '-81px', width: '100px', height: '130px'}]
      }],
      lightningImage,
      wheelBg,
      wheelPointer
    }
  },
  methods: {
    startCallback () {
      this.$refs.myLucky.play()
      setTimeout(() => {
        const index = 0
        this.$refs.myLucky.stop(index)
      }, 3000)
    },
    endCallback (prize) {
      console.log(prize.fonts[0].text)
    },
  }
}
</script>