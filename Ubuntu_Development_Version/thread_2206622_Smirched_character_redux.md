---
title: "Smirched character redux"
date: 2014-02-19
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-02-19
I seem to have run into ventrical's **smirched** character problem. It started after the compiz updates over the last couple of days. I was using the nvidia-331 binary driver, and I've also tried nvidia-331-updates, and the problem hasn't been solved. I'm currently running the nouveau driver, but I very occasionally get a hard lockup, that only a cold reboot will solve.

This installation was fresh when the toolchain was uploaded, and I was hoping to run it all the way through this development cycle, but I am willing to create a new install on another partition just to see if it is because of kruftiness on the original installation.

---

### Post by Mateusz Stachowski on 2014-02-20
For all I know this is a bug in Chromium/Chrome not Compiz/Unity. There are several people on Arch Linux with the same problem.

[https://code.google.com/p/chromium/issues/detail?id=55458](https://code.google.com/p/chromium/issues/detail?id=55458)

---

### Post by QDR06VV9 on 2014-02-20
My fonts display as advertised but since yesterdays fresh install I have random smirches without chromium.I use nvidia-331 from xedgers.

---

### Post by ventrical on 2014-02-20
My smirching is coming strictly on firefox. Thanks for sharing you guys. I see that you are both using different browsers so it is not a ff problem or intel graphics only problem.

  My problem install was an original saucy salamander and then uploaded  the toolchain. Kept it original but had to re-install (without the format option) and the kept the 'smirching' still prevalent. I did a fresh install on the same machine (with nVidia 210/218) nouveau and so I will be keeping an eye on it.

regards..

btw .. It seems that the smirching comes when you magnify the screen using Ctrl + Shift + '+'. It takes soem time to show up . It is very capricious and often disappears when you scroll it out or de-magnify. I would guess compiz or other.. not drivers , ff of google.

---

### Post by cariboo on 2014-02-20
I had the problem with everything including osd notifications, it didn't matter what application I opened, it was there on synaptic, qbittorrent, thunderbird, chromium-browser or firefox. even the terminal. The problem is moot now, as the hard drive that my home partition was located on decided to take a dump, so I'll have to do a fresh install on another drive, and yes I did a backup last night before starting troubleshoot the problem.

---

