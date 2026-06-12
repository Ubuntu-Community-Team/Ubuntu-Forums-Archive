---
title: "Problem mounting external usb hard drive."
date: 2011-06-19
forum: Server Platforms
---

### Post by donniezazen on 2011-06-19
I have attached a 1.5 TB external hard drive to my new Ubuntu server. I mount it in /media/external. I used sudo mount /dev/sdx# /media/external but sdx# keeps changing. I added a line to fstab to mount it permanently but after couple of our it unmounts itself and /media/external is empty. It is in vfat format but webmin shows it as ntfs.

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=24e9e2dd-6bbe-4673-bb31-63337fe93c32 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7e6ca071-eb81-4f45-ac2e-64261e2fc3f3 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=65dfd3e6-edfe-4d7f-99e3-967d6e433484 none            swap    sw              0       0
#External Hard drive
UUID=FF9B-CFA1  /media/external  vfat  uid=1000,gid=1000  0  0


>  df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              9842208   1935836   7406404  21% /
none                   1022892       264   1022628   1% /dev
none                   1029500       276   1029224   1% /var/run
/dev/sda7             79971176    305452  75603416   1% /home
/dev/sdc1            1464423472 837458544 626964928  58% /media/external

>  sudo blkid
[sudo] password for donnie:
/dev/sda1: UUID="782003C920038CF6" TYPE="ntfs"
/dev/sda5: UUID="24e9e2dd-6bbe-4673-bb31-63337fe93c32" TYPE="ext4"
/dev/sda6: UUID="65dfd3e6-edfe-4d7f-99e3-967d6e433484" TYPE="swap"
/dev/sda7: UUID="7e6ca071-eb81-4f45-ac2e-64261e2fc3f3" TYPE="ext4"
/dev/sdc1: LABEL="Sudhir" UUID="FF9B-CFA1" TYPE="vfat"

What am i doing wrong?

Thanks.

---

### Post by donniezazen on 2011-06-20
Please help.

---

### Post by linkageless on 2011-06-21
Weird, what you have in your fstab looks surprisingly short for UUID to me. (Forgive me if I'm wrong.)

Are you able to confirm the uuid through /dev/disk/by-uuid/?

The FS type might be picked up incorrectly if the partition type is set wrong in the partition table. You could fix that using fdisk or a similar partition editor, but as far as I know it should do no harm and I don't think this is related to your main problem. (I'd leave it alone while you have precious data in there!)

---

### Post by linkageless on 2011-06-21
Having re-read your post, I suspect autofs or usbmount is getting in your way, hence it being unmounted when it thinks you no longer need it.

I don't either so can't really help, but with luck this will set you on the right path of enquiry.... I imagine you can set rules for this specific device, or have it ignored altogether so you can do it 'manually' through traditional mount.

---

### Post by donniezazen on 2011-06-22
ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2011-06-22 13:30 24e9e2dd-6bbe-4673-bb31-63337fe93c32 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-06-22 13:30 65dfd3e6-edfe-4d7f-99e3-967d6e433484 -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-06-22 13:30 782003C920038CF6 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-06-22 13:30 7e6ca071-eb81-4f45-ac2e-64261e2fc3f3 -> ../../sda7
lrwxrwxrwx 1 root root 10 2011-06-22 13:30 FF9B-CFA1 -> ../../sdb1

---

### Post by oldfred on 2011-06-22
Fstab entry looks close, I do not know all the parameters allowed with each type of format. Note sure is UID & GID settings are valid.

This was my setting

```
# /windowsold was on /dev/sdc8 during installation
UUID=F6A6-705D  /windowsold     vfat    utf8,umask=007,gid=46 0       1

```

You did make a mount point of /media/eternal?

If you run this does it tell you if something is wrong. If it returns it remounts everything ok.

sudo mount -a

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by donniezazen on 2011-06-22
> **linkageless said:**
> Having re-read your post, I suspect autofs or usbmount is getting in your way, hence it being unmounted when it thinks you no longer need it.

I don't either so can't really help, but with luck this will set you on the right path of enquiry.... I imagine you can set rules for this specific device, or have it ignored altogether so you can do it 'manually' through traditional mount.

