---
title: "Broken USB Audio after upgrade to 3.10.0-4-generic"
date: 2013-07-20
forum: Ubuntu Development Version
---

### Post by zonum on 2013-07-20
I have a C-Media USB Audio Device that has been working without issues prior to 3.10.0-4, but since yesterday when I upgraded to it, the system does not see the USB audio device any longer via the Sound Settings.  I did boot with 3.10.0-3 and it does show as an audio device and it works.

Similarly, my Logitech QuickCam Pro 9000 also "broke" with the upgrade to 3.10.0-4 (it does work on 3.10.0-3).

Anyone experiencing similar issues on Saucy as of today (Jul 20) with 3.10.0-4?

Thanks,
zonum

---

### Post by zonum on 2013-07-20
One additional piece of information.  In /var/log/syslog, I am getting this error now:

kernel: [    2.612236]  snd_usb_audio: Unknown parameter `index'

Thanks,
zonum

---

### Post by deri on 2013-07-20
better to report the issue on linux kernel mailing list

---

### Post by zonum on 2013-07-20
I resolved (bandaid?) the issue I was having with the USB audio.

In essence I had to comment out all entries of "options snd-usb-audio index=-2" in /etc/modprobe.d/alsa-base.conf, then removed and re-inserted the USB audio device and all was well.

Thanks,
zonum

---

