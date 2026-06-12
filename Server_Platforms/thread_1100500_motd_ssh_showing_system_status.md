---
title: "motd ssh showing system status"
date: 2009-03-19
forum: Server Platforms
---

### Post by gujumax on 2009-03-19
Ubuntu server has a neat future when log into it with ssh the banner shows system status, such as cpu usage and so on.  How can I can get this in Ubuntu (non-server edition)?? Anybody have the contents of motd file from ubuntu server?

---

### Post by castrojo on 2009-03-19
Install update-motd.

Instructions are in the manpage. More info here: [https://wiki.ubuntu.com/UpdateMotd](https://wiki.ubuntu.com/UpdateMotd)

---

### Post by piju on 2010-04-26
landscape-sysinfo

---

### Post by piju on 2010-04-28
> **piju said:**
> landscape-sysinfo

sudo apt-get install landscape-client

---

