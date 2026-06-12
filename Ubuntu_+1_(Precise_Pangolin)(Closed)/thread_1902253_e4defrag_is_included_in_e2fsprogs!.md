---
title: "e4defrag is included in e2fsprogs!"
date: 2011-12-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2011-12-30
Following this bug for a while: [https://bugs.launchpad.net/bugs/321528](https://bugs.launchpad.net/bugs/321528)

e4defrag is now in e2fsprogs! Yay! Thanks to Anssi Hannula for pointing it out. :)

$ man e4defrag

```
NAME
       e4defrag - online defragmenter for ext4 filesystem

SYNOPSIS
       e4defrag [ -c ] [ -v ] target ...

DESCRIPTION
       e4defrag  reduces fragmentation of extent based file. The file targeted
       by e4defrag is created on ext4 filesystem made with "-O extent"  option
       (see  mke2fs(8)).   The  targeted  file gets more contiguous blocks and
       improves the file access speed.

       target is a regular file, a directory, or a device that is  mounted  as
       ext4 filesystem.  If target is a directory, e4defrag reduces fragmenta&#8208;
       tion of all files in it. If target is a device, e4defrag gets the mount
       point of it and reduces fragmentation of all files in this mount point.

OPTIONS
       -c     Get  a  current  fragmentation  count and an ideal fragmentation
              count, and calculate fragmentation score based on them. By  see&#8208;
              ing  this  score,  we  can  determine  whether we should execute
              e4defrag to target.  When used with -v option, the current frag&#8208;
              mentation  count  and  the ideal fragmentation count are printed
              for each file.

              Also this option outputs the average data size in one extent. If
              you  see it, you'll find the file has ideal extents or not. Note
              that the maximum extent size is 131072KB in ext4 filesystem  (if
              block size is 4KB).

              If this option is specified, target is never defragmented.

       -v     Print  error  messages  and  the  fragmentation count before and
              after defrag for each file.

NOTES
       e4defrag does not support swap file, files in lost+found directory, and
       files  allocated in indirect blocks. When target is a device or a mount
       point, e4defrag doesn't  defragment  files  in  mount  point  of  other
       device.

       Non-privileged  users  can  execute e4defrag to their own file, but the
       score is not printed if -c option is specified. Therefore, it is desir&#8208;
       able to be executed by root user.

AUTHOR
       Written  by  Akira Fujita <a-fujita@rs.jp.nec.com> and Takashi Sato <t-
       sato@yk.jp.nec.com>.

SEE ALSO
       mke2fs(8), mount(8).

```

---

### Post by dino99 on 2011-12-30
whats new ?

This package contains programs for creating, checking, and maintaining
ext2/3/4-based file systems.

---

### Post by xyzzyman on 2011-12-30
It's been requested to be added to e2fsprogs for years but has just recently been added into it for Precise. It's not even in Oneirc's e2fsprogs package:

