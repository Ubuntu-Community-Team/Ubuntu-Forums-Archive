---
title: "Virus Scanner for external HD"
date: 2010-10-18
forum: Security
---

### Post by newinochi on 2010-10-18
Okay... So hopefully I can explain my question. I would like to scan my external HD for Microsoft viruses using my Ubuntu machine. I have Ubuntu 10.10 (love it btw) however unfortunately I have an XP machine at work as well. I'd like to be able to scan the drive before I plug it into the work computer. Anyone know of something I could use?

---

### Post by Barriehie on 2010-10-18
> **newinochi said:**
> Okay... So hopefully I can explain my question. I would like to scan my external HD for Microsoft viruses using my Ubuntu machine. I have Ubuntu 10.10 (love it btw) however unfortunately I have an XP machine at work as well. I'd like to be able to scan the drive before I plug it into the work computer. Anyone know of something I could use?

clamav with clamtk should do it.  In the repos.

HTH

---

### Post by ventrical on 2010-10-19
> **newinochi said:**
> Okay... So hopefully I can explain my question. I would like to scan my external HD for Microsoft viruses using my Ubuntu machine. I have Ubuntu 10.10 (love it btw) however unfortunately I have an XP machine at work as well. I'd like to be able to scan the drive before I plug it into the work computer. Anyone know of something I could use?

AVG has a rescue program for LINUX. You can run it either from a CD or pendrive and it will boot on it's own and scan the  sleeping Windows drive. It can also be run as a side by side install .

  You have to learn how to use it though. 

For Ubuntu - first download and install the package from AVG.

sudo -i
(enter your password when prompted - it will not come up on the terminal)
sudo avgscan /media/

Media is usually the Windows drive.

*note* sudo -i will put you in the root directory of Ubuntu!!

---

