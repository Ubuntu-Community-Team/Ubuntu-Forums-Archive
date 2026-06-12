---
title: "panic: problem migrating LVM data to new physical drives"
date: 2009-07-19
forum: Server Platforms
---

### Post by semi-newbie on 2009-07-19
I needed to move my data from /dev/md0 (a mirroring RAID of two 0.5Tb drives) to a mirroring RAID of two new 1.5Tb drives.

I had made a new /dev/md1 successfully, then went

pvcreate -v -M2 --metadata-copies 2 /dev/md1
vgextend mooch /dev/md1
pvmove -i 15 /dev/md0 /dev/md1

The first two commands worked, but then pvmove gave an error:

ABORTING: Can't find mirror LV in mooch for /dev/md0

I think this is because I was supposed to run lvcreate for each of the logical volumes, but I didn't know to do so, and therefore hadn't done so.  The real problem is that the machine was SHUT DOWN.   The lvm had my / (but not my /boot) filesystem on it!  Now, when I try to boot, I get:

There appears to be one or more degraded LVM volumes, and your root device may depend on the LVM modules being online.  One or more of the following LVM modules are degraded:

Reading all physical volumes.  This might take a while...
Couldn't find device with uuid '[uuid here]'
Couldn't find all physical volumes for volume group mooch.
Couldn't find device with uuid '[same uuid here as before]'
Couldn't find all physical volumes for volume group mooch.
Volume group "mooch" not found.

I threw in my Ubuntu 9.04 Live/Desktop CD, and booted the live system to attempt to rescue the system.  It didn't have lvm at all, so I went

sudo apt-get install lvm2

That worked fine, but now I am out of my depth and am not sure how to proceed.

Running from the Ubuntu 9.04 live CD, "fdisk -l" yields:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006d480

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009bdc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 20.4 GB, 20411080704 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf94df94d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         620     4980118+  83  Linux
/dev/sde2             621        1085     3735112+  82  Linux swap / Solaris
/dev/sde3            1086        2481    11213370    b  W95 FAT32


Running from the Ubuntu 9.04 live CD, "mount" yields:

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

ls -l /dev | grep md gives nothing, so the RAID devices don't even exist right now.  I feel like the situation should be recoverable from but that I am in over my head, so I wanted to post for help instead of screwing this up totally.

---

### Post by semi-newbie on 2009-07-19
I was able to do something like the following:

(in busybox)
mdadm --assemble --scan

(after rebooting, using the live CD)
mknod /dev/md0 b 9 0
mknod /dev/md0 b 9 1


I now have the following:

/etc/mdadm/mdadm.conf:

DEVICE partitions
CREATE owner=root group=disk
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=cafebabe:cafed00d:deadbeef:baadf00d
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=baddcafe:feedface:defec8ed:fee1dead

lvdisplay shows my volumes (/dev/mooch/root, /dev/mooch/tmp, /dev/mooch/home, /dev/mooch/usr, /dev/mooch/usr, /dev/mooch/var, /dev/mooch/srv).  I can mount them individually to /mnt and see their contents.

So, it seems I've made progress, but now how do I repair my bootup procedure?  I am not sure what to do next.

---

### Post by semi-newbie on 2009-07-20
At this point, I've figured out that when I reach busybox, if I type the following commands then I can get the system up and running:

echo "ARRAY /dev/md0 level=raid1 num-devices=2 UUID=cafebabe:cafed00d:deadbeef:baadf00d" >> /etc/mdadm/mdadm.conf

mdadm --assemble --scan

vgchange -a y   (I am not sure that I need this command every time.)

exit

and voila, the system will then boot.  However, every single reboot sends me back to busybox, so I have to perform these procedure on every single reboot.  Can anyone tell me how to repair the remaining problem?

Basically, something somewhere is using the old raid's UUID and I need it to instead use the new UUID.  Unfortunately, I don't even know where to look to try and change this, because I don't understand the boot process sufficiently well.

I did look in /boot/grub/menu.lst, but didn't see anything in it that specified the UUID of /dev/md0.

---

### Post by semi-newbie on 2009-07-20
Each time in busybox, it's:

echo "ARRAY /dev/md0 level=raid1 num-devices=2 UUID=cafebabe:cafed00d:deadbeef:baadf00d" >> /etc/mdadm/mdadm.conf

mdadm -A -s-

vgchange -a y

exit

and voila, the system will then boot.  I think the problem is that the UUID set in my initramfs is not the same as my current UUID for the raid1 array.  Unfortunately, "update-initramfs -u" does not actually fix this problem, nor do I see anything relevant in /etc/initramfs-tools/conf.d/mdadm.

As per the man page for mkinitramfs,

cd /tmp
sh -x mkinitramfs -o initramfs-$(uname -r) > log.txt 2> log.err

produces a mkinitramfs_VMFVoc directory (the suffix changes).  /tmp/mkinitramfs_VMFVoc/etc/mdadm/mdadm.conf contains the old UUID -- if it had the new one for the new raid array, probably everything would work.  Yet I don't know where mkinitramfs is reading this UUID from.  Can anyone tell me?

---

### Post by semi-newbie on 2009-07-20
So, the final piece of the puzzle appears to be that once I have the main system loaded, I needed to:

nano /etc/mdadm/mdadm.conf
(change the uuid in this file)
mkinitfs -k `uname -r` -c

This built a new /boot/initrd.img-2.6.28-11-server for me that has the proper UUID, and reboot now succeeds without dropping to busybox.

---

### Post by BillHungDotNet on 2011-06-26
Thank you semi-newbie, because of you my server now boots again.
The most useful command above were those you made with the busybox. For future reference if someone runs into the same problem. Here are some of the stuff I had to do.
----------------
> echo "ARRAY /dev/md0 level=raid1 num-devices=2 UUID=cafebabe:cafed00d:deadbeef:baadf00d" >> /etc/mdadm/mdadm.conf
mdadm --assemble --scan
vgchange -a y (I am not sure that I need this command every time.)
exit
I actually didn't need to vgchange, and vgchange didn't work for me with Ubuntu 9.04 anyway. I did
```

echo "ARRAY /dev/md0 level=raid1 num-devices=2 UUID=64309496:7e92933d:da82b7b9:5ddb066e" >> /etc/mdadm/mdadm.conf
mdadm --assemble --scan
exit

```

The thing was, I didn't note down my UUID, and there was no way that UUID could be found, especially 9.04 is out-dated and sudo apt-get using the Live CD didn't get many packages. So I had to install 10.04 using another hard disk, and install mdadm there to get the UUID of the 2 hard disks that no longer boot. 
I printed the UUID by doing the mdadm command (after playing around with lvm2 among other stuff)
sudo mdadm --examine --scan
------------------
> nano /etc/mdadm/mdadm.conf
(change the uuid in this file)
mkinitfs -k `uname -r` -c

You gave me the right idea of what to do, but you somehow used mkinitfs which was not available to the out-dated 9.04. I used the ubuntu default mkinitramfs
```

sudo mkinitramfs -o `uname -r`
sudo mv /boot/2.6.28-19-generic /boot/initrd.img-2.6.28-19-generic
ls -lrt /boot

```
after this, I checked the initrd.img-2.6.28-19-generic timestamp (in /boot/  mounted at md5 for me) was the current date and at a different size from the original one. 
And after a reboot everything works.
-----------------
Thanks again semi-newbie.

---

