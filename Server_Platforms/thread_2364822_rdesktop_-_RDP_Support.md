---
title: "rdesktop - RDP Support"
date: 2017-06-28
forum: Server Platforms
---

### Post by krozzox on 2017-06-28
Hi all,

I am trying to implement a LTSP setup at work that uses linux boxes to RDP straight into a windows RDP session. I am needing it to support at least version 7.1 of RDP has anyone had this working within an LTSP enviroment?

Cheers

---

### Post by QIII on 2017-06-28
Moved to Server Platforms.

Hello!

Could you explain in a bit more detail what it is you are trying to accomplish?

---

### Post by TheFu on 2017-06-29
RDP has a history of security issues.  If you choose to go this way, be certain that 
* the LAN really is trustworthy (they usually are not)
* a full, secured, VPN is used for any non-LAN RDP traffic.

I saw another MiTM RDP attack announced today, BTW.  [https://www.mdsec.co.uk/2017/06/rdpinception/](https://www.mdsec.co.uk/2017/06/rdpinception/) Enjoy.

---

