---
title: "I have accepted a challenge. Please help me."
date: 2005-10-06
forum: The Cafe
---

### Post by kagashe on 2005-10-06
Hi,
I have accepted a challenge to prove that Linux works on any hardware and would like to start with Ubuntu because I find it the best Linux community. One person has given the hardware specifications which are attached here. After sufficient feedback is there on this thread I will invite him to see it. Following is from his message:> This image is from the mainboard manual, and lists the specs of the basic hardware. I don't use the onboard VGA however, having installed an nVidia card myself. I also have 1gb ram.
The video card is nVidia GeForce FX5200 (AGP).
The USB modem i use is a Dlink DSL-200 (USB DSL modem).
kagashe

---

### Post by davmac on 2005-10-06
Linux works on *any* hardware? Woohoo - you're a braver person than me, to accept a challenge like that, if I may say so!
Have you seen [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)? There's load of info about what hardware is supported and to what extent.
HTH,
Dave Mac

---

### Post by tehwa on 2005-10-06
If it gives you any confidence, I use that motherboard (P4SGX-MX), and everything worked out of the box (important only for sound really, since your mate is using an nVidia card, but the onboard was fine).

I think the only concern is the USB modem. Work on that first.

---

### Post by Brunellus on 2005-10-06
dude.  bad bet.

Linux works with *lots* of hardware. *most* hardware.  But *any* hardware is a bit of a stretch.

Linux does work with lots of *architectures* but that probably doesn't help you

---

### Post by kagashe on 2005-10-06
[QUOTE=tehwa]If it gives you any confidence, I use that motherboard (P4SGX-MX), and everything worked out of the box (important only for sound really, since your mate is using an nVidia card, but the onboard was fine).
I think the only concern is the USB modem. Work on that first.[/QUOTE]Yes, he says that sound is going to be the problem.
I use a USB modem but it is a CDMA mobile instrument not DSL. My modem is detected by the system as /dev/ttyACM0 and I have set up /etc/wvdial.conf to use it. The hotplug automatically loads the driver.
I would like to know how Ubuntu detects a DSL USB modem and what protocol is used to connect to internet (if not ppp).

kagashe

---

### Post by az on 2005-10-06
The sound should not be a problem.

---

### Post by kagashe on 2005-10-06
[QUOTE=azz]The sound should not be a problem.[/QUOTE]Thanks.

Meanwhile I have found the driver for his ADSL USB modem here:
[http://www.qbik.ch/usb/devices/showdev.php?id=1562](http://www.qbik.ch/usb/devices/showdev.php?id=1562)

kagashe

---

### Post by kagashe on 2005-10-10
[QUOTE=azz]The sound should not be a problem.[/QUOTE]
Hi,

I would like to know the meaning of this reply. I have searched for the soundcard on:
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
and don't find it listed.
Then I serched on Google and found a mail dated July 28 by none other than Linus Torvald himself:
[http://lwn.net/Articles/145435/](http://lwn.net/Articles/145435/)
The mail is about Patch: Linux 2.6.13-rc4 and lists the sound card as:> Sergey Ulanov:
  [ALSA] Jack Sense support for AD1980 and AD1888.

Does it mean that he required the latest linux kernel 2.6.13 with patches if necessay, to support the sound card.

kagashe

---

### Post by tehwa on 2005-10-10
Hi, sorry, my earlier post was ambiguous.

I use the onboard sound for that motherboard  (P4SGX-MX), Hoary detected and set it up automatically (kernel 2.6.10).

That kernel post seems to be some about improvements to ALSA, although without those improvements, this soundcard will still work swimmingly.

---

