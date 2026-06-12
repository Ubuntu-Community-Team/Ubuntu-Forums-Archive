---
title: "Ubuntu &amp; Windows mixed network"
date: 2010-12-19
forum: Server Platforms
---

### Post by rogtek on 2010-12-19
Hello everyone!

I would like your help in a rather complex subject.
My goal is to implement the best solution in order to create a mixed (windows & ubuntu) network in a small company (2 servers, 15 workstations). Since now the first server was a Windows Server 2008 Active Directory Domain Controller and I was able to connect all the workstations to the domain. I want to replace Windows Domain with an Ubuntu Server to act as a domain controller.

I am searching and trying many methods but I haven't found a clean solution.

So my questions:

1. Is it possible to create a mixed windows - ubuntu network with an Ubuntu Server as the domain controller (I can create a Samba PDC and join all Windows workstations but not Ubuntu workstations)?

2. Is it possible to have roaming profiles for Ubuntu workstations?

3. If a try to create a Samba PDC with ldap authentication, could it be the way to implement this mixed network?

---

### Post by windependence on 2010-12-19
1. You should be able to join both the Windows boxes and the Ubuntu boxes to the Domain without problems.
 
2.  [https://help.ubuntu.com/community/RoamingProfilesWithNetworkManager](https://help.ubuntu.com/community/RoamingProfilesWithNetworkManager)
 
3.  This is probably the way I would go. 
Some helpful info:
[http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)
 
HTH
 
-Tim

---

