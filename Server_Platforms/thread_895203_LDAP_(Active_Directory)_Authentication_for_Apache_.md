---
title: "LDAP (Active Directory) Authentication for Apache in Hardy"
date: 2008-08-19
forum: Server Platforms
---

### Post by freelinuxhelp on 2008-08-19
According to everything I can find on the subject of authenticating Apache users against AD ldap, I need to install libapache-mod-ldap. My problem is that it's not available in the repos. Links below seem to indicate that the package is broken or no longer maintained. Is this the case? If the package is no longer maintained, is there a different package that I should use? If there's not a different package to use, is there another way to do this?
I'm using 8.04.1 Server.
[https://launchpad.net/ubuntu/+source/libapache-mod-ldap](https://launchpad.net/ubuntu/+source/libapache-mod-ldap)
[http://qa.ubuntuwire.com/debcheck/debcheck.py?dist=gutsy&package=libapache-mod-ldap](http://qa.ubuntuwire.com/debcheck/debcheck.py?dist=gutsy&package=libapache-mod-ldap)

Thanks for all the help! :-)

---

### Post by vertigo23 on 2008-08-20
Me too!  I'm not able to get any of the modules to compile from source, so this would be really really REALLY helpful!  Is it normal for newer versions to *drop* functionality?  This worked in gutsy!!

EDIT: Never mind - found that authnz_ldap is included in apache2.2-common

---

### Post by freelinuxhelp on 2008-08-20
So authnz_ldap is the new module to use then?

---

### Post by dynacrylic on 2008-08-22
Curious about this too as I've been trying to get this working. 

Here is the post I started a couple days ago:

[http://ubuntuforums.org/showthread.php?t=894800](http://ubuntuforums.org/showthread.php?t=894800)

Please let me know if you get it working.

---

### Post by dynacrylic on 2008-08-22
> **dynacrylic said:**
> Curious about this too as I've been trying to get this working. 

Here is the post I started a couple days ago:

[http://ubuntuforums.org/showthread.php?t=894800](http://ubuntuforums.org/showthread.php?t=894800)

Please let me know if you get it working.

I resolved my problem. Hopes this helps you or someone else:

[http://ubuntuforums.org/showthread.php?p=5643114#post5643114](http://ubuntuforums.org/showthread.php?p=5643114#post5643114)

---

### Post by freelinuxhelp on 2008-08-22
That link got me fixed up.
Thanks!

---

