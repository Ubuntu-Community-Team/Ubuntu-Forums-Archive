---
title: "Multiple vulnerabilties in ClamAV"
date: 2006-10-17
forum: Server Platforms
---

### Post by nocturn on 2006-10-17
I just filed a bugreport here: [https://launchpad.net/distros/ubuntu/+source/clamav/+bug/66510](https://launchpad.net/distros/ubuntu/+source/clamav/+bug/66510)

Multiple vulnerabilities have been fixed with the release of version 0.88.5 of the free and open-source ClamAV AntiVirus product related to the handling of PE files and the unpacking of CHM help files.  The PE handling issue poses a significant risk and users of versions prior to ClamAV 0.88.5 are urged to upgrade ASAP.

As I said in the bugreport, this is remotely exploitable, so quite critical.

This also brings up my point again that we need something like Debian volatile, because Dapper will be out there for 5 years on servers.  Some of these are bound to be spam/virus traps.

---

