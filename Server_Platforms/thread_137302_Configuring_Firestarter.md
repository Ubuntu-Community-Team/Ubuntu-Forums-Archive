---
title: "Configuring Firestarter"
date: 2006-02-27
forum: Server Platforms
---

### Post by newlinuxuser on 2006-02-27
What is the most secure configuration for firestarter, im running Ubuntu on my laptop. I read through the help but didnt really understand it, thanks in advance. :p

---

### Post by gila_monster on 2006-02-27
Firestarter is just a front end for iptables. iptables is set by default to no open incoming ports, which is about as secure as you can get. So unless you are running a server of some sort (I presume not, as this is on your laptop), the default config should do you very well.

---

