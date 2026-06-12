---
title: "New krb5 breaks samba"
date: 2011-12-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-12-21
New krb5 source (package libkrb5-3), version 1.10+dfsg~alpha1-6 (in Precise repos)
breaks current samba (package libsmbclient).
It needs samba version 2:3.6.1-2 or newer.
The latest in repos is 2:3.5.11~dfsg-4ubuntu3.

> **Changelog**

         krb5 (1.10+dfsg~alpha1-6) unstable; urgency=low     * Fix segfault with unknown hostnames in krb5_sname_to_principal,     Closes: #650671   * Indicate that this library breaks libsmbclient versions that depend on     krb5_locate_kdc, Closes: #650603, #650611   -- Sam Hartman <email address hidden>  Thu, 01 Dec 2011 19:34:41 -0500

---

### Post by Harry33 on 2011-12-21
Oh yes, here is the source page:

[https://launchpad.net/ubuntu/precise/+source/krb5/1.10+dfsg~alpha1-6](https://launchpad.net/ubuntu/precise/+source/krb5/1.10+dfsg~alpha1-6)

---

### Post by Harry33 on 2011-12-21
Now there are updates for krb5 and samba available to fix this incompatibility issue:
krb5 version 1.10+dfsg~alpha1-6ubuntu1
and
samba version 2:3.5.11~dfsg-4ubuntu4

Here:
[https://launchpad.net/ubuntu/precise/+source/krb5/1.10+dfsg~alpha1-6ubuntu1]("https://launchpad.net/ubuntu/precise/+source/krb5/1.10+dfsg%7Ealpha1-6ubuntu1")
[https://launchpad.net/ubuntu/precise/+source/samba/2:3.5.11~dfsg-4ubuntu4](https://launchpad.net/ubuntu/precise/+source/samba/2:3.5.11~dfsg-4ubuntu4)

> **Changelog**

          krb5 (1.10+dfsg~alpha1-6ubuntu1) precise; urgency=low    * fix LP: [#907227]("https://launchpad.net/bugs/907227") - Drop Breaks on libsmbclient to 2:3.5.11~dfsg-4ubuntu3     since that will be the version in Ubuntu which would be built against the     version of libkrb5-3 with the private symbols     (see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650541](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650541))     - update debian/control   * Mark Debian Vcs-* entries as XS-Debian-Vcs-*     - update debian/control  -- Micah Gersten <email address hidden>   Wed, 21 Dec 2011 03:50:56 -0600

> **Changelog**

          samba (2:3.5.11~dfsg-4ubuntu4) precise; urgency=low    * fix LP: [#907227]("https://launchpad.net/bugs/907227") - Bump build dependency on libkrb5-dev to (>= 1.10+dfsg~) to     make sure we're not getting any private symbols     (see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650541](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650541))     - update debian/changelog   * Mark Debian Vcs-* entries as XS-Debian-Vcs-*     - update debian/control  -- Micah Gersten <email address hidden>   Wed, 21 Dec 2011 03:45:34 -0600      


---

