---
title: "Remotely Accessing my Desktop Server"
date: 2011-10-20
forum: Server Platforms
---

### Post by sindhughanti on 2011-10-20
Hi
I have a desktop with Ubuntu Server v10.04 installed, and have been using it as the server in my home office. We keep accessing it for our daily work (*accessing/modifying/adding new files and folders, and also printing), via Samba*. Our daily work heavily depends on it. If I move out of town for a couple of days, and i want to access my desktop via Remote Access, how do I do it? I may not want to copy all the files/folders on my laptop every-time i travel.
Please Help!
Thanks!

---

### Post by Sef on 2011-10-20
Moved to server platforms.

---

### Post by HermanAB on 2011-10-20
Howdy,

Read the snailbook:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by lucas8880 on 2011-10-20
hi, i have a server that i have to access remotely aswell.
i suggest installing an ftp server: proftpd and an ssh server: ssh
with ftp you can transfer files easily and with ssh you can do any sort of command
that will execute on the remote system

---

### Post by Lars Noodén on 2011-10-20
+1 for the "Snail Book" / SSH.  

Regarding FTP, [FTP is insecure](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and should not be installed these days.  If you have SSH then you already have SFTP, too, and do not need FTP.  

If you have SSH and want to remotely access files, one very secure way is to use [SSHFS](http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html).  

Otherwise, it should also be possible to tunnel Samba over SSH.

---

### Post by LtPitt on 2011-10-20
I'd also suggest (if your files size doesn't exceed 2 gb) to try Ubuntu One.
It solved my problem without hassle :)

---

