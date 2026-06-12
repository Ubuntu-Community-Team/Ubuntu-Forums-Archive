---
title: "Upgrading office machines to 12.04 remotely with Cluster SSH- Doable?"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kodb on 2012-04-09
Hi everybody
In prep for eventually upgrading to Precise, I was wondering if I would be able to mass update my office machines using ClusterSSH.  I have that setup currently and do most if not all of my routine admin that way.  That allows me terminal access accross the office network.  Will I be able to upgrade via this route?  Currently we are at 10.04.3 for 9 clients and sometime after the intial bugs are worked out I want to upgrade to 12.04.  Is this a good, bad, or acceptable option?  Is there an easier way?
Thanks in advance to you intallation/upgrade gurus
Bob:popcorn:

---

### Post by searchfgold6789 on 2012-04-09
> **kodb said:**
> That allows me terminal access accross the office network.
You can upgrade via the terminal that way, if that's how your normally do things with root access on those computers. A simple ```
sudo do-release-upgrade -q
``` is the command to start the upgrade process in the terminal assuming that / is on the machine you are upgrading.

---

### Post by drs305 on 2012-04-09
Moved to Ubuntu+1. 

Although the Upgrades/Installation forum is also appropriate, since you are asking about Precise migration I've moved it here in case there are issues specific to Precise that might need consideration.

---

### Post by kodb on 2012-04-21
Thanks for the code!   I wasn't sure if because I was doing via a remote ssh connection whether a do release upgrade would work at all so I really appreciate the help
Bob

---

### Post by cariboo on 2012-04-21
I'd suggest you use screen on the systems being upgraded, just in case the system you are working from gets disconnected for any reason.

---

