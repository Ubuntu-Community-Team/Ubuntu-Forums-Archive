---
title: "Kernel 5.16.12 and NFS Share not working"
date: 2022-03-03
forum: Ubuntu Development Version
---

### Post by dschaefer79 on 2022-03-03
Hi,

I have tried to mount NFS share with PPA kernel 5.16.12 on Ubuntu 21.10 but it's not working. on Kernel 5.13 and 5.14 it's working.

Here the error :

root@dreampc:~# sudo mount -vvv 192.168.1.5:/datas /media/datas
mount.nfs: timeout set for Thu Mar  3 11:06:21 2022
mount.nfs: trying text-based options 'vers=4.2,addr=192.168.1.5,clientaddr=192.168.1.11'

Can someone help me ?

Thanks,

Dominique Schaefer

---

### Post by dschaefer79 on 2022-03-03
_**I read this on a forum :**_

I just want to raise attention and warn everyone here that changes in NFSv4 introduced in Linux kernel 5.16.10 are not compatible with Qnap NASes.
You can get the details at:
[https://bugzilla.redhat.com/show_bug.cgi?id=2055362](https://bugzilla.redhat.com/show_bug.cgi?id=2055362)
where some folks have pinpointed where the problem lays.

I hope this will avoid someone else to screw up wondering why their shares are not mounted anymore...

____________________

I set the nas to nfs 3 and now it's working, Problem Solved

---

