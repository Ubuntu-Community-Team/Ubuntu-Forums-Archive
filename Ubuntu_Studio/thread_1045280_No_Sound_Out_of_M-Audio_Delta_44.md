---
title: "No Sound Out of M-Audio Delta 44"
date: 2009-01-20
forum: Ubuntu Studio
---

### Post by Abu_Dayya on 2009-01-20
I have everything setup ( I think ). when I try to play an mp3, I can see from the 'Monitor PCMs' tab that the bars are lighting, like there is something playing. But I don't hear anything coming out from the speaker.

Ok. So, here is my setup:

Envy24control:
Monitor Inputs tab: Unmuted all controls and brought them up to 25
Monitor PCMs tab: Unmuted ONLY left control of PCM OUT 1 and the right control of PCM OUT 2 (as the delt 44 only has mono inputs and outputs)
Patchbay/Router tab: set H/W OUT 1 and H/W OUT 2 to Digital Mix ( There seem to be no 'Digital Mix' option for PCM OUT 3 & 4, but there is PCM OUT)
Hardware Setting tab: Master Clock is set to 96000. All Other things are left at default
Analog Volume tab: All controls are setup to 100 (DAC0-DAC3, and ADC0-ADC3)

System -> Pref -> Sounds
Sound Events: sound playback set to ALSA (Tried both ALSA and ICE1712 multi, nothing worked)
Music and Movies: sound playback set to ALSA
Audio Conferencing: playback set to ALSA . Sound Capture set to ALSA 
Default Mixer Tracks: Device is M Audio Delta 44 (Alsa mixer). The Other option is  ICE1712 - multitrack (OSS Mixer)

My Hardware Setup
I have a Y cable (two mono jacks to one stereo jack) connects the breakout box of the Delta 44 card to a (1/4" to 1/8") adapter to a speaker

OnBoard Audio: Disabled from bios

Some Outputs of my system
```
yousef@MyStudio:~$ lspci | grep audio
04:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

yousef@MyStudio:~$ sudo lshw
...
           *-multimedia
                description: Multimedia audio controller
                product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
                vendor: VIA Technologies Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ICE1712 latency=32 module=snd_ice1712

...

yousef@MyStudio:~$ lsmod | grep -i ice17
snd_ice1712            63860  2 
snd_ice17xx_ak4xxx      5120  1 snd_ice1712
snd_ak4xxx_adda         9472  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             10240  1 snd_ice1712
snd_ac97_codec        101284  1 snd_ice1712
snd_pcm                78852  4 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_i2c                 6528  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9984  1 snd_ice1712
snd                    57636  19 snd_rtctimer,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


yousef@MyStudio:~$ asoundconf list
M44
yousef@MyStudio:~$

```


This is all I can think of. Please help

---

### Post by Abu_Dayya on 2009-01-21
OMG

I can't tell you how stupid I feel right now. This is so embarrassing....

Instead of plugging the cables from the 'OUT' plugs of the delta card.... I pluged them into the 'IN' plugs........... Now I have sound and everything is alright


I can't tell you all how hard I searched to get an answer for my problem, and nothing worked......

I feel STUPID, but releived

---

### Post by Abu_Dayya on 2009-01-21
I sould mention that I added this line to my /etc/modprobe.d/alsa-base file```
options snd-ice1712 model=delta44
```
This was added when I was troubleshooting (before I realized my stupidity), and I guess I forgot to comment it out. But since everything is working now, I'm not changing it. I'll leave it there.

---

