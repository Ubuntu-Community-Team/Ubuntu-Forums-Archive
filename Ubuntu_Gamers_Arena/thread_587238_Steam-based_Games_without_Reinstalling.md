---
title: "Steam-based Games without Reinstalling"
date: 2007-10-22
forum: Ubuntu Gamers Arena
---

### Post by FrankP on 2007-10-22
So, heres my setup.

I have two harddrives. HD1 has got my Windows install on, and pretty much thats it. HD2 has two partitions; one around 150GB big which acts as storage for games and musicto Windows. The second partition houses Ubuntu - a 6GB one.

Now I've got the dual boot working fine, and Ubuntu can see and write to both HD1 and HD2. I can even see the Steam GCF files. 

HOWEVER, as the Ubuntu partition is merely 6GB, how can I tell Steam on Ubuntu to read the GCFs from HD2, thus not having to reinstall them?

---

### Post by FrankP on 2007-10-23
Anyone whos interested I've found a solution. Simply make symlinks to the GCFs on the other parittion and put those symlinks in you're GCF folder. This makes Wine/Steam believe that there are GCFs in you're SteamApps, but in fact, there are not, just shortcuts.

---

