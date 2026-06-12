---
title: "Mounted NFS share will not unmount"
date: 2010-01-08
forum: Server Platforms
---

### Post by david00 on 2010-01-08
Hi all,

We have a server running Hardy.  I configured it as an NFS client and mounted a share.  The NFS server is remote and accessed through TCP only (no UDP allowed through the firewall).  Now I've mounted it, though, I can't unmount it!

```
david@scatha $ mount | grep nfs
example.com:/home/david on /mnt/tmp type nfs (rw,tcp,addr=123.123.123.123)
```Now when I try to unmount it:

```
david@scatha $ sudo umount /mnt/tmp
umount.nfs: Server failed to unmount 'mail.proporta.com:/home/david'
umount.nfs: /mnt/tmp: must be superuser to umount
umount.nfs: Server failed to unmount 'mail.proporta.com:/home/david'
umount.nfs: /mnt/tmp: must be superuser to umount
```As you can see I'm already the superuser when I try to umount it.  Tried logging in as root instead of using sudo, that doesn't work either.  No idea why the error occurs twice.

Trying to use the "force" option of mount changes the output a little bit:

```
david@scatha $ sudo umount.nfs  /mnt/tmp -f
umount.nfs: Server failed to unmount 'example.com:/home/david'
umount2: Operation not permitted
umount.nfs: /mnt/tmp: must be superuser to umount
```Also as demonstrated above, using umount.nfs directly makes no difference to the problem.

How can I unmount this share?  I can't reboot the server since it's a production machine!  I guess it's not doing any harm just sitting there, but I find it really annoying sitting there in my "mount" output constantly...  and how can I receive 'Permission denied' even when I'm root?

Thanks for any help.
David

---

### Post by david00 on 2010-01-18
Bump

---

### Post by david00 on 2010-01-25
Bump

---

### Post by Adina on 2010-01-25
I do not know if this is the case with you, but you cannot unmount a directory if you are currently in it, if you understand.

if you cd into the directory you mounted and then try to unmount it, it will not work because you are using it. you have to cd out of the directory to unmount it. Hope this made any sense.

---

### Post by david00 on 2010-01-26
Adina, thanks for the reply.  Pretty sure I was not in the directory when I tried to unmount it, but anyway, I tried to umount it again today, and hey presto, it worked.  Possibly the ancient handle to the NFS share just timed out somehow and made itself unmountable.  Anyway, thanks for the help!

---

