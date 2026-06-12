---
title: "Ubuntu 6.10 on blade 150 - hanging on install boot"
date: 2006-10-31
forum: Sun Sparc Users
---

### Post by jfinn on 2006-10-31
I'm currently trying to install Ubuntu 6.10 on a blade 150.

After booting from the cd and entering:

boot: install

It will load the kernel and initial ramdisk and then it says:

[B]Remapping the kernel...done.
Booting Linux...[/B]

It just hangs there and goes nowhere.  I upgraded the OBP and problem persists.  Any ideas would be greatly appreciated.  (I attempted to load 6.06 as well and same thing happens.)

---

### Post by jfinn on 2006-11-01
It ended up being the video card.  I had to remove the PCI video card and go with the onboard card.  Also it would not boot 6.10 only 6.06.

---

### Post by morgano on 2006-11-15
I can confirm no boot on a Blade 100 (OBP 4.17.1) with 6.10](*,)

---

### Post by netztier on 2006-11-15
> **morgano said:**
> I can confirm no boot on a Blade 100 (OBP 4.17.1) with 6.10](*,)

Does the info from this thread (and other threads linked in there) help, especially the part with adding "append ide=nodma" as option when installting from CD-ROM? [Sun Blade 100]("http://www.ubuntuforums.org/showthread.php?t=255249&highlight=ide%3Dnodma").

But of course you've been searching the forums for "Sun Blade 100" and you have read all of these threads, and you've doubtlessly been trying all of these hints, haven't you :rolleyes: 

regards

Marc

---

### Post by morgano on 2006-11-15
I've read everything I could find on the forum for Blade 100/150/etc and Ubuntu 6.10 ... It seems to be the kernel causing the problem, there are multiple posts reporting failure to boot after apt-get upgrade involving the 2.6.17/18 version. I guess I'll install 6.06 and upgrade while holding back the kernel, that should get me running. :-?

---

### Post by Delta_Farce on 2006-11-16
I've had the same problem with 6.10 on my Sunblade 150 (both doing a dist upgrade and doing a clean install with a 6.10 server disk).

6.06 works a treat though so I guess I'll stick with that for now.

---

### Post by shoki on 2007-02-18
I was also not able to get 6.10 running with ide=nodma.

Burned a 6.06 disc and no problems. Not sure what is going wrong but I am happy I got the OBP upgraded and at least started to get ubuntu running on this thing :)

---

