---
title: "Cant Connect --- inetd not running !"
date: 2006-03-28
forum: Server Platforms
---

### Post by webfoot0 on 2006-03-28
Hi All
Like some others I have had a problem with:
ftp
telnet
and maybe samba

This was apparently because inetd was not included in the installation.

This is part of the security risk of telnet and ftp as lots of services appear to be started if called for by this deamon.

Any service with an executable in /etc/services can be started when the inetd demon is running.

"Till someone tells me otherwise"

Keith

---

