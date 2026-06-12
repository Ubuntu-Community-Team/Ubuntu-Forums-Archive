---
title: "Problems with kernel 3.2.0-59-generic x86_64"
date: 2014-02-21
forum: Server Platforms
---

### Post by fmouse on 2014-02-21
Are there known issues with Ubuntu kernel 3.2.0-59-generic x86_64 (12.04 LTS)?  I upgraded my server to this kernel version as advised by a security notice pulled in as part of a list of available upgrades - something I do on a regular basis.  Two things happened immediately.  Our list server (Mailman) stopped communicating with the SMTP server (courier) on the localhost IF, and bind9, also running on the same box, stoppped responding to queries from the VPN and localhost interfaces unless there was a specific IPv4 ACL listing them in the bind9 config file.  Previously bind9 listened on *all* IPv4 interfaces *unless* there was an interface ACL in the config file which limited such access.  I also have a report, but not yet any details, of a mail redirection failing while this kernel was installed, a process that involves SMTP submission by the MDA on the localhost interface.  I backed out the kernel upgrade, which solved list server problem, and verified my observation by commenting out the interface ACL in the bind9 config, noting that the name server once again worked *without* such an explicit list.

Any insight on this problem will be greatly appreciated!!

---

