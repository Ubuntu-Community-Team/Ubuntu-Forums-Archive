---
title: "Mounting vboxsf shares guest Hardy"
date: 2008-09-24
forum: Virtualisation
---

### Post by Sycrat on 2008-09-24
Hey guys.

I've been mucking around for a bit on my xp box trying to get Virtual Box's new "Seamless mode" going alright.

I'm going alright, but can't get the vboxsf share to mount properly...

Well.. I'll clarify..

I use
```
sycrat@Zendora:~$ sudo mount -t vboxsf MyDocs /home/sycrat/Documents -o rw,exec,uid=1000,gid=1000,dev
```

But I still get..

```
sycrat@Zendora:~$ mkdir ~/Documents/Test
mkdir: cannot create directory `/home/sycrat/Documents/Test': Permission denied
```

I don't know how to check permissions other than in nautilus, but in nautilus it says I'm the owner, but I can only access, and it won't let me change it, even if I sudo nautilus.

I've also tried chmod etc.

Once I get it working I'm going to fstab it, if there's any special way of doing that aswell.

Cheers!

EDIT: My share is pointing to E:\

---

