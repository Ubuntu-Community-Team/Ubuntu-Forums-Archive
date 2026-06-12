---
title: "postfix virtual_mailbox_base protection"
date: 2018-12-21
forum: Server Platforms
---

### Post by lister171254 on 2018-12-21
I'm trying to figure out why I cannot access/view files in the postfix virtual_mailbox_base folder.

I am a member of the virtual group
```
llist@llmail:~$ id
uid=1000(llist) gid=1000(llist) groups=1000(llist),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),117(sambashare),1001(admin),5000(virtual)

```

The home folder looks as follows

```

llist@llmail:~$ ls -lsa /home
 4 drwxr-xr-x  10 root     root      4096 Dec 16 01:39 .
 4 drwxr-xr-x  22 root     root      4096 Dec 21 20:13 ..
 4 drwxrwxr-x   9 root     llist     4096 Dec 21 15:00 backups
 4 drwx--xr-x   3 virtual  virtual   4096 May 12  2014 vmail

```

When I list the backup folder, I get
```
ls -lsa /home/backups/
total 36
4 drwxrwxr-x  9 root llist 4096 Dec 21 15:00 .
4 drwxr-xr-x 10 root root  4096 Dec 16 01:39 ..
4 drwxr-xr-x  2 root root  4096 Dec 16 01:41 20181216_014101
4 drwxr-xr-x  2 root root  4096 Dec 16 01:41 20181216_014132
4 drwxr-xr-x  2 root root  4096 Dec 16 15:00 20181216_150001
4 drwxr-xr-x  2 root root  4096 Dec 18 15:00 20181218_150001
4 drwxr-xr-x  2 root root  4096 Dec 19 15:00 20181219_150001
4 drwxr-xr-x  2 root root  4096 Dec 20 15:00 20181220_150001
4 drwxr-xr-x  2 root root  4096 Dec 21 15:00 20181221_150001

```

When I try and list the vmail folder I get
```

llist@llmail:~$ ls -lsa /home/vmail
ls: cannot open directory '/home/vmail': Permission denied

```

With sudo I get
```

llist@llmail:~$ sudo ls -lsa /home/vmail
total 12
4 drwx--xr-x  3 virtual virtual 4096 May 12  2014 .
4 drwxr-xr-x 10 root    root    4096 Dec 16 01:39 ..
4 drwx--x--- 14 virtual virtual 4096 Oct 17 19:06 zudiewiener.com

```

All vmail folders have group execute and file read

What am I missing?
Thanks

---

