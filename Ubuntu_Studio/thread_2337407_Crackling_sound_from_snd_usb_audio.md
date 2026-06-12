---
title: "Crackling sound from snd_usb_audio"
date: 2016-09-17
forum: Ubuntu Studio
---

### Post by eggplant3 on 2016-09-17
Hi,

I think that the low latency kernel 4.4.0-36-lowlatency and snd_usb_audio that comes with 16.04.01 is buggy. I get crackling sound from my Soundcraft Signature 12MTK with both jack, pulseaudio and pure alsa. With my work laptop (opensuse tumbleweed) I have no crakling at all with a stock kernel (4.7.2-2-default) and pulseaudio or jack. Is this a know issue with 16.04.01?

---

### Post by #&amp;thj^% on 2016-09-17
This one helped me: (Static and crackling in my audio?)

edit with your favorite editor

```
/etc/pulse/default.pa
```

look for

```
load-module module-udev-detect
```

add **tsched=0 **So it now looks like below.

```
load-module module-udev-detect tsched=0
```

reboot

---

### Post by eggplant3 on 2016-09-19
Thanks for the reply. But the same static and crackling as before. But it got me a starting point to figure out the problem. To many usb devices on the same interrupt. I'll report back in a few days.

---

### Post by #&amp;thj^% on 2016-09-19
I have also seen with Newer intel audio chips that the solution was to add a line in "alsa-base.conf"
The Chips that this fix was used on were: "Intel Z97/H97"
If you are unsure which chip you have...use inxi to get it.
```
inxi -A
```
But the work-around they used went like this:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

Add options"**snd-hda-intel vid=8086 pid=8ca0 snoop=0" **at the end of the file.

Restart PC

---

