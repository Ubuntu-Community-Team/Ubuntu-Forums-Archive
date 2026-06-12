---
title: "Kernel 3.6 rc7"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-09-25
The Linux 3.6-rc7 mainline kernel is out now.

nVidia 304.51 is available in the Edger's PPA too...  :)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-24-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-sep-2012-2.png")[/INDENT]

---

### Post by synaptix on 2012-09-26
Using kernel 3.6.0-rc7 currently on Xubuntu 12.10 with open source radeon drivers, working perfectly. :)

---

### Post by jfernyhough on 2012-09-26
All good for me! xserver 1.12, fglrx 9.00. Kubuntu and Ubuntu.

---

### Post by robtygart on 2012-09-26
Links? or could someone point me in the right direction?

---

### Post by VinDSL on 2012-09-26
> **robtygart said:**
> Links? or could someone point me in the right direction?
Generally: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)

Specifically:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/)

---

### Post by Starks on 2012-09-26
Is 3.6 going to make the kernel freeze?

---

### Post by serdotlinecho on 2012-09-27
I'm using kernel 3.6rc7 now on samsung n148 plus netbook. With kernel 3.5, ubuntu always kernel panic or blank screen at boot.
```
root@quantal:~# cat /etc/issue.net;uname -r;lspci | egrep 'VGA|Network';dpkg -l | grep linux-image
Ubuntu quantal (development branch)
3.6.0-030600rc7-generic
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ii  linux-image-3.5.0-14-generic                  3.5.0-14.19                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-15-generic                  3.5.0-15.23                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.6.0-030600rc6-generic           3.6.0-030600rc6.201209161835              i386         Linux kernel image for version 3.6.0 on 32 bit x86 SMP
ii  linux-image-3.6.0-030600rc7-generic           3.6.0-030600rc7.201209232235              i386         Linux kernel image for version 3.6.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-14-generic            3.5.0-14.19                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-15-generic            3.5.0-15.23                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.6.0-030600rc6-generic     3.6.0-030600rc6.201209161835              i386         Linux kernel image for version 3.6.0 on 32 bit x86 SMP
ii  linux-image-extra-3.6.0-030600rc7-generic     3.6.0-030600rc7.201209232235              i386         Linux kernel image for version 3.6.0 on 32 bit x86 SMP
ii  linux-image-generic                           3.5.0.15.15                               i386         Generic Linux kernel image
ii  linux-image-generic-pae                       3.5.0.15.15                               i386         Transitional package


```

---

### Post by IanW on 2012-09-27
> **Starks said:**
> Is 3.6 going to make the kernel freeze?

Kernel freeze is Oct 4th, so maybe it will. It's up to Linus whether 3.6 final is released by then.

---

### Post by robtygart on 2012-09-27
> **VinDSL said:**
> Generally: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)

Specifically:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/)


Thank you!

---

### Post by linuxvstheworld on 2012-09-27
> **VinDSL said:**
> The Linux 3.6-rc7 mainline kernel is out now.

nVidia 304.51 is available in the Edger's PPA too...  :)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-24-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-sep-2012-2.png")[/INDENT]

How'd you get that cool little thing where it shows the status of your computer on the right?

---

### Post by VinDSL on 2012-09-27
> **linuxvstheworld said:**
> How'd you get that cool little thing where it shows the status of your computer on the right?
It's called Conky.  Be warned (up front) it's very addictive!

There's a HOWTO link, in my sig.

I'm in the process of switching the weather feed to WU (Weather Underground) via Conkywx (a new app).

If you're interested in this sort of stuff, read the HOWTO on page-1, then fast-forward to the end of the thread.

I'll be doing a data dump, once I get all my ducks in a row, but that thread will give you the general idea...  ;)

---

### Post by thotz on 2012-09-28
> **serdotlinecho said:**
> I'm using kernel 3.6rc7 now on samsung n148 plus netbook. With kernel 3.5, ubuntu always kernel panic or blank screen at boot.


Here on my Thinkpad Edge E530 (Ivy Bridge) I get a kernel panic with the 3.6rc7 kernel.

Kernel 3.5 is working great here :)

---

### Post by linuxvstheworld on 2012-09-28
> **VinDSL said:**
> It's called Conky.  Be warned (up front) it's very addictive!

There's a HOWTO link, in my sig.

I'm in the process of switching the weather feed to WU (Weather Underground) via Conkywx (a new app).

If you're interested in this sort of stuff, read the HOWTO on page-1, then fast-forward to the end of the thread.

I'll be doing a data dump, once I get all my ducks in a row, but that thread will give you the general idea...  ;)

Do i need to download a repository to sudo apt-get install? Or is the repo already implemented in ubuntu and I can just sudo apt-get it?

---

### Post by cyrex on 2012-10-01
I also REALLY hope that 3.6 comes to 12.10. That would mean a 4 version jump from 3.2 to 3.6 and all the goodies that 3.6 brings: [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

---

### Post by thotz on 2012-10-01
> **cyrex said:**
> I also REALLY hope that 3.6 comes to 12.10. That would mean a 4 version jump from 3.2 to 3.6 and all the goodies that 3.6 brings: [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

I also think this is a great idea.

I have read somewhere that the kernel 3.5 won't be supported any more with updates because there's now Linux kernel 3.6.

---

### Post by IanW on 2012-10-01
[Kernel 3.6 now declared final.]("http://lkml.indiana.edu/hypermail/linux/kernel/1209.3/04237.html")

Linus is now looking at the first round of patches for 3.7.

---

### Post by VinDSL on 2012-10-01
> **Starks said:**
> Is 3.6 going to make the kernel freeze?

> **IanW said:**
> Kernel freeze is Oct 4th, so maybe it will. It's up to Linus whether 3.6 final is released by then.

> **cyrex said:**
> I also REALLY hope that 3.6 comes to 12.10.

> **thotz said:**
> I also think this is a great idea.

> **IanW said:**
> [Kernel 3.6 now declared final.]("http://lkml.indiana.edu/hypermail/linux/kernel/1209.3/04237.html")
Hopefully, Linux 3.6 will come to Ubu 12.10!

After all, it's a non-LTS release, yes?

What the heck!?!?!  Go for the gold...  :D

---

### Post by cariboo on 2012-10-01
Removed duplicate post.

---

### Post by cyrex on 2012-10-03
I have to add that after testing the released version of 3.6 a problem found here for me: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1060268](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1060268) looks solve. If the problem appears again I will mention it here, else I will be just enjoying my crash freeze Ubuntu.

---

### Post by IanW on 2012-10-04
Looks like it's not going to happen for the release version of Quantal after all.

After the official freeze, the latest version in proposed is 3.5.0-17.26

3.6 will hopefully land sometime before RR is released.

---

