---
title: "How to play sound through my m_Audio Fast Track Pro? (It works on regular ubuntu)"
date: 2012-07-25
forum: Ubuntu Studio
---

### Post by Chiel92 on 2012-07-25
Hi,

I don't know how I can get sound through my m_Audio Fast Track Pro usb audio interface. I use Ubuntu Studio 12.04.
Ideally, I want to select the fasttrack pro as the standard system output, such that jack sends the system output to the fasttrack pro.
However, I don't know what is the best way to do that. Moreover, the info I read on the internet didn't seem to work for me.

When I select the fasttrack pro in qjackctl, it still outputs the system sound to my regular built-in soundcard. I also selected the fasttrack as fallback in PulseAudio Volume Control, didnt help either.

Does anyone have any ideas how I can get my system sound though the fast track pro interface?
Many thanks in advance!

---

### Post by Chiel92 on 2012-07-25
I guess that setting the fasttrack usb audio as default soundcard could solve my problem. From what I read on the internet I deduce that there is no standard/gui way to do it.
It is often suggested to disable the built-in soundcard in the BIOS. I want to avoid this, since I use the soundcard on other distro's. 
The second suggestion ([http://www.linuxquestions.org/questions/ubuntu-63/change-detected-default-sound-card-in-ubuntu-10-10-a-857918/](http://www.linuxquestions.org/questions/ubuntu-63/change-detected-default-sound-card-in-ubuntu-10-10-a-857918/)) consists of editing the soundcard indices in /etc/modprobe.d/alsa-base.conf.
Above the line saying "# Prevent abnormal drivers from grabbing index 0" I added
```
options snd_usb_audio index=0

```and commented out the line stating: 
```
options snd-usb-audio index=-2
```After rebooting, "cat /proc/asound/modules" still prints:
```
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_usb_audio
```Any ideas?

---

### Post by Chiel92 on 2012-07-25
Although "cat /proc/asound/modules" still prints the initial order, "pactl stat" shows that the default sink is the fasttrack pro :)
I have jack set to the default interface, and everything appears to work fine! I get sound through the usb audio interface :)
Not that I really get what's going on, but it works.

---

