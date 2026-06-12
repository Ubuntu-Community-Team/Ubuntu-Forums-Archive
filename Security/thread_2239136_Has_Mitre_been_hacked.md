---
title: "Has Mitre been hacked ?"
date: 2014-08-12
forum: Security
---

### Post by rmstock2 on 2014-08-12
I run this old optiplex occasionally with Ubuntu 10.04.4 LTS on there, which runs ok.
This morning update-manager reports :

25 packages can be updated.
23 updates are security updates.
 
where amongst others libc kerberos TLS and all of openssl etc. I clicked through on one of them 
and got this :

[IMG]http://s3.postimg.org/mcqy0iclf/Mitre_Hack_1.jpg[/IMG]

[IMG]http://s28.postimg.org/sbs821zb1/Mitre_Hack_2.jpg[/IMG]

---

### Post by tgalati4 on 2014-08-12
There were some serious security vulnerabilities in SSL and websites that rely on SSL for https.  So if your system or the host system has not been updated, then it's time to do so.

Those security changes to SSL were backported to older distros (which is why you got them in 10.04.)  I don't see any issues.

---

### Post by coffeecat on 2014-08-12
But you have another problem. You are running a GUI in 10.04. The server version of 10.04 is supported until next year, but desktop support has long finished and, indeed, recent server updates which are not tested against the desktop have been known to cause problems:

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

If you wish to run a system with a GUI desktop, you need to upgrade to or re-install with a supported version.

---

