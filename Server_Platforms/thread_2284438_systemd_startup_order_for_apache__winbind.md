---
title: "systemd startup order for apache / winbind"
date: 2015-06-29
forum: Server Platforms
---

### Post by andersbolager on 2015-06-29
Hi.

When logging my Ubuntu 15.04 upgraded server using systemd, apache fails to start, complaining user not found. The user in question is administered by Active Directory, and apache therefore requires winbind to be running.

The strange thing is that this works fine when booting with upstart.

Regards,
Anders

---

