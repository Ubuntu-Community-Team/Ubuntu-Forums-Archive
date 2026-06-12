---
title: "Problems with FTP"
date: 2009-01-28
forum: Server Platforms
---

### Post by designcentral on 2009-01-28
Hi,

I can't get FTP working, i've installed proftpd and couldnt get that to work so i uninstalled it. then i installed pureftp and that didnt work either. i uninstalled it. then i installed vsftpd and guess what? IT DIDNT WORK! so i deleted it and want to start at the beginning.

With no ftp servers that i know of installed, when I try to connect to the server via FTP using filezilla it says:

Status:	Connecting to 192.168.1.107:21...
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server


I have no idea what to do.

I just want to be able to connect via FTP to my apache /var/www directory!

Thanks in advance!

---

### Post by utnubuuser on 2009-01-28
That's most likely something with your account (ftp) settings.   Either wrong password, wrong port, wrong username, wrong type of connection, etc.
Don't take this as gospel though.  It could be something else, like a firewall etc.
I'm not all that familiar with ftp protocols,  I use Filezilla, but the only time I've gotten that kind of error message was when I entered incorrect info.

---

### Post by designcentral on 2009-01-28
Nope, I just went quick connect where I entered nothing apart from username/password and ip address. still same error even though there is no ftp program running on the server... help pl0x im a linux n00b

---

### Post by utnubuuser on 2009-01-28
Yeah, what, are you trying to connect to /var/www on the same machine?

---

### Post by designcentral on 2009-01-28
Nah, apache document root is still default at the moment i don't even have a FTP server running on the darn thing... ill try get pureftpd now...

---

### Post by designcentral on 2009-01-29
ok ive got pureftpd and i still get the same error message. HELP PLEASE :S

---

### Post by hyper_ch on 2009-01-29
why do you use ftp and not sftp/scp over ssh?

---

### Post by MobiusNZ on 2009-01-29
Have you made sure the FTP server is even running?

```
sudo /etc/init.d/proftp start
```
(replace proftp with your ftp server program)

---

