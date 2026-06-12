---
title: "dpkg: error processing mail-stack-delivery (--configure)"
date: 2012-01-20
forum: Server Platforms
---

### Post by bpb_21 on 2012-01-20
I'm running into a problem on my Ubuntu 11.10 server, whenever there are updates to be installed, or removed, or whenever apt-get or dpkg is used.  The error I receive from apt-get upgrade is:
Setting up mail-stack-delivery (1:2.0.13-1ubuntu3.2) ...
ln: creating symbolic link `/etc/ssl/private/ssl-mail.key': File exists
dpkg: error processing mail-stack-delivery (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mail-stack-delivery
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've got it set to email the results of unattended upgrades and no matter what the upgrade, this is always part of the email:

Setting up mail-stack-delivery (1:2.0.13-1ubuntu3.2) ...
ln: creating symbolic link `/etc/ssl/private/ssl-mail.key': File exists
dpkg: error processing mail-stack-delivery (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-libc-dev (3.0.0-15.25) ...
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 mail-stack-delivery
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

I receive the email, I can otherwise install and remove packages, and except for the error itself everything seems to be working.  Any ideas?

---

### Post by bpb_21 on 2012-02-15
Anyone?

---

