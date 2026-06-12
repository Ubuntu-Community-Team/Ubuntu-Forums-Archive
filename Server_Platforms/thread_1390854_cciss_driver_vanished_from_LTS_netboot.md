---
title: "cciss driver vanished from LTS netboot?"
date: 2010-01-26
forum: Server Platforms
---

### Post by Paul Weaver on 2010-01-26
I tried to build a HP DL380 today, and the drive wasn't detected. Suspecting hardware issues, I tried it on a 360, same issue.

We built these machines before with no problems

I used the 8.10 install on our PXE server, and it worked fine.

I suspect it's related to the upcoming 8.04.4 release, perhaps a new kernel has been inserted and has missed the cciss driver? 

Booting using 8.04, and running find /|grep cciss, doesn't find anything. I can't remember the last hp 8.04 build I did, but it was in the last month or so.

Doing it with 8.10 finds the driver.

(this is the 32 bit install)

Has anyone else had these issues?

---

### Post by Paul Weaver on 2010-01-26
The problem appears to be with block-modules...udeb -- it's not being retrieved on an 8.04 netboot, it is on 8.10

Any ideas?

---

### Post by Paul Weaver on 2010-01-26
Ahh, changing the netboot kernel and initrd to the ones available at [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/)

has done the trick. Phew.

---

