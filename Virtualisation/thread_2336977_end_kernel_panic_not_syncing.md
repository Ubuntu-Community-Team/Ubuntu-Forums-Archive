---
title: "end kernel panic not syncing"
date: 2016-09-13
forum: Virtualisation
---

### Post by keshav112 on 2016-09-13
i am trying to install ubuntu desktop 16.04 on a virtualbox using normal settings (1000 MB RAM)
the following error occurs when i boot into .iso (the window snap is attached)
please help me

---

### Post by &amp;KyT$0P# on 2016-09-13
First off, Ubuntu 16.04 will need more RAM than that to run.  I'd suggest you either increase the RAM to at least 2 GB (2048 MB), or try a lighter flavor such as Lubuntu 16.04 or Xubuntu 16.04.

Can you please provide more details about the VM's hardware?


EDIT Also what version of VirtualBox are you using?

---

### Post by keshav112 on 2016-09-13
[ATTACH=CONFIG]271162[/ATTACH]i am using VM 5.0.24 version 
other hardware details are attached in snapshot

---

### Post by &amp;KyT$0P# on 2016-09-13
Can you try a 64-bit (amd64) iso of Ubuntu 16.04?
(Some hardware settings of 32-bit VM might not be compatible with 64-bit OS.  Being so early into the process, it might be easiest to create a new VM for use of 64-bit Ubuntu.)

---

### Post by ynota on 2016-09-14
have you tried turning off the paravirtualization, the other settings look ok to me

---

