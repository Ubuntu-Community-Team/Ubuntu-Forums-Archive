---
title: "Server Console / Terminal Font Size Way Too Small"
date: 2018-07-01
forum: Server Platforms
---

### Post by humanjhawkins on 2018-07-01
I have seen other closed threads on this, but the solutions have not worked... So asking for further thought here. I am running Ubuntu Server 18.04 as a fresh installed Hyper-V from a Windows 10 system. The screen is high res for my viewing distance, and the characters in terminal are almost impossible to read.

I have tried [COLOR=#800000]sudo dpkg-reconfigure console-setup[/COLOR], but my original size was already 8 x 16, and the largest option there appears to be 8 x 18. Those numbers are pixels, no? If so, I need to get minimally to around 20 x 40 or so. 

Thanks for any help on this.

---

### Post by TheFu on 2018-07-08
Use ssh for all systems admin work, then the font choice is client-side.
I've never used or even seen hyper-v, but with other VM solutions, the client controls scaling.  There is a "View-->Scale Display" setting in virt-manager, for example.

---

