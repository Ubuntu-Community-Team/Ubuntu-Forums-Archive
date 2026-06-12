---
title: "Is it possible to use PXE to set up a &quot;Live CD&quot; Server?"
date: 2007-03-15
forum: Server Platforms
---

### Post by AsGF2MX on 2007-03-15
I like to try out live CDs but I hate having to burn CDs. Is there any manner in which it would be easy to boot a LiveCD with all its GUI and stuff?

I can deal with "Net Installing" right now...though I only have Ubuntu setup. I want to actually be able to boot Live CDs off the network. For example right now, I'm trying to get the Ubuntu 6.10 Live CD to work...

I can manage to get it to boot till the point where it now say cannot find /sbin/init.
I already have a tftp (serving PXE Linux as the boot loader) server running and it has Samba and NFS shares as well...it can currently serve up XP and Netinstalls of Ubunutu (more on the way but...).

Live CDs using ISOLINUX and the like...any help would be great. Surely this isn't an impossible task but a general where to begin or is it even feasible would help...

---

### Post by AsGF2MX on 2007-03-16
Is this truly an impossible feat?

---

### Post by elst on 2007-03-16
PXE and TFTP are normally used for delivering quite small boot images to clients. If you use virtual machine software like VMware or QEMU (which is OSS and in the repositories) you can use an ISO image file as if it was a CD drive, and boot a blank virtual machine from it. I test LiveCDs and betas that way, and it's pretty fast and convenient.

---

### Post by adrighem on 2007-03-19
I've seen this on Knoppix. It shares the kernel and initrd through pxe/tftp, and exports the CD through other means (probably NFS). So, you should be able to pull that off once you get at least one PC running with the liveCD (maybe a vmware-session). If you want to run this without a single liveCD running, you should loopmount the liveCD on a server, export that directory and read a root-NFS howto.

---

### Post by AsGF2MX on 2007-03-20
elst, your point is noted but I can already use VMs to test ISOs but somethings are a pain (XGL for example) and there are times when you just want to try things out natively or do a recovery. 

adrighem, what you say sounds about right but one thing I am confused about - how do I tell if the kernels used have NFS support?

---

