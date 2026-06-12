---
title: "EMU-1212m:  ALSA and jack not happy"
date: 2013-02-21
forum: Ubuntu Studio
---

### Post by kelargo on 2013-02-21
I am working on a fairly new install of Ubuntu Studio. (Ubuntu 12.10)  

The install went fine and I was able to get most things working. 

I have the alsa-firmware loaded and my EMU-1212m (PCI v1 card) is sort of recognized. But the driver that gets loaded is not recognized correctly in the system and jackd fails.

For example, when I go into qjackctl setup, and select the hardware input & device device in the pull down, I can see, for example, "hw:3,0 ADC capture/standard PCM playback"  or "hw:3,2 Multichannel Capture/PT Playback"

But when I start jack, it fails when there are more than two channels in Channel I/O and only works for "hw:3".
> ALSA: cannot set channel count to 3 for capture
ALSA: cannot configure capture channel
cannot load driver modula alsa

When I go into alsamixer, I can select the ADC and select the ADAT channels. (I have a Alesis ADAT connected.)
everything mostly appears correct at that level, except for the card name. The card shows up as "EMU-1010" and not "EMU-1212" has it did before, when I had this working, in the past, on a different distro. 

Seems like ALSA is loading, but not quite correct and seems like jack isn't interfacing to it correctly, as a result?? 

What to do next?   

thanks


here is my alsa-info .
[http://www.alsa-project.org/db/?f=c19517570577b14052eb8d63aa74b3d9f7be3f14]("http://www.alsa-project.org/db/?f=c19517570577b14052eb8d63aa74b3d9f7be3f14")

here are the modules. 

```
snd_emu10k1_synth      17294  0 
snd_emux_synth         42804  1 snd_emu10k1_synth
snd_seq_virmidi        13421  1 snd_emux_synth
snd_seq_midi_emul      13660  1 snd_emux_synth
snd_emu10k1           152374  2 snd_emu10k1_synth
snd_ac97_codec        134270  1 snd_emu10k1
snd_util_mem           14118  2 snd_emux_synth,snd_emu10k1
snd_hwdep              17699  4 snd_emux_synth,snd_emu10k1,snd_usb_audio,snd_hda_codec
snd_pcm                96668  6 snd_emu10k1,snd_hda_codec_hdmi,snd_ac97_codec,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_seq                61555  10 snd_seq_dummy,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            30513  4 snd_seq_virmidi,snd_emu10k1,snd_usbmidi_lib,snd_seq_midi
snd_timer              29426  4 snd_hrtimer,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14498  6 snd_seq_dummy,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_seq,snd_rawmidi
snd_page_alloc         18485  3 snd_emu10k1,snd_hda_intel,snd_pcm
snd                    74825  24 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_codec_hdmi,snd_ac97_codec,snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: EMU1010 [E-mu 1010 [MAEM8810]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 3: EMU1010 [E-mu 1010 [MAEM8810]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 3: EMU1010 [E-mu 1010 [MAEM8810]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

edit note-  I rebooted and the card got a newer card number.. one time hw:0 and then another time hw:3

---

### Post by jejeman on 2013-02-22
For card order either:
1. disable the cards you don't use - the best
2. order them in alsa-base.conf

---

### Post by kelargo on 2013-02-22
Thanks. I can do that card ordering... Wasn't my big concern just yet.

Any ideas on why the card appears EMU-1010 instead of EMU -1212?  

Its like the ADAT interfaces appear in alsamixer but are not available to jack.

---

### Post by kelargo on 2013-02-23
reduce frames from the default 1024  and it will launch.

---

