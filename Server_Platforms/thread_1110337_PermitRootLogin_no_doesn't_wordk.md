---
title: "PermitRootLogin no doesn't wordk"
date: 2009-03-29
forum: Server Platforms
---

### Post by Windows_ on 2009-03-29
Hi everybody.

I've wrote **PermitRootLogin no** in /etc/ssh/ssh_config, then made /etc/ini.d/ssh restart and log out.

But when I try root login via ssh again to check new option - I was able again to make it! **PermitRootLogin no** doesn't work. What's the problem?

---

### Post by brian_p on 2009-03-29
> **Windows_ said:**
> 

What's the problem?

You have altered the incorrect file. You want /etc/ssh/sshd_config.

---

### Post by BkkBonanza on 2009-03-29
Also check the file carefully. It comes by default with that statement set to yes. So if you simply add a new line it could be that the original one is still in there and active. I don't know for sure how it reacts to multiple entries but it could be either way.

---

