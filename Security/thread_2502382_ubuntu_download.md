---
title: "ubuntu download"
date: 2024-11-12
forum: Security
---

### Post by ncgjiju138 on 2024-11-12
Hi. 


We are downloading the  local repository  for ubuntu 20.04 using apt-mirror.  It is downloading all the patches including cgminer file. Is it possible to exclude files while using apt-mirror.

regards,

George

---

### Post by TheFu on 2024-11-13
Did you check the manpage for apt-mirror?  [https://manpages.ubuntu.com/manpages/focal/man1/apt-mirror.1.html](https://manpages.ubuntu.com/manpages/focal/man1/apt-mirror.1.html)  Seems pretty limited.  You can control which architecture and which repos are mirrored ... but it is called "apt-mirror" for a reason.  Perhaps a different tool would be better?  Maybe an apt-cacher-ng setup that doesn't timeout files?  IDK.

Standard support for 20.04 ends in April, so why would anyone need to start mirroring now?  A newer LTS should be deployed at this point.  22.04 or 24.04 would be the options.

I'm assuming you are running either Ubuntu Server or the standard Ubuntu Desktop (using Gnome4+), since all other flavors lost support June 2023.

---

