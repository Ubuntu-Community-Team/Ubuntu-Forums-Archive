---
title: "Ubuntu Running Slow"
date: 2007-04-10
forum: Server Platforms
---

### Post by xkenshin on 2007-04-10
I run Ubuntu 6.06 on IBM ThinkPad with 1 GB RAM.
I installed Apache, PHP and MySQL to serve my application.
When i open my web application, it seems that it loads very slow. and i mean very2 slow, even for a simple search. Last time the RAM was 512MB, so i decide to upgrade it. Unfortunately, the upgrades doesn't make much different. Anyone have any idea why is this happens or having the same problem ?
thanks

---

### Post by heimo on 2007-04-10
> **xkenshin said:**
> Anyone have any idea why is this happens or having the same problem ?

Could be anything. You should try to give us more information and perhaps use top to see which processes are taking CPU or memory. Turn on / up logging in php/mysql/apache and watch what's going on. Add debugging to your application, exit points, logging, timing.

---

