---
title: "425 error with vsftpd"
date: 2012-05-04
forum: Server Platforms
---

### Post by da2357 on 2012-05-04
Hello. I've set up Ubuntu Server 12.04 and have, so far, added only the vsftpd server. I configured the /etc/vsftpd.conf file to
- not allow anonymous logins,
- allow local logins,
- enable local write (uploads).

I've created a local user (sudo adduser jsmith) and changed the user's group to staff (sudo chgrp staff /home/jsmith).

I restarted the vsftpd service (sudo service vsftpd restart).

On a separate Win7 machine, I launched a command window:
- connected to the ftp server,
- entered login ID and password,
- and was left at a prompt ("Login successful.").

Next, when I try to run the command: ls -la

200 PORT command successful. Consider using PASV.
425 Failed to establish connection.

THE QUESTIONS: Why am I getting this 425 error and how do I resolve it? I want to use this FTP server on an internal network only.

---

### Post by codemaniac on 2012-05-04
Sounds like a firewall issue. simply add the "default" FTP port (21/TCP) given in system firewall, Apply this and restart Iptables. And here you will get the data access threw port 21.

---

### Post by da2357 on 2012-05-08
All resolved. It did turn out to be a firewall issue and once I added a few rules to our district firewall (allowing TCP 20-21 and all UDP) between the designated copier-scanner and the FTP server... everything worked quickly and well.

Thanks!

---

