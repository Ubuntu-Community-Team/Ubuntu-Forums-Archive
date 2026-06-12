---
title: "Firestarter needs kindling"
date: 2007-08-24
forum: Server Platforms
---

### Post by gimpguy2000 on 2007-08-24
Howdy,

I installed Firestarter but had a question, first, it only runs from command line, su >Password>firestarter...

However, when I close the command window, the whole program closes. Not sure if it's supposed to or not but I checked keep in tray, it simply hasn't or won't. Is this supposed to be this way?

One more thing, when I do run the command I get this..

(firestarter:32122): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

 I use Ub feisty. 

Thanks,

Paul

---

### Post by gimpguy2000 on 2007-08-25
After 6 re-installs it finally works :confused:  Oh well, at least it's working. 

Solved...

---

### Post by Warren Watts on 2007-08-25
Firestarter is just a GUI interface that allows for easy modification of the iptables on your system.  Firestarter isn't a firewall, it's just an interface to the firewall that is already running on your computer.

The only advantage to having firestarter running all the time is that you can see possible intrusions to your system in real time.  Once you have configured your iptables using firestarter, you don't have to have it running for your system to be protected.

---

