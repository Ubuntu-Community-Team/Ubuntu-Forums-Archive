---
title: "LDAP installation problems in 8.04"
date: 2009-05-29
forum: Server Platforms
---

### Post by apfergus on 2009-05-29
I'm working on moving a server over from Red Hat Enterprise to Ubuntu Server. The way in which LDAP works seems to differ so much between the two that I've decided to reconfigure it from scratch to mount home directories and so forth. I'm hitting a snag right at the beginning, though.

Following [these]("https://help.ubuntu.com/community/OpenLDAPServer") instructions, I've installed slapd, ldap-utils, and db4.2-utils. I've tried to run dpkg-reconfigure slapd, and filled out all the information when prompted. This doesn't modify the slapd.conf file at all--it's completely identical to the version at installation.

If I modify it by hand, and add the information as in the documentation instructions, slapd will not even start. Running /etc/init.d/slapd restart displays an error saying to look at the system logs (which don't offer any more illuminating information).

Any idea what's going on?

---

### Post by LEO_Servers on 2009-05-29
I think i Know your problem your running LDAP:p might be easer if you put into E-Director and moved the tree's as long as there in the same forrest you will be fine

---

