---
title: "Secure FTP"
date: 2005-02-15
forum: Server Platforms
---

### Post by froust on 2005-02-15
I'm interested in setting up a secure ftp server on my home computer (amd64 hoary) for personal use (no anonymous is needed). Can anyone point me to a good How-To for this, or offer some pointers?
 - Liam

---

### Post by az on 2005-02-15
Actually, anonymous ftp is more secure since passwords are sent out in plain text otherwise.

apt-cache search ftp|grep server

I have heard some people recommend wu-ftpd.

---

### Post by froust on 2005-02-16
What I ended up doing was installing vsftpd, and then connecting to it via a sftp ssh tunnel using FileZilla. Seems to be working :)

---

### Post by hndrcks on 2005-02-18
If you are working with windows as a client, I suggest WinSCP:

[http://winscp.sourceforge.net/eng/download.php](http://winscp.sourceforge.net/eng/download.php)

Truly one of my useful tools in the toolbox!

---

