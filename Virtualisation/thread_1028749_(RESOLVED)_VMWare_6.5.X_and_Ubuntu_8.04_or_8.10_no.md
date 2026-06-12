---
title: "(RESOLVED) VMWare 6.5.X and Ubuntu 8.04 or 8.10 no sound /dev/dsp /dev/dsp1"
date: 2009-01-02
forum: Virtualisation
---

### Post by ljerabek on 2009-01-02
I've seen many posts about Audio issues with VMWare 6.5.X and Ubuntu 8.04 or 8.10 this has worked for me everytime and I hope it will work for you.

To resolve the WMWare 6.5.X audio issue in Ubuntu 8.04 and Ubuntu 8.10 change the device. Instead of using /dev/dsp or /dev/dsp1 or Auto Detect just simply use /dev/audio by typing it in manually in VMware. Hope this helps I have had no issues. My systems are using Alsa Mixer which I think is default.

Regards,

Lu

---

### Post by mitchs on 2009-02-20
yes works for me, but be aware if you are parallelly running a flash applet the sound won't work.

---

