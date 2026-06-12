---
title: "Set default domain"
date: 2008-06-23
forum: Server Platforms
---

### Post by Benismyhorse on 2008-06-23
Hi, was hoping if anyone knows of a way to set a default domain to log on to, I am using likewise and can logon to the domain by going DOMAIN\user is there a way I could change this so you only have to enter the user name.
Thanks

Sorry Found out how to do it thanks,

---

### Post by darkman738 on 2009-03-18
> **Benismyhorse said:**
> Hi, was hoping if anyone knows of a way to set a default domain to log on to, I am using likewise and can logon to the domain by going DOMAIN\user is there a way I could change this so you only have to enter the user name.
Thanks

Sorry Found out how to do it thanks,

Could you, or anyone else share how it is done, thanks!

---

### Post by darkman738 on 2009-03-18
I found [this]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/192598") which stated:

> 

To make likewise-open use the default domain, you can add the following statement to /etc/samba/lwiauthd.conf:

winbind use default domain = yes

Then restart the likewise-open-service. Users now don't have to type the "domain\"-prefix when logging in.


Not sure if this works, but I'm trying it now....

---

