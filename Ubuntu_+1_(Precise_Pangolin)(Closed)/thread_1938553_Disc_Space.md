---
title: "Disc Space"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-03-09
G'Day;  I have a strange problem, I have 12.04 installed on a 65 Gb partition but now I'm told I have no room left to transfer music files from 11.10 to 12.04. does anyone have any suggestions please
 Regards Miykel

---

### Post by matt_symes on 2012-03-09
Hi

> **Miykel said:**
> G'Day;  I have a strange problem, I have 12.04 installed on a 65 Gb partition but now I'm told I have no room left to transfer music files from 11.10 to 12.04. does anyone have any suggestions please
 Regards Miykel

Open a terminal and type these commands.

```
df -h
```

```
sudo dumpe2fs /dev/sda1 | grep -i ^inode
```

Change sda1 as required. Post back results here.

Kind regards

---

### Post by fabricator4 on 2012-03-09
> **Miykel said:**
> G'Day;  I have a strange problem, I have 12.04 installed on a 65 Gb partition but now I'm told I have no room left to transfer music files from 11.10 to 12.04. does anyone have any suggestions please
 Regards Miykel

Please show us the output of 

df -H

and 

df -i


Thanks

---

### Post by Miykel on 2012-03-09
Thanks so much for the replies guys, I run the commands please find the results following

[
miykel@miykel-H61M-USB3-B3:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb6        61G   58G   36M 100% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           788M  976K  787M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  156K  2.0G   1% /run/shm


miykel@miykel-H61M-USB3-B3:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sdb6      8077312 163300 7914012    3% /
udev            501869    674  501195    1% /dev
tmpfs           504061    625  503436    1% /run
none            504061      1  504060    1% /run/lock
none            504061      7  504054    1% /run/shm ]

  I don't understand how Icould use so much room on such a large partition without installing many programs, I run the same commands in 11.10, which is installed on an 80Gb partition, and found the same result, I had no idea Ubuntu was such a large OS as I also have W7 on an 80Gb partition with many programs installed and it has only used 32Gb, am I missing something or is this normal ??
 Kind Regards Miykel

P.S.  Finally got this to run  lol
miykel@miykel-H61M-USB3-B3:~$ sudo dumpe2fs /dev/sdb6 | grep -i ^inode
[sudo] password for miykel: 
dumpe2fs 1.42 (29-Nov-2011)
Inode count:              8077312
Inodes per group:         16384
Inode blocks per group:   512
Inode size:              128

Miykel

---

### Post by dcstar on 2012-03-09
> **Miykel said:**
> Thanks so much for the replies guys, I run the commands please find the results following

```
miykel@miykel-H61M-USB3-B3:~$ df -h
Filesystem      Size  Used Avail **Use%** Mounted on
/dev/sdb6        61G   58G   36M **100%** /
```
.......

100% full is 100% full. You need to see what is taking up the space in the root partition:
```
gksudo baobab
```

---

### Post by fabricator4 on 2012-03-10
> **Miykel said:**
> 
  I don't understand how Icould use so much room on such a large partition without installing many programs, I run the same commands in 11.10, which is installed on an 80Gb partition, and found the same result, I had no idea Ubuntu was such a large OS as I also have W7 on an 80Gb partition with many programs installed and it has only used 32Gb, am I missing something or is this normal ??


Yes, you're missing something. A clean install of Ubuntu will use around 3.5 GB, possibly a bit more for the beta.  You've got to find out what is using the other 57GB.  I note that you're using 100% disk space, but only about 3% of the inodes, which means you'd be looking for a big heap of really large files: Full length HD movies, a large database, some virtual hard drivers (like for VB or similar), some large compressed backup files, or a combination of all of these.

Chris

Edit: The fastest way to fill up a hard drive is to recursively back up /home/username to a network share that exists in the /home/username directory.

I actually did this once, but only the once ;-)

Chris

---

### Post by Miykel on 2012-03-10
Thanks so much guys, the code from dcstar gave me the answer, I have 58.5 Gb of music in my music file, blast !!! no wonder I ran out of space ...lol,
  Must have a good clean out !!, I have the music on another drive so I'll loose nothing, as I always say ..ignorance is not always bliss ... explains why I have the same problem with 11.10  damn!!!
  
  What is the command  "autoremove" for btw

Many Thanks Miykel

---

### Post by Harry33 on 2012-03-10
> **Miykel said:**
> 
...
  What is the command  "autoremove" for btw

Many Thanks Miykel

It is:

> sudo apt-get autoremove

---

### Post by Elfy on 2012-03-10
> **Miykel said:**
> What is the command  "autoremove" for btw

Many Thanks Miykel

> **Harry33 said:**
> It is:
> 
autoremove - autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed.

```
man apt-get |grep autoremove
```

---

### Post by Miykel on 2012-03-10
Thanks once again for all your help;
Cleaned out my "music" folder, didn't realize how much junk I'd accumulated in that file, I'd just copied it from W7...blast !!..now I've got lotsa room  lol.
Kind Regards  Miykel

---

