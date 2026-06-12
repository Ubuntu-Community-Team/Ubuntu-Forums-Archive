---
title: "Can't install VirtualBox 4.3 on 13.10"
date: 2013-11-22
forum: Virtualisation
---

### Post by nashant on 2013-11-22
I've been trying to install VirtualBox but no luck. Whether I try 4.2 or 4.3 it gets to this...

Setting up virtualbox-4.3 [or 4.2] (4.3.2-90405~Ubuntu~raring) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMSError! Your kernel headers for kernel 3.8.0-19-generic cannot be found.
Please install the linux-headers-3.8.0-19-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

Tried installing linux-headers-3.8.0-19-generic but it's deprecated and no longer has an install candidate. Anyone able to point me in the direction of a fix?

---

### Post by nashant on 2013-11-22
Wrong kernel version being reported by uname. Probably has something to do with my boot issues too!

---

### Post by howefield on 2013-11-22
What is being reported by uname ?

---

### Post by nashant on 2013-11-22
[COLOR=#000000]3.8.0-19 for some reason. Had to boot to live usb and run boot-repair after I removed all traces of that kernel and ran update-grub and it would only boot to memtest. All working now though, and vbox installed![/COLOR]

---

### Post by christian-sacks on 2014-02-27
How did you solve this?

---

### Post by SeijiSensei on 2014-02-27
By installing the correct linux-headers version that matched his kernel version.

If you're asking about how to install VirtualBox, I recommend the [method]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") described on the VirtualBox site.

---

