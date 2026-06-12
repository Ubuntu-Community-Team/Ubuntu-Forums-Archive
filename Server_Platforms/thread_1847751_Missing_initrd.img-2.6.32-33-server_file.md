---
title: "Missing initrd.img-2.6.32-33-server file?"
date: 2011-09-21
forum: Server Platforms
---

### Post by lcadman on 2011-09-21
Upon restarting my Dell PE 2950 running 10.04 LTS x64, I noticed an error :(

**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**

Upon booting into the 10.04.3-server CD and running the rescue, I mounted /boot and noticed what appears to be a missing **initrd.img-2.6.32-33-server** file.

I see all these other files:

System.map-2.6.32-33-server
abi-2.6.32-33-server
config-2.6.32-33-server
vmcoreinfo-2.6.32-33-server
vmlinuz-2.6.32-33-server

There are also past files from kernel builds 2.6.32-24 through 2.6.32-32

How can I recreate or obtain **initrd.img-2.6.32-33-server** file? Is this file specific to my PE server with its hardware config?

This system is also using Grub2, and I have yet to locate the config files for boot-up that reference the initrd.img file :confused:

Thanks


**EDIT**: Looks like the /boot is 98% full which was why initrd.img-2.6.32-33-server file was never created. 2.6MB available on the partition. It should be safe to delete previous file versions 2.6.32-24 through 2.6.32-28, correct? This would leave 2.6.32-31 to 2.6.32-33.

**EDIT**: I went ahead and moved those 2.6.32-24 through 2.6.32-28, so I the /boot partition has more than 50% capacity now. I noticed in the / root there are symbolic links for initrd.img pointing to the old one boot/initrd.img-2.6.32-32-server which is still present.

Any thoughts?

---

