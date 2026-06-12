---
title: "One Server, Two Drives with Two Installs"
date: 2018-08-13
forum: Server Platforms
---

### Post by kit.plummer on 2018-08-13
I have an environment where there is a single compute instance loaded with two SSDs, and the second is a bit-level clone of the partitions and software of the first.  I'm wondering if it is possible to use GRUB (or other boot software) to try to boot the first, and if there is a failure of some sort, to reboot into the second.

Anyone have insight?

TIA,
Kit

---

### Post by darkod on 2018-08-13
When you run sudo update-grub in theory it should detect all other OSs and make an entry for them in the boot menu.
But I'm not sure this is the best way to create HA. Can't you set up real HA witj two servers?
If you intend to boot from the second disk while the first is still present, some apps might not work because their reference will be to the first disk while the second will be booted. It depends on your setup...

---

### Post by kit.plummer on 2018-08-13
> **darkod said:**
> When you run sudo update-grub in theory it should detect all other OSs and make an entry for them in the boot menu.
But I'm not sure this is the best way to create HA. Can't you set up real HA witj two servers?
If you intend to boot from the second disk while the first is still present, some apps might not work because their reference will be to the first disk while the second will be booted. It depends on your setup...

Each disk has a full OS install pointing to it's own disk.  It is definitely not a normal use-case.  In some ways my I'm trying to replicate firmware NVRAM operation.  The trick is to boot a 'second' config if/when the first fails.

---

### Post by LHammonds on 2018-08-14
Well, that is tricky.  If grub is on drive 0 and drive 0 dies, the system expects to load drive 0...even if it is just to give you a menu to load an OS on drive 1.

I guess you could also have a USB stick setup so that it boots the USB which presents a menu selection for both disks (but defaults to drive 0 so the normal boot process does not pause).  If the USB is not present, it loads GRUB off drive 0 and presents both options.  The USB would be a backup to let you boot drive 1 if 0 is dead.  If USB boot is not possible, another potential is a custom CDROM but I think you would have to be at the console to activate the boot from CD option.

Not sure if you can configure GRUB to auto-select drive 1 if drive 0 is not working though.

I have not tried to configure a system like this...just throwing out some potential ideas.

But to test our your end-result, simply unplug drive 0 and see what happens when it is offline.  It is possible your BIOS might prevent it from auto-booting with drive 0 offline until you reconfigure the BIOS to not expect it.

LHammonds

---

### Post by kit.plummer on 2018-08-14
I _think_ the solution is in rewriting GRUB during the process to default boot after our processes run.  If the processes fail, then GRUB's config doesn't change.

---

