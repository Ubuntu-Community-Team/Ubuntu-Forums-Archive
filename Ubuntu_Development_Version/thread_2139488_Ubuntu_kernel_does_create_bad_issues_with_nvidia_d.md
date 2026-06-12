---
title: "Ubuntu kernel does create bad issues with nvidia drivers"
date: 2013-04-27
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-04-27
My setup is AMD64 with Nvidia 285GTX.
I use Gnome3 and Gnome3 Staging PPA, so I have the new logind in use (instead of consolekit).
In fact I have purged the packages consolekit and libck-connector0.

After upgrading to logind startup system, I noticed a new and strange behaviour during the booting process.
Suddenly booting stopped right where gdm should start. TTY1 was fine and I was able to command "startx" - and then the DE was up.
This started during the late raring dev cycle with the RR official 3.8.0 kernel.

Then I tried the mainline 3.9 rc8 kernel and the booting issue was immediately gone.

Later, turning to saucy dev cycle (keeping the Gnome3 and Gnome3 Staging, raring branch, enabled),
I installed the SS official 3.9.0 kernel, which is also rebased to 3.9 rc8.
The booting issue came right back.
And just to be sure, installing the mainline kernel back, the issue was solved again.

Now there is something in Ubuntu flavor of the linux kernel, that does not work very well with Nvidia proprietary drivers and causing the booting process to hang.
So now I stick to mainline kernel.

This may or may not have something to do with the HDMI sound issues with Ubuntu kernels.

---

### Post by dino99 on 2013-04-27
hm, i think that the "staging" packages have something related with your issue; maybe purge that ppa. I use 313-updates here on i386 with gnome3 ppa (but not "staging") and have no trouble with raring/saucy kernels. I've chosen lightdm here.

---

### Post by pqwoerituytrueiwoq on 2013-04-27
The issues with nvidia and hdmi audio (nvidia/ati/intel) are known issues with the 3.8.0-18 and 3.8.0-19 kernels; this issues is Ubuntu's there is no issues upsteam, they should have a fix out in a few days, till then there is the [mainline kernel](http://ubuntuforums.org/showthread.php?t=2127673) <-- linked to easy installer/updater for it

---

### Post by Harry33 on 2013-04-27
> **pqwoerituytrueiwoq said:**
> The issues with nvidia and hdmi audio (nvidia/ati/intel) are known issues with the 3.8.0-18 and 3.8.0-19 kernels; this issues is Ubuntu's there is no issues upsteam, they should have a fix out in a few days, till then there is the [mainline kernel]("http://ubuntuforums.org/showthread.php?t=2127673") <-- linked to easy installer/updater for it

Well yes I know. Now the issue here is not actually HDMI. I do not even use HDMI audio output, but the analog one instead.
However, I can very well see this also with the saucy kernel 3.9.0 (rebased to 3.9.0 rc8).
But like I said, not with the mainline kernel. That works perfectly.

In addition, I did notice this behaviour rigth after I switched to logind.

---

### Post by Harry33 on 2013-04-27
> **dino99 said:**
> hm, i think that the "staging" packages have something related with your issue; maybe purge that ppa. I use 313-updates here on i386 with gnome3 ppa (but not "staging") and have no trouble with raring/saucy kernels. I've chosen lightdm here.

You may very well be correct.
I did notice this behaviour right after I switched to logind (from Gnome3 Staging PPA).
I use nvidia-319.12 driver and pure gnome-shell with gdm.

However, ATM I am happy with the mainline kernel.

---

