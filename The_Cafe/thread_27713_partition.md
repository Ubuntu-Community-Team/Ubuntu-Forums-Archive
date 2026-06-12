---
title: "partition"
date: 2005-04-17
forum: The Cafe
---

### Post by doom on 2005-04-17
sorry, im a n00b but how do you make a partition?  I want to use wine but i need a C: and so i need to make a partition...

---

### Post by UbuWu on 2005-04-17
Search for gparted in synaptic.

---

### Post by baza41 on 2005-04-17
You don't need a C: to use wine.

Baza

---

### Post by doom on 2005-04-17
I know... but you do if you want to install certain thing...

---

### Post by doom on 2005-04-17
I have gparted... when i try to open in i get a pop up saying that i cant

---

### Post by burlap on 2005-04-17
Wine will create fake windows drive (C: ) itself - just run wine or winetools (package can be found in backports repositories). You will find the drive in /home/your_user_name/.wine. And if you install programs with "wine program.exe" they will find this fake drive automatically.

---

### Post by TravisNewman on 2005-04-17
It's actually NOT a good idea to use a C: drive with Wine-- at least, it's a bad idea to use a Windows installation for Wine. If you already have a Windows installation you can run SOME programs you've installed (ones that don't put files everywhere), but it's normally a better idea to just install them through wine.

---

