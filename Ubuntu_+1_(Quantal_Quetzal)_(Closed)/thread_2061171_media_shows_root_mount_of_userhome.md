---
title: "/media shows root mount of user/home"
date: 2012-09-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by xombie on 2012-09-21
I cannot figure how to not mount my /home under root with normal tools. My /media shows mounted /home with a bizarre group of directories.

---

### Post by cariboo on 2012-09-21
WHat does your /etc/fstab look like? Mine looks like this:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=ffb84565-e4aa-4f3a-9ea5-e4ad01cfb985 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=71bb33aa-04ed-4189-9046-a501e760d7f1 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=0af95ddd-e62a-4494-9ada-02b7b5288e50 none            swap    sw              0       0
```

Or do you mean you are seeing something like this:

```
cariboo@alexis:/media$ ls -l
total 8
drwx------  2 root root 4096 Sep 14 09:02 4FF9-D698
drwxr-x---+ 2 root root 4096 Sep 18 09:02 cariboo
```

---

### Post by Elfy on 2012-09-22
Probably seeing something like this I suspect 

```
hob@sidh:/media$ ls -l
total 4
drwxr-x---+ 28 root root 4096 Sep 19 14:20 hob
hob@sidh:/media$ ls 
hob
hob@sidh:/media$ cd hob/
hob@sidh:/media/hob$ ls -l
total 104
drwx------ 2 root root 4096 Aug 26 14:42 1204good
drwx------ 2 root root 4096 Aug 27 13:29 1204good1
drwx------ 2 root root 4096 Aug 27 14:01 1204good2
drwx------ 2 root root 4096 Aug 27 14:30 1204good3
drwx------ 2 root root 4096 Aug 27 16:31 1204good4
drwx------ 2 root root 4096 Aug 30 11:15 1204good5
drwx------ 2 root root 4096 Sep  5 20:15 1204good6
drwx------ 2 root root 4096 Sep  6 19:03 1204good7
drwx------ 2 root root 4096 Aug 30 11:15 463e2436-4147-494a-8ec0-6629f0f33329
drwx------ 2 root root 4096 Sep  4 17:31 4ED7-6245
drwx------ 2 root root 4096 Sep  5 20:15 5827c96b-df08-42d8-97eb-e02228d6b2d5
drwx------ 2 root root 4096 Sep  6 19:02 5827c96b-df08-42d8-97eb-e02228d6b2d51
drwx------ 2 root root 4096 Sep  6 12:34 5aec4edf-2fe0-430a-9ddb-9bd414ad821d
drwx------ 2 root root 4096 Sep  6 13:27 5aec4edf-2fe0-430a-9ddb-9bd414ad821d1
drwx------ 2 root root 4096 Sep  6 12:21 9B3D-AB89
drwx------ 2 root root 4096 Aug 27 14:02 b59ae9b7-b9fe-40a9-a6dc-fb83074de8c0
drwx------ 2 root root 4096 Aug 26 12:00 bleh
drwx------ 2 root root 4096 Aug 27 13:29 bleh1
drwx------ 2 root root 4096 Aug 27 14:01 bleh2
drwx------ 2 root root 4096 Aug 27 14:30 bleh3
drwx------ 2 root root 4096 Aug 27 16:31 bleh4
drwx------ 2 root root 4096 Sep  4 18:10 c5738119-bbc6-4927-b554-f99af31a3830
drwx------ 2 root root 4096 Sep  5 08:42 c5738119-bbc6-4927-b554-f99af31a38301
drwx------ 2 root root 4096 Sep  5 20:15 e7b638cc-bb87-41ea-9c69-9eb1caae5ddd
drwx------ 2 root root 4096 Sep  6 19:03 ea0988ae-9d45-4dd6-adbc-fc28de58d434
drwx------ 2 root root 4096 Aug 27 14:02 FF1D-9A27
```

This started about the same time as I started seeing double entries for partitions in thunar.

---

### Post by cariboo on 2012-09-22
My /media/cariboo looked like that on my previous install, I just removed all the entries, and haven't seen a build up like that on this install so far.

I did have 4 drive icons in the Launcher yesterday after an update, but I removed those, and they haven't returned since.

---

### Post by Elfy on 2012-09-22
I only actually noticed as I was wandering about looking for this dual partition showing thing I have here.

I'll just delete them then :)

---

### Post by mc4man on 2012-09-22
> **cariboo907 said:**
> 

I did have 4 drive icons in the Launcher yesterday after an update, but I removed those, and they haven't returned since.
That's likely part of the unity upgrade, (if you're using), so now, once removed they will never come back. 
I did prefer to have them show in launcher 'only when mounted', but that doesn't appear to be a current option

---

### Post by cariboo on 2012-09-22
> **mc4man said:**
> That's likely part of the unity upgrade, (if you're using), so now, once removed they will never come back. 
I did prefer to have them show in launcher 'only when mounted', but that doesn't appear to be a current option

I added myself to your bug report.

---

