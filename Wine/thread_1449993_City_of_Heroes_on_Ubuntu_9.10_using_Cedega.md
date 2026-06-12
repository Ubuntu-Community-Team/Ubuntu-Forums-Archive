---
title: "City of Heroes on Ubuntu 9.10 using Cedega"
date: 2010-04-08
forum: Wine
---

### Post by Ironhead3 on 2010-04-08
I'm about to pull my hair out on this one.

The game City of Heroes/Villains installs and starts fine on Ubuntu 9.10 64 bit with nVidia 185.18 driver and using Cedega with the newest engine. The problem is, character movement is sometimes erratic. Kind of like a skipping while walking thing. The key here is "sometimes". The problem comes and goes. Almost like something is putting a heavy load on the system but not quite. I'll assume that is sufficiently cryptic. :(

I'm trying to track down the exact problem here. This game ran excellent on older versions of Mandriva and Ubuntu using the 180.*  and earlier nVidia drivers while also using Cedega with the newest engine installed.

Guild Wars still runs like a champ on Ubuntu 9.10 64 bit. We'll refer to it as, "Old Faithful".

I suppose I can just wait until 10.04 LTS releases to see if the newest nVidia driver solves this problem. Just curious to see if anyone else has encountered this particular problem.


After further research, this problem has been solved. This "stuttering" is caused by a problem with the XOrg Server in Ubuntu 9.10. Specifically with repeating keys. The solution is to go to 
System/Preferences/Keyboard and disable or uncheck Repeat Keys.

---

