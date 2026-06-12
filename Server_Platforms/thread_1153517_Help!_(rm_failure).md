---
title: "Help! (rm failure)"
date: 2009-05-08
forum: Server Platforms
---

### Post by keycommand on 2009-05-08
Hello, i was in a directory and I meant to type rm ./* but I accidentally typed rm /*  . It came up saying it couldn't remove the directories, but I know there were a few files in / , how do i recover (make new ones)?

---

### Post by hictio on 2009-05-09
How can we know what files did you had on your '/' partition?
The other thing, did those files got deleted executing 'rm' without 'sudo'?

---

### Post by lykwydchykyn on 2009-05-09
Were you root or using sudo?

The only files in my / are symlinks to the cdrom directory, kernel and initrd:
```

lrwxrwxrwx   1 root root    11 2008-06-03 06:20 cdrom -> media/cdrom
lrwxrwxrwx   1 root root    33 2009-04-28 08:37 initrd.img -> boot/initrd.img-2.6.28-11-generic
lrwxrwxrwx   1 root root    30 2009-04-28 08:37 vmlinuz -> boot/vmlinuz-2.6.28-11-generic


```

You can recreate those with the ln command, e.g.:
```

ln -s media/cdrom
ln -s boot/initrd.img-2.6.28-11-generic initrd.img

```

can you post the output of "ls -l /"?

---

### Post by keycommand on 2009-05-09
root@gt:~# ls -l /
total 84
drwxr-xr-x   3 root root  4096 2009-04-16 20:15 backups
drwxr-xr-x   2 root root  4096 2009-03-22 21:28 bin
drwxr-xr-x   3 root root  4096 2009-04-23 11:06 boot
drwxr-xr-x  13 root root 13640 2009-03-31 20:53 dev
drwxr-xr-x 102 root root  4096 2009-05-08 15:14 etc
drwxr-xr-x  12 root root  4096 2009-05-04 22:06 home
drwxr-xr-x  13 root root 12288 2009-05-02 23:43 lib
drwx------   2 root root 16384 2009-03-22 20:55 lost+found
drwxr-xr-x   3 root root  4096 2009-03-22 20:56 media
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 mnt
drwxr-xr-x   2 root root  4096 2009-03-22 20:57 opt
dr-xr-xr-x 112 root root     0 2009-03-31 20:53 proc
drwxr-xr-x   3 root root  4096 2009-05-08 20:53 root
drwxr-xr-x   2 root root  4096 2009-04-23 11:05 sbin
drwxr-xr-x   2 root root  4096 2009-03-22 20:57 srv
drwxr-xr-x  12 root root     0 2009-03-31 20:53 sys
drwxrwxrwt   4 root root  4096 2009-05-07 22:08 tmp
drwxr-xr-x  11 root root  4096 2009-03-22 21:01 usr
drwxr-xr-x  18 root root  4096 2009-05-07 19:33 var

Yes, I was root at the time, I usually sudo and use better measures against this sort of thing. I had no other files in my / partition except the defaults needed to function so I'll recreate those now and when i eventually need to reboot hopefully it goes well. 73 days uptime so far. Thanks for the help.

---

