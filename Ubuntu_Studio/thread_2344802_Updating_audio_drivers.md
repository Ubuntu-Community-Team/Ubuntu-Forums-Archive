---
title: "Updating audio drivers?"
date: 2016-11-28
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2016-11-28
Ubuntu Studio 16.04.1

I am having frequent periodic bad audio distortion, usually while watching videos with Firefox v50 on YouTube but the problem can also be heard when playing audio files locally in VLC. Audio is fine after rebooting but the distortion kicks in after a while.

What is the simplest way of re-installing audio drivers for my EchoAudio Mia 24/96 soundcard?

```

**** List of PLAYBACK Hardware Devices ****
card 0: Mia [Mia], device 0: PCM [Mia]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]


  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1

```

```

~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/bebob/snd-bebob.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/oxfw/snd-oxfw.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/dice/snd-dice.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/tascam/snd-firewire-tascam.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/snd-isight.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/digi00x/snd-firewire-digi00x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/firewire/fireworks/snd-fireworks.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/synth/snd-util-mem.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/snd-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-dummy.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-mts64.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/drivers/snd-aloop.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/bcd2000/snd-bcd2000.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/line6/snd-usb-pod.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/line6/snd-usb-toneport.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/line6/snd-usb-variax.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/line6/snd-usb-podhd.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/usb/line6/snd-usb-line6.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-hwdep.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-hrtimer.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-pcm-dmaengine.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-pcm.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-rawmidi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-compress.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/core/snd-timer.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/xtensa/snd-soc-xtfpga-i2s.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/fsl/snd-soc-fsl-asrc.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/fsl/snd-soc-imx-audmux.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/fsl/snd-soc-fsl-esai.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/fsl/snd-soc-fsl-sai.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/fsl/snd-soc-fsl-spdif.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/fsl/snd-soc-fsl-ssi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42xx8-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42xx8.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-pcm512x-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-gtm601.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-pcm1681.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ak5386.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs4271-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ak4613.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-sta350.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tlv320aic31xx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tas571x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-es8328.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8804-spi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ssm2602-spi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ak4554.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ac97.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rt5640.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ssm2602-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tas2552.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-pcm512x-spi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ts3a227e.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-sigmadsp-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs4349.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tlv320aic23-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-sigmadsp.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-pcm512x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-sti-sas.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs4271-spi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rt286.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs4265.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rl6231.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tfa9879.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-pcm1792a-codec.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8804-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rt5670.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tlv320aic23-spi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-ssm4567.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-tas5086.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-dmic.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42l51-i2c.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-adau1701.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs35l32.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rt5645.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs42l56.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-rl6347a.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/snd-soc-core.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/atom/snd-soc-sst-mfld-platform.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/atom/sst/snd-intel-sst-core.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/atom/sst/snd-intel-sst-acpi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/common/snd-soc-sst-acpi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/common/snd-soc-sst-dsp.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/common/snd-soc-sst-ipc.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/skylake/snd-soc-skl-ipc.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/skylake/snd-soc-skl.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/haswell/snd-soc-sst-haswell-pcm.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/baytrail/snd-soc-sst-baytrail-pcm.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-broadwell.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-haswell.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-byt-rt5640-mach.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-max98090_ti.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-byt-max98090-mach.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-bytcr-rt5640.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5672.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5645.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/soc/intel/boards/snd-soc-skl_rt286.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-als300.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-cs4281.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-rme32.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-fm801.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-rme96.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-ad1889.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-atiixp.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-via82xx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-es1938.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-maestro3.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-als4000.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-bt87x.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-cmipci.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-ens1371.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hdausername@username-Inspiron-560:/snd-hda-codec-idt.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-generic.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-ens1370.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-es1968.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/pci/snd-azt3328.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/hda/snd-hda-core.ko
/lib/modules/4.4.0-47-lowlatency/kernel/sound/hda/ext/snd-hda-ext-core.ko

```

