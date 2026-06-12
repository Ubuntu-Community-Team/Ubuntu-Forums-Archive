---
title: "Ubuntu Precise - stuck update-initramfs"
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tubezninja on 2012-03-22
I'm having a problem with a stuck update-initramfs process on a server.  This is a 32-bit system running ubuntu precise beta server.

It's been running fine so far,but this morning while doing an apt-get dist-upgrade, the process got stuck on:

```
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-20-generic /boot/vmlinuz-3.2.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-20-generic
```

It'll sit like this for hours if I let it. I've interrupted the process but of course that puts me in "dpkg --configure -a" hell, and running that only puts me in the same stuck spot.

Also attempted to run sudo update-initramfs -u on its own, to no avail.  For (hopefully) obvious reasons, I've not dared a reboot.

What I'd like to do, if I can, is get update-initramfs into a state where it no longer wants to generate /boot/initrd.img-3.2.0-20-generic and hopefully, not get stuck in this process.  Is there a way to do this?

---

### Post by oldos2er on 2012-03-22
Moved to Ubuntu +1 (Precise Pangolin).

---

