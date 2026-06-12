---
title: "[SOLVED] Belkin UPS Install"
date: 2008-01-24
forum: Server Platforms
---

### Post by maustin2 on 2008-01-24
I am getting Permission denied when attempting to execute a ./setup.bin file for the title subject.

I am at root@hostname:/file location, when I issue command

Has anyone encountered this situation? 
More importantly would be has anyone founded a solution?

](*,)

---

### Post by smileypaul on 2008-01-24
Which one did you get?  ihave the 1500VA one.. works beautifully.

anyways, there was no setup required for mine?  If you check the UPS hardware compatibility list, you may find which driver to use.. and odds are, it will work out of the box.

anyways, i have a series of servers running at my business, and I set up "nut" .. i couldnt be happier.. one server monitors the belkin ups.. and when it see's that it is on low battery , it sends a signal to the other servers.. and they all gracefully shutdown before the UPS runs out of juice.. i highly suggest looking into it..

anyways, on the setup.bin .. as root.. type..

chmod u+x ./setup.bin

that should fix it.

---

