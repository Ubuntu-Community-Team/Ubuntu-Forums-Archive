---
title: "How to finish upgrade to 14.04?"
date: 2014-02-09
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-09
I ran command 
update-manager -d
It downloaded everything and was upgrading.

When I came back, the screen was full of corruption. 
colored lines, still running, but made me think an unsupported resolution, this IBM LED monitor can not go beyond 1024 by 768.

So I unplugged and rebooted and it comes up as 13.10, but some icons on top gnome 3 look different.

Rerun update and computer tells me it is up to date? 
Login screen says it is 13.10
In terminal it tells me it is 14.04

---

### Post by Mateusz Stachowski on 2014-02-09
If in terminal you see Ubuntu Trusty Tahr (development branch) than you are running 14.04.

The login screen and "About computer" still show 13.10 this will change in later cycle of the development (it's always like that).

---

### Post by sdowney717 on 2014-02-09
ok, thanks for that.

---

### Post by SurfaceUnits on 2014-02-11
You can run these two commands to check if anything is left hanging

sudo dpkg --configure -a 
and 
sudo apt-get install -f

---

