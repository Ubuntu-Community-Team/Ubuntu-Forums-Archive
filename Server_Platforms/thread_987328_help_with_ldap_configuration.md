---
title: "help with ldap configuration"
date: 2008-11-19
forum: Server Platforms
---

### Post by rkleemann on 2008-11-19
Hi,

I have Ubuntu Hardy server setup with ldap, and I have ldap authentication working well with courier (imap).

I've made the changes in nsswitch.conf and the /etc/pam.d/ files.

But it doesn't seem that either ssh or vsftpd are working with ldap. 

For example when I attempt to ssh in, I'm getting a failed password error. The ldap accounts are using the standard userPassword field.

I wonder if maybe it has something to do with which password encryption method is being used?

How can I properly debug this?

Thanks
Ricardo

---

