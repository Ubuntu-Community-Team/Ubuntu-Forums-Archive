---
title: "CPU running at 100% with Samba + fix loses Software Center: Solved"
date: 2016-05-25
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2016-05-25
Greetings,
System = Yakkety 16.10
Problem = CPU continuously running at 100%
Problem source = Samba 
Solution = Remove Samba (it is not necessary to purge Samba, just remove), sudo apt-get remove samba, or use Synaptic.
Observed problem with the removal of Samba = loss of Ubuntu Software Center. 
Solution of loss of Ubuntu Software Center = Reinstall with , sudo apt-get install software-center. (NOT ubuntu-software-center).
The reinstall of Software Center will restore samba libs but not samba. 

Additional information. 
1. This is an upgraded (rolled over from Xenial) Yakkety and not a fresh/clean/new install. So I don't know if the problem persists in a new install of Yakkety. 
2. This is an All Intel Hardware system. So I don't know if the problem persists with other hardware. 

FYI

---

