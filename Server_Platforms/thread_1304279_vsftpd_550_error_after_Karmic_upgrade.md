---
title: "vsftpd 550 error after Karmic upgrade"
date: 2009-10-29
forum: Server Platforms
---

### Post by msbarker on 2009-10-29
Hi Everyone,

I have been running an anonymous ftp server with vsftpd for about four months on Jaunty.  It is a very basic config that chroots all users and only allows anonymous downloads.  However, after upgrading to the Karmic RC I am experiencing "550 Failed to change directory" errors.  Has anybody else experienced this problem after the upgrade?  Any suggestions for a fix?  Is this related to the pasv regression in vsftpd 2.2.0?

Thanks for any help in advance!

-Mike

---

### Post by ericab on 2009-10-29
*edit*

---

### Post by msbarker on 2009-10-29
Problem solved!  Apparently the new location for the ftp folder is now /srv/ftp instead /home/ftp.  Once I moved the folders over everything was back to normal.

---

