---
title: "Samba share access from Windows poblem"
date: 2007-04-11
forum: Server Platforms
---

### Post by mopok on 2007-04-11
Hello. I have installed Ubuntu Dapper and configured it to authenticate using Active Directory via kerberos. Everything goes fine: AD users can login to Dapper box and access windows resources using samba without any additional authentication (exept printers, but I'm going to fix it soon). Now I've tried to access samba share from my Windows XP machine and got such a message (this is not exact translation cause I'm using localized version of XP):
No access to \\Dapper....
This security account cannot be used to access network from this machine.

On the other hand I can easily access any windows share from my Windows XP machine. So, I think the issue is somewhere in samba.

Samba on Dapper is configured to use security = ads and to use kerberos keytable.

Any suggestions on what am I doing wrong?

---

