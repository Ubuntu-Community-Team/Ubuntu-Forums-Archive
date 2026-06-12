---
title: "*** WINE PACKAGES FOR 1.1.12 on Intrepid and Hardy may be broken.  READ ME ***"
date: 2009-01-06
forum: Wine
---

### Post by hikaricore on 2009-01-06
It's come to my attention that the Ubuntu packages for 1.1.12 have some issues.
**The advice I will give you is to stick with 1.1.11 or 1.1.10 until the next release.**

> wine: Call from 0x7b8456d0 to unimplemented function ntoskrnl.exe.KeInitializeSemaphore, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeSemaphore called at address 0x7b8456d0 (thread 0024), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart. 

Not really sure what the problem is at this time just throwing it out there after numerous threads have been posted on said issue.

If you installed 1.1.12 ON **INTREPID 8.10** and need to downgrade here's a direct link to 1.1.11: [i386]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb") [amd64]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb")


If you installed 1.1.12 ON **HARDY 8.04** and need to downgrade here's a direct link to 1.1.10: [i386]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.10~winehq0~ubuntu~8.04-0ubuntu1_i386.deb") [amd64]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.10~winehq0~ubuntu~8.04-0ubuntu1_amd64.deb")


If for any reasons these links don't work, you'll be able to download WINE for other Ubuntu versions here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by hikaricore on 2009-01-16
Updated 01/16/09

---

### Post by hexilum on 2009-01-17
This fixed my .NET 2.0 framework installation errors.

---

### Post by binbash on 2009-01-17
1.1.13 released,those crashes which was on 1.1.12 is fixed

---

### Post by hikaricore on 2009-01-17
> **binbash said:**
> 1.1.13 released,those crashes which was on 1.1.12 is fixed

We'll see when the packages are up. :P

I'm not going to jump the gun on this.

---

### Post by The Joe on 2009-01-18
I got 1.1.12 from adding it in Ubuntu Tweak - no problems so far...

Just upgrading to 1.1.13...


edit: wow that was quick

---

### Post by hikaricore on 2009-01-18
The 1.1.13 packages fixed the issue that some users were having.  So the crisis is over.  :)

---