```

~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Dell 82801JI (ICH10 Family) HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
--
    Subsystem: Echo Digital Audio Corporation Mia rev.0
    Flags: bus master, medium devsel, latency 192, IRQ 16
    Memory at feb00000 (32-bit, non-prefetchable) [size=1M]
    Kernel driver in use: snd_mia
    Kernel modules: snd_mia

```

---

### Post by CrocoDuck on 2016-11-29
You need to reinstall ALSA. I think you might try to reinstall [alsa-base]("http://packages.ubuntu.com/yakkety/alsa-base") from the repositories. If you need the latest version of ALSA (and not the version in the repos) I am afraid you will have to compile it from source. You should find instructions on how to do that on the ALSA website. Your device seem to have [a page]("http://www.alsa-project.org/main/index.php/Matrix:Module-mia") on the [ALSA Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main"), check that out in case it says something relevant to you. You probably should make sure it is not a PulseAudio related thing first. The Arch Linux wiki has a good [PulseAudio troubleshooting page]("https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting"). Have a look at these two:

[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Choppy.2Fdistorted_sound](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Choppy.2Fdistorted_sound)
[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling)

If you need to a clarification on what PulseAudio, ALSA and the like are, hopefully [this post]("https://thecrocoduckspond.wordpress.com/2016/11/19/the-linux-audio-anatomy/") on my blog will shed some light.

---

### Post by shaunthesheep on 2016-12-04
Many thanks for your extremely useful advice.

I have downloaded the Alsa-base deb file and it is sitting on my desktop. Please excuse my ignorance (refugee from Windows) but do I need to uninstall the existing Alsa-base *first* before reinstalling or can I simply over-write the existing installation? **Update**: after re-reading the instructions on the Alsa-base page, I have used Synaptic to re-install it, so I assume that will take care of matters.

Any idea why rebooting always (temporarily) solves the problem until it happens again?

Thanks.

---

### Post by CrocoDuck on 2016-12-04
Using the package manager is the way to go. No need to uninstall (I don't think the package manager would even allow that as alsa-base is a dependency for many things).

I don't know why reboot helps. This makes me think pulseaudio might be the cause. I wonder whether it could be some auto-level thing? Few applications (like skype) can automatically set device levels. This might yield to digitital or hardware clipping. Keep an eye on alsamixer (just enter alsamixer in the terminal) and make sure that the levels are not to the highest at all time (better to be conservative).

---

### Post by shaunthesheep on 2016-12-05
I have just noticed the following while playing back videos on YouTube (but same happens when playing audio files locally in VLC). After audio distortion kicks in, I see something called 'Speech Dispatcher' activated on the Playback tab of Sound Settings. I am guessing this could be the source of the weird distortion (a continuous low volume static sound that obscures all the music which should be playing). Usually, it is Firefox audio stream which is activated when sound playback is normal but that disappears and is replaced by Speech Dispatcher' when sound distortion is happening. 

What could be causing 'Speech Dispatcher' to spontaneously activate and replace Firefox audio stream and how can I stop this happening? I don't use text to speech on my desktop PC.

Thanks.

---

### Post by CrocoDuck on 2016-12-05
Interesting. Never heard of that. If you don't really need it, uninstall the package supplying that functionality. It should be as easy as

```

sudo apt-get remove speech-dispatcher

```

Or, disable its automatic startup. These threads might be helpful:

[http://askubuntu.com/questions/378223/how-to-stop-ubuntu-from-talking-to-me](http://askubuntu.com/questions/378223/how-to-stop-ubuntu-from-talking-to-me)
[URL="http://askubuntu.com/questions/293244/problem-with-speech-dispatcher#360115"]http://askubuntu.com/questions/293244/problem-with-speech-dispatcher#360115
[/URL]https://www.howtoinstall.co/en/ubuntu/trusty/speech-dispatcher?action=remove

Other related packages: [http://packages.ubuntu.com/search?keywords=speech+dispatcher&searchon=names&suite=yakkety&section=all](http://packages.ubuntu.com/search?keywords=speech+dispatcher&searchon=names&suite=yakkety&section=all)

---

### Post by shaunthesheep on 2016-12-06
Thanks for all your help.

---

