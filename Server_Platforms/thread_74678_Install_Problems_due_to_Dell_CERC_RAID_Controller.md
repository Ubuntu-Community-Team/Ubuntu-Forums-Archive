---
title: "Install Problems due to Dell CERC RAID Controller"
date: 2005-10-12
forum: Server Platforms
---

### Post by cantoit on 2005-10-12
Hello all (I've already posted this on the beginners forum, but don't seem to be getting any response)

I have a Dell PowerEdge 1600SC server with one of their CERC RAID controllers. At present the server has the "testing" distribution of Debian installed, which is using the "megaraid" kernel module to support the hardware RAID controller.

I'm now trying to install Ubuntu 5.10 (RC1 - Breezy Badger), but I cannot get it to recognise the RAID contoller or any of the disks etc. I've done a "server-expert" install, have exited to a shell and done "modprobe megaraid", which has added the module to the kernel, but I still cannot get the installation to recognise any partitions.

Does anyone have any ideas?

Many thanks,
Duncan.

---

### Post by bubba on 2005-10-22
It appears that legacy megaraid support is broken in the Breezy 2.6.12 kernel.  My CERC/i4 card was unrecognized after my upgrade to Breezy.  I rolled back to 2.6.10 and things are fine.  I've posted this in the sticky upgrade notes thread but who knows if it will be addressed.

Bubba

---

### Post by bubba on 2006-01-25
It looks like Breezy users /etc/mkinitramfs instead of /etc/mkinitrd, so make sure you update your modules file from /etc/mkinitrd to /etc/mkinitramfs.  It appears that the 2.6.12-10 may have fixed any CERC issues.  I'll reboot when I get home and find out.

---

### Post by bubba on 2006-02-14
FYI, this has been fixed in linux-image-2.6.12-10-686 2.6.12-10.26

[http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=commitdiff;h=edb3146fdeaa599a27a52fa045c68c87e5e3208f](http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=commitdiff;h=edb3146fdeaa599a27a52fa045c68c87e5e3208f)

---

