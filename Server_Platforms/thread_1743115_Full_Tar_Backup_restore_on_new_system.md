---
title: "Full Tar Backup restore on new system"
date: 2011-04-29
forum: Server Platforms
---

### Post by Understandmoe on 2011-04-29
I am trying to migrate my server to a new sever I am doing a full backup of the file system using TAR as a backup of the root directory. I copy the tar file over to the new server and extract it, i can see all the files fine when navigating around. Once I reboot it comes up with a window saying - "Gave up waiting for root device. ALERT! /dev/mapper/dc-root does not exist. Dropping to a shell!" I know its something with the mapper files not being mounted so i copied from the new system the fstab and the grub folder because i wanted it from the new server configuration so it would boot. I have been trying everything and i have to do this on a few more servers that have LVM's that i would like to make it a little more quicker of a process. I have searched around and i can't find any solution that worked. If anyone could direct me to the right path that would be very helpful. Thanks

---

### Post by 3L33T on 2011-04-29
> **Understandmoe said:**
> I am trying to migrate my server to a new sever I am doing a full backup of the file system using TAR as a backup of the root directory. I copy the tar file over to the new server and extract it, i can see all the files fine when navigating around. Once I reboot it comes up with a window saying - "Gave up waiting for root device. ALERT! /dev/mapper/dc-root does not exist. Dropping to a shell!" I know its something with the mapper files not being mounted so i copied from the new system the fstab and the grub folder because i wanted it from the new server configuration so it would boot. I have been trying everything and i have to do this on a few more servers that have LVM's that i would like to make it a little more quicker of a process. I have searched around and i can't find any solution that worked. If anyone could direct me to the right path that would be very helpful. Thanks

Seems you copied the whole tar'd file to the " / " ?  is this correct?  Do a full new clean o/s install on the new server.  copy your tar single file to a mounted partition large enough to hold your tar single file backup.  Then, do a selective untar of the files you need to migrate from the old server to the new server?

---

### Post by Understandmoe on 2011-04-29
Correct I extracted the tar from "/" and it puts all the files in there from what i see. The steps that i did to do this was I copied the tar file over to this clean installed O/S same version of Ubuntu 10.10. I restarted the server into recovery mode and ran the extract from there. When i reboot I get that message. On my tar backup i exclude /dev /proc /sys. Once i extract it it seems to work fine but it somehow loses the LVM mapper information.

---

### Post by dtfinch on 2011-04-29
Was the LVM volume on the destination server named dc-root before you copied over or was it named something else? When it drops you to a shell, can you see what's in "/dev/mapper/"?

---

### Post by Understandmoe on 2011-05-04
the dc-root is not in the dev mapper folder, how do i go about remapping this so it will detect the LVM drive?

---

