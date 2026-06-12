---
title: "why does boot fsck hang with 2.6.23-2[2-4]?"
date: 2010-08-24
forum: Server Platforms
---

### Post by iaw4 on 2010-08-24
My system has two kernels: 2.6.32-21 (came with 10.04) and 2.6.32-24 (pushed by update).  when I boot the first, everything works fine.  when I boot the second, fsck just hangs.  I can ctrl-alt-del, but it just doesn't continue.  Ctrl-C does nothing.

now, I know that the boot process stops on an fsck for a /dev/md1 device (identified via uuid).  (these kernels are the -server varieties of the kernels).  I can see just before the screen flashes by that RAID6 was loaded.  (It goes by too quickly, so I cannot see whether the RAID1 module is loaded, and/or whether /dev/md1 exists or what /dev/disk/by-uuid/* are.)

[LIST=1]
[*]How do I get the fsck.ext4 during boot to be a lot more verbose about what it thinks it is doing??
[*]How do I get a simple program (fdisk -l /dev/md1) to be executed the instant just before the fsck?  (this must be after the screen resolution switches, which happens just before the fsck.)
[*]How do I keep the boot.log from being overwritten?  the problem is that I cannot copy it, of course, when it hangs.
[/LIST]

help appreciated.

/iaw

---

### Post by ian dobson on 2010-08-24
Hi,

Maybe try starting with the noplymouth and noquiet kernel command line options (edit them in grub).

This might help, or maybe try booting in recovery mode with a serial console attached (another pc with null modem cable).

Regards
Ian Dobson

---

### Post by CharlesA on 2010-08-24
Hit "s" to see it continues. It's probably failing to mount a device.

---

### Post by iaw4 on 2010-08-26
thank you, everyone.

Charles---you were right.  the 'S' hint is what I needed.  It allowed me to get to a prompt.   interesting, when verbose is set (which I have), so that I see the kernel messages, it never tells me about 'S'.  this would have been a nice hint there.

regards,

/iaw

---

### Post by andersja on 2010-08-30
FYI I am seeing the same behaviour. No visual feedback what so ever when booting as a "normal" user. Booting in recovery mode on the older kernel shows a (non-blocking) fsck error.

FYI these bugs might be related and anyone experiencing this error should consider contributing to their resolution:
[https://bugs.launchpad.net/ubuntu/+bug/573356](https://bugs.launchpad.net/ubuntu/+bug/573356)
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/563916](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/563916) (for servers)

---

