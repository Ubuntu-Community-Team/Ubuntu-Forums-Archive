---
title: "vmware unable to fnd kernel headers for running kernel"
date: 2012-02-01
forum: Virtualisation
---

### Post by SuiCiDeSiNiSTeR on 2012-02-01
title says it.. ive googled. 
 tried  sudo apt-get install linux-headers-`uname -r`  and i get ...
E: Unable to locate package linux-headers-2.6.32-38-generic
E: Couldn't find any package by regex 'linux-headers-2.6.32-38-generic'
ive googled for the source for 2.6.32-38 and find nothing
ive tried updatig kernels for some reason when i try to boot into 2.6.35-32 kernel it hangs on black screen with blinking cursor. ive also tried the kernels in between my current 2.6.32-38 and the 2.6.35-32 and they hang aswell.
any and all help is greatly appriciated.

---

### Post by toddkaufmann on 2012-02-09
What version of ubuntu is running that kernel?  or have you just not updated it in a long time?

Try linux-headers-2.6.32-38-server instead?


It seems I have to reconfigure vmware and rebuild the modules everytime there is a kernel update, or maybe even every time my server reboots.

I installed the headers once, and now it seems like I get them installed automatically with kernel updates,
the most recent being 2.6.38-13 on 1/24 (for 11.04).

---

