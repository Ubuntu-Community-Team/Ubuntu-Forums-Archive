---
title: "linux domain controller"
date: 2008-11-05
forum: Server Platforms
---

### Post by bcbotha on 2008-11-05
is it possible to create a ubuntu domain controller that has similar functionality to that of windows server 2003?

---

### Post by lykwydchykyn on 2008-11-05
With Ubuntu server and SAMBA it is possible to:
 - Create an NT-Domain style primary domain controller.
 - Create an NT-Domain style backup domain controller to a SAMBA (but not windows) PDC
 - Join a windows 2k or later Active Directory as a member server

You cannot create an active directory (windows 2k-style) domain controller with Samba (and thus ubuntu).  Only NT4.

Of course, if you're not specifically wanting a Microsoft-style domain you can centralize authentication using NIS or LDAP.  But that's a slightly different animal.

---

### Post by renzokuken on 2008-11-05
this is for gutsy but i used it and it worked out fine. be sure to disable the roaming profiles.....

[http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller](http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller)

---

### Post by bab1 on 2008-11-05
> **bcbotha said:**
> is it possible to create a ubuntu domain controller that has similar functionality to that of windows server 2003?

Yes, with the product called eBox.  See [[COLOR="Green"]**here**[/COLOR]]("http://ebox-platform.com/").

eBox is basically Ubuntu with Perl scripts which allow you to configure through a graphical interface (browser).  It has the same capabilities as WS2003

---

