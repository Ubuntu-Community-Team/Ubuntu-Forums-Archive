---
title: "HA INFO DAC - nothing but distortion in Linux"
date: 2012-12-15
forum: Ubuntu Studio
---

### Post by jkorten on 2012-12-15
I have a brand new DAC that actually allows me to do s/pdif in in windows. But also allows me to put out 192KHz in Windows.

The DAC works fine in Windows. In Ubuntu it shows up in sound settings, but if I select it, the only thing I hear through it is distortion. Related to the sound, but pure distortion. (No matter what sample rate. I'm using a Lenovo T510 btw).

I use audacity to record and play stuff (live). And I'd really like to stay in the Linux world doing this. But I can't hear my dac. :-(

On my stereo by the way, I have a REGA DAC and can play through USB to that with no difficulty (although the sample rate remains at 44.1 no matter what I play).

I think I am missing something kind of fundamental here. If you have any suggestions. I would be much obliged.

---

### Post by CrocoDuck on 2012-12-17
Hi. Could you repost your DAC model? Do you know if your DAC is class compliant? Have you tried to use your DAC with JACK? Repost the output of those commands:

```
cat /proc/asound/cards

``````
cat /proc/asound/devices

``````
cat /proc/asound/pcm
``````
cat /proc/asound/card*/stream0 | grep Rates

```

---

### Post by jkorten on 2012-12-17
> **CrocoDuck said:**
> Hi. Could you repost your DAC model? Do you know if your DAC is class compliant? Have you tried to use your DAC with JACK? Repost the output of those commands:

```
cat /proc/asound/cards

``````
cat /proc/asound/devices

``````
cat /proc/asound/pcm
``````
cat /proc/asound/card*/stream0 | grep Rates

```

Thanks for your help!

I have gotten the DAC to work. Not yet sure what sample rate (will work on this). I ended up using KDE System Settings (not system settings which is I guess the gnome version) then going to multi media->phonon->audio hardware setup

Here I selected the HA INFO and selected Analog Stereo Duplex (it does S/PDIF input). I also selected it as sound device under device configuration and specified connector = analog output.

I'm not sure how I got there but it works now. 

I am answering your questions anyhow. Looks like the gnome system settings needs a bit more detail - or else I need to know about somewhere else to go to make these settings under gnome.

cat /proc/asound/cards

jerry@jerry-ThinkPad-T510:~$ cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8520000 irq 46
 1 [U0x46d0x9a6    ]: USB-Audio - USB Device 0x46d:0x9a6
                      USB Device 0x46d:0x9a6 at usb-0000:00:1a.0-1.5.2, high speed
 2 [PLUS           ]: USB-Audio - HA INFO U2 PLUS
                      HA INFO U2 PLUS at usb-0000:00:1a.0-1.1, full speed
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 6MHT43WW-1.18

cat /proc/asound/devices

jerry@jerry-ThinkPad-T510:~$ cat /proc/asound/devices
  1:        : sequencer
  2: [29]   : control
  3: [ 0- 3]: digital audio playback
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 3]: hardware dependent
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
  9: [ 1- 0]: digital audio capture
 10: [ 1]   : control
 11: [ 2- 1]: digital audio playback
 12: [ 2- 0]: digital audio playback
 13: [ 2- 0]: digital audio capture
 14: [ 2]   : control
 33:        : timer



cat /proc/asound/pcm

jerry@jerry-ThinkPad-T510:~$ cat /proc/asound/pcm
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
00-03: HDMI 0 : HDMI 0 : playback 1
01-00: USB Audio : USB Audio : capture 1
02-00: USB Audio : USB Audio : playback 1 : capture 1
02-01: USB Audio : USB Audio #1 : playback 1



cat /proc/asound/card*/stream0 | grep Rates

jerry@jerry-ThinkPad-T510:~$ cat /proc/asound/card*/stream0 | grep Rates
    Rates: 16000
    Rates: 8000, 16000, 32000, 44100, 48000, 96000
    Rates: 8000, 16000, 32000, 44100, 48000, 96000
    Rates: 8000, 16000, 32000, 44100, 48000, 96000
    Rates: 8000, 16000, 32000, 44100, 48000, 96000

---

### Post by CrocoDuck on 2012-12-17
Hi. I'm happy that you managed to get it working;). Basically the output of those commands says us that everything is okaysh and ready to go. Everytime I need to set up audio on my installation I use alsamixer, typing in a terminal

```
alsamixer
```

consider to give it a try when you don't know how to solve a problem.

---

### Post by jkorten on 2012-12-18
> **CrocoDuck said:**
> Hi. I'm happy that you managed to get it working;). Basically the output of those commands says us that everything is okaysh and ready to go. Everytime I need to set up audio on my installation I use alsamixer, typing in a terminal

```
alsamixer
```

consider to give it a try when you don't know how to solve a problem.

Thanks CrocoDuck! That looks like a great tool.

:D

---

