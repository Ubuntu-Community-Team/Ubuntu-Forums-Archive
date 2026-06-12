---
title: "chmod-ing to allow guest to access file"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-02
the guest user does not have access to the [FONT=Courier New]/mnt[/FONT] folder
i want to allow the guest to read/write this file
[FONT=Courier New]/mnt/windows/virtual-box/Vista.vdi[/FONT]
non-relevant aside:
that thing took about 8 hours to get running right most of which was installing updates and fighting with the guest addons drivers

---

### Post by cariboo on 2012-10-03
> **pqwoerituytrueiwoq said:**
> the guest user does not have access to the [FONT=Courier New]/mnt[/FONT] folder
i want to allow the guest to read/write this file
[FONT=Courier New]/mnt/windows/virtual-box/Vista.vdi[/FONT]
non-relevant aside:
that thing took about 8 hours to get running right most of which was installing updates and fighting with the guest addons drivers

Wouldn't it have been a lot easier to create another user to access vbox?

---

### Post by pqwoerituytrueiwoq on 2012-10-03
why cant the guest read /mnt?
```
guest-YrZXWX@Compaq-Presario-CQ60:~$ ls -a -l /
total 104
drwxr-xr-x  23 root root  4096 Sep 30 15:08 .
drwxr-xr-x  23 root root  4096 Sep 30 15:08 ..
drwxr-xr-x   2 root root  4096 Oct  2 23:26 bin
drwxr-xr-x   4 root root  4096 Sep 30 16:00 boot
drwxr-xr-x   2 root root  4096 Sep 29 11:04 cdrom
drwxr-xr-x  15 root root  4300 Oct  3 08:29 dev
drwxr-xr-x 149 root root 12288 Oct  3 08:49 etc
drwxr-xr-x   4 root root  4096 Sep 29 11:05 home
lrwxrwxrwx   1 root root    32 Sep 29 11:26 initrd.img -> boot/initrd.img-3.5.0-16-generic
lrwxrwxrwx   1 root root    33 Sep 29 11:25 initrd.img.old -> /boot/initrd.img-3.5.0-16-generic
drwxr-xr-x  22 root root  4096 Sep 29 11:23 lib
drwxr-xr-x   2 root root  4096 Sep 26 01:49 lib64
drwx------   2 root root 16384 Sep 29 11:01 lost+found
drwxr-xr-x   3 root root  4096 Oct  2 11:44 media
**dr-xr-xr-x   3 root root  4096 Oct  2 11:59 mnt**
dr-xr-xr-x 157 root root     0 Oct  3 08:29 proc
drwx------   8 root root  4096 Sep 30 22:51 root
drwxr-xr-x  23 root root   820 Oct  3 08:33 run
drwxr-xr-x   2 root root 12288 Oct  2 23:26 sbin
drwxr-xr-x   2 root root  4096 Jun 11 14:36 selinux
drwxr-xr-x   2 root root  4096 Sep 26 01:49 srv
dr-xr-xr-x  13 root root     0 Oct  3 08:29 sys
drwxrwxrwt   8 root root  4096 Oct  3 08:49 tmp
drwxr-xr-x  11 root root  4096 Sep 29 11:23 usr
drwxr-xr-x  14 root root  4096 Oct  2 23:49 var
lrwxrwxrwx   1 root root    29 Sep 29 11:26 vmlinuz -> boot/vmlinuz-3.5.0-16-generic
lrwxrwxrwx   1 root root    29 Sep 29 11:25 vmlinuz.old -> boot/vmlinuz-3.5.0-16-generic
guest-YrZXWX@Compaq-Presario-CQ60:~$ ls /mnt
ls: cannot open directory /mnt: Permission denied
guest-YrZXWX@Compaq-Presario-CQ60:~$ ls -l /tmp
total 12
drwx------ 23 guest-YrZXWX guest-YrZXWX  680 Oct  3 08:49 guest-YrZXWX
drwx------  2 guest-YrZXWX guest-YrZXWX 4096 Oct  3 08:49 pulse-2L9K88eMlGn7
drwx------  2 root         root         4096 Oct  3 08:29 pulse-PKdhtXMmr18n
drwx------  2 guest-YrZXWX guest-YrZXWX 4096 Oct  3 08:49 ssh-WbTnTAHMMa4J
guest-YrZXWX@Compaq-Presario-CQ60:~$ 


```

---

