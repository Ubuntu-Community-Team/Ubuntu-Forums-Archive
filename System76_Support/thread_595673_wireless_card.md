---
title: "wireless card"
date: 2007-10-29
forum: System76 Support
---

### Post by Neuralgia on 2007-10-29
Do you know which card the system76's use in their Koala systems?

It's not listed in the wiki

I don't know if I'm being rude asking this, but I'm trying to build my own micro pc, and I'm not sure which PCI card can I use for wireless access.

If I'm being rude, please let me know to erase the thread.

Thanx

---

### Post by jml on 2007-10-29
Rather than erase the thread, you may want to ask a forum mod to move it to the networking/wireless sub-forum.  You will probably get more responses there.  I do not know the answer to your question, but I can help in a general way.  Wireless cards that utilize the Atheros, and the Ralink, (especially thr RT 2500) chipsets enjoy relatively good support in Linux.  Ubuntu also supports the Intel 3945 ABG card out of the box.  (At least Feisty did, have not tested with Gutsy)  

I would also recommend avoiding cards that utilize the Broadcom Chipset.  In Feisty the Broadcom drivers do not seem to work and one has to go through the process of blacklisting the driver, and utilizing the Windows driver with ndiswrapper.  I have made it work in the past, but its a bit of a pain.  I have not tested the Broadcom card with Gutsy, so your milage may vary.  Hope that this helps.

Joe

---

