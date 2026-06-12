---
title: "vsftpd, Active Directory and home directories"
date: 2009-08-31
forum: Server Platforms
---

### Post by MightyMartian on 2009-08-31
I have an Ubuntu server that is a member server on a Windows Server 2003 AD network.  It is configured to allow logins via SSH and FTP (vsftpd server) for AD users, and that works fine.

What I would like to do is for certain AD users to alter the FTP home directory they get dropped into.  Is this is even possible?

---

### Post by drave on 2009-09-01
there can only be 1, home directories that is. so ssh and ftp will go to the same place, whatevers in the directory.

create anOTHERuser set there home directory and have people connect as that user (maybe)

---

