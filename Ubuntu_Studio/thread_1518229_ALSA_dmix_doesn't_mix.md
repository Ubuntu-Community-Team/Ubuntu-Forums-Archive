---
title: "ALSA dmix doesn't mix"
date: 2010-06-26
forum: Ubuntu Studio
---

### Post by mrowth on 2010-06-26
Hi! I've looked at this page from the unofficial ALSA wiki:

[http://alsa.opensrc.org/index.php/Hardware_mixing,_Software_mixing](http://alsa.opensrc.org/index.php/Hardware_mixing,_Software_mixing)

And I've copied the .asoundrc:

```
pcm.my_card {
    type hw
    card 0
    # mmap_emulation true
}

pcm.dmixed {
    type dmix 
    ipc_key 1024 
    #  ipc_key_add_uid false   # let multiple users share
    #  ipc_perm 0666           # IPC permissions for multi user sharing (octal, default 0600)
    slave {
    pcm "my_card" 
    #   rate 48000
    #   period_size 512
    }
}

pcm.dsnooped {
    type dsnoop 
    ipc_key 2048 
    slave {
    pcm "my_card" 
    #   rate 48000
    #   period_size 128
    }
}

pcm.asymed {
    type asym 
    playback.pcm "dmixed" 
    capture.pcm "dsnooped"
}

pcm.pasymed {
    type plug 
    slave.pcm "asymed"
}

pcm.dsp0 {
    type plug
    slave.pcm "asymed"
}

pcm.!default {
    type plug
    slave.pcm "asymed"
}
```

And it does the opposite of what was intended: I can **not** play two wav files simultaneously (anymore). Not with plain aplay, and not with aplay -D pasymed:

```
$ aplay -D pasymed in_the_field_again-96-32.wav                                                                      
Playing WAVE 'in_the_field_again-96-32.wav' : Float 32 bit Little Endian, Rate 96000 Hz, Mono
```

(Other terminal, file is still playing:)

```
$ aplay -D pasymed in_the_field_again-48-16.wav                                                                      
ALSA lib pcm_dmix.c:1060:(snd_pcm_dmix_open) unable to open slave
aplay: main:608: audio open error: Invalid argument

```

(It doesn't have to do with the sample formats; the result is the same when both samples are 48k/16bit.)

When I delete the .asoundrc, I have no problems of this nature anymore. That's not a surprise, because my soundcard (Audigy 2 ZS Platinum) has hardware-mixing... so right now I don't actually need dmix/dsnoop/asym tricks. But I might want to buy a laptop with nasty on-board sound and would like to understand ALSA a little better so as not to panic when the time comes (I also find Pulse **very** confusing, and JACK it seems is not general-purpose enough for mere 'entertainment' uses). 

So can anybody give me a hint? Thanks!

~~~~~~~~~~~ PS: ~~~~~~~~~~~

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

(I also don't yet know what card 0, devices 2-4 and card 1, device 1 are...)

---

