---
title: "Directory access in ftp"
date: 2006-09-17
forum: Server Platforms
---

### Post by leach on 2006-09-17
Hello friends, I've set up an ftp server with vsftpd and it works great but I do have a small problem. All the accounts that log into my server have the home directory of /home/ftp/ but I can't figure out how to lock them into that directory so they can't browse up a level and all over my filesystem. If someone could give me a point in the right direction I would appreciate it. Thanks.

---

### Post by lamego on 2006-09-17
You need to do some research on your configuration (/etc/vsftpd.conf):

> # You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES


---

### Post by leach on 2006-09-17
> **lamego said:**
> You need to do some research on your configuration (/etc/vsftpd.conf):

!, I looked through my vsftpd.conf a few times for something like that. It is clearly getting late. Thanks for the help.

---

