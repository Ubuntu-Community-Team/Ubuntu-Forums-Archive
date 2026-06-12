---
title: "What happened to libapache2-mod-auth-pam?"
date: 2009-11-18
forum: Server Platforms
---

### Post by sgarman on 2009-11-18
I recently upgraded from Jaunty to Karmic (by performing a clean install of Karmic, not an in-place upgrade). My apache setup used to use the mod_pam module, which could be found in the package libapache2-mod-auth-pam. This package does not appear to exist in the Karmic repositories.

My searching so far has suggested that there is some sort of new authentication system that uses a package called pwauth. Can someone verify this and point me to some documentation on how to migrate my config file correctly?

Thanks,

Scott

---

### Post by m000 on 2010-01-13
What happened really? Any clues why it was removed?

After several hours of googling, :confused: and ](*,), I got a hint here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1747008.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1747008.html)

libapache2-mod-auth-pam was replaced with a libapache2-mod-authnz-external+pwauth combo. The steps to reproduce the previous functionality with the new packages are:

Install new packages:
```
# apt-get install pwauth
# a2enmod authnz_external
```Then at the directory level of your apache config, set the new module to use pwauth. You can keep the old config on the side:
```
        <IfModule mod_pam.c>
                AuthPAM_Enabled on
        </IfModule>
        <IfModule mod_authnz_external.c>
                AuthBasicProvider external
                AuthExternal pwauth
        </IfModule>
```At the VirtualHost level of your apache config, add some extra options for the module:
```
<IfModule mod_authnz_external.c>
        AddExternalAuth pwauth /usr/sbin/pwauth
        SetExternalAuthMethod pwauth pipe
</IfModule>
```Finally restart apache:
```
# /etc/init.d/apache2 restart
```These steps should get password authentication working again.

IMHO the libapache2-mod-auth-pam was much more elegant, at least from the scope of the server administrator. I really hate having to add two blocks of configuration instead of one, but I guess I'll have to live with it.

---

### Post by sgarman on 2010-01-13
Thank you - this is exactly the kind of information I was looking for.

Scott

---

### Post by wdaniels on 2010-06-24
> **sgarman said:**
> Thank you - this is exactly the kind of information I was looking for.

+1 Thanks! Helped me out also.

Far more complicated that way :S
But looks like the libapache2-mod-auth-pam package is [back since Lucid]("http://packages.ubuntu.com/lucid/libapache2-mod-auth-pam") though :)

---

### Post by Crass Spektakel on 2010-07-30
Thanks for your idea, let me point out two other great sources:

 1. [A similiar FreeBSD-HowTo]("http://blog.innerewut.de/2007/6/26/apache-2-2-authentication-with-mod_authnz_external")

 2. Your local documentation in /usr/share/doc/pwauth/

> But looks like the libapache2-mod-auth-pam package is back since Lucid though

 Don't use it. It requires apache to run as root or add www-data to group shadow which is nearly as bad.

 authnz_external is a solid base and pwauth a simplistic but complete implementation. It wont hold up to high traffic but then who would implement that through pam anyway?

---

