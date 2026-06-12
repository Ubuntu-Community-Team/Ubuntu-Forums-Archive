---
title: "After Installing Xen, Grub Drops to Command Line"
date: 2011-10-16
forum: Server Platforms
---

### Post by SBJ95 on 2011-10-16
Howdy everybody, my Google-Fu has turned up nothing, so I hope somebody has some insights...any thoughts are much appreciated!

Today, I installed Kubuntu Oneric x64 on my desktop, and configured mdraid.  The system was able to boot with no problems.  I then installed Xen as best I could ([FONT="Courier New"]xen-hypervisor-4.1-amd64[/FONT] & [FONT="Courier New"]xen-tools[/FONT]) and attempted to reboot into the Xen kernel.  Grub dropped to its command line.  I'm still able to manually boot the normal kernel with:

```
set root=(md/0)
kernel /vmlinuz root=/dev/md0 ro quiet splash
initrd /initrd.img
boot
```

but I can't, for the life of me, get Grub to actually present a menu.  Maybe I'm missing something obvious?  Anyways, I'd really appreciate any help any of you can offer.

P.S. Does anybody know how to get rid of the "fd0" error right before Grub loads?

---

