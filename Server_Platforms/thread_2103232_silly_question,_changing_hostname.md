---
title: "silly question, changing hostname"
date: 2013-01-09
forum: Server Platforms
---

### Post by ZenMasta on 2013-01-09
my hostname is generic, ie my-ip-address

I tried sudo vi /etc/hostname and replaced my-ip-address with tacobell-hq, and after relogging it wasn't changed.

What am I doing wrong?

---

### Post by chadk5utc on 2013-01-09
> **ZenMasta said:**
> my hostname is generic, ie my-ip-address

I tried sudo vi /etc/hostname and replaced my-ip-address with tacobell-hq, and after relogging it wasn't changed.

What am I doing wrong?

try in terminal 
> sudo hostname followed by new hostname

---

### Post by The Cog on 2013-01-09
Check that /etc/hosts has been changed as well.
You probably need to reboot, not just log out/in.

---

### Post by ZenMasta on 2013-01-09
Thanks I edited both locations and rebooted, looks good now :)

---

