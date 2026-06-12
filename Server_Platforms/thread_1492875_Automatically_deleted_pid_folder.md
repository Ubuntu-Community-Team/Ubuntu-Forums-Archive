---
title: "Automatically deleted pid folder"
date: 2010-05-25
forum: Server Platforms
---

### Post by karesmakro on 2010-05-25
Hello there!
I'm new to Ubuntu (at least on server distributions). I used debian versions for a long time and thought, to try ubuntu LTS 10.0.4, because of the long time support cycle.

I had problems, to install this distribution on a x86 plattform (used with ASUS P4B533-v), because of kernel panic after installation. So I used a trick to get it running. I installed Ubuntu LTS 8.04 and compiled a kernel 2.6.34 and made a distupgrade. All went o.k. and is now running as a productiv system.

My question now belongs to the used pid folder /var/run. I'm using some self compiled programs and had to create a separatly folder (e.g. /var/run/stunnel). My problem is, after rebooting the system, the folder is deleted automatically! Never saw this issue on other distributions. Is there any reason why?
Of course, I can write a section in my init script, searching for existing folder and if not, creating it ... 

I hope, someone can direct me to the point, where to search!

regards

---

### Post by cdenley on 2010-05-25
/var/run is mounted as a tmpfs filesystem. Nothing of any significant size is stored there, yet it is used often, and nothing in that directory should need to be persistent, so why store it on disk? It gets written to memory, so nothing written to that directory will remain after a reboot.

---

### Post by karesmakro on 2010-05-25
O.k., I understand! Thank you, for your quick reply!

---

