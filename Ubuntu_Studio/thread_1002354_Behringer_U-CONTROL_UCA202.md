---
title: "Behringer U-CONTROL UCA202"
date: 2008-12-04
forum: Ubuntu Studio
---

### Post by rolodoom on 2008-12-04
Hello, I'm having tthis trouble. I have a Behringer U-CONTROL UCA202 USB Sound Card, and when I used to reboot my laptop HP dv6721la with the usb card connected, it was always my default card. Today I realized that it's not working, I mean the card It's working but it doesn't matter if it is connected to my laptop the default system sound is by the nvidia internal card and not by the usb card.

How can i fix this???

---

### Post by zettberlin on 2008-12-06
> **rolodoom said:**
> 

How can i fix this???

It depends ;-)

I use the jackd-server, with qjackctl I can access the card I want to and thus I never have any problems with that.

Pulsaudio *should* have the same capabilities though I dont know, if it really works. 

I all cases the key is ALSA and its way to approach the soundcards. On my system the Behringer (I have the very same...) is always hw:1. I thought, that should not be a problem anymore...

---

### Post by prismatic7 on 2008-12-07
> **rolodoom said:**
> Hello, I'm having tthis trouble. I have a Behringer U-CONTROL UCA202 USB Sound Card, and when I used to reboot my laptop HP dv6721la with the usb card connected, it was always my default card. Today I realized that it's not working, I mean the card It's working but it doesn't matter if it is connected to my laptop the default system sound is by the nvidia internal card and not by the usb card.

How can i fix this???

Check out [this tutorial](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices) on the UbuntuStudio help wiki...

---

