---
title: "Active Directory Domain Controller not in server documentation"
date: 2017-08-05
forum: Server Platforms
---

### Post by volkswagner on 2017-08-05
I'm curious why [Ubuntu's SAMBA documentation]("https://help.ubuntu.com/lts/serverguide/samba.html") does not contain
instructions for setting up SAMBA as ADDC.

Docs describe PDC and BDC NT4 style domains, but not more modern ADDC.
They only describe integration with an existing Active Directory.

Is this something in the works, or does Ubuntu not officially support
using server as ADDC?

---

### Post by cariboo on 2017-08-05
Is this what you are looking for?

[https://help.ubuntu.com/lts/serverguide/samba-dc.html](https://help.ubuntu.com/lts/serverguide/samba-dc.html)

---

### Post by volkswagner on 2017-08-05
Active Directory Domain Controller, SAMBA3 PDC/BDC, and SAMBA4 have been more than
confusing to me. From all the things I've read... my interpretation is that in a modern
Active Directory Domain environment there is no such thing as a Primary or Secondary controller.
In Active Directory, all domain controllers are equal except the "FSMO" role is assigned to just one controller.

From the link provided, it seems to be describing the old setup that was available in SAMBA3 with NT4 style PDC, BDC.

I don't see any reference to:

```

[global]
SERVER ROLE = ACTIVE DIRECTORY DOMAIN CONTROLLER
```

Please see [section regarding classic PDC/BDC roles ADDC]("http://www.sloop.net/smb.conf.html").

---

### Post by Doug S on 2017-08-08
There has finally been some subject matter expert contribution to the Ubuntu Serverguide in the Samba area. There was an update point release of the guide just a month or two ago. If you can not find what you want, maybe a bug report against the serverguide would help. [Example]("https://bugs.launchpad.net/serverguide/+bug/1654377"), so you know how to set "Affects".

Note that in general we struggle to get subject matter expert input for the Ubuntu Server guide, however the server team has been helping of recent.

Note also that there can be significant delays between bzr branch updates and official publication, so we have added a "dev" (development) publication in U.S. English only that might have the latest, yet to be officially published, edits. [Here]("https://help.ubuntu.com/dev/serverguide/index.html").

EDIT: The page cariboo referenced is somewhat old. Maybe [this bug report]("https://bugs.launchpad.net/serverguide/+bug/1604530") applies, not sure.

---

