---
title: "sftp on vsftpd"
date: 2011-04-13
forum: Server Platforms
---

### Post by elliotbeken on 2011-04-13
hi all i have a vsftpd server running well but i want to make/force all users to use sftp and not just ftp is this possible ?

thanks

---

### Post by dfreer on 2011-04-13
SFTP, as far as I know, is SSH File Transfer Protocol, and has nothing to do with vsftpd, which is a secure FTP server. To use SFTP, simply install SSH and make sure the line in the /etc/ssh/sshd_config file that deals with sftp is not commented out.

In short, SFTP != FTP. If you only want users to use SFTP, disable vsftpd and use SSH. Depending on what you want your users to do, this may not be the best option since with SSH they can login to your system and run commands.

If you were already aware that SFTP and FTP are not the same thing, disregard my comments. Simply enable ssh and disable ftp to force your users to use SFTP.

---

