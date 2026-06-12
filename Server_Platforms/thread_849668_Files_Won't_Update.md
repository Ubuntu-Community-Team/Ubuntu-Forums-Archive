---
title: "Files Won't Update?"
date: 2008-07-04
forum: Server Platforms
---

### Post by davidshq on 2008-07-04
I have a Hardy Heron server runing. It has Apache 2.2, PHP, ProFTPd, and Webmin all installed. It runs very well generally, but recently I've been having a problem. I use FileZilla has my FTP client. I am attempting to update the current website file (a smarty tpl file) with a newer version on my local machine. I've tried the following:
1. Upload and overwrite the file (says successful).
2. Delete old file and then upload new file (says successful).
3. Delete through webmin and then upload the file (says successful).
Every time though the changes aren't applied and if I view the contents of the file through webmin it shows the same contents as before. Any thoughts? Has anyone experienced anything similar? Thanks.
David.

---

### Post by windependence on 2008-07-04
Clear your web cache and see if they are still the same.

-Tim

---

### Post by davidshq on 2008-07-04
Well, I'm looking at the physical file on the server and it isn't changed.
David.

---

### Post by windependence on 2008-07-04
Are you looking at it through Webmin or directly through an ssh session? If through Webmin, the cache could still be the issue.


-Tim

---

### Post by davidshq on 2008-07-04
Okay...I looked at it using nano on an ssh session and it was still the old file. I also manually uploaded the file using webmin instead of ftp - and that worked. what is going on?
The logs in FileZilla show that the transfer completed correctly:
Response:	200 PORT command successful
Command:	STOR link_summary.tpl
Response:	150 Opening ASCII mode data connection for link_summary.tpl
Response:	226 Transfer complete
Status:	File transfer successful
Any ideas why FTP would do this? I'm using proftpd for the ftp server and FileZilla for the FTP client.
David.

---

### Post by windependence on 2008-07-04
Are you the only one who does the file updates? If so, I would recommend not usinf FTP at all, and just use WinSCP or if you are on a Linux client nautilus or Konqueror will do drag and drop sftp.

-Tim

---

### Post by davidshq on 2008-07-04
WinSCP is a FTP/SFTP client? I can use it and downloaded it - it looks nifty...but I'd still need a FTP server for WinSCP to connect, no?
David.

---

### Post by windependence on 2008-07-05
No, it's not an ftp client it'ts an scp client. It works over ssh, using secure copy, much more secure than ftp, and no need for an ftp server. This is much easier to use than setting up an ftp server. Just make sure you have ssh installed (probably alreay is).

-Tim

---

