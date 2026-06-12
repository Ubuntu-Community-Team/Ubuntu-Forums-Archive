---
title: "Joining Gutsy to Windows Server 2003 Domain"
date: 2008-01-14
forum: Server Platforms
---

### Post by endfx on 2008-01-14
I'm having some problems joining a Windows Server 2003 domain in Gutsy. I've done this in pretty much every other Ubuntu release without any problems.

I basically follow this guide: [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

With Gutsy, I do the same thing. The server joins the domain just fine.
"wbinfo -u" and "wbinfo -g" work just fine.
"id Domainusername" will give a uid for domain users but not the domain group listings.

But neither:
getent passwd
getent group
work. They only give local users.

So basically, local users work but domain users don't. Though, wbinfo works, and I can get a UID for domain users but cannot look up group membership through the domain.

Any ideas?

Thanks!

---

### Post by crmanski on 2008-01-15
> **endfx said:**
> 
But neither:
getent passwd
getent group
work. They only give local users.


I would check the /etc/samba/smb.conf file and add these if they are not in there...
```
winbind enum users = yes
winbind enum groups = yes
```

---

### Post by endfx on 2008-01-15
crmanski: That worked. Thanks a lot.

I've never had to specify those options before in the many dapper servers I've setup. I guess the new versions of samba have those enum options off by default.

Thanks again.

---

