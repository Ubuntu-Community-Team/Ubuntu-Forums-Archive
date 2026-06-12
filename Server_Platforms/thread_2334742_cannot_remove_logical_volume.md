---
title: "cannot remove logical volume"
date: 2016-08-22
forum: Server Platforms
---

### Post by evertmdc on 2016-08-22
Hello,

I have this old logical volume on one of my machines and I wanted to get rid of it. It claims there is an active filesystem on there.
Google was not my friend on this one. There is some more info below.

```
sudo lvremove ssd/ssd
  Logical volume ssd/ssd contains a filesystem in use.

```

dmsetup info -c
```
ssd-ssd           252   0 L--w    1    2      0 LVM-C09ifq2bjSlk2YzsGuuAj102rhUwEfLUOVNmOqdI1zZlsFjTeIOm0M9WaUWqTYJS
```

It is not mounted.
```
umount /dev/mapper/ssd-ssd
umount: /dev/mapper/ssd-ssd is not mounted (according to mtab)
```

Someone wrote that it may be NFS that's blocking the filesystem, but there is no exports file.
```
cat /etc/exports
cat: /etc/exports: No such file or directory

```

Does anyone have any pointers as to how this can be solved?

---

### Post by steeldriver on 2016-08-22
Maybe you need to deactivate the volume (lvchange -an ...) ?

---

### Post by evertmdc on 2016-08-22
Hello Steeldriver,

That gives me the same output unfortunately.
```

sudo lvchange -an /dev/mapper/ssd-ssd
  Logical volume ssd/ssd contains a filesystem in use.
```

---

### Post by darkod on 2016-08-22
Could you possibly have LVM inside LVM? What if you list all PV devices?
```
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

---

### Post by evertmdc on 2016-08-25
Hello Darkod,

Here is the output:

  ```
--- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               ssd
  PV Size               223.57 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              57233
  Free PE               0
  Allocated PE          57233
  PV UUID               ayqQoe-qXRm-ynzd-vlvi-gDD6-tWTo-LhChII


  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               ssd
  PV Size               223.57 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              57233
  Free PE               1033
  Allocated PE          56200
  PV UUID               9PQFet-AHCK-1KAJ-XVvI-XiHa-YYoA-eUjWid
```

  ```
--- Volume group ---
  VG Name               ssd
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  11
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                8
  Open LV               8
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               447.13 GiB
  PE Size               4.00 MiB
  Total PE              114466
  Alloc PE / Size       113433 / 443.10 GiB
  Free  PE / Size       1033 / 4.04 GiB
  VG UUID               C09ifq-2bjS-lk2Y-zsGu-uAj1-02rh-UwEfLU
```

  ```
