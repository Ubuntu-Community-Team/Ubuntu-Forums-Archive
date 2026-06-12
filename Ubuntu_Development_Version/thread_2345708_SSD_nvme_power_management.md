---
title: "SSD nvme power management"
date: 2016-12-07
forum: Ubuntu Development Version
---

### Post by fthx on 2016-12-07
Hi,

Does somebody know the shape of nvme drives power management, running recent kernels (e.g. 4.9 !) on Ubuntu ?

Thanks !

---

### Post by dino99 on 2016-12-07
Found that related discussion  [https://mjg59.dreamwidth.org/41713.html](https://mjg59.dreamwidth.org/41713.html)

---

### Post by fthx on 2017-02-14
Hi,

It seems that kernel 4.10 does not contain the APST patch. There is :
                                                  [https://github.com/damige/linux-nvme](https://github.com/damige/linux-nvme) (for Arch)
[http://lists.infradead.org/pipermail/linux-nvme/2017-February/008051.html](http://lists.infradead.org/pipermail/linux-nvme/2017-February/008051.html)

Will CKT include this patch in Zesty's 4.10 kernel ?
The power management leak causes huge battery drain vs SATA drive.

---

### Post by dino99 on 2017-02-14
is a launchpad/upstream bug report already exist ? if not, maybe you should do  :confused:

---

### Post by fthx on 2017-02-14
Here we go !
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602)

---

### Post by dino99 on 2017-02-14
an other report [https://bugzilla.kernel.org/show_bug.cgi?id=116671](https://bugzilla.kernel.org/show_bug.cgi?id=116671)

---

### Post by fthx on 2017-02-21
Maybe some hope :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666401](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666401)

---

### Post by fthx on 2017-02-23
It will be in 4.11 anyway :
[http://lists.infradead.org/pipermail/linux-nvme/2017-February/008422.html](http://lists.infradead.org/pipermail/linux-nvme/2017-February/008422.html)

---

### Post by fthx on 2017-02-25
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=1802979ab1ee8ec5a72987ad518f5a91bf41cd89](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=1802979ab1ee8ec5a72987ad518f5a91bf41cd89)
pulled for 4.11.

---

### Post by The__Doctor on 2017-02-27
I own a Dell XPS 13, is there anything I can do to manually install the patch for NVMe powersaving?

---

### Post by fthx on 2017-02-28
AFAIK you have to compile the Ubuntu 4.10 kernel including yourself the patch...

My advice is to simply wait for the CKT's patched 4.10 kernel for Zesty, Y and X. If I have understood correctly [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666401](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666401) coming from a Canonical people, the APST patch should be applied for XYZ Ubuntu releases.

IMHO it would be terrible if not, as Linux with TLP has proven a very good power usage these years on laptops. But not running NVMe at the moment.

---

### Post by fthx on 2017-03-06
I'm back to 4.23 W IDLE with 4.11 RC1 with NVMe APST Andy Lutomirski's patch.

Great ! Hope it will be here in 4.10 Ubuntu soon.

---

### Post by The__Doctor on 2017-03-08
Looks like from launchpad that there's a committed fix for both zesty and xenial (which I use).

---

### Post by fthx on 2017-03-09
If you have a link ?
I only have rather bad news :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602)

---

### Post by The__Doctor on 2017-03-12
I was just going off this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666401](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666401)

---

### Post by fthx on 2017-03-13
That's I wrote at latest post from [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1664602]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602") : I don't understand such a patch if it's to not release some NVMe APST stuff for Zesty. I must have missed one step.

---

### Post by fthx on 2017-03-15
Please give some feedback from this 4.10 APST patched kernel from Canonical dev :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602/comments/20](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602/comments/20)
(no Nvidia support at the moment, but you can boot as Intel with proprietary drivers without issue).

It's fully working now in my laptop. Roughly as good as 4.11 for power management.

---

### Post by fthx on 2017-03-16
Patched in Zesty's kernel !
[https://lists.ubuntu.com/archives/kernel-team/2017-March/083013.html](https://lists.ubuntu.com/archives/kernel-team/2017-March/083013.html)

---

### Post by dino99 on 2017-03-17
Some more fixes from canonical-kernel ppa with 4.10.0.14

 * Using an NVMe drive causes huge power drain (LP: #1664602)
    - nvme: Add a quirk mechanism that uses identify_ctrl
    - nvme: Enable autonomous power state transitions

---

### Post by fthx on 2017-03-17
That's the same fixes. ;)
It's being built at the moment...

---

### Post by fthx on 2017-03-19
solved, finally !

---

