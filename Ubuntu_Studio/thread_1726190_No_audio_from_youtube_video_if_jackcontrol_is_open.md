---
title: "No audio from youtube video if jackcontrol is open"
date: 2011-04-10
forum: Ubuntu Studio
---

### Post by ubnewbie2 on 2011-04-10
I am using a Yamaha Audiogram6 USB device and I have discovered that if I have jackcontrol running, even if it is stopped, I cannot get any sound from youtube videos in Firefox.  As soon as I quit jackcontrol, the sound starts working from Firefox.

---

### Post by Pablo_F on 2011-04-11
Hi,

You can either "jackify" the flash player or play pulseaudio through jack. See

[http://ubuntuforums.org/showthread.php?t=1717272](http://ubuntuforums.org/showthread.php?t=1717272)

---

### Post by ubnewbie2 on 2011-04-11
> **Pablo_F said:**
> Hi,

You can either "jackify" the flash player or play pulseaudio through jack. See

[http://ubuntuforums.org/showthread.php?t=1717272](http://ubuntuforums.org/showthread.php?t=1717272)


I see. I appreciate the answer. That is so complicated however.  

I might have to put up with a workaround that I came up with a short time ago.  That is, I left the system sounds (and flash etc) set to use the soundcard on the motherboard.  I can then feed the soundcard output to a spare input on the Yamaha mixer/usb interface using a physical cable - or just let it play through the computer speakers.

---