LV Path                /dev/ssd/ssd
  LV Name                ssd
  VG Name                ssd
  LV UUID                OVNmOq-dI1z-ZlsF-jTeI-Om0M-9WaU-WqTYJS
  LV Write Access        read/write
  LV Creation host, time eu3, 2014-08-05 13:25:07 +0200
  LV Status              available
  # open                 1
  LV Size                360.00 GiB
  Current LE             92160
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
```

The logical volume contains old data and is taking up most of the space in the volumegroup.

---

### Post by darkod on 2016-08-25
And df -h is not listing /dev/ssd/ssd as mounted at any mount point?

You have not used it as any raid device or similar? You said it is old LV so you were/are using it. Do you remember the mount point and how do you use it? That might help to pinpoint how to unmount it.

PS. It just crossed my mind that if the filesystem (folders) are really in use, it can deny to unmount. That is normal behavior. Check where is /dev/ssd/ssd mounted and what is using that mount point. Something like samba using a share on it would block it from unmounting. Any service that is using that mount point?

And another note about the naming convention of LVM. Instead of /dev/mapper/VGname-LVname you can also use /dev/VGname/LVname. I prefer the latter. Maybe it will unmount if you try with that. But first i would double check:
a) Where is it mounted
b) What is using it

When you find out that you can also try unmounting the mount point, not using the device name:
```
sudo umount /mountpoint
```

---

### Post by evertmdc on 2016-08-26
No it is not listed in df -h
The entry is still in my /etc/fstab so I have the mountpoint
When trying to unmount either /dev/ssd/ssd or /dev/mapper/ssd-ssd I get the message that it is not mounted.

I checked with lsof if there was anything with the name ssd mounted but got no results
It does give a lot of messages with > lsof: no pwd entry for UID 99
I assume this has something to do with docker

---

### Post by darkod on 2016-08-26
OK.

But just to clarify, /dev/ssd/ssd or /dev/mapper/ssd-sdd are not mount points. Those are synonyms for the device name. If you have the mountpoint from fstab you can try that, but if df -h doesn't show it, I see it as pointless.

So it doesn't look mounted but it does keep saying it has FS in use... Weird one. Don't tell me you have swap there, swap doesn't show in df -h. :) But usually you don't create 340GB swap. Can you post the output of:
```
sudo parted -l
```

Especially the part about /dev/ssd/ssd (if it displays it).

PS. Actually you might be able to print the parted info only for that LV with something like:
```
sudo parted /dev/ssd/ssd print
```

---

### Post by evertmdc on 2016-08-26
No the mountpoint is /ssd/oldlvm

Here is the part for the lv that came from parted -l
```
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ssd-ssd: 387GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  387GB  387GB  ext4
```

Thanks for your help on this.

---

### Post by darkod on 2016-08-26
Very weird... So, just to try:
```
sudo umount /ssd/oldlvm
```

Also, if you go into /ssd/oldlvm, does it show any content there??? You know that mount point should be empty folders, but in case something happens and the physical device fails, the actual folder in root can start getting filled with data. Although that wouldn't explain you not being able to delete the LV...

---

### Post by evertmdc on 2016-08-26
The directory is empty
```
> ls -al /ssd/oldlvm
total 8
drwxr-xr-x  2 root root 4096 Jul 12 10:09 ./
drwxr-xr-x 11 root root 4096 Jul 25 09:25 ../
```
And unmount is saying that it was not mounted..
```
> sudo umount /ssd/oldlvm
umount: /ssd/oldlvm: not mounted
```

---

### Post by darkod on 2016-08-26
Do you have any volume snapshots maybe?

Here it mentioned you can force the remove but it does say even the -f won't deactivate a volume with mounted FS.
[http://manpages.ubuntu.com/manpages/xenial/man8/lvremove.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/lvremove.8.html)

So, just to give it a shot:
```
sudo lvremove -f ssd/ssd
```

A snapshot might be holding it back but I have never used one so I will have to search how to check for one.

PS. And just to check, does this return anything?
```
lsof | grep '/ssd/oldlvm'
```

PPS. In one place it says if all else fails use a live session and remove the volume. That's actually not a bad idea. The live session does not mount any of your OS parts. I just don't remember if lvm is included in ubuntu desktop live cd now (earlier it wasn't). So in the live session you might need to do sudo apt-get install lvm2. Do not even activate the volumes, simply try the lvremove ssd/ssd.

If it complains the VG is not active, then try to activate it. So it would go something like:
```
sudo apt-get install lvm2
sudo vgchange -ay (if needed)
sudo lvremove -f ssd/ssd
```

---

### Post by evertmdc on 2016-08-29
Here's the output:
```
sudo lvremove -f ssd/ssd
  Logical volume ssd/ssd contains a filesystem in use.
```


No there is no content under /ssd/oldlvm no.

---

### Post by darkod on 2016-08-29
Did you see the rest of my post too?

If you are reading the replies only in email, don't. Visit the forum and open the thread. Because when we edit a post, you don't receive the modification by email, only the initial post.

I added few things to my last one...

---

### Post by evertmdc on 2016-08-29
I was indeed looking through mail.

When running the lsof command there was a long list of lines with 'lsof: no pwd entry for UID 999'. But those are not standard output lines because when I do a wc -l it says 0

I can't try the live cd because it's a production machine unfortunately.

---

### Post by evertmdc on 2016-10-06
For anyone having the same issue:
The problem here was a container running cadvisor. Stopping the container allowed me to remove the logical volume without issues.
There are issues open on the cadvisor issue tracker that explain that containers started before the cadvisor container started could not be removed. It seems the same is true for the lvm volume.

---

