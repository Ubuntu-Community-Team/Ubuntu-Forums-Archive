---
title: "Ubuntu Server: unable to FTP into"
date: 2012-05-23
forum: Server Platforms
---

### Post by geidorei on 2012-05-23
Hi

setup ubuntu server - getting confused and not done this before - website test page shows when entering ip into url.

can ftp from internal network, but cant ftp to my ip address.

all i belive is setup correctly, ports open on server and on router - 80, 20-22.

Any suggestions? Filezilla just wont login, fails and cant login via ssh either.

Help! Thanks.

---

### Post by geidorei on 2012-05-23
as a note setup vsftpd and can ftp in without any issues - just cant sftp.

---

### Post by papibe on 2012-05-23
Hi geidorei.

Did you install the package openssh-server?

If so, try to see if the default ssh port is available (and not block by your ISP). You can test it here: [http://www.canyouseeme.org/]("http://www.canyouseeme.org/").

Regards.

---

### Post by geidorei on 2012-05-24
hi - yes installed, and all ports aok - good link!

to recap - ftp aok - sftp just doesnt want work. Any suggestions? Ta.

---

### Post by papibe on 2012-05-24
If you client is a Linux machine we can get a lot of information if you use the triple verbose option:
```
sftp -vvv ubuntuserver
```
Regards.

---

