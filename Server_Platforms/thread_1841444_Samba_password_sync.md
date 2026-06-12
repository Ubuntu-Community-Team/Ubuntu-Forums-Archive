---
title: "Samba password sync"
date: 2011-09-09
forum: Server Platforms
---

### Post by Caesius on 2011-09-09
Hello,

I'm running Ubuntu server 11.04 on my home server. Some users on this server want to have a different password for their Samba log in. In other words, I do not want the samba passwords to be synchronized with system accounts.

I thought the following setting in the Samba config file [FONT=Verdana]would fix this behavior:[/FONT]

unix password sync = no

[FONT=Verdana]However, it hasn't. Every time I change the password through smbpasswd the password is only changed temporarily. How can I stop the passwords from being resynchronized?

Thanks.
[/FONT]

---

### Post by Entilza on 2011-09-09
Are you adding the users through webmin by any chance?  There is an option there to sync passwords in samba maybe you have the checked off?  If the passwords aren't the same windows will ask for a login/password when accessing the share the first time.

---

### Post by Morbius1 on 2011-09-09
Go into synaptic and see if you have the following package:
```
libpam-smbpass
```If it's there remove it.

It has only one function and that's to force the samba password to match the local users login password at every boot regardless of how you may have set it manually. It's a goofey package for the exact reason you posted.

---

### Post by Caesius on 2011-09-09
> **Entilza said:**
> Are you adding the users through webmin by any chance?  There is an option there to sync passwords in samba maybe you have the checked off?  If the passwords aren't the same windows will ask for a login/password when accessing the share the first time.
No. I do have Webmin installed but not a single user has been added by the use of Webmin.

These are just regular users which have Unix password X and want Samba password Y.

When I change the Samba password (smbpasswd) Windows accepts the new password. The problem is, usually the password has been reset to the Unix password the next day.

---

### Post by Caesius on 2011-09-09
> **Morbius1 said:**
> Go into synaptic and see if you have the following package:
```
libpam-smbpass
```If it's there remove it.

It has only one function and that's to force the samba password to match the local users login password at every boot regardless of how you may have set it manually. It's a goofey package for the exact reason you posted.
Just removed the package. We'll see what happens. Thanks!

---

