---
title: "FTP download timeouts after 10 minutes"
date: 2009-08-26
forum: Server Platforms
---

### Post by OutWest on 2009-08-26
I've been trying to resolve this for a couple of weeks now and have finally run out of things to check.
When I attempt to download a large file 2-3GB from my 8.04LTS server, I experience a timeout. I have tried a variety of file sizes (up to 2.7GB) and the common factor appears to be time. If the transfer takes more than 10 minutes, the file is transferred intact but the client just sits & waits, while the server log shows the session disconnected after the transfer completed. The client appears to be waiting for a response from the server which never comes. I need to be compatible with other equipment, therefore I must run ftp.
+ If the server is placed on an internal network where the transfer rates are higher, all files transfer successfully due to shorter times. If the file is placed on the internet where my transfer rates are down to 2.5Mb, the sessions time out after a successful transfer taking longer than 10 minutes. 
+ Client filesystems are varied and none of them are file size dependent; either Mac or ext3.
clients: I use the command line and run ftp from there. Whether I use regular ftp or wget, the same problem occurs. The platform does not matter. I have tried multiple Linux platforms and Mac platforms. All have the same 10-minute issue.
+ server: 8.04LTS, fully patched, reinstalled from scratch twice, ext3 filesystem.
+ ftp daemon: currently running pure-ftpd. I have tried both vsftpd, proftpd (all three exhibit the same problem)
Sorry for the length. 
Any help would be appreciated.

---

### Post by jocampo on 2009-08-27
I think that your problem is automatic disconnection, nothing to do with Ubuntu. A keep-alive package should fix the problem. Check the documentation for your FTP and enable NOOP if you can.

---

