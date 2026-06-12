---
title: "Setting USB Soundcard as primary ALSA device."
date: 2009-11-03
forum: Ubuntu Studio
---

### Post by Vigh on 2009-11-03
Hi I was just wondering if there was a configuration file I could edit to set my usb device as primary device. I am running latest ALSA 1.0.21. And the soundcard is an NI Audio Kontrol 1. Cheers

---

### Post by AutoStatic on 2009-11-03
You can achieve this by modifying your */etc/modprobe.d/alsa-base.conf* file. You have to add the following line:
```
options snd-card-usb-caiaq index=0
```
What this line does is telling Alsa to assign hw0 to your NI device.

---

