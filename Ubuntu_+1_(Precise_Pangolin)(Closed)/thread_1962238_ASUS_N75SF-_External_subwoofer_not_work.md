---
title: "ASUS N75SF- External subwoofer not work"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neco198 on 2012-04-20
Hi all,
How do I set it to subwoofer work?
I have Ubuntu 12.04 64x (amd64).

---

### Post by VinDSL on 2012-04-20
Hrm...

What kind of sub are you using?!?!?

Currently, I'm running an Old Skool Altec-Lansing Multimedia model ACS-45 setup (the original - the ones Dell used to sell in the last century) and my sub works just fine.

---

### Post by neco198 on 2012-04-21
[http://laptopreviewshop.com/wp-content/gallery/asus_n55_subwoofer/img_2468.jpg](http://laptopreviewshop.com/wp-content/gallery/asus_n55_subwoofer/img_2468.jpg) 
Default subwoofer 
I found this [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808) 
 ... but i cant to set to work.

---

### Post by neco198 on 2012-04-23
I add on **etc/modprobe.d/alsa-base.conf **and add this line: **options snd-hda-intel model=asus-mode4**
and now working. :D

---

