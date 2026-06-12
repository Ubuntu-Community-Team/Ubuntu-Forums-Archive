---
title: "Can't get wuftpd to work"
date: 2008-10-11
forum: Server Platforms
---

### Post by craigcrawford114 on 2008-10-11
Hi,

I have wuftpd running, but it wont let me login on through ftp...

Can someone let me know how I allow the user to login?

> [21:45:02] Resolving host name "72.14.xx.xx"
[21:45:02] Connecting to 72.14.xx.xx Port: 21
[21:45:02] Connected to 72.14.xx.xx.
[21:45:03] 220 ubuntu FTP server (Version wu-2.6.2(1) Tue Jul 31 23:25:21 GMT 2007) ready.
[21:45:03] USER datamatrix
[21:45:03] 331 Password required for datamatrix.
[21:45:03] PASS (hidden)
[21:45:05] 530 Login incorrect.


---

### Post by craigcrawford114 on 2008-10-11
In syslog:

> Oct 11 16:45:05 ubuntu wu-ftpd[2360]: connection from 82-46-xx-xx.cable.ubr12.live.blueyonder.co.uk [82.46.xx.xx]
Oct 11 16:45:07 ubuntu wu-ftpd[2360]: failed login from 82-46-xx-xx.cable.ubr12.live.blueyonder.co.uk [82.46.xx.xx]
Oct 11 16:53:39 ubuntu wu-ftpd[2360]: FTP session closed


---

