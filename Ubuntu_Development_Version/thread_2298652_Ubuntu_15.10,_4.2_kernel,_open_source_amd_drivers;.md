---
title: "Ubuntu 15.10, 4.2 kernel, open source amd drivers; steam refuses to load."
date: 2015-10-12
forum: Ubuntu Development Version
---

### Post by tminus36 on 2015-10-12
Hi all,

I'm having a chicken and an egg issue here. Since the latest batch of kernel updates I've basically been left with only the option of the 4.2 kernel. After installing the amd proprietary drivers, the system boots to the splash screen and freezes. Never makes it to the login screen. If I uninstall and use the open source drivers, the kernel loads the system, I can login, but steam refuses to start with the following error:

```
user@host:~/$ steamRunning Steam on ubuntu 15.10 64-bit
STEAM_RUNTIME is enabled automatically
[2015-10-12 19:56:42] Startup - updater built Oct  8 2015 14:01:49
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

```
Anyone happen to solve this problem of AMD drivers, the 4.2 kernel, and possibly steam as well? It's obvious I have 3d accell working with the open source drivers because downloading and playing Urban Terror and Xonotic work fine! Quite fun too. I miss CS:GO though. :)

---

### Post by R33D3M33R on 2015-10-13
Try these commands: [http://askubuntu.com/questions/50634.../538907#538907]("http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907")

---

### Post by Bucky Ball on 2015-10-13
*Thread moved to **Ubuntu Development Version**.*

---

