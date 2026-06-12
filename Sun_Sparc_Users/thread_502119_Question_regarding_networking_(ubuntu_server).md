---
title: "Question regarding networking (ubuntu server)"
date: 2007-07-16
forum: Sun Sparc Users
---

### Post by RazerDad on 2007-07-16
I have installed 7.04 server onto an old Ultra5 workstation I had lying about (well, who doesn't have one lying about ;-) )

Anyway, to cut a long story short,during installation I didn't have the machine connected to a network and it hung at 85% during the "update-core-manager" package installation. Consequently,  I had to install it without configuring the network by opted to configure the network manually.

However, I cannot find the network device in /dev. I expected it to be something like hme0 (remembering back to my old Sun days) but it wasn't there.

Could anyone enlighten me as to how to install networking from scratch or am I doomed to reinstallation...

Thx
M.

---

### Post by prince_of_hackers on 2007-09-13
Networking shouldn't need to be "installed", everything should be built into the kernel. I don't know what the device name is in Ubuntu, in Aurora (Fedora/Redhat) I think it is hme0 like you said. However, to determine what network interfaces are available, and how they are configured, type ifconfig -a. This should print out all network interfaces, including the loopback interface, and give you information such as address and mask. Just typing ifconfig without the -a argument will just list active interfaces. Hope this helps.

---

