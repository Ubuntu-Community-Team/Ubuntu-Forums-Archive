---
title: "Problems upgrading samba"
date: 2013-08-25
forum: Ubuntu Development Version
---

### Post by s-cradock on 2013-08-25
Yesterday an upgrade to samba was not successfully completed. The error message is:

Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (2:3.6.18-1ubuntu1) ...
update-rc.d: /etc/init.d/samba exists during rc.d purge (use -f to force)
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1

I've tried running "dpkg-reconfigure samba", "dpkg --force-configure samba", reinstalling from Synaptic, completely uninstalling + re-installing using Synaptic. I checked that the file flagged in the error report (/etc/init.d/samba) had been removed before the re-installation.

All to no avail.

Anyone else seeing the same/have any suggestions to fix?

Curiously, Synaptic does not flag any broken packages, though "dpkg-reconfigure samba" says it can't because samba is broken.

---

### Post by rtalcott on 2013-08-25
Yes....same situation here...

---

### Post by deadflowr on 2013-08-25
Here's the bug report
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1216438](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1216438)

If it affects you, mark it as so.

Unless you have something to add, comments are unnecessary.

---

### Post by s-cradock on 2013-08-25
Thanks - that's the one! Should be fixed soon, with vorlon on the case!

---

### Post by cariboo on 2013-08-25
I just did an update, and the issue is fixed now.

---

