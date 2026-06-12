---
title: "[SOLVED] lost internet connection on host and virtual"
date: 2007-11-25
forum: Virtualisation
---

### Post by christina_svats on 2007-11-25
I have installed virtualbox and have Ubuntu 7.10 as host and Windows XP as a virtual. At first, I had no problem with my internet connection on XP, however, every time I used virtualbox and then stopped it, I had to reboot in order to have internet connection on Ubuntu. Then, I had reason to install firestarter but it refused to run and gave me a message concerning the configuration of eth0. Since then, I have no internet connection at all.

I tried switching to manual configuration of my connection, but no luck. i have no idea what to do or where to look for the problem. Could anybody help me? ( right now I am using a LiveCD in order to have a connection)

---

### Post by snaileater on 2007-11-25
Did you try ifconfig to see the state of your nic?

---

### Post by christina_svats on 2007-11-25
yes, I have tried ifconfig, thanks for the answer. 
Anyway, it came back on both host and virtual machine the same way it went away: without me doing anything!
I hope it lasts!

---

