---
title: "FTP Server in 6.10 Server"
date: 2007-04-16
forum: Server Platforms
---

### Post by edlentz on 2007-04-16
Can someone point me to a Howto  so I can get FTP to run in 6.10 server.   I have tried:
sudo apt-get install proftpd and all I get is that it can't find the files.

Thanks alot

---

### Post by bmathis on 2007-04-17
you first need to make sure all repositories are enabled in /etc/apt/sources.list and then follow the instructions here - [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/ftp-server.html]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/ftp-server.html") - for vsftpd.

---

### Post by tone77 on 2007-04-17
If I were you, I would setup a SFTP because it is a whole lot more secure and still very easy for the end user, they simply change one or two settings in the ftp client.
Check out this forum: [http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)

---

### Post by jason732 on 2007-04-20
Would these instructions for the SFTP work for 7.04 as well?

---

### Post by tone77 on 2007-04-20
They should, I don't see any reason they won't.

---

### Post by supernix on 2007-04-25
I can't get my vsftpd to stay running everytime I click on start then look for the instance of it running I find nothing and no log messages anywhere to explain it either.

---

