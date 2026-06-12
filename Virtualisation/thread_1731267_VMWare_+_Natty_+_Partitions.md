---
title: "VMWare + Natty + Partitions"
date: 2011-04-16
forum: Virtualisation
---

### Post by dsimcha on 2011-04-16
I'd been running the same Maverick installation on a physical partition both on the bare metal and as a guest under Windows 7 using VMWare player.  This worked quite well.  Now that I've upgraded to Natty beta, I can no longer get Grub to come up in my virtualization window when I create a .vmdk file with only the Linux partition.  When I try, the VM goes into an endless loop of trying to load Grub, then rebooting.  It still works when I create a .vdmk with the whole drive, though this is dangerous because the Windows partition could be accidentally mounted concurrently in the host and guest.

Did something about Grub change between releases that makes it impossible for Grub to load in the presence of "missing" partitions?  The way (I think) VMWare works when using physical partitions is that it copies the master boot record to a file, allows access to the selected partitions and lets the guest see a partition filled with zeros for the unselected partitions.

EDIT:  If I create a vmdk "using partitions" instead of using "entire disk" but select all partitions, it still doesn't work.

---

