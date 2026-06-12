---
title: "Slackware 12.1: GRUB Issues"
date: 2008-12-07
forum: Slackware and derivatives
---

### Post by Jengajam2 on 2008-12-07
I did a successful install of Slackware, but I'm having trouble using Grub to boot it. The first time I installed it and tried getting Grub to boot it I got an "Error 17 Cannot Mount Selected Partition" and "File system Unknown" when trying to boot it. I thought it had to do with using the JFS file system, so I reinstalled it with an ext2 file system. But I still got the same error. The installation and boot worked on my laptop just fine, but not on my desktop. Gparted  detected the partition just fine. 

Here's my menu.lst
```
title		Slackware Linux (Slackware 12.1.0) (on /dev/sda7)
root		(hd0,0)
kernel		/boot/vmlinuz-huge-2.6.24.5 root=/dev/sda7
savedefault
boot
```

Any help will be appreciated.

---

### Post by caljohnsmith on 2008-12-07
Usually getting a Grub error 17 when booting an OS entry in Grub's menu means that the (hdX,Y) is wrong. How about first posting:
```
sudo fdisk -lu
```
And please identify your Slackware partition. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by Jengajam2 on 2008-12-07
> **caljohnsmith said:**
> Usually getting a Grub error 17 when booting an OS entry in Grub's menu means that the (hdX,Y) is wrong. How about first posting:
```
sudo fdisk -lu
```
And please identify your Slackware partition. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.
sudo fdisk -lu
```
disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   307339514   153669726    7  HPFS/NTFS
/dev/sda2       307339515   470270744    81465615    5  Extended
/dev/sda3       470270745   488392064     9060660    c  W95 FAT32 (LBA)
/dev/sda5       463539573   470270744     3365586   82  Linux swap / Solaris
/dev/sda6       307339641   425658239    59159299+  83  Linux
/dev/sda7       430847298   463539509    16346106   83  Linux
/dev/sda8       425658303   430847234     2594466   82  Linux swap / Solaris

```Partition /dev/sda7 is Slackware while /dev/sda8 is it's swap.

```
/dev/sda1: eb52
2:xxd: /dev/sda2: No such file or directory
3: e9a7
5:0000
6:0000
7:0000
8:0000

```

and finally: ```
1:0066

```

NOTE: I may have found the problem, look at the attached picture.
I took space from my linux mint partition to make my slackware partitions, so now they're in /dev/sda2.

---

### Post by caljohnsmith on 2008-12-07
OK, if Slackware is on sda7, that would be (hd0,6) in Grub's Convoluted World, so I think all you would need to do is change all your Slackware Grub entries to use "root (hd0,6)" instead of the "root (hd0,0)" that you show in the first post. How about giving that a shot and let me know how it goes. :)

---

### Post by Jengajam2 on 2008-12-07
> **caljohnsmith said:**
> OK, if Slackware is on sda7, that would be (hd0,6) in Grub's Convoluted World, so I think all you would need to do is change all your Slackware Grub entries to use "root (hd0,6)" instead of the "root (hd0,0)" that you show in the first post. How about giving that a shot and let me know how it goes. :)

Thank you, it boots up now.

---

### Post by Vince4Amy on 2008-12-08
Just out of interest did you not like lilo? I've found lilo to be easier and more reliable than GRUB. But that's my experience just curious to know yours.

---

### Post by Jengajam2 on 2008-12-08
> **Vince4Amy said:**
> Just out of interest did you not like lilo? I've found lilo to be easier and more reliable than GRUB. But that's my experience just curious to know yours.

I just didn't install LILO because I already had GRUB installed. I've used LILO on my old computer for DEli Linux, no problems as far as I could tell.

---

### Post by Vince4Amy on 2008-12-09
Oh I understand fair enough.

---

### Post by capn_hector on 2008-12-11
another thing i noticed on your setup is your using 2 swap partitions, you only need 1, i dual boot ubuntu and slackware and both feed off the same swap, swap is hdd based ram (simplistic and not totaly correct but close enough) now if changing it is going to be a pain it does not hurt any thing but you could free up some space by just using 1 swap partition.

---

