---
title: "Those of u running Dovecot Postfix I'd like to ask of u a small favor can you test"
date: 2016-12-24
forum: Server Platforms
---

### Post by MechaMechanism on 2016-12-24
**A patch has been submitted.  No need to comment on bug report page.**





Distributor ID:	Ubuntu
Description:	Ubuntu 16.10
Release:	16.10
Codename:	yakkety

I recently had trouble trying to get SASL auth working for Postfix.  It turned out that an Apparmor profile was stopping Dovecot from accessing /var/spool/postfix/private/auth.  I had done ```
sudo aa-enforce /etc/apparmor.d/*
```  Several months ago and had forgotten about it.  The specific Apparmor profile was usr.lib.dovecot.auth.  Putting usr.lib.dovecot.auth in complain mode allowed Dovecot to access /var/spool/postfix/private/auth and voila!  SASL auth now works.

I filed a bug report here; [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1652131](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1652131)
Can you put your dovecot apparmor profiles into enforce mode.  ```
sudo aa-enforce /etc/apparmor.d/*
```  If you no longer have access to the /var/spool/postfix/private/auth and you'll know in syslog.  Can you fix the profile and upload the patch to the bug report as above.

To put the Apparmor profile back to complain mode use; ```
sudo aa-complain usr.lib.dovecot.auth
```  Thank you.

---

