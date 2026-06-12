---
title: "How to uninstall the ubuntu-desktop"
date: 2015-11-07
forum: Server Platforms
---

### Post by Jake_Simmons on 2015-11-07
I decided to install the ubuntu-desktop on my device. Instant regret. I cant find out how to uninstall the thing. Its so irritating.
The code I used to install the desktop was the simple:
```
sudo apt-get install ubuntu-desktop
```
however when i try
```
sudo apt-get purge ubuntu-desktop
```
or instead of purge, remove...
but it simply wont work.

ill paste in the response i get once i figure out how to...

any help will be greatly appreciated.

---

### Post by westie457 on 2015-11-07
It is possible to remove all of the desktop packages, however usually something goes wrong and ends with a reinstall.
IMHO this is one of those times it will be quicker and easier to start again after backing up all files you want to keep.

---

### Post by ian-weisser on 2015-11-07
Apt includes a list of all packages you installed manually vs those that get pulled in (automatically) as dependencies.

Unfortunately, it predates the Ubuntu install iso, and that leads to a design incompatibilty: If the installer marks ubuntu-desktop as 'manual', the other thousands of packages will all be pulled in automatically...BUT if any user removes that package, the *entire system* becomes eligibile for autoremove.

This happens to people who use the Minimal iso on occasion; it's a real problem. So the installer's workaround is to choose the safe option: It marks EVERY package as 'manual'.

This keeps your system safe, but at the cost of being able to remove whole slabs of packages upon demand.

Your best workaround to the installer workaround is, as westie457 wrote, is to reinstall the flavor you prefer. Or reinstall using the Minimal iso, and...er, remember to not accidentally delete your entire system.

---

