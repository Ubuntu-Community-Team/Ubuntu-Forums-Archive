---
title: "Uninstalled tar accidentally"
date: 2007-05-26
forum: Server Platforms
---

### Post by bgammill on 2007-05-26
I uninstalled tar accidentally, and I need to get it back. Whenever I try apt-get, it says cannot find tar.
Thanks

---

### Post by pbw on 2007-05-26
Try downloading it manually here: [http://ftp.osuosl.org/pub/ubuntu/pool/main/t/tar/tar_1.16-2_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/main/t/tar/tar_1.16-2_i386.deb) and install it with sudo dpkg -i tar_1.16-2_i386.deb

-- pbw

---

### Post by bgammill on 2007-05-26
> **pbw said:**
> Try downloading it manually here: [http://ftp.osuosl.org/pub/ubuntu/pool/main/t/tar/tar_1.16-2_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/main/t/tar/tar_1.16-2_i386.deb) and install it with sudo dpkg -i tar_1.16-2_i386.deb

-- pbw

bgammill@server:~$ sudo dpkg -i tar_1.16-2_i386.deb
Password:
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing tar_1.16-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 tar_1.16-2_i386.deb

---

### Post by pbw on 2007-05-26
[http://pbw.fdns.net/files/](http://pbw.fdns.net/files/) download tar and place it in /bin, then run apt/dpkg as usual and you should be good to go. install tar via apt and force-overwrite since it'll probably say file exists already.

---

### Post by bgammill on 2007-05-29
> **pbw said:**
> [http://pbw.fdns.net/files/](http://pbw.fdns.net/files/) download tar and place it in /bin, then run apt/dpkg as usual and you should be good to go. install tar via apt and force-overwrite since it'll probably say file exists already.

Your link doesn't work :(

---

### Post by bgammill on 2007-05-30
Thanks a bunch, everything is back to normal. I would pay you if I could!

---

### Post by pbw on 2007-05-30
No prob, happy to help. :)

-- pbw

---

