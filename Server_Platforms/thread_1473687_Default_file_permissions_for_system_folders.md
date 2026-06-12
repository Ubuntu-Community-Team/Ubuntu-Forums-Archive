---
title: "Default file permissions for system folders"
date: 2010-05-05
forum: Server Platforms
---

### Post by msigley on 2010-05-05
This is probably a noob question.

I had a major raid event recently which caused my Ubuntu 9.04 server to recover part of its file journal on the system partition.
This caused some of the file permissions to go all funny and I now need to change them manually.

I was wondering if someone knew what the file permissions should for the following folders:

/etc/
/home/
/lost+found/
/mnt/
/root/
/sbin/
/srv/
/tmp/

The server is running and I fixed the some of the ownership issues already. I use a basic LAMP setup with samba, and proftp.

Any help or information you guys can provide would be appreciated.

---

### Post by Gompa on 2010-05-05
drwxr-xr-x  88 root root  4096 2010-04-28 15:50 etc
drwxr-xr-x   4 root root  4096 2010-04-25 04:00 home
drwx------   2 root root 16384 2010-04-25 03:42 lost+found
drwxr-xr-x   2 root root  4096 2010-04-15 02:18 mnt
drwx------   4 root root  4096 2010-04-25 03:51 root
drwxr-xr-x   2 root root  4096 2010-04-28 15:48 sbin
drwxr-xr-x   2 root root  4096 2010-04-25 03:43 srv
drwxrwxrwt   3 root root  4096 2010-05-05 18:48 tmp

---

### Post by msigley on 2010-05-05
Nice. Thank you for the speedy reply. I was surprised at how hard this information was to find.

All of my issues seem to be resolved AKA everything is working.
Anyone have any ideas as to other things to look for when recovering from an error like this?

---

