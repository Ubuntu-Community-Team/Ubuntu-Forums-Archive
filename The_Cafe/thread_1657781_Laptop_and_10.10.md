---
title: "Laptop and 10.10"
date: 2011-01-01
forum: The Cafe
---

### Post by mamamia88 on 2011-01-01
Anyone else have a laptop and have a bunch of freezing on 10.10?  It's the main reason I'm searching for a new distro right now.  Went back to windows 7 a few months ago but really want to get back into the Linux world.

---

### Post by NightwishFan on 2011-01-01
Any periodic (non permanent) freezing I had was due to Compiz on the Nvidia drivers. Try burning a live cd, running the check to ensure it was burned right, and testing for a while from the live cd session. After the freezing, if it is not permanently stuck, check the logs for information.

---

### Post by what_indeed on 2011-01-01
I had the same problem, cpu froze & spiked every 9.5 sec.  I simply went to Update Manager and ran it, it downloaded a kernel patch automatically and the problem disappeared without even having to reboot!

---

### Post by kaldor on 2011-01-01
If you want something similar to Ubuntu, but not quite as easy/polished, go for LMDE. Link is in my sig below ;)

---

### Post by mamamia88 on 2011-01-01
yeah i tried LMDE before and everything seemed to work ok.  Thing is every time I downloaded an update for the xserver etc it would break comparability with the nvidia driver i installed

---

### Post by HermanAB on 2011-01-02
The freezing issues have been around for a long time.  The NVIDIA device drivers are buggy and they don't seem to improve with updates.  I have been running the generic VESA driver (the one Linux uses during the installation process) since I bought my laptop and it is now almost a year old.

BTW, my machine crashes in Windows 7 too - also due to the NVIDIA video driver - so going over to the dark side isn't a solution either and on a laptop one cannot change the video system.

Sooo, I'm stuck with stupid Nvidia and their crummy software.

---

