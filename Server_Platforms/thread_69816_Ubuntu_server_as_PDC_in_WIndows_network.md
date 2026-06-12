---
title: "Ubuntu server as PDC in WIndows network?"
date: 2005-09-28
forum: Server Platforms
---

### Post by snpz on 2005-09-28
Hi folks!:)
I have to make Primary Domain Controller for network with ~30 XP workstations.
Do anyone suggest Ubuntu for such a thing? Maybe some of u have good manual how to set it up on Ubuntu?
Thnx for your attention!;)

---

### Post by LordHunter317 on 2005-09-28
You can use Samba, and the offical Samba HOWTO covers everything you need to know to do this.

However, Samba can only function at the level of an NT4 domain, which is really cruddy.  As such, I recommend you buy two copies of .NET 2003 Server and run Active Directory.

If you want, you can use Linux to host the DNS, and perform fileserving and several other tasks.

---

