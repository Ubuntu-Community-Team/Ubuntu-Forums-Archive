---
title: "LDAP PAM unable to dlopen map_mkhomedir.so"
date: 2014-04-11
forum: Server Platforms
---

### Post by HarvesterOfBeer on 2014-04-11
Hello. I have an Ubuntu 13.10 x64 machine joined to an Active Directory domain via Samba. I have user authentication to the domain working properly (I can SSH to the box using domain credentials). However, I'm unable to have PAM automatically create a home directory for users when the log in. I have this in /etc/pam.d/common-session:

```
session [default=1]     pam_permit.so
session requisite       pam_deny.so
session required        pam_permit.so
session optional        pam_umask.so
session optional        map_mkhomedir.so skel=/etc/skel umask=0644
session optional        pam_krb5.so minimum_uid=1000
session required        pam_unix.so 
session optional        pam_ldap.so 
session optional        pam_systemd.so 

```

When I log in, the user home directory is not created, and I get this in /var/log/auth.log:

```
Apr 11 10:28:09 rred1rund01 sudo: PAM unable to dlopen(map_mkhomedir.so): /lib/security/map_mkhomedir.so: cannot open shared object file: No such file or directory
Apr 11 10:28:09 rred1rund01 sudo: PAM adding faulty module: map_mkhomedir.so
```

The specified directory (/lib/security) does not exist on this machine. I checked, and libpam-modules is installed.

The user has UNIX ids and home settings in AD.

Any pointers?

---

### Post by anthony-geoghegan on 2014-05-16
While following the instructions at  [http://technet.microsoft.com/en-us/magazine/2008.12.linux.aspx](http://technet.microsoft.com/en-us/magazine/2008.12.linux.aspx), I just  ran into the same problem and Google was of no help to me (which was how  I found this forum post). 

I eventually realised that the problem was that the module's name is **pam_mkhomedir.so** -- not *map_mkhomedir.so*

**Edit**: You should also change the umask to be 0022:

```
 session     optional    pam_mkhomedir.so skel=/etc/skel umask=0022
```

---

