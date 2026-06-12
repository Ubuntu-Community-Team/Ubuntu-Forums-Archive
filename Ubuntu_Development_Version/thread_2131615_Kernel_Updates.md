---
title: "Kernel Updates"
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-04-02
Whenever I get a Kernel Update via Software Updater the Updater seems to stop at Preparing installation of linux-image-3.8.0-xx-generic, e.g today's round of updates it seems to have frozen at Preparing installation of linux-image-3.8.0-16-generic, has the updater crashed or does it just take along time when it comes to Kernel updates?

Roland

---

### Post by wojox on 2013-04-02
I installed via cli this morning and the new kernels hung the system on reboot. Something sounds strange with today's images.

---

### Post by roly33 on 2013-04-02
With the last Kernel image 3.0.8-15-generic crashed the Updater and after a reboot I was unable to run Software Updater, causing me to have to do a re-install and the Kernel updated fine.

Looks like that might be on the cards again.

Roland

---

### Post by clive littlewood on 2013-04-02
Hi

This happened to me also (from UK servers)

frozen at Preparing installation of linux-image-3.8.0-16-generic     

Will check again later.

PS. can stil run the updater after reboot, then freezes again.

Clive

---

### Post by philinux on 2013-04-02
> **roly33 said:**
> Whenever I get a Kernel Update via Software Updater the Updater seems to stop at Preparing installation of linux-image-3.8.0-xx-generic, e.g today's round of updates it seems to have frozen at Preparing installation of linux-image-3.8.0-16-generic, has the updater crashed or does it just take along time when it comes to Kernel updates?

Roland

Happens every time with software updater. It also says it has been bugged but redirect to launchpad fails to "have u lost spmething".

I'm using cli now for kernel updates.

---

### Post by philinux on 2013-04-02
> **roly33 said:**
> With the last Kernel image 3.0.8-15-generic crashed the Updater and after a reboot I was unable to run Software Updater, causing me to have to do a re-install and the Kernel updated fine.

Looks like that might be on the cards again.

Roland
No need just do sudo apt-get install -f

---

### Post by Frogs Hair on 2013-04-02
This has been reported by others and not just for kernel updates. I have been sticking to synaptic and the terminal for updates.

---

### Post by sgage on 2013-04-02
No problem with the update using Synaptic.

---

### Post by rburkartjo on 2013-04-02
i also am just updating from the terminal and have no problems when the kernel is updated.

---

### Post by craig10x on 2013-04-02
Had the same problem also this morning...software updater froze on the kernel update...had to fix it (just like the last time) by going into package manager and upgrading the currently installed kernel with the newly downloaded one...once it installed it, i re-booted, ran software updater and it worked fine again, noted that my system was up to date...

I assume this rather serious bug has been reported?
Seems to do it ONLY when there is a kernel update...downloads it fine but can't install it through the software updater...

---

### Post by dino99 on 2013-04-02
****I assume this rather serious bug has been reported? ******

better to report & let Apport doing its job; if its a dupe, then it will be marked.

**** if a bug is not reported, then its not a bug, as no one knows about it. ******

---

### Post by slickymaster on 2013-04-02
+1, updating from the terminal and it just hangs there. Several tries, always the same result. 

Also, tried once through update manager and after a while it just crashed. Ended up filing a bug at Launchpad: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1163245](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1163245)

---

### Post by craig10x on 2013-04-02
thanks for reporting it...i find you can easily fix it in the package manager...just type linux-kernel and locate the old and new kernels (it's already been downloaded by software updater) you should see a
! mark next to the current kernel, click on to that and select "upgrade" and package manager will install the new kernel for you and after that, software updater works normal again (at least until the next kernel update...lol)...

i did follow the crash report over to launchpad and report it in that manner too...everyone should do that....

---

### Post by slickymaster on 2013-04-02
> **craig10x said:**
> thanks for reporting it...i find you can easily fix it in the package manager...just type linux-kernel and locate the old and new kernels (it's already been downloaded by software updater) you should see a
! mark next to the current kernel, click on to that and select "upgrade" and package manager will install the new kernel for you and after that, software updater works normal again (at least until the next kernel update...lol)...

i did follow the crash report over to launchpad and report it in that manner too...everyone should do that....

Yeah. That's what I finally ended up doing this morning, after filling the bug. In any case thanks anyway for the pointer.

---

### Post by philinux on 2013-04-02
apport says the bug is no. 1026149 but goes to a lost something launchpad page. No sign of that bug. Odd.

---

### Post by slickymaster on 2013-04-02
> **philinux said:**
> apport says the bug is no. 1026149 but goes to a lost something launchpad page. No sign of that bug. Odd.

You are referring to [Bug #1163245]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1163245"), right?

---

### Post by philinux on 2013-04-02
> **slickymaster said:**
> You are referring to [Bug #1163245]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1163245"), right?

No. The bug I'm referring to is the one that apport crash detection says is linked to software updater crashing.

---

### Post by slickymaster on 2013-04-02
> **philinux said:**
> No. The bug I'm referring to is the one that apport crash detection says is linked to software updater crashing.

Yes, you're right.

I tried to look it myself but strangely there is no bug  #1026149 in update-manager. Sorting by bug number, you go from #1026060 to #1026257. It's odd indeed.

---

### Post by dino99 on 2013-04-02
> **philinux said:**
> No. The bug I'm referring to is the one that apport crash detection says is linked to software updater crashing.

might be set as "private"

---

### Post by hfa2010 on 2013-04-02
I had problem upgrading today to kernel 3.8.0-16 as the software update got stuck and i had to finish and remove the lock. I solve the problem by running sudo apt-get install  linux-image-3.8.0-16-generic on the terminal. And then sudo apt-get  update && sudo apt-get dist-upgrade&#65279;. Noting that after i got the error on software updater i went to terminal, ran sudo dpkg --configure -a and saw a error about linux-image-generic being dependent on linux-image-3.8.0-16-generic but that wasn't being to be installed. So i installed it and solve the problem. Seems like a error on the script of software updater or on it's dependencies cache or something.

---

### Post by zika on 2013-04-02
It seems to me that SWU has a problem with recognizing and initiating dist-upgrade needed to upgrade kernel-set...

---

### Post by anarchticgrimm on 2013-04-02
I've had the exact thing with, what, last 2 kernel updates.. Updating via CLI has no problems though. Seems to be a problem within Software Updater itself. - In fact, I don't know why I was using Software Updater anyways. I was always in love with Terminal.

---

### Post by mörgæs on 2013-04-03
We have quite a few automatic bug reports: 
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1161306](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1161306)

---

