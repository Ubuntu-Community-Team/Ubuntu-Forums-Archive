---
title: "Atftp help please..."
date: 2008-12-18
forum: Server Platforms
---

### Post by qigong888 on 2008-12-18
Greetings everyone...

Reason for this post is because I am stuck with the atftp install on ubuntu-server 8.10 on an i386 machine (command line only).
CPU = 1GHz AMD : RAM = 2GB : IDE HDD = 360GB

I have followed many different methods and guides and I keep getting the same problems.  The one that worked the best was this one:
[http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html)
but it gives me the following errors when I use tftp client from another ubuntu machine:

When Trying to Download a file from the server:
----------------------
tftp> get config.jpg
tftp: error received from server <File not found>
tftp: aborting
----------------------

AND

When Trying to Upload a file to the server:
----------------------
tftp> put config.jpg
tftp: error received from server <Access violation>
----------------------

I've checked the permissions of the /tftpboot folder and it has all read/write access for ALL users.

I've got plenty experience with apache via port 80 and 443 (http and https) and also ftp.  But i've never worked with tftp before and its proving to be so hard to get going.

Am I missing something?

Please help... I am desperate to get this going :frown:
Any help would be greatly appreciated so thanks in advance.

---

### Post by qigong888 on 2008-12-23
Anyone?  Is it possible that there is no one who has experience with atftp ???

---

### Post by rukna on 2009-08-20
Just saw your post while having a similar issue. I solved it by creating the directory /var/lib/tftpboot, since I noticed the atftpd server listening on that directory.

Give it 0777, chown to nobody, restart atftpd and you should be set.

---

