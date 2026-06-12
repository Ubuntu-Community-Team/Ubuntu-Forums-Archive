---
title: "Pobshare. Share large files and folders within your network."
date: 2019-03-14
forum: Ubuntu Application Development
---

### Post by pobfdm on 2019-03-14
I would like to propose and introduce my new application. Pobshare.
[IMG]http://www.freemedialab.org/software/pobshare/imgs/pobshare-linux.png[/IMG]
Pobshare is a simple and pleasant graphical interface to quickly share files and folders in the local network. It has several options to ensure safety and is suitable for beginners. Drag the folder you want to share and you're done! I hope it can be useful to someone.

Website:
[http://www.freemedialab.org/software/pobshare/](http://www.freemedialab.org/software/pobshare/)

---

### Post by TheFu on 2019-03-14
GPLv3 - nice. Couldn't find any mention of security or protocols supported.  Is this just for plain FTP?

---

### Post by pobfdm on 2019-03-15
Yes for now only ftp. Later I would like to add ftps support.

---

### Post by TheFu on 2019-03-15
> **pobfdm said:**
> Yes for now only ftp. Later I would like to add ftps support.

There are some issues with ftps.  Perhaps sftp would be better?  Plus being able to use the built-in ssh-keys would make it trivial for known system-to-system transfers.  OTOH, existing Linux file managers already support sftp and plain FTP.

IMHO, plain FTP should have died in the mid-1990s, like telnet, rsh, rlogin, rcp. Wish they'd stop teaching it.

---

### Post by pobfdm on 2019-03-21
2019-03-21 Added support for FTPS in 0.2

---

