---
title: "Broken link to repository due to wine"
date: 2009-06-23
forum: Wine
---

### Post by NoonienSoong97 on 2009-06-23
Here is what I get when I try to get into Synaptic, or try Gdebi, and also I can't even do anything with the software sources after installing wine.

E: Type '--11:35:30--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I also tried changing or deleting the winehq.list file, and the system wouldn't allow it.

---

### Post by NightMKoder on 2009-06-23
You typed the wget command wrong I'm pretty sure

sudo rm /etc/apt/sources.list.d/winehq.list

will delete it.

---

### Post by NoonienSoong97 on 2009-06-24
Thanks. didn't realize that you have to go through the terminal to delete systems files manually.

---

