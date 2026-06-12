---
title: "Unable to start vmware-server-console"
date: 2007-11-23
forum: Server Platforms
---

### Post by satimis on 2007-11-23
Hi folks,


Ubuntu 7.04 server amd64 (Host OS)
CentOS 5 x86_74 (Guest OS)
VMWare server


Previously as satimis(user) on console running
$ /usr/bin/vmware-server-console start

-> local host -> connect

vmware-server-console can be started.  Unfortunately I accidentally removed /home/satimis but w/o removing the satimis because login.  Now I can't start vmware-server-console by ;

$ /usr/bin/vmware-server-console start

-> local host -> connect

Following warning popup:- 
Unable to open: Virtual machine "start" is not in the inventory.


Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by k_grdn on 2007-11-23
Hi,

Try:

vmware-server-console & to start the console then create/open VM image.

Regards,

k_grdn

---

### Post by satimis on 2007-11-23
> **k_grdn said:**
> Hi,

Try:

vmware-server-console & to start the console then create/open VM image.

Hi,


Thanks for your advice.


I think my problem is caused by removing /home/satimis.  Previously I download "CentOS-5_lamp.x86_64.zip" on centos.org and depressed it on /home/satimis/CentOS-5_lamp.x86_64/

(All of the VMDK files are VMWare disk images)

now everything gone.

Just have a fresh "CentOS-5_lamp.x86_64.zip" download.  Where will be the ideal directory to extract it other than /home/satimis again?  TIA


B.R.
satimis

---

### Post by conjur3r on 2007-11-24
Anywhere you will remember not to accidentally remove the folder!  It'll work wherever you place it.  If it's important, then create a new partition by itself and call it something like /vmware so all of your vmimages can be placed in there.  It's really up to you.

---

### Post by satimis on 2007-11-24
> **conjur3r said:**
> If it's important, then create a new partition by itself and call it something like /vmware so all of your vmimages can be placed in there.  It's really up to you.
I build this virtual machine for testing in order to learn, not for production.

I also have your idea making vmware and other gust OS residing on another partition.

So at start I partitioned the HD, 160G  into 2 equal LV (2 partitions of equal capacity), installing Ubuntu 7.04 server amd64 on one LV.

$ sudo fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

```
On installing VMWare I can't get it installed on another LV.  I can't find this empty LV.  I don't know why?

Now I'm prepared to keep "CentOS-5_lamp.x86_64.zip" on the empty LV and decompress it there.  How can I make it?  TIA

$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/ubuntu-root /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sda1
UUID=16932771-ab2e-41cf-aea9-f744b7a252eb /boot           ext3    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```


B.R.
satimis

---

