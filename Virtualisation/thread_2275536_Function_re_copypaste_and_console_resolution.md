---
title: "Function re copy/paste and console resolution"
date: 2015-04-26
forum: Virtualisation
---

### Post by satimis on 2015-04-26
Hi all,

VM- Ubuntu 14.04 server
Host - Ubuntu 14.04 desktop
Virtualbox

How to;
1) increase console terminal size
2) copy and paste between server console and host

I'm now solving
1) with following steps:```

sudo nano /etc/default/grub
Change GRUB_GFXMODE= (e.g. GRUB_GFXMODE=1920x1200x32)
Set GRUB_GFXPAYLOAD_LINUX to GRUB_GFXPAYLOAD_LINUX=keep
sudo update-grub
reboot system

```

but it is NOT very convenient.  Is there a prompt action without reboot?

I have no solution to 2).  Please advise.

Thanks

Regards
satimis

---

