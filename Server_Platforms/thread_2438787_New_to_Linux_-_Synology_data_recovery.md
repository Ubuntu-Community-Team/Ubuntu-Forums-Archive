---
title: "New to Linux - Synology data recovery"
date: 2020-03-18
forum: Server Platforms
---

### Post by shortbread on 2020-03-18
Hello folks,
I'm new to Linux and in under my head! I have a Synology NAS that died, no lights etc and it's likely because of the C2000 bug. To get my data back off the array I have to attach them to a PC and mount the array in Linux as it's btrfs format and I should be able to access it that way. Synology have given me this tutorial to follow: [https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC](https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC)

So I have followed the tutorial's commands (installed adadm and lvm2) and got it up to a point where Linux sees the array using mdadm and lvm2, but it can't mount it because of this error. 
```
root@ubuntu:~# mdadm -Asf && vgchange -ay
mdadm: No arrays found in config file or automatically
```
It seems the array is assembled already though, but when I go to mount it, it fails.
```
root@ubuntu:~# mount /dev/vg1/volume_1 /mnt -o ro
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-volume_1, missing codepage or helper program, or other error.
```
[IMG]https://drive.google.com/open?id=1wT6ryLMoBIPPjbA6NqUtJ64ATbAGFBcF[/IMG][IMG]https://drive.google.com/open?id=1wT6ryLMoBIPPjbA6NqUtJ64ATbAGFBcF[/IMG][ATTACH=CONFIG]285232[/ATTACH]
As you may notice I have Ubuntu as a VM and passed through the physical disks.
[ATTACH=CONFIG]285233[/ATTACH]

From some other sites I got some useful commands:
```
root@ubuntu:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md2 : active raid6 sdc5[4] sdd5[2] sde5[3] sdb5[0]
      7804374912 blocks super 1.2 level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

root@ubuntu:~# pvscan
  PV /dev/md2   VG vg1             lvm2 [<7.27 TiB / 0    free]
  Total: 1 [<7.27 TiB] / in use: 1 [<7.27 TiB] / in no VG: 0 [0   ]


root@ubuntu:~# lsblk -f
NAME    FSTYPE      LABEL                      UUID                                   MOUNTPOINT
loop0   squashfs                                                                      /snap/gnome-characters/3
loop1   squashfs                                                                      /snap/gtk-common-themes/
loop2   squashfs                                                                      /snap/gnome-system-monit
loop3   squashfs                                                                      /snap/gnome-logs/81
loop4   squashfs                                                                      /snap/gnome-calculator/7
loop5   squashfs                                                                      /snap/gnome-system-monit
loop6   squashfs                                                                      /snap/vlc/1397
loop7   squashfs                                                                      /snap/gnome-logs/93
loop8   squashfs                                                                      /snap/gnome-characters/4
loop9   squashfs                                                                      /snap/gnome-calculator/5
loop10  squashfs                                                                      /snap/core/8268
loop11  squashfs                                                                      /snap/gnome-3-28-1804/11
loop12  squashfs                                                                      /snap/core/8689
loop13  squashfs                                                                      /snap/core18/1668
sda                                                                                   
&#9492;&#9472;sda1  ext4                                   c647d1d0-62fa-48ef-bf08-c5cfdb3fd81a   /
sdb                                                                                   
&#9500;&#9472;sdb1                                                                                
&#9500;&#9472;sdb2                                                                                
&#9492;&#9472;sdb5  linux_raid_ Shortology:2               11c3e526-3541-17bf-c20a-fce27d411c93   
  &#9492;&#9472;md2 LVM2_member                            J5K67i-i0Yw-uBG0-TGD1-zJzw-u4Zl-D9sie4 
    &#9500;&#9472;vg1-syno_vg_reserved_area
    &#9474;                                                                                 
    &#9492;&#9472;vg1-volume_1
        btrfs       2018.09.07-19:51:00 v23739 290b37f3-871e-45d8-973d-1da778d0cdcc   
sdc                                                                                   
&#9500;&#9472;sdc1                                                                                
&#9500;&#9472;sdc2                                                                                
&#9492;&#9472;sdc5  linux_raid_ Shortology:2               11c3e526-3541-17bf-c20a-fce27d411c93   
  &#9492;&#9472;md2 LVM2_member                            J5K67i-i0Yw-uBG0-TGD1-zJzw-u4Zl-D9sie4 
    &#9500;&#9472;vg1-syno_vg_reserved_area
    &#9474;                                                                                 
    &#9492;&#9472;vg1-volume_1
        btrfs       2018.09.07-19:51:00 v23739 290b37f3-871e-45d8-973d-1da778d0cdcc   
sdd                                                                                   
&#9500;&#9472;sdd1                                                                                
&#9500;&#9472;sdd2                                                                                
&#9492;&#9472;sdd5  linux_raid_ Shortology:2               11c3e526-3541-17bf-c20a-fce27d411c93   
  &#9492;&#9472;md2 LVM2_member                            J5K67i-i0Yw-uBG0-TGD1-zJzw-u4Zl-D9sie4 
    &#9500;&#9472;vg1-syno_vg_reserved_area
    &#9474;                                                                                 
    &#9492;&#9472;vg1-volume_1
        btrfs       2018.09.07-19:51:00 v23739 290b37f3-871e-45d8-973d-1da778d0cdcc   
sde                                                                                   
&#9500;&#9472;sde1                                                                                
&#9500;&#9472;sde2                                                                                
&#9492;&#9472;sde5  linux_raid_ Shortology:2               11c3e526-3541-17bf-c20a-fce27d411c93   
  &#9492;&#9472;md2 LVM2_member                            J5K67i-i0Yw-uBG0-TGD1-zJzw-u4Zl-D9sie4 
    &#9500;&#9472;vg1-syno_vg_reserved_area
    &#9474;                                                                                 
    &#9492;&#9472;vg1-volume_1
        btrfs       2018.09.07-19:51:00 v23739 290b37f3-871e-45d8-973d-1da778d0cdcc   
sr0
```                                                                              
I hope you lovely bunch will be able to help me recover my data, thanks in advance!

