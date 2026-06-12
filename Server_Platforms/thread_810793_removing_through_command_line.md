---
title: "removing through command line"
date: 2008-05-28
forum: Server Platforms
---

### Post by dacool25 on 2008-05-28
How can I remove libpam_smbpass?

I tried apt-get remove libpam_smbpass and aptitude remove libpam_smbpass

Neither of which find the process.  It is creating errors on my auth.log file

Thanks

---

### Post by jasoncusick on 2008-05-28
That is not a package that can be removed from the system by itself.  It's probably packaged with samba (smb windows file sharing) or pam (Pluggable Authentication Modules).

Something is trying to use it to authenticate.  Maybe something is configured weird?  If you have Samba running check that.  If not check your /etc/pam.conf

---

### Post by pytheas22 on 2008-05-28
> It is creating errors on my auth.log file

This error is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990") in Ubuntu 8.04.  To avoid it you need simply to comment-out the lines involving pam_smbpass.so in /etc/pam.d/common-auth and /etc/pam.d/common-password.

---

