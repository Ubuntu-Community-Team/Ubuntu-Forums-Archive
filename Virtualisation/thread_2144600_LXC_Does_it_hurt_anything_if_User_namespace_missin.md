---
title: "LXC: Does it hurt anything if User namespace: missing ???"
date: 2013-05-12
forum: Virtualisation
---

### Post by held7over on 2013-05-12
Ubuntu 12.04

On my dual processor AMD 64 bit machine, when I do a lxc-checkconfig every is enabled. However, when I ask the same question of my single processor AMD 32 bit machine, everything is enable except User namespace: missing

Does this mean I can't go ahead and set my 32bit machine up to use LXC? Or can I still go ahead and use it?

Thanks!:p

---

### Post by held7over on 2013-05-13
Everything seems to work. I guess I will assume having namespaces in the 32 bit version not enabled isn't going to jeaprodize my use of the containers. It just seemed strange to me that the 64 bit version of 12.04 had this enabled and the 32 bit version didn't....but it appears that this is suppose to be corrected in the next Looooonnnnggggg Term release....

---

