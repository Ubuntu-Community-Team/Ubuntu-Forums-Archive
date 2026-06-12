---
title: "Vsftpd"
date: 2009-04-08
forum: Server Platforms
---

### Post by dustervoice on 2009-04-08
Im new to ubuntu server. ive installed vsftpd via the command line. now i want to edit my config file to block anonymous login and have vsftpd get logins via a username and password. how do i do that in the file? also what directory is shared by default for ftp?

---

### Post by HermanAB on 2009-04-08
The default setup should work - leave it alone! 
At first anyway :)

The most common cause of grief with vsftpd and proftpd is users editing the configuration file, so first of all, make a backup of the file before you change anything.  By default, users will have access to their home directories.

---

### Post by khelben1979 on 2009-04-08
From my own experience, I experienced [PureFTPd]("http://en.wikipedia.org/wiki/Pure-FTPd") as a faster FTP server than any other ftp server that I've ever tried with Linux.

Just wanted to point this out as another possible choice in this.

---

