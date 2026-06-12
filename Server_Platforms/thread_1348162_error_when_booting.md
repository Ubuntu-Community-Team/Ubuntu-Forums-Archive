---
title: "error when booting"
date: 2009-12-06
forum: Server Platforms
---

### Post by kwickcut on 2009-12-06
One or more of the mounts listed in  /ect/fstab can not be mounted waiting for UUID=9ea34148-31b7-4d5c-baee-c2e2022562ea 

i just hit escape and then ran this code

```
vi /etc/fstab
```then found this

```
UUID=9ea34148-31b7-4d5c-baee-c2e2022562ea /boot           ext2    defaults        0       2

```
and changed it to this

```
#UUID=9ea34148-31b7-4d5c-baee-c2e2022562ea /boot           ext2    defaults        0       2

```i rebooted my box and the error went away.... i dont know if this is the rite thing to do but it worked... does anyone know the pros and  or cons to this



kwick

---

### Post by poltr1 on 2009-12-07
I was getting a similar error, after installing Karmic 32-bit server on a custom-built machine.  I'll have to try this when I go back to it tomorrow.

No, I don't know what the ramifications are for doing this, but are you able to start up Ubuntu after commenting out the line?  

Also, is there a quick reference guide for GRUB available?  I know none of the commands.

---

### Post by poltr1 on 2009-12-15
I tried installing an earlier version (9.04/Jaunty) on the server box, and it booted properly.  Would this be a viable option for you?

If I remember correctly, 9.10/Karmic introduced a new version of GRUB and the ext4 file system.

---

### Post by kwickcut on 2010-01-11
UPDATE

I have been having troubles with the server crashing every 5 to 7 days






 i have a friend that is a system admin and has been helping me out hear and there i have edit the code with his help and server rebooted and is now running i will repost if the the server does not crash 


this is the original code 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/server1-root /               ext4    errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0       1
# /boot was on /dev/sda5 during installation
UUID=9ea34148-31b7-4d5c-baee-c2e2022562ea /boot           ext2    defaults        0       2
/dev/mapper/server1-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```edited code 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/server1-root /               ext4    defaults 0       1
```

after you edit these line you must reboot server

hope this helps someone



kwick

---

