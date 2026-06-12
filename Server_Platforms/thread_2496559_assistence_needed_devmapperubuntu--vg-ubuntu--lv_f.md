---
title: "assistence needed: /dev/mapper/ubuntu--vg-ubuntu--lv full, but lsblk says 800Gb free"
date: 2024-04-03
forum: Server Platforms
---

### Post by michaeltorfs on 2024-04-03
Hi,

Looking for some assistance, i'm quite a noob still:)

My default drive is full, I get all kinds of errors (logical if disk is fulll).
But df -h confirms the disk if full, but another command lsblk give a much bigger disk. How is this possible? The physical drive is 1TB. Ubuntu proposed me a 100GB drive during installation, I (thought) I enlarged it to use the full physical disk.

[FONT=courier new]mto@ubuntu:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              1.6G  2.6M  1.6G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   98G   93G  4.2M 100% /
tmpfs                              7.7G     0  7.7G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
/dev/sda2                          2.0G  130M  1.7G   8% /boot
/dev/sda1                          1.1G  6.1M  1.1G   1% /boot/efi
/dev/nvme0n1p1                     916G   57G  813G   7% /var/system01
/dev/md0                           9.1T  6.0T  2.6T  70% /var/data01
tmpfs                              1.6G  4.0K  1.6G   1% /run/user/1000
mto@ubuntu:~$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
sda                         8:0    0 931.5G  0 disk
&#9500;&#9472;sda1                      8:1    0     1G  0 part  /boot/efi
&#9500;&#9472;sda2                      8:2    0     2G  0 part  /boot
&#9492;&#9472;sda3                      8:3    0 928.5G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0 928.5G  0 lvm   /
sdb                         8:16   0   9.1T  0 disk
&#9492;&#9472;sdb1                      8:17   0   9.1T  0 part
  &#9492;&#9472;md0                     9:0    0   9.1T  0 raid1 /var/data01
sdc                         8:32   0   9.1T  0 disk
&#9492;&#9472;sdc1                      8:33   0   9.1T  0 part
  &#9492;&#9472;md0                     9:0    0   9.1T  0 raid1 /var/data01
nvme0n1                   259:0    0 931.5G  0 disk
&#9492;&#9472;nvme0n1p1               259:1    0 931.5G  0 part  /var/system01[/FONT]


As you can see, df says 98GB and 4MB available (so full)
But lsblk says it is 928.5GB

I would like df to also recognize the 928GB.


Kind regards,
Michael

---

### Post by darkod on 2024-04-03
When using LVM basically you have three main building blocks.

1). The physical disk partition that you use as LVM physical volume (PV). In your case it seems to be /dev/sda3 with size 928GB.

2). The volume group (VG) that uses the PV. In your case seems to be named ubuntu-vg.

3). The logical volume (LV) which is the volume actually holding the filesystem and used. In your case ubuntu-lv.

If your LV is 98GB it will get full even if you have a lot of unused space on the PV of 928GB. That is big size difference between the both.

Usually in LVM you would use one of more VGs to hold one or more LVs. If you create only one VG with only one LV and assign it the whole space of the PV, it sort of beats the point because you are not actually using the LVM benefits.

To help you further post the output of the following commands in CODE tags:
```
sudo pvs
sudo vgs
sudo lvs
```

---

### Post by Dennis N on 2024-04-03
> As you can see, df says 98GB and 4MB available (so full). But lsblk says it is 928.5GB. I would like df to also recognize the 928GB.
To resize the file system of ubuntu-lv to use all the space in the lv:
```
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv
```
This can be done on a mounted file system.

---

### Post by darkod on 2024-04-04
Correct. I didn't notice that part in the lsblk output. The LV ubuntu-lv already seems to be 928GB, the maximum size of the physical partition. But your filesystem is only 98GB and you can extend that live while mounted as Dennis said.

The output of 'sudo lvs' would have given us the size of the LV to avoid any doubt.

---

