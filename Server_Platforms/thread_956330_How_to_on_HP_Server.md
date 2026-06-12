---
title: "How to on HP Server"
date: 2008-10-23
forum: Server Platforms
---

### Post by mattyherts on 2008-10-23
Hi

I am about to undertake a ubuntu installation on a new HP DL385 G5 whilst I am relatively comfortable with the installation I have a question around the initial installation. The hardware is out the box and given I have only ever configured these machines with Windows Server is the ubuntu installation carried out in the same way through the HP automated installation utility? Obviously through this utility it created the RAID sets etc, I need to set this up with RAID 10. Or is it a case of booting off the ubuntu CD?

Any help would be greatly appreciated!!

Thanks

---

### Post by PilotJLR on 2008-10-23
HP isn't going to support Ubuntu... so use the SmartStart boot CD to start the ACU and configure your local array. After that's done, just reboot with an Ubuntu CD and install the OS normally.
This also means that Insight agents won't be installed.

---

