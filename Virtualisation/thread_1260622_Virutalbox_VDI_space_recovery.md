---
title: "Virutalbox VDI space recovery"
date: 2009-09-07
forum: Virtualisation
---

### Post by kiran88pnjr on 2009-09-07
:confused::(
Hai,

I'm now using Ubuntu 9.04 AMD 64. I've recently installed Virtualbox in my system. I built VDI for it using 8.0 GB space of my home partition. But later I've completely removed Vbox, but before that I've removed VDI from home as root. Later my property showed that out of 22.9 GB of my home partition only 5.1 GB is free & 7.9 GB is used. I lost about 9.9 Gb space including 8.0 GB space I've used for Vbox before.

Please anyone help me to get back 8.0 GB 

:confused::confused::confused:

---

### Post by dk06 on 2009-09-08
You can try some data recovery software and in the future you might want to back up your virtual disks to a flash drive.

[http://www.guzu.net/linux/datarecovery.php](http://www.guzu.net/linux/datarecovery.php)

---

### Post by megamania on 2009-09-08
> **kiran88pnjr said:**
> 
Please anyone help me to get back 8.0 GB 

:confused::confused::confused:
It's probably in the trash of the root user.

From terminal, type:
```

gksudo nautilus /root/.local/share/

```
That opens Nautilus as root. Now, navigate to the trash folder of the root user, and SHIFT-DELETE the Trash folder.

I can't be more specific because I'm not at home right now.

---

