---
title: "HOWTO: recover lost partition after unexpected shutdown (Lucid)"
date: 2011-02-05
forum: Tutorials
---

### Post by dentaku65 on 2011-02-05
Two days ago "someone" took out brutally (but without intention) the power supply of my box; when I reboot the machine I've got this message just after the Grub was loaded:
```
No init found. Try passing init= boot arg
BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

```
Mmm, I've never seen this, but I quickly understood that my box was seriously damaged, the access to my data was impossible; user in panic :-)

After two days of trying to fix the issue I've been able to get back my disk intact; I know, I'm a pretty lucky folk.

First to all this "*guide*" worked for me and for my case; for what I've understood the problem was regarding something about EXT4 filesystem that was locking the access to the disk due to the unexpected shutdown (of course); Grub was ok, hardware disk was ok; I'm not so deep involved in the knowledge of the filesystem stuff, but I had the high suspect that the *inode* structure was denying the system to be mounted/accessed for some pending operations.

At this moment I've created a USB key with the live of **Ubuntu Rescue Remix** [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) and I booted the machine with this distro.

As a first step I've just list my partitions (sda in my case it's the only drive):
```
sudo fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000619b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29844   239721898+  83  Linux
/dev/sda2           29845       30401     4474102+   5  Extended
/dev/sda5           29845       30401     4474071   82  Linux swap / Solaris
```
The damaged partition, in my case, was /dev/sda1.
Now I've tried to do an fsck:
```
sudo fsck -yv /dev/sda1
```
but
```
fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```
What? The disk was obviously not mounted (although I did an umount); no way, I was not able to do an fsck on that partition.

I've tried everything:
[LIST]
[*]Create an image with dd and mount the image after an fsck (the image was unusable due to an arror in the filesystem)
[*]Back-up the partition with PhotoRec (the files saved were really trivial)
[*]Mount the disk as slave (the Ubuntu Rescue freezed trying to mount it)
[/LIST]
I've was almost to give up and prepare myself to format the disk, when I came across this technical document (for EXT3) 
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/) 
So I decided to try it as last resource (remove the first *inode*), **based on consideration that all my data was already lost**.
```
sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs:  **clri <8>**
debugfs:  **quit**
```
Then I've launch fsck:
```
sudo fsck -yv /dev/sda1
```
but
```
fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```
Damn! No way; but I was thinking that maybe a reboot (*****) was needed.
(*****) to reboot with Ubuntu Rescue I've used ALT+PrnScreen+r+e+i+s+u+b instead of normal reboot because the normal reboot was not working :-(

Then I've launch fsck again:
```
sudo fsck -yv /dev/sda1
```
and now this time worked!
Fsck fix the filesystem errors; I've had not need to do a tune2fs as stated in the document reported above for the re-creation of the journalized filesystem.

Rebooted the machine with my disk and everything is all there.
Happy user.

---

### Post by tarpat1 on 2011-02-17
I cant thank you enough for this, you just saved me from wiping and reloading!

---

### Post by matt_symes on 2011-02-17
Hi

```
sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs:  clri <8>
debugfs:  quit
```

Clearing the journal inode. Must remember that one :) Nicely done.

Kind regards

---

### Post by danijela86 on 2011-02-18
Thank you!!! You really saved me. :)

---

### Post by Liz on 2011-03-06
excellent !!

thanks so much. saved me hours of time to fix my sisters laptop. much much appreciated.

---

### Post by emtdan on 2011-03-08
You sir are a gentleman and a scholar. If you every need a pizza when you are in Philly shoot me a message.

---

### Post by vineetma on 2011-03-11
This was great. Saved so much of time and stress that I was getting into. Unfortunately, it didn't come through google as the  top solution but got through one of the links in another thread.

---

### Post by anto01 on 2011-03-12
ok so the same thing happened to me 

when i do fdisk -l /dev/sda i get 
/dev/sda1                       boot    system
                                        *       NTFS
warning: partition 1 does not end on cylinder boundary 

same for /dev/sda2 , /dev/sda5 , /dev/sda6

so when i try
sudo fsck -yv /dev/sda1
i get fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for dev/sda1

