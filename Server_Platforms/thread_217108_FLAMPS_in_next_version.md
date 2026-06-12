---
title: "FLAMPS in next version?"
date: 2006-07-16
forum: Server Platforms
---

### Post by alecjw on 2006-07-16
How about this: instead of LAMP (Linux, Apache, MySql, PHP) you could have FLAMPS instead (FTP, Linux, Apache, MySql, PHP, SSH).

It should be a normal server install but with openssh-server and vsftpd installed.


Another thing - in the /etc/mysql/my.cnf file, the listen IP is set to 172.0.0.1, which means that it does not allow any external computers to connect via the network. It should automatically be set to the computer's IP.


Those are just my pointless ideas for Ubuntu Server 7...

---

