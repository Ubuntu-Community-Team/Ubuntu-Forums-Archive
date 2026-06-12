---
title: "[SOLVED] CPU clock issue"
date: 2008-07-09
forum: Virtualisation
---

### Post by Stunts on 2008-07-09
Hi all!

I'm using WinXP pro under Virtualbox on my Ubuntu 8.04 AMD64 system.
Everything is working fine, except one detail.
I'm trying to install software on the virtual machine that requires a CPU speed of at least 733 Mhz. However, the install aborts with the message that my CPU is only running at 341 Mhz.
I've checked in the Windows system and It says " Intel Core2Due @ 2.2 Ghz 341 Mhz 777 RAM".

How can I change this value?
I'm actually running in a 2.2 Corando, so It got that part right.

To add some more data, the program installs fine on my windows install on the same machine. (Since I only use windows for this program I'm trying to get rid of the partition).

Anyone got any ideas?

Thanks in advance!

---

### Post by Stunts on 2008-07-10
Hi all!
I've found a solution.
If I reboot the virtual machine enough times I start getting different clock speeds.
I eventually got one a bit higher then the required minimum.
I guess that settles it. Hope it gets to help someone else with the same issue.

---