This is probably i need to do. [http://ubuntuforums.org/showthread.php?t=168221&page=1](http://ubuntuforums.org/showthread.php?t=168221&page=1)

I don't know if things have changed since 2006 but udevinfo -a -p $(udevinfo -q path -n /dev/sdx#) doesn't seem to work. I get error command not found.

---

### Post by ruffEdgz on 2011-06-22
> **soham_1207 said:**
> This is probably i need to do. [http://ubuntuforums.org/showthread.php?t=168221&page=1](http://ubuntuforums.org/showthread.php?t=168221&page=1)

I don't know if things have changed since 2006 but udevinfo -a -p $(udevinfo -q path -n /dev/sdx#) doesn't seem to work. I get error command not found.

Try this:
```
sudo udevadm info --attribute-walk --path=$(udevadm info --query=path --name=/dev/sdx#)
```
I'm watching this ticket myself because I am curious about this as well ;) Will help if I can.

Cheers!

---

### Post by donniezazen on 2011-06-22
> **oldfred said:**
> Fstab entry looks close, I do not know all the parameters allowed with each type of format. Note sure is UID & GID settings are valid.

This was my setting

```
# /windowsold was on /dev/sdc8 during installation
UUID=F6A6-705D  /windowsold     vfat    utf8,umask=007,gid=46 0       1

```

You did make a mount point of /media/eternal?

If you run this does it tell you if something is wrong. If it returns it remounts everything ok.

sudo mount -a

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

As mentioned in HOWTO:Mount NTFS forum i am trying with 

UUID=FF9B-CFA1 /media/external vfat defaults,auto,uid=1000,gid=1000,umask=750 0 0

my uid and gid is infact 1000 and i am using umask 750 to give user read and write, group read and execute and others none permission.

uid=1000(donnie) gid=1000(donnie) groups=1000(donnie),4(adm),20(dialout),24(cdrom),46(plugdev),110(libvirtd),111(sambashare),116(lpadmin),117(admin)

Do i need to run chown -R myusername:myusername /media/external ?

Thanks will report later.

---

### Post by oldfred on 2011-06-22
You cannot set permissions or  ownership on NTFS or FAT partitions. They just do not support them. The only setting is in fstab.

What did this say?

sudo mount -a

Settings in fstab vary by partition format type, so not all settings work with each format.
Fstab is backwards to standard settings.
umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx.

# before uuid  /dev/sda4 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

      umask=value
              Set the umask (the bitmask  of  the  permissions  that  are [B] not
              present[/B]).  The default is the umask of the current process.  The
              value is given in octal.
       
dmask=value
              Set the umask applied to directories only.  The default  is  the
              umask of the current process.  The value is given in octal.

       fmask=value
              Set the umask applied to regular files only.  The default is the
              umask of the current process.  The value is given in octal

---

### Post by donniezazen on 2011-06-23
> **oldfred said:**
> You cannot set permissions or  ownership on NTFS or FAT partitions. They just do not support them. The only setting is in fstab.

What did this say?

sudo mount -a

Settings in fstab vary by partition format type, so not all settings work with each format.
Fstab is backwards to standard settings.
umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx.

# before uuid  /dev/sda4 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

      umask=value
              Set the umask (the bitmask  of  the  permissions  that  are [B] not
              present[/B]).  The default is the umask of the current process.  The
              value is given in octal.
       
dmask=value
              Set the umask applied to directories only.  The default  is  the
              umask of the current process.  The value is given in octal.

       fmask=value
              Set the umask applied to regular files only.  The default is the
              umask of the current process.  The value is given in octal


sudo mount -a does not yield anything. 

I haven't lost the mount point all day. It is working in a sense. But i can't ssh using regular user whose id i have chosen. I have to be root user to cd into drive mount.

If user permissions are not allowed in NTFS or FAT32 partition, how is it defined who can rwx it.

Is their a better file system for linux servers? I do want to keep it accessible to windows computer.

thanks.

---

### Post by donniezazen on 2011-06-23
> UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

User = mount as/for home user
auto = mount at boot
Why do you have 4 strings in fmsak and dmask? Should it not be only 3 for user, group and others.
fmask is for files which you have set to reading in opposite direction to chmod values to read and write by user, group and other. dmask is for directory and it is set to read, write and execute by any user. Is umask same file permission for both files and directory?
I do not want to set specific file permissions i want to treat it as a home folder and permissions set to default of home user.

Thanks for your help.

---

### Post by donniezazen on 2011-07-06
I just tried the other forums lets see if it works.

---

### Post by oldfred on 2011-07-06
umask=750 means you have no permissions.

umask=value
              Set the umask (the bitmask  of  the  permissions  that  are [B] not
              present[/B]).

Setting is opposite of normal settings if you will. so you want 047 so something similar.

---

### Post by donniezazen on 2011-07-10
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

Tried setting udev rules but no luck, it unmounts itself regularly.
I am just going to remove udev rules, put a simple fstab line and setup a corn job to mount external hard drive every three hours. Any opinion, this has been really frustrating experience with Ubuntu.

---

### Post by CharlesA on 2011-07-10
Any reason why you are running FAT on a 1.5TB drive?

Either use NTFS or EXT3/4.

Anything listed in dmesg when the drive unmounts?

---

