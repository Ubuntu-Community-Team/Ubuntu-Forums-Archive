---
title: "Linux Server always booting to grub rescue after install"
date: 2019-10-02
forum: Server Platforms
---

### Post by b1khulk on 2019-10-02
Hey everyone. I am fairly new to the linux operating system and I am trying to set up a server to host Plex. I bought a 8tb hard drive ([This one to be exact]("https://www.amazon.com/Seagate-IronWolf-256MB-3-5-Inch-Internal/dp/B07D962J5R/ref=sr_1_1_sspa?keywords=8tb+hard+drive&qid=1569808951&s=gateway&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExSFk1QjZVOTZLTVFNJmVuY3J5cHRlZElkPUEwOTI0MjUwMzRTMko4V0xWVFdBUiZlbmNyeXB0ZWRBZElkPUEwOTAyNDU2MTBDTlZKTjY4MFpGVCZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=")) and re-partitioned it to a gpt partition table. then proceeded to install server and after a completed install and a reboot, I get:
 
error: file '/grub/i386-pc/normal.mod' not found 
grub rescue>

It does not matter which version of server I install. 12.04 up to 18.04. results are the same. 

I tried to look for the normal.mod file on all the partitions.

error: file '/grub/i386-pc/normal.mod' not found 
grub rescue> ls
(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (fd0)
grub rescue> ls (hd0,gpt2)
(hd0,gpt2): Filesystem is ext2
grub rescue> ls (hd0,gpt2) /boot/grub/i386-pc/normal.mod
error: file ' /boot/grub/i386-pc/normal.mod' not found
grub rescue> ls (hd0,gpt2)/boot.

grub rescue>


It look like to me that the files too boot from grub are missing. I tried to install the same versions on a 640gb hard drive and its boots correctly. Im beginning to believe it has something to do with my hard drive. Does anyone know what the problem could be?

---

### Post by b1khulk on 2019-10-03
I used a linux ubuntu desktop live session and used GParted to look at my server filesystem

it looks like this:

Partition            File System                 Size                     Used                    Unused                    Flags
/dev/sda1         grub2core.img             1.00MiB                 --                          --                        bios_grub
/dev/sda2         ext4                            7.28TiB                 60.10GiB            7.22TiB  
/dev/sda3         linux-swap                   975.00MiB.            0.00B.                975.00MiB

looks like the grub partition is there. Why is linux booting into grub rescue?

---

