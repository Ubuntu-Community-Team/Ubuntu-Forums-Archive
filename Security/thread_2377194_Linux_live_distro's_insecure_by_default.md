---
title: "Linux live distro's insecure by default"
date: 2017-11-10
forum: Security
---

### Post by alwayshacked on 2017-11-10
So a linux live distro is a historical snapshot of a linux distro, so considering the first thing someone needs to do is update the OS and some updates need a reboot before they work properly yet these are never burnt to optical disc, how does someone make a linux live distro secure? 

It seems that using linux live distro's from an optical disc and quite possibly a USB memstick, is a futile circular activity, unless someone knows different?

If someone does know different, would they care to share how to get around this problem?

---

### Post by C.S.Cameron on 2017-11-10
You can encrypt the home of a Full or Persistent install and encrypt partitions also.
The only thing written to in many persistent installs, such as UNetbootin, YUMI and Universal make, is one file named casper-rw, and maybe swap. Swap can be turned off.
If you want an OS built for security, have a look at Tails, Swap is turned off by default and if you choose encrypted persistence, you can choose what class of items you wish to save.

---

### Post by alwayshacked on 2017-11-10
That works for encrypted installations, but the Intel ME and AMD PSP means they can still have clear site of your system as these are just coprocessors just like the old days when co-processors existed on the earliest pc. 

It still doesnt address a live cd which needs updating as its first step before anything else takes place online. Likewise there's also the rare but not unheard of instance of compromised mirrors.

---

### Post by wildmanne39 on 2017-11-10
Live version of Ubuntu is just for testing so it is assumed you will either install it in a few minutes or not use it at all, it is not a long term version, you can make a persistent usb drive if you want to use the OS without installing it.

---

### Post by C.S.Cameron on 2017-11-11
Did you have a look at Tails?

[https://tails.boum.org/index.en.html](https://tails.boum.org/index.en.html)

---

### Post by HermanAB on 2017-11-12
If you are paranoid, then you need to be paranoid about the whole system, end to end, starting at the mirror server used to get the install files from.  This is required if you are building systems for a large corporation, a bank, a defence contractor, or government entity.  In this case, you will likely be mandated by the powers that be, to use Redhat or OpenBSD, not Ubuntu.

If you are in a normal situation, then you can relax a bit and just use the Live CD - it will be fine for the little bit of use that it will get.

---

