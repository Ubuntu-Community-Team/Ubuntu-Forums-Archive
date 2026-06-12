---
title: "Job task: Load desktop from server to workstations"
date: 2012-04-14
forum: Server Platforms
---

### Post by Lundix on 2012-04-14
Hello, here is the challenge: my employer want to have a network where the employees desktops are loaded from a server to their workstations. 

Its  a quite simple network setting with one router and three workstations and the server connected to the router. I assume I will have to actually install Ubuntu on and use it as a server and create the user accounts on it.

Now the question is, how can I configure the system so that the desktops are loaded from the server / PC to the other workstations when they boot? Do I need to configure some kind of scripts for this? How should I proceed? 

Regards, 

lundix

---

### Post by oldwindows geek on 2012-04-14
Hello, although I am new to Ubuntu, the cost of the OS is very low, and unless the workstations do not have Hdd capacity, it may be easiest to install the OS on each workstation!  That way if your sever goes down, they can still work?

---

### Post by Gyokuro on 2012-04-15
You can achieve this request with an Ubuntu LTSP setup ([https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)).

---

### Post by Lundix on 2012-04-15
Thanks, I think the lltsp is exactly what i am looking for.

---

