---
title: "[SOLVED] luks for second volume, no passphrase asked at boot time"
date: 2008-08-17
forum: Security
---

### Post by mewn on 2008-08-17
Hi guys,


I have an installation with encrypted hard disk and LVM on top of it.
Working fine.

However I want now to turn my hard-disk into a raid1 one.


The actual system 8.04 LTS :
> @spike:~$ uname -a
Linux spike 2.6.24.3-epia6 #1 Thu Aug 14 17:10:04 BST 2008 i686 GNU/Linux

I had to patch the source to get around #8653 ( [http://bugzilla.kernel.org/show_bug.cgi?id=8563](http://bugzilla.kernel.org/show_bug.cgi?id=8563) ) and to get my grfx card working properly

=> this is not relevant to the problem at hand, just to give a bit of background info.

> @spike:~$ cat /etc/crypttab
sda5_crypt /dev/disk/by-uuid/5d1cb1fe-fa9d-40dc-9260-a42d0af8e1d0 none luks

> @spike:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/mapper/sda5_crypt
  VG Name               spike
  PV Size               465.52 GB / not usable 1.33 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              119173
  Free PE               0
  Allocated PE          119173
  PV UUID               30mxhM-Kd0w-2QL3-Xq8s-0O2w-WVf6-oRzrFZ



> @spike:~$ sudo lvdisplay 
  --- Logical volume ---
  LV Name                /dev/spike/root
  VG Name                spike
  LV UUID                ZK0MQ6-GclH-d35l-QMFa-chNb-rViG-l7MvcU
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                462.75 GB
  Current LE             118464
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1
   
  --- Logical volume ---
  LV Name                /dev/spike/swap_1
  VG Name                spike
  LV UUID                RwaIR2-4EGB-E3Mg-4lbB-kQ8u-r3rT-gACsKQ
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                2.77 GB
  Current LE             709
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:2


> @spike:~$ df -PH
Filesystem             Size   Used  Avail Use% Mounted on
/dev/mapper/spike-root   493G    47G   422G  10% /
[...]


My new HD is sdb and the same model as sda.


My Action Plan was :

[LIST=1]
[*]- create md0 with sdb5 in it
[*]- encrypt md0 to md0_crypt
[*]- pvcreate of md0_crypt
[*]- add md0_crypt to my mainVG
[*]- migrate all LV on mainVG to md0_crypt
[*]- remove sda5_crypt from mainVG
[*]- add sda5_crypt to md0
[/LIST]

> @spike:~$ cat /etc/crypttab
sda5_crypt /dev/disk/by-uuid/5d1cb1fe-fa9d-40dc-9260-a42d0af8e1d0 none luks
md0_crypt /dev/md0 none luks

> @spike:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/mapper/sda5_crypt
  VG Name               spike
  PV Size               465.52 GB / not usable 1.33 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              119173
  Free PE               0
  Allocated PE          119173
  PV UUID               30mxhM-Kd0w-2QL3-Xq8s-0O2w-WVf6-oRzrFZ

  --- Physical volume ---
  PV Name               /dev/mapper/md0_crypt
  VG Name               spike
  PV Size               465.52 GB
  Allocatable           NO
  PE Size (KByte)       4096
  Total PE              119173
  Free PE               119173
  Allocated PE          0
  PV UUID               M3Q9TJ-zy1S-ZgAR-RB4J-4NjO-OcUH-hCZHfJ


so I did it up to point 4 and the did a reboot to check that everything is fine.

Well no. It wasn't.
At boot time, I'm asked for the passphrase of sda5_crypt as usual.
But no question for md0_crypt. And after that it just cr*ped on me because one of the pv of the LVM was missing. Did a rescue boot and a reducevg to get myself out.

Now am doing some testing and I found out the following :
no matter what I do, how many lines I have in my crypptab, I am always only asked for the passphrase of my first line ( sda5_crypt )



My questions are :
- If we have many lines in crypttab, are we supposed to get as many prompt for a passphrase as boot time ?
- Any tips on what I missed ?


NB :
- luks is working fine for the first volume and passphrase is asked at boot time
- luks is working fine for the second volume ( I can luksOpen it )

---

### Post by hyper_ch on 2008-08-18
dunno about lvm but you should be asked for every entry in crypttab.

---

### Post by mewn on 2008-08-19
I will reply myself the correct answer....


NO we don't get asked for every entry from the crypttab at boot time : when we generate a new initrd image, a list ( cryptroot ) of FS to be prompted for the password at boot time is populated.
In this list will be :
- the root "/" in fstab if it's also in crypttab
- any "resume" type ( UPS? ) partition who's also in crypttab.


It seems that the generation of the cryptroot file in the initrd is a bit flaky : it was able to detect that my second PV was a md0 ( raid1 ) encrypted ( and thus in need for a passphrase ) ( but I do agree it was a sub optimal setup ).


I then proceeded with the following actions to change my crypt->LVM setup to raid1 -> crypt -> LVM :

> 
sda5 was my encrypted partition, and spike the LVM above it.
sdb5 is the identical size partition on my new disk.

sudo mdadm -C /dev/md0 -l 1 -n 2 /dev/sdb5 missing
sudo cryptsetup luksFormat /dev/md0
sudo cryptsetup luksOpen /dev/md0 md0_crypt
sudo vgextend spike /dev/mapper/md0_crypt
sudo udevtrigger
sudo pvmove -v /dev/mapper/sda5_crypt /dev/mapper/md0_crypt
-> takes looooong time
sudo vgreduce spike /dev/mapper/sda5_crypt
sudo pvremove /dev/mapper/sda5_crypt
sudo cryptsetup luksClose /dev/mapper/sda5_crypt
sudo mdadm /dev/md0 --add /dev/sda5
sudo vi /etc/crypttab
-> modify the crypttab
sudo mdadm --examine --scan > /etc/mdadm/mdadm.conf

then generate a new initrd :

sudo mkinitramfs-kpkg -o /boot/initrd.img-`uname -r` `uname -r`

I then verified that in my initrd.img. /conf/conf.d/cryptroot was properly populated.

and it didn't fail \o/


This procedure can be followed to modify a standard install of ubuntu on an encrypted partition with LVM to a raid 1 encrypted partition with LVM.


Have fun.

---