[http://packages.ubuntu.com/oneiric/amd64/e2fsprogs/filelist](http://packages.ubuntu.com/oneiric/amd64/e2fsprogs/filelist)
[http://packages.ubuntu.com/precise/amd64/e2fsprogs/filelist](http://packages.ubuntu.com/precise/amd64/e2fsprogs/filelist)

---

### Post by Sworddragon on 2012-01-03
I didn't know anything about e4defrag before this thread so I made some tests with it. I'm a little wondering about one thing. I used the following command:
```
e4defrag -v '/virtualbox/VirtualBox VMs/Ubuntu 32 Bit/Ubuntu 32 Bit.vdi'
```
And got:
```
[1/1]/virtualbox/VirtualBox VMs/Ubuntu 32 Bit/Ubuntu 32 Bit.vdi:	100%  extents: 71 -> 71	[ OK ]
```
So there was no defragmentation because e4defrag thought the file was already optimized. After this I tried the command again and e4defrag started to defragment the file which needed some minutes:
```
[1/1]/virtualbox/VirtualBox VMs/Ubuntu 32 Bit/Ubuntu 32 Bit.vdi:	100%  extents: 71 -> 69	[ OK ]
```
I tried the command again and there was again no defragmentation:
```
[1/1]/virtualbox/VirtualBox VMs/Ubuntu 32 Bit/Ubuntu 32 Bit.vdi:	100%  extents: 69 -> 69	[ OK ]
```
But the next time e4fdefrag started to defragment the file again:
```
[1/1]/virtualbox/VirtualBox VMs/Ubuntu 32 Bit/Ubuntu 32 Bit.vdi:	100%  extents: 69 -> 68	[ OK ]
```

Can somebody explain me why e4defrag wants to defragment sometimes and sometimes not? And why doesn't it reduce the extents to the minimum size possible on the first try (in my example the optimum extents of the file are 5)? I got even after another try a problem with the filesystem and it was mounted read-only. But I can't say if it really was because of e4defrag.

---

### Post by dino99 on 2012-01-03
Once again:

This package contains programs for creating, checking, and maintaining
ext2/3/4-based file systems.

meaning: virtualbox has its own file system, so not concerned.

---

### Post by jerrrys on 2012-01-03
thanks for the heads-up on this JF

---

### Post by MacUntu on 2012-01-03
> **dino99 said:**
> virtualbox has its own file system

That doesn't matter at all. If the guest uses ext4/btrfs/NTFS, all ext4/btrfs/NTFS tools will work without a problem.

> **dino99 said:**
> so not concerned.

That virtual disk file is quite likely residing on an ext4 partition...

---

### Post by Sworddragon on 2012-01-03
> **dino99 said:**
> meaning: virtualbox has its own file system, so not concerned.

"/virtualbox/VirtualBox VMs/Ubuntu 32 Bit/Ubuntu 32 Bit.vdi" is a file on a host system and not a virtual machine. The content of it doesn't matter because it is for e4defrag just a simple file on an ext4 filesystem. I have even tested e4defrag on a guest system and it was working there like on a host system. I'm just wondering about the behaviour on my previous post.

---

### Post by jfernyhough on 2012-01-03
> **Sworddragon said:**
> Can somebody explain me why e4defrag wants to defragment sometimes and sometimes not? And why doesn't it reduce the extents to the minimum size possible on the first try (in my example the optimum extents of the file are 5)? I got even after another try a problem with the filesystem and it was mounted read-only. But I can't say if it really was because of e4defrag.I tried running e4defrag on a large DVD .iso to see what it had to say.

$ sudo e4defrag -v -c LargeDVD.iso

```
Total/best extents                 65/4
Average size per extent            116759 KB
Fragmentation score                0
[0-30 no problem: 31-55 a little bit fragmented: 56- needs defrag]
This file (LargeDVD.iso) does not need defragmentation.
Done.
```$ sudo e4defrag -v LargeDVD.iso

```
ext4 defragmentation for LargeDVD.iso
[1/1]LargeDVD.iso:    100%  extents: 65 -> 65    [ OK ]
Success:             [1/1]
```OK, so reading on Wikipedia an extent can map up to 128MB of data, when a file needs more than four extents it maps the rest in an HTree. This mean the file above needs 65 extents to map its data (65*128=8320), including the HTree. Four extents would indeed be ideal, but that's not going to happen. :)

The fragmentation score shows e4defrag thinks the file really doesn't need defragmenting.

Running the same file through shake-fs:

$ sudo shake -vvv LargeDVD.iso

```
IDEAL    START    END    FRAGC    CRUMBC    AGE    SHOCKED    NAME    FRAGS
0    44023808    72707556    13    2    65    0    LargeDVD.iso    44023808:8192,58359808:32768,64577536:270336,64856064:155648,65150976:1957888,67239936:1966080,69337088:589824,69935104:122880,70066176:401408,70475776:827392,71434240:745472,72187904:245760,72441856:265708
```So shake-fs thinks the file has 13 fragments. Due to its age, size and number of fragments isn't going to be defragmented (running with the default settings). I guess I could force it to run, though.

---

### Post by Sworddragon on 2012-01-03
> **jfernyhough said:**
> OK, so reading on Wikipedia an extent can map up to 128MB of data, when a file needs more than four extents it maps the rest in an HTree. This mean the file above needs 65 extents to map its data (65*128=8320), including the HTree. Four extents would indeed be ideal, but that's not going to happen. :)

This explains the high number of theoretical extents but not why e4defrag is sometimes reducing this number and sometimes not. It is trying to defrag an already previous defragmented file again which will need a lot of time on big files. I will open a ticket for this and see what will happen.

I have made now some tests with e4defrag if there is some I/O at the defragmentation process. 2 runs with a few write operations - my filesystem was mounted 2 times read-only because an error occured. e4defrag is an online defragmentation tool and asynchronous write operations shouldn't make problems. I will open for this a ticket too.

---

