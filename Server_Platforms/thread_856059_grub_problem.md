---
title: "grub problem"
date: 2008-07-11
forum: Server Platforms
---

### Post by fouadk on 2008-07-11
hi everyone...

i have an ibm system x3500 server with 8 hard disk and RAID5...

i installed ubuntu server and the step that installs grub fails but lilo does not fail....

after installation i followed the steps in here to install grub: 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

when i reach the step that says: ```
find /boot/grub/stage1
```

i get an error15: file not found

why???

how would i fix that in order to install grub successfully ???

please help

thanks in advance

---

### Post by Zack McCool on 2008-07-11
When you are booted to the LiveCD, can you see the local hard drives?

It would seem to me that you are using a hardware RAID solution that does not have a driver loaded in the LiveCD.  Or, alternately, grub was never installed during your build.  If you can see the local drives, look in the /boot directory and see if there is a /boot/grub/stage1.

If that is there, and you can access the drive in the first place, I'm not sure why you can't get grub installed.

---

### Post by kevmitch on 2008-07-11
I frequently find that find command doesn't work, though it appears to work for me now. I've always tried to avoid the grub shell and just run

```
sudo grub-install /dev/sda
```

Which assumes that your boot directory is located at /boot/. 
If you have /boot/ in a strange place, then you can add --root-directory=$DIR so that it looks for it at $DIR/boot. I actually just did this today. I booted into the live cd and mounted my root directory at /mnt/root 

```
sudo mount /dev/sda5 /mnt/root
```

this meant that my normal /boot/ directory was located under /mnt/root/boot/ so . . .

```
sudo grub-install /dev/sda --root-directory=/mnt/root
```

Did it for me.

What type of file system are you using on top of the RAID array? Is it hardware or software? I've always had problems trying to install grub on XFS partitions, so I just make a separate boot partition formatted ext3. So actually, I lied in the above, I actually did this:

```
sudo mount /dev/sda5 /mnt/root
sudo mount /dev/sda2 /mnt/root/boot
grub-install /dev/sda --root-directory=/mnt/root

```


where /dev/sda2 is my ext3 /boot partition.

---

### Post by fouadk on 2008-07-11
hi...

i did: ```
sudo grub-install /dev/sda
```
it gave me: ```

Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

```

this is a copy of my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d27de316-fec8-43c2-a4e1-fb678a73b0f1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=96eaf2d4-40fb-400c-9a24-72e625ebdaf4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

this is a copy of device.map:
```

(hd0) /dev/sda

```

this is a copy of some of the menu.lst
```

title Ubuntu 8.04.1, kernel 2.6.24-16-server
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-server root=UUID=d27de316-fec8-43c2-a4e1-fb678a73b0f1 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-server

title           Ubuntu 8.04.1, kernel 2.6.24-16-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-server root=UUID=d27de316-fec8-43c2-a4e1-fb678a73b0f1 ro single
initrd          /boot/initrd.img-2.6.24-16-server


```

please help...

thanks in advance

---

### Post by kevmitch on 2008-07-11
Allright, we'll have to admit you have me mostly stumped. I'm not sure, but it looks like a hardware raid card seeing as how the comments seem to suggest that the device file is /dev/sda1. I think software raid would be mapped to something different. What kind of raid card/controller is it? What does

```
sudo lshw -C storage
```

give you?

---

### Post by fouadk on 2008-07-11
hey...
The raid is most probably a hardware raid ... It is an ibm serveRAID 8

The server is at my workplace now so on monday ill see what that command return...

Thanks a lot

---