so i am pretty over my head at present and would like to recover the items

---

### Post by dentaku65 on 2011-03-13
Hi,
this guide it is for EXT4 filesystem where the first inode lock the access to the disk; be careful with the commands in this guide with a different filesystem (NTFS).

Afaik for NTFS there is a suite called **ntfsprogs** that should be included in Ubuntu Remix for helping your situation (type ntfs+tab on terminal for the command list below, in red maybe two useful commands for your situation, see always man pages):
```
ntfs-3g
ntfs-3g.usermap
ntfscluster
[COLOR="Red"]ntfsfix[/COLOR] 
ntfsls
ntfsundelete
ntfs-3g.probe
ntfscat
ntfscmp
[COLOR="Red"]ntfsinfo[/COLOR]
ntfsmount         
ntfs-3g.secaudit
ntfsclone
ntfscp
ntfslabel
ntfsresize
```
Again, this guide it is for EXT4 issue only with a "fix" derived from EXT3 (as documented).

Good luck

> **anto01 said:**
> ok so the same thing happened to me 

when i do fdisk -l /dev/sda i get 
/dev/sda1                       boot    system
                                        *       NTFS
warning: partition 1 does not end on cylinder boundary 

same for /dev/sda2 , /dev/sda5 , /dev/sda6

so when i try
sudo fsck -yv /dev/sda1
i get fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for dev/sda1

so i am pretty over my head at present and would like to recover the items

---

### Post by Cype on 2011-04-29
Thank you so much, was searching for a solution for about a week now and this finally solved it.

---

### Post by jackantares on 2011-05-07
OMG!!! Thank you! I spent my day trying to recover my Ubuntu... Thank you very very much!

---

### Post by geazzy on 2011-05-10
I save it, maybe one day I experienced something like this ....

btw thanks for this tutorial

---

### Post by obieito on 2011-05-22
Two words for you:


*** THANK ***

*** YOU ***

---

### Post by ryman90 on 2011-07-17
Even I had the same problem I've put a probable solution here 

[http://ubuntuforums.org/showthread.php?p=11056317#post11056317](http://ubuntuforums.org/showthread.php?p=11056317#post11056317)

Hope that helps..good luck..:)

---

### Post by dentaku65 on 2011-07-18
> **ryman90 said:**
> Even I had the same problem I've put a probable solution here 

[http://ubuntuforums.org/showthread.php?p=11056317#post11056317](http://ubuntuforums.org/showthread.php?p=11056317#post11056317)

Hope that helps..good luck..:)

Hi ryman90,
pointing on step 4 of your solution should in fact works as you indicated, but in my case (Ubuntu Rescue Remix it is a Live CD as well) I've got this "funny" message

```
fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

This means that the file system is locked even if is not mounted.

---

### Post by learst on 2011-11-16
Thanks! Your solution was the perfect one and solved my problem after I had to manually shut down Ubuntu when it hanged after the monitor went to sleep (which I'm still puzzled at).

---

### Post by leedald on 2012-01-06
***********************************
*********** t h a n k *  y o u ***********
***********************************

Sprang back to life without loosing anything, saved weeks of work

Ironically, I broke the system doing a rsync backup with a directory name containing a space so some strange overwrites or something happened (I think that was the problem). Afterwards the shutdown dialogue box showed no buttons. I used a hard powerdown. Next time I booted I had the dreaded mount error and busy sda1 mount problem. This shows the power of a large user community.

---

### Post by alameen on 2012-01-14
WOW! I spent almost two weeks trying to fix ubuntu having the same problem to no avail. But this thread just saved me. Worked perfectly, Thank God. Thank you very much also. :)

---

### Post by roopeshmicasa on 2012-02-14
I am also facing same problem BUT haven't got any solution to it and system is still not working. Seems like something really went wrong with the system. Nothing is working HERE. HELP!!!

Here is the link to the thread where I have posted my problem 

[http://ubuntuforums.org/showthread.php?t=1914197](http://ubuntuforums.org/showthread.php?t=1914197)

Any help will be much appreciated

---

### Post by avec on 2012-02-15
[FONT=monospace]The problems startet when I did a upgrade for 10.04.

Ran a Live CD and 
[/FONT]sudo fsck -yv /dev/sda1 
[FONT=monospace]Not the first time fsck has rescued me from slightly panic :D


[/FONT]

---

### Post by omac on 2012-02-28
dentaku65 .....

THANK YOU THANK YOU THANK YOU THANK YOU!

Your solution worked perfectly.  I thought I'd lost the contents of the drive for good.

Again, thank you. :)

---

### Post by inixon on 2012-03-19
Thank you!!!
You save a lot of my time!!!:D

---

### Post by nkl on 2012-04-14
zillions of thanks!! you are a life saver dentaku65 :KS!!!

---

### Post by TMD on 2012-06-08
So this thread is the gift that keeps giving. Thank you dentaku!

---

### Post by dreamsrobotic on 2012-07-25
Seriously, thank you! I had the exact same problem and your solution was perfect. Your original post keeps giving.

---

### Post by kg4cna on 2012-09-10
Wow...quick and easy!

Thanks so much for sharing :)

Allen

---

### Post by pankajcambure on 2012-09-27
> **dentaku65 said:**
> Two days ago "someone" took out brutally (but without intention) the power supply of my box; when I reboot the machine I've got this message just after the Grub was loaded:
```
No init found. Try passing init= boot arg
BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