---

### Post by slickymaster on 2020-03-18
Thread moved to **Server Platforms** for a better fit

---

### Post by shortbread on 2020-03-19
Ok thanks, hopefully someone will have some help for me.

---

### Post by TheFu on 2020-03-19
> **shortbread said:**
> Ok thanks, hopefully someone will have some help for me.

it is a fairly specific issue, so hardly anyone, anywhere will be able to help.

i would try to help if only LVM were involved, but btrfs has been deprecated by redhat for a number of reasons. it isn't available in RH8 at all.  With my limited knowledge, I’m struggling to understand why, why, why, anyone would use both LVM and BTRFS. Just doesn't make sense.

Btrfs lies to normal Unix system tools, so the tools I’d normally use can't be trusted.

But i don't know btrfs, so perhaps there's some odd, but great reason to mix both.

Sorry.  My recommendation is to seek help on a Synology-specific support forum and to learn from whatever happened so the data isn't at risk next time anything similar happens.

Might check whether any file systems in /dev/mapper/
Here's mne:
```
$ ls -l  /dev/mapper/*
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-home--lv -> ../dm-3
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-root -> ../dm-1
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-stuff -> ../dm-4
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-swap_1 -> ../dm-2
```
So, i'd mount "stuff using:
```
sudo mkdir /stuff
sudo mount -t ext4  /dev/mapper/ubuntu--vg-stuff   /stuff
```
The type ext4 is for that file system.  No clue how to mount btrfs. Sorry.  Not certain i'd assume a regular mount would do it.

---

### Post by shortbread on 2020-03-27
> **TheFu said:**
> it is a fairly specific issue, so hardly anyone, anywhere will be able to help.

i would try to help if only LVM were involved, but btrfs has been deprecated by redhat for a number of reasons. it isn't available in RH8 at all.  With my limited knowledge, I’m struggling to understand why, why, why, anyone would use both LVM and BTRFS. Just doesn't make sense.

Btrfs lies to normal Unix system tools, so the tools I’d normally use can't be trusted.

But i don't know btrfs, so perhaps there's some odd, but great reason to mix both.

Sorry.  My recommendation is to seek help on a Synology-specific support forum and to learn from whatever happened so the data isn't at risk next time anything similar happens.

Might check whether any file systems in /dev/mapper/
Here's mne:
```
$ ls -l  /dev/mapper/*
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-home--lv -> ../dm-3
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-root -> ../dm-1
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-stuff -> ../dm-4
lrwxrwxrwx 1 root root       7 Mar 14 12:51 /dev/mapper/ubuntu--vg-swap_1 -> ../dm-2
```
So, i'd mount "stuff using:
```
sudo mkdir /stuff
sudo mount -t ext4  /dev/mapper/ubuntu--vg-stuff   /stuff
```
The type ext4 is for that file system.  No clue how to mount btrfs. Sorry.  Not certain i'd assume a regular mount would do it.

I see. Well, thanks for taking a look anyway.

---

