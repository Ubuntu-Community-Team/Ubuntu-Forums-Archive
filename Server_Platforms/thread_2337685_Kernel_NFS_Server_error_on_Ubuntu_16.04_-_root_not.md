---
title: "Kernel NFS Server error on Ubuntu 16.04 - root not squashing"
date: 2016-09-20
forum: Server Platforms
---

### Post by sombrafam on 2016-09-20
Hi guys, I'm trying to setup a server with root_squash. The export has the option 'root_squash' but after mounting, the root does not have permissions to write to the file-system.

```

 root@106-nfs-plugin:/# cat /etc/exports.d/stack_nfs.exports 
/srv/nfs1       localhost(rw,root_squash)
root@106-nfs-plugin:/# mount -t nfs -o vers=4 localhost:/srv/nfs1/ /mnt/
root@106-nfs-plugin:/# cd /mnt/
root@106-nfs-plugin:/mnt# touch test
touch: cannot touch 'test': Permission denied
su ubuntu
ubuntu@106-nfs-plugin:/mnt$ ls
ubuntu@106-nfs-plugin:/mnt$ touch test
ubuntu@106-nfs-plugin:/mnt$ ls
test
ubuntu@106-nfs-plugin:/mnt$ ls -la
total 8
drwxr-xr-x  2 ubuntu root   4096 Sep 20 15:36 .
drwxr-xr-x 23 root   root   4096 May  3 12:32 ..
-rw-rw-r--  1 ubuntu ubuntu    0 Sep 20 15:36 test
ubuntu@106-nfs-plugin:/mnt$ 



```

I should allow the file to be created and owned by nobody. What is the problem? Does anyone has had the same problem? This happens even if I use vers=3

---

