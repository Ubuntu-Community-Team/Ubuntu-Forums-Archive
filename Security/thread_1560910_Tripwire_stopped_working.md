---
title: "Tripwire stopped working"
date: 2010-08-25
forum: Security
---

### Post by Mark2010 on 2010-08-25
Hi new to this forum

I have a problem with tripwire monitoring a WINDOWS directory via a cifs mount and hope someone can help. This was working fine until a recent round of WINDOWS and ubuntu updates and now I get the follow error message every time tripwire tries to check the dir.

1.   File system error.
     Filename: /srv/location/servername/d
     Value too large for defined data type

This happens on various server mounts and on different mounted drives on a single machine.

sudo siggen -a * also returns the same result.

All mounts are valid and file etc can be read using the mount points. Have tried rebooting machine, rebuilding mounts, tweaking privs etc but no success.

Next stage I think is to rollback updates !!

Anyone got any ideas ...

---

### Post by Mark2010 on 2010-08-25
Sorry should have also said that I have stripped my twpol.txt file back to the minimum. The internal default linux stuff all works and a rebuild of the tripwire db also does not solve the issue.

WINDOWS servers are running WINDOWS Server 2003

---

