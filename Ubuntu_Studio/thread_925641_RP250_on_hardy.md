---
title: "RP250 on hardy"
date: 2008-09-20
forum: Ubuntu Studio
---

### Post by thelinuxer on 2008-09-20
Hey guys,
I bought a new RP250 effect processor, I connected it to my PC using a usb cable but my kernel doesn't detect it correctly. I am using Ubuntu Hardy 32bits.

Here is the output of dmesg:
> 
[  356.175717] usb 3-1: new full speed USB device using uhci_hcd and address 5
[  356.364786] usb 3-1: config 1 has an invalid interface number: 6 but max is 4
[  356.364791] usb 3-1: config 1 has an invalid interface number: 7 but max is 4
[  356.364797] usb 3-1: config 1 has no interface number 3
[  356.364801] usb 3-1: config 1 has no interface number 4
[  356.383872] usb 3-1: configuration #1 chosen from 1 choice
[  356.400821] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:1:1: cannot get freq at ep 0x1
[  356.404758] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:1:2: cannot get freq at ep 0x1
[  356.409756] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:2:1: cannot get freq at ep 0x82
[  356.413789] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:2:2: cannot get freq at ep 0x82
[  357.277936] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:1:1: cannot get freq at ep 0x1
[  357.385720] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:2:1: cannot get freq at ep 0x82


I tried installing alsa-firmware-loaders but nothing happened. Of course the device doesn't appear in lsusb, but it appeared when I tried ```
aplay -l
```

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RP250 [DigiTech RP250], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Can anyone explain to me the nature of the problem ?

Thanx in advance

---

### Post by Stochastic on 2008-09-21
Hmm, google claims it should be supported by alsa - and your aplay results suggest that isn't the issue.  If I had to guess right now I'd say that those first couple lines of your dmesg output are the key.  Do you have many other USB devices plugged in?  Try unplugging them & rebooting, then just plug in the RP250.  Do you get the same results?

---

### Post by thelinuxer on 2008-09-21
> **Stochastic said:**
> Hmm, google claims it should be supported by alsa - and your aplay results suggest that isn't the issue.  If I had to guess right now I'd say that those first couple lines of your dmesg output are the key.  Do you have many other USB devices plugged in?  Try unplugging them & rebooting, then just plug in the RP250.  Do you get the same results?

Thanx fpr replying. Tried your suggestion but lsusb still doesn't show the device. 
I noticed something funny. I was wearing my headphones ( which are plugged into the RP250), and I started watching a video on youtube. The sound came out of my headphones and not from the speakers. I think although there is a problem reported in dmesg, the device is connected and working !

What I want to do is to use my computer and the sub woofer attached to it as an amplifier for my guitar, is that possible using the usb connection ?

---

### Post by Stochastic on 2008-09-22
> **thelinuxer said:**
> What I want to do is to use my computer and the sub woofer attached to it as an amplifier for my guitar, is that possible using the usb connection ?

Yeah, that should be fine - once the card starts behaving proper.

Oh but be warned you won't get any nice overdrive characteristics that you would from a normal amp - just digital distortion.
Unless you add overdrive as an effect through jack rack or something.

---

### Post by thelinuxer on 2008-09-22
> **Stochastic said:**
> Yeah, that should be fine - once the card starts behaving proper.

Oh but be warned you won't get any nice overdrive characteristics that you would from a normal amp - just digital distortion.
Unless you add overdrive as an effect through jack rack or something.

I was wondering if there was a howto about this some where.

---

### Post by desowin on 2009-04-01
There's [Digitech library utility for Linux](http://desowin.org/gdigi/) available

---

