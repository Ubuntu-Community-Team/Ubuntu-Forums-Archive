---
title: "unknown filesystem type: 'aufs'"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by surfer on 2012-02-23
i am updating my [FAI]("http://fai-project.org/") installation process to precise. at startup FAI mounts an NFS share with aufs to the directory it will use later. but this aufs mount fails.

therefor i have started to toy-model an afs mount on my machine. i installed aufs-tools but
```
$ sudo mount -t aufs ...
```
gives me the following error code: 
```
unknown filesystem type: 'aufs'
```
how can this be fixed?

---

### Post by surfer on 2012-02-23
even if i try
```
$ sudo mount.aufs ...
```
i get the same error message.

does the kernel need aufs support? and is it no longer included? or is there a kernel module?

please help!

---

### Post by dino99 on 2012-02-23
something old but [http://ubuntuforums.org/showthread.php?p=5362116](http://ubuntuforums.org/showthread.php?p=5362116)

---

### Post by surfer on 2012-02-23
thanks dino99. i've been there before posting.

i had a lot of help and found out, that for my kernel (3.2.0.-15-generic) aufs is activated in the config (CONFIG_AUFS_FS=m) but the aufs.ko module is missing (in the initrd and in the filesystem).

---

### Post by surfer on 2012-02-29
looks like aufs support will be dropped in kernel 3.2. i'm running on a different kernel now; as i use it for FAI only, i followed their suggestion and started to use the grml kernel.

---

