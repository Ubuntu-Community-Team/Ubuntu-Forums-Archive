---
title: "Xorg 7.2 and DTWM compatibility issue"
date: 2008-04-03
forum: Sun Sparc Users
---

### Post by parker13 on 2008-04-03
Hi,

My company uses Sun machines and I used to be able to bring the Solaris X screens up on my Ubuntu box. However, since Gutsy, there's been a problem. If I log in using:

> X :1 -query rs1

After login, the windows do not have any borders.


It seems to boil down to an incompatibility between dtwm and the Ubuntu X server. If I attempt to log in and run dtwm directly, I get:

```

$ ssh -X rs1
Last login: Thu Apr  3 10:55:45 2008 from 151.214.46.169
Sun Microsystems Inc.   SunOS 5.8       Generic Patch   February 2004
RS1:/home/garry> /usr/dt/bin/dtwm
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  159 (XINERAMA)
  Minor opcode of failed request:  2 (XINERAMAGetScreenCount)
  Resource id in failed request:  0x0
  Serial number of failed request:  16
  Current serial number in output stream:  16

```

Using a different window manager fixes this, but we have a large number of legacy systems which use DTWM, so I'd like to get to the bottom of this issue.

Can anybody help?

---

