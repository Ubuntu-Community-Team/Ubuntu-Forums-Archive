---
title: "Volume Groups Disappeared in KVM machine!!"
date: 2011-11-30
forum: Server Platforms
---

### Post by batonac on 2011-11-30
I just created a disaster by trying to create more space on a KVM virtual machine.  I'm very new at working with LVM and I think I really screwed up the filesystem.

After enlarging the virtual machine's disk image*, I rebooted the virtual machine and it recognized the free space, but I couldn't figure out how to enlarge the LVM physical volume on the virtual machine, so I created a second LVM partition using cfdisk.  After writing the changes to disk, Ubuntu didn't recognize the presence of a new partition, so I figured I must need to reboot.  Now, however, the virtual machine won't start!

It gives the message:

```
error: no such device: 205ca59b-079d-4b64-a119-5c32c8ef1383.
error: no such disk.
Gave up waiting for root device.
```

I started up the virtual machine using the Ubuntu Server ISO in rescue mode, and ran partman, which recognizes the partitions, but no LVM volume groups!  Somehow cfdisk seems to have screwed up my LVM configuration! Please Help!

Both the host and the server run Ubuntu Server 10.04.  

*The virtual machines' disk image on the host machine is actually an LVM Logical Volume, but I THINK that is irrelevant.

---

### Post by batonac on 2011-11-30
Update: I attached the screen shot from the virtual machine with the full error message.

---

### Post by batonac on 2011-11-30
Well, I hate to mark this forum as solved, since the original problem wasn't really solved, but I did restore my files with UFS Explorer, and I'm just planning on reinstalling the virtual machine.

---

