---
title: "Ubuntu 13.10 Virtualbox host very slow"
date: 2013-10-24
forum: Virtualisation
---

### Post by hornetster on 2013-10-24
Have been running a Windows 8 guest in virtualbox on a couple of linux hosts basically since release.
Initially setup running Virtualbox on Opensuse, and worked fine there, but shortly after setup, I installed Ubuntu 13.04 as a host, to test, and immediately noticed issues with speed, both on the host ubuntu PC, and in the Win8 guest. Fiddled with Virtualbox there, installing directly from the Virtualbox website downloads, and also the Ubuntu Software Centre downlaods, and continued having issues with speed. Eventually gave up, and went back to Opensuse, which has worked fine since then for many months.
With the release of Ubuntu 13.10, again thought I would try.
Have installed 13.10 (x64 - Clean install, but using the original home directory), and it is fully patched. Virtualbox installed (4.2.16_Ubuntu r86992 + relevant Extensions + Guest Additions. Guest machine has been updated to Win8.1 - and tested in Opensuse), have tried enabling/disabling 2D/3D acceleration, have enabled IO APIC etc, and my PC is still basically unusable (does work, but probably 1/5 normal pace - apps keep "graying out" waiting to process, etc.)
Was hoping I could use Ubuntu 'full-time', at least for a period, but if this continues, will be going back to openSuse very shortly.
Appreciate any thoughts.
Thanks.

---

### Post by hornetster on 2013-10-28
Anyone?

---

### Post by ian-weisser on 2013-10-28
My Windows XP guest runs the same speed under hosts on 12.04, 12.10, 13.04, and 13.10.
I don't have a slowdown under 13.10.

---

### Post by SeijiSensei on 2013-10-28
Have you tried giving Windows a bit more physical memory?

---

### Post by TheFu on 2013-10-28
Good first steps, but .... 
is the virtual HDD on a spinning disk (not SSD)?  If so, preallocating the entire storage (do not use sparse) will greatly improve performance. Sadly, this it the main setting that cannot be fixed later easily.  Sure, you can add another vHDD that is pre-allocated, then dd the older one over and remove the older one, rename the new-file to the old-filename ... done, but that is not as trivial as toggling a checkbox in a GUI. ;)

---

### Post by novo2809 on 2013-11-27
I believe hdd and graphic card are the problem to slow your host down. If you dont have enough memory in your host, maybe ubuntu take/use swap space which will even slow your system even more.

---

### Post by TheFu on 2013-11-27
All my wisdom about virtualbox performance is here: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) Alas, I've never tried Win8-anything. I hope it helps. More facts would be helpful - exact HW specs, exact settings ... or you can just try the detailed settings that I've outlined in that article.  I has worked for many others.

---

