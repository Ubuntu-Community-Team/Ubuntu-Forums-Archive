---
title: "Network system for an company"
date: 2010-01-22
forum: Server Platforms
---

### Post by nyu2007 on 2010-01-22
Hi All,

I prepare to upgrade my current system (Windows Server 2000 and Windows XP Client) to Ubuntu Server/ Ubuntu Desktop client.
My current system have about 300 clients.
PDC: Windows Advance Server 2000 include DHCP, DNS.
BDC: Backup for PDC (same services)
Mail: Exchange Server 
Firewall: ISA 

Upgrade:
OS: Ubuntu 8.04LTS
PDC: Samba + OpenLDAP + DHCPD + Bind9
BDC: Samba + OpenLDAP + DHCPD + Bind9
Mail: Zimbra ZCS
Firewall: Iptables + Hardware

Could you suggest the best solutions?
I love Ubuntu very much!!! :D

Many thanks for any suggestion...
Best regards,
NYU

---

### Post by bluefrog on 2010-01-22
do it step by step.

Changing everything at once will certainly lead to failure and to a roll back.

windows server, ISA can be transparent for your end-users so OK.

exchange server and 300 pc, that's another story. 
Don't underestimate the reluctance of your end-users to use new tools whether their reluctance is funded (problems of compatibility between permissive excel formulas and strictness of openoffice and so on...) or not funded (why the start menu is not called start... change of habits)

Introduce desktops where the impact will be the less visible (pc used to connect to the web only for example)

In any case, plan to train your users and to offer them good support after the transition.

The change will cost you. It's only after a while (in the long run) that the the cost savings will be obvious.

---

