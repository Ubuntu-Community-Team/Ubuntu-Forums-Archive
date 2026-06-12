---
title: "libpam-mysql pam_mysql.so: undefined symbol: make_scrambled_password"
date: 2016-04-25
forum: Server Platforms
---

### Post by own3mall on 2016-04-25
Hi Guys,

I noticed that in all versions of Ubuntu 16.04, the libpam-mysql package or (pam-mysql for older versions of Ubuntu) is broken.  When trying to interface with mysql, I get this error:

PAM unable to dlopen(pam_mysql.so): /lib/security/pam_mysql.so: undefined symbol: make_scrambled_password

Anyone have a fix?

---

### Post by own3mall on 2016-04-25
I originally thought I had a fix for this, but I didn't.  Applying the patches from Fedora's version causes stack overflows even though the code compiles.  It doesn't do that in Ubuntu 14.04 though when I apply the same patch even though it isn't needed in that version of Ubuntu.

---

### Post by mlentink on 2016-08-19
Has anyone seen a solution for this, other then using the imapserver as authenticator?

---

