---
title: "Firestarter and a router firewall"
date: 2005-08-30
forum: Server Platforms
---

### Post by Jason-X on 2005-08-30
Hi all,

Is it worth installing Firestarter if I have a Router with a built in firewall? As far as I know nothing can get past the router so would Firestarter be a waste of time?

Just curious really :)

---

### Post by N'Jal on 2005-08-30
firestarter is only a GUI to the firewall iptables i think so if you have iptables installed it's 6 and half a doozen really, if you don't have iptables installed don't bother.

---

### Post by robert_pectol on 2005-08-30
[QUOTE=Jason-X]Hi all,

Is it worth installing Firestarter if I have a Router with a built in firewall? As far as I know nothing can get past the router so would Firestarter be a waste of time?

Just curious really :)[/QUOTE]


Yeah... pretty much not worth it unless you plan on making your host a DMZ host or if you move it from network to network (such as a laptop).  However, depending on your security stance, network configuration, etc. you may opt to install a firewall on it (such as to protect it from other internal hosts etc.).

Generally speaking, the typical user behind a firewalling NAT router will only be inconvenienced by implimenting a firewall on their box.  The arguable added security in this scenerio probably wouldn't be worth it for most users.

---

### Post by bionnaki on 2005-08-30
yup, a properly configured nat firewall is all you really need. unless you wear a tin foil hat.

---

### Post by Jason-X on 2005-08-31
Thanks for the replys. Pretty much what I thought :)

---

### Post by sinbad782 on 2005-09-13
Having firestarter can be useful if you need to set up remote access from a known machine and block it from others, since you can easily define rules for each service for individual hosts, ip ranges etc. 

I've put firestarter on a couple of hosts that I administer remotely using SSH. This then blocks machines not using my own IP address from connecting on port 22. 

I also use my own linux machine as an image server (using systemimager-server) for cloned linux installs and I use firestarter there to stop other machines connecting to rsync on my machine.

---

