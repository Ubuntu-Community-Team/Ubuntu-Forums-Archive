---
title: "There is no sound in Ubuntu 10.04"
date: 2010-05-01
forum: Ubuntu Studio
---

### Post by zengzhangsong on 2010-05-01
Yestaday I had installed Ubuntu 10.04 ,but there is no sound when i use earphone.
I'm sure the drivers is OK,because my sound box is working.My earphone is OK,because it work well in Windows 7.
Anybody can tell me what should I do!!!!

---

### Post by cub on 2010-05-01
Have you checked in alsamixer if headphones might be muted? Open a terminal and write **alsamixer**.

---

### Post by zengzhangsong on 2010-05-01
> **cub said:**
> Have you checked in alsamixer if headphones might be muted? Open a terminal and write **alsamixer**.
OK! I will try! Thank you!

---

### Post by goat69 on 2010-05-01
Same with my Acer D250, no sounds at all.  Opened alsamixer and found speaker volume at 0.

---

### Post by sosias on 2010-05-01
In my case ( cm8738 ) nothing is muted. Sound disappeared with upgrade from karmic to lucid. I'm clueless...

---

### Post by toyman61 on 2010-05-01
> **cub said:**
> Have you checked in alsamixer if headphones might be muted? Open a terminal and write **alsamixer**.

Thanx!  This made my day.. :-)

---

### Post by sgx on 2010-05-01
> **sosias said:**
> In my case ( cm8738 ) nothing is muted. Sound disappeared with upgrade from karmic to lucid. I'm clueless...

try   

sudo alsconf

It should start a routine to choose and configure your sound,
and raise the mixer to audible levels.

Cheers

---

### Post by lilpiggie on 2010-05-01
Try opening a terminal and type the command: ```
alsamixer
```

Check if it says "MM" under any of the playback devices such as Master, Speaker, etc. ("MM" means the left+right stereo channels are muted)
You can toggle muting on or off by pressing the "m" key, use the arrow keys to navigate and change it to "OO".

---

### Post by sbike on 2010-05-02
I tried alsconf, no such binary.  Did you mean alsaconf?  Or maybe alsamixer?

I noticed that it seems like my audio card (CM8738 ) seems to be in surround sound mode, and the earphones I'm using (plugged straight into the card) are acting as if they are the rear channels.  So audio/video I get some background noise and theme music, but not vocals.

So I'm guessing I have to switch the audio card from thing I want 5 channel audio to stereo, or play with the channel mapping so the earphones get front/right and front/left channels.

Ideas?

Oh, lspci:
05:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
 cat /proc/asound/cards 
 0 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xe800, irq 20
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdbc000 irq 17


Additional info from the alsa-info script:
[http://www.alsa-project.org/db/?f=c8abb5dad45cf0065564277fd65c22af6ea988b](http://www.alsa-project.org/db/?f=c8abb5dad45cf0065564277fd65c22af6ea988b)

---

### Post by mango42 on 2010-05-02
There seems to be an ongoing issue with what *fundamentally* controls the sound output (and input!). In 9.04 & 9.10 I make a point of starting every session by checking the 'Sound Preferences' applet.

I don't know why it varies from session to session but being of a slightly political paranoid nature I am often alarmed that this applet insists on making my internal laptop microphone **live** seemingly at random, whether I want it or not - is this Big Brother trying to listen into people's (ordinary, mostly boring, occasionally derogatory about our 'world leaders' and the insane global situation) conversations or what? It doesn't seem to matter how many times I adjust it but the mic *almost always* starts up un-muted - not good; not confidence building in this 'Worlde Gonne Mad'

-----

A little ergonomic mod I would like to see is letting the 'pop up' that tells one the exact level in dB when hovering the mouse over the *panel icon* to persist when adjusting the level with its drop down vertical slider.

---

### Post by americka on 2010-05-15
I find the sound being corrupted every time I "upgrade" to a new version of ubuntu. 

What I find even more magical is that the sound can work for one user but not for another. This could however be a hint to solve the problem ... where are the dot-files that set the sound preferences?

---

### Post by 12_String on 2010-05-15
I changed to 10.04 and had to change back because weird things were happening...and after switching back to jaunty jackalope, I have no sound. I have tried changing settings and everything looks right, but nothing makes any sound. Not even with headphones.

---

### Post by sgx on 2010-05-16
Hi, below I have two lines taken from the output of  lspci, they mention
the two sound devices on my system, first the motherboard soundchip, then the pci card. Below those is the output of    lsmod
showing a clump of sound related kernel modules. If you run those two command, lsmod and lspci, and compare their output, you shouls see entries for each soundcard/chip on your computer. If any are missing, then it may be possible to use a command and adjust things.


00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

03:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

-------------------------------------------------------------------------

snd_ice1712            63476  1
snd_ice17xx_ak4xxx      5248  1 snd_ice1712
snd_ak4xxx_adda         9472  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             10112  1 snd_ice1712
snd_ac97_codec        100516  1 snd_ice1712
snd_pcm                77188  3 snd_pcm_oss,snd_ice1712,snd_ac97_codec
snd_timer              24836  2 snd_seq,snd_pcm
snd_page_alloc         11656  1 snd_pcm
snd_i2c                 6656  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9856  1 snd_ice1712
snd_rawmidi            25632  1 snd_mpu401_uart
snd_seq_device          9484  4 snd_seq_dummy,snd_seq_oss,snd_seq,snd_rawmidi
snd                    56100  16 snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9440  1 snd

---

