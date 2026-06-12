---
title: "Two Desktop on Dual Monitor"
date: 2014-08-30
forum: Ubuntu, Linux and OS Chat
---

### Post by pietrofontana77 on 2014-08-30
Hi All,
i've configured my Samsung gaming rig to use dual monitor with the latest NVIDIA proprietary drivers.

The procedure was pretty easy, it works, i have choose to have to XScreen instead of Clone, each of Screen have their desktop. 

The problem is that if a program is running on Screen 1, it can't run on Screen 2, and i'm wondering if there's a possibility to run multiple istance of applications on different screen at same time or something like this.

Thanks.

Regards.

---

### Post by TheFu on 2014-08-31
It really depends on how the game developer wrote the software.

Normally, on a multi-user system, running multiple instances of a product isn't too hard, but if the developer didn't create a game for this sort of configuration, it is easy to be lazy and make assumptions about it being used by 1 user at a time on 1 computer at a time.

BTW - it is usually NOT a good idea to load video drivers from outside the package manager. I know that Windows needs that, but usually not Linux. In fact, it can lead to system instability and may cause patch management to break in a month or so.  Stay with the repo video drivers unless there isn't any other choice. Avoid ever installing files outside the well-know and trusted repos.

---

