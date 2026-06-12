---
title: "UEC - Xen enabled kernel 2.26.32.21 for download - to be used with Lucid lynx"
date: 2010-06-09
forum: Server Platforms
---

### Post by sathya288 on 2010-06-09
I am experimenting with Ubuntu enterprise Cloud. The machines I have do not support hardware virtualization. Even though, my UEC set up works fine, when I launch an instance ( euca-run-instance), the instance goes to pending->shutting down->terminated states.

Now, I want to try UEC with Xen. Building the kernel with xen patch all the way from source is quite tedious. ( [http://bderzhavets.wordpress.com/2010/04/24/set-up-ubuntu-10-04-server-pv-domu-at-xen-4-0-dom0-pvops-2-6-32-10-kernel-dom0-on-top-of-ubuntu-10-04-server/](http://bderzhavets.wordpress.com/2010/04/24/set-up-ubuntu-10-04-server-pv-domu-at-xen-4-0-dom0-pvops-2-6-32-10-kernel-dom0-on-top-of-ubuntu-10-04-server/)) 

Is there someplace from where I can download the kernel that has dom0 support. I am using 10.04 kernel 2.6.32-21. I need the Xen enabled 2.6.32-21 kernel that would be compatible with 10.04 Lucid Lynx

---

### Post by stlsaint on 2010-06-09
Maybe these can get you started:

1. Go [here]("http://www.kernel.org/pub/linux/kernel/v2.6/") to view changelogs of kernels.

2. Go [here]("http://www.kernel.org/") to download source.

---

### Post by sathya288 on 2010-06-09
I could not find any xen enabled kernels (2.6.32-21) in the location you mentioned.

---

### Post by stlsaint on 2010-06-09
Are you sure you have the correct kernel version?

---

### Post by sathya288 on 2010-06-10
I can find the standard kernel at kernel.org. But what I need is a xen enabled one.
I could find one such at [http://packages.debian.org/lenny-backports/linux-image-2.6.32-bpo.4-xen-686](http://packages.debian.org/lenny-backports/linux-image-2.6.32-bpo.4-xen-686).
But it is a different issue that after I installed this I get a kernel panic (on reboot).

Btw, to restate my requirement, I am looking for a xen dom0 kernel that will run on LucidLynx (kernel 2.6.32-21)

---

### Post by sathya288 on 2010-06-10
oops ... I mistyped it as "2.26.x" it should be "2.6.32-21". But this is what I used throughout and so the content of the above posts are still valid.

---

