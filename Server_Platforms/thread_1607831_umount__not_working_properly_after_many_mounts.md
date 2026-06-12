---
title: "umount  not working properly after many mounts"
date: 2010-10-28
forum: Server Platforms
---

### Post by Znarkus on 2010-10-28
Hi!

Our server is having severe problems unmounting directories that have been mounted with -o bind. We have some hundred directories mounted like this.

Running umount customer/ftp/folder doesn't yield any errors.

But rmdir customer/ftp/folder returns "Device or resource busy". What makes me blame umount is that I can run umount again as if it is still mounted.

After a lot of trial and error I always succeed in unmounting the directory, but can't see a pattern. I just run umount and alternate the options [non] -r -f and -l (not -l and -f anymore, since I have a feeling that -l just makes it worse by queueing the unmount, and -f doesn't make much sense hehe). After repeatedly running umount (-r) and rmdir it finally succeeds.

I've also asked at [http://serverfault.com/questions/192150/reliability-of-mount-umount](http://serverfault.com/questions/192150/reliability-of-mount-umount).

I'm at a loss here, would appreciate any ideas.

```
root@server:/# umount -V
umount (util-linux-ng 2.16)
```

:popcorn:

**Edit 1:** The below is a real "conversation" I just had.

```
root@server:/customers# rmdir /customers/customer/ftp/*
rmdir: failed to remove `/customers/customer/ftp/folder': Device or resource busy
root@server:/customers# umount -r /customers/customer/ftp/folder/ && rmdir /customers/customer/ftp/folder/
rmdir: failed to remove `/customers/customer/ftp/folder/': Device or resource busy
root@server:/customers# umount -r /customers/customer/ftp/folder/ && rmdir /customers/customer/ftp/folder/
rmdir: failed to remove `/customers/customer/ftp/folder/': Device or resource busy
root@server:/customers# umount -r /customers/customer/ftp/folder/ && rmdir /customers/customer/ftp/folder/
rmdir: failed to remove `/customers/customer/ftp/folder/': Device or resource busy
root@server:/customers# umount -r /customers/customer/ftp/folder/ && rmdir /customers/customer/ftp/folder/
root@server:/customers#
```

Succeeded at last, but why and how?

---

### Post by andrewc6l on 2010-10-28
Is it possible that you've got a process that is automatically mounting the directory repeatedly? I know in my 10.04 server, I've been able to mount /dev/sdb1 /foo and then mount /dev/sdb1 foo again - and have to umount twice to get Ubuntu to forget about it.

---