```
Mmm, I've never seen this, but I quickly understood that my box was seriously damaged, the access to my data was impossible; user in panic :-)

After two days of trying to fix the issue I've been able to get back my disk intact; I know, I'm a pretty lucky folk.

First to all this "*guide*" worked for me and for my case; for what I've understood the problem was regarding something about EXT4 filesystem that was locking the access to the disk due to the unexpected shutdown (of course); Grub was ok, hardware disk was ok; I'm not so deep involved in the knowledge of the filesystem stuff, but I had the high suspect that the *inode* structure was denying the system to be mounted/accessed for some pending operations.

At this moment I've created a USB key with the live of **Ubuntu Rescue Remix** [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) and I booted the machine with this distro.

As a first step I've just list my partitions (sda in my case it's the only drive):
```
sudo fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000619b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29844   239721898+  83  Linux
/dev/sda2           29845       30401     4474102+   5  Extended
/dev/sda5           29845       30401     4474071   82  Linux swap / Solaris
```
The damaged partition, in my case, was /dev/sda1.
Now I've tried to do an fsck:
```
sudo fsck -yv /dev/sda1
```
but
```
fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```
What? The disk was obviously not mounted (although I did an umount); no way, I was not able to do an fsck on that partition.

I've tried everything:
[LIST]
[*]Create an image with dd and mount the image after an fsck (the image was unusable due to an arror in the filesystem)
[*]Back-up the partition with PhotoRec (the files saved were really trivial)
[*]Mount the disk as slave (the Ubuntu Rescue freezed trying to mount it)
[/LIST]
I've was almost to give up and prepare myself to format the disk, when I came across this technical document (for EXT3) 
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/) 
So I decided to try it as last resource (remove the first *inode*), **based on consideration that all my data was already lost**.
```
sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs:  **clri <8>**
debugfs:  **quit**
```
Then I've launch fsck:
```
sudo fsck -yv /dev/sda1
```
but
```
fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```
Damn! No way; but I was thinking that maybe a reboot (*****) was needed.
(*****) to reboot with Ubuntu Rescue I've used ALT+PrnScreen+r+e+i+s+u+b instead of normal reboot because the normal reboot was not working :-(

Then I've launch fsck again:
```
sudo fsck -yv /dev/sda1
```
and now this time worked!
Fsck fix the filesystem errors; I've had not need to do a tune2fs as stated in the document reported above for the re-creation of the journalized filesystem.

Rebooted the machine with my disk and everything is all there.
Happy user.

Hidentaku65,

Thanks a lot .. the following command worked for me..\

sudo fdisk -l /dev/sda

Regards

Pankaj C

---

### Post by geazzy on 2012-09-27
Thanks for great tutorial :)

---

### Post by deruwied on 2012-10-29
Thank you!

---

