---
title: "Trust Relationship failed - Win7"
date: 2010-12-09
forum: Server Platforms
---

### Post by Newbie50 on 2010-12-09
afternoon
 
my server is running Ubuntu. i have no problem adding a windows XP to the domain. i however have a problem with windows 7 laptop. i keep getting the following error
" the user could not be added because the following error has occured:
The trust relationship between this workstation and the primary domain failed"
 
please help
regards

---

### Post by windependence on 2010-12-09
Your passwords must match on the laptop and the server for the same account. Also, you should make sure the same user exists on both boxes.
 
-Tim

---

### Post by Newbie50 on 2010-12-14
> **Newbie50 said:**
> afternoon
 
my server is running Ubuntu. i have no problem adding a windows XP to the domain. i however have a problem with windows 7 laptop. i keep getting the following error
" the user could not be added because the following error has occured:
The trust relationship between this workstation and the primary domain failed"
 
please help
regards
hi
 
has anyone had any ideas on this one? i am still stuck with this laptop.

---

### Post by windependence on 2010-12-14
Try this link:
 
[http://www.winserverkb.com/Uwe/Forum.aspx/sbs/5361/Logins](http://www.winserverkb.com/Uwe/Forum.aspx/sbs/5361/Logins)
 
 
-Tim

---

### Post by koenn on 2010-12-14
I've seen similar errors when joining win7 to a win2000 domain.
It's a compatibility issue and there should be a hotfix or an update that fixes it : [http://support.microsoft.com/kb/976494/en-us](http://support.microsoft.com/kb/976494/en-us)

Don't know if this applies to your samba domain as well, but you may wanna have a look.

---

