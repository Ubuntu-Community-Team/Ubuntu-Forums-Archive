---
title: "lvm, mdadm and usb = }:-|"
date: 2010-08-20
forum: Server Platforms
---

### Post by zbot on 2010-08-20
I've searched far and wide for this, came across many similar-yet-different posts and now I humble myself before the ever wise community...

Running Dapper Drake on a simple server, and have physical/root access...

Problem: using mdadm I created a raid1 array and extended a logical volume using lvm2... everything worked and it was beautiful... that is, until I rebooted and everything went south.  mdadm runs before the usb disk is mounted and of course it "cannot find the physical device"...  I've tried adding a rootdelay but this does not work.  I believe the problem is associated with the initrd image since when I delete this line from the grub startup sequence mdadm does not try to run, but the problem then becomes that the booting sequence cannot find the root partition...

Anyway, I am armed with my Ubuntu live CD but have no idea how to chroot myself back into the system as the root partition is a partition of the LV.  Essentially I need to tell mdadm to run after the usb disk is mounted.

I'm trying to keep this succinct, but if anyone is willing to help I can/will provide more details.  Thanks in advance.

zbot

---

### Post by zbot on 2010-08-20
bump...

---

