---
title: "software-center / Oneconf footprint"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-04-17
****

OneConf provides the ability to sync your computer's configuration data over
the network.
*****

It seems that Oneconf is continously trying to scan a network when in fact there is none because it is a single system. As a result, in such case, system-monitor is showing that 160 Mb ram is used on my system :( Thats way too much to syncing nothing.

What is the ram footprint on your system (without lan/wan) ?

Right now i've purged both oneconf & software-center as it using it.

[https://bugs.launchpad.net/ubuntu/+source/oneconf/+bug/894314](https://bugs.launchpad.net/ubuntu/+source/oneconf/+bug/894314)

---

### Post by baizon on 2012-04-17
Indeed i have the same "problem". The oneconf service is using a lot of memory and I'm not even using it.

---

### Post by dino99 on 2012-04-17
> **baizon said:**
> Indeed i have the same "problem". The oneconf service is using a lot of memory and I'm not even using it.

Please confirm the bug reported above to catch devs attention for fixing. (affect me to)

---

### Post by clifford junior on 2012-04-17
confirmed.

ubuntuone-syncdaemon also eats up my memory.

---

### Post by dino99 on 2012-04-17
> **clifford junior said:**
> confirmed.

ubuntuone-syncdaemon also eats up my memory.

Good :) i'm sure we are not alone with this issue. Cant confirm about ubuntuone here, its not installed, i've no need. You might open an other bug report about ubuntuone then.

---

### Post by dino99 on 2012-04-17
Please confirm the bug if you see ram highly used by oneconf inside System Monitor

---

### Post by clifford junior on 2012-04-17
i think they may have fixed this with the latest updates. since updating earlier today i dont even see it in my system monitor. i'll keep an eye on it and let you know.

---

### Post by clifford junior on 2012-04-17
ok i spoke too soon. 

its back and seems to appear and expand in memory when i have terminal open and running commands such as autoremove or update && upgrade

---

