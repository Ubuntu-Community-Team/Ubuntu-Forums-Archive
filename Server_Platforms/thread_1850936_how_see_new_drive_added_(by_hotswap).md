---
title: "how see new drive added (by hotswap)"
date: 2011-09-27
forum: Server Platforms
---

### Post by skrite on 2011-09-27
Hey all, 

i have a server that i need to make an identical copy of the boot drive /dev/sda1. It is sitting on a SCSI drive right now. The server allows us to hot-plug a drive, but when i hot plug a drive, i don't know where to find it. /var/log/messages doesn't help any more (gone) and i don't know how to find it's /dev/?   if i do fdisk -ls, the output is the same as before i plugged the drive in.
i need to do this because i plan to unmount the boot drive and use dd to make the copy. any ideas?

---

