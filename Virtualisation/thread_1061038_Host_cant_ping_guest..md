---
title: "Host cant ping guest."
date: 2009-02-05
forum: Virtualisation
---

### Post by breakman on 2009-02-05
I'm runnig Virtualbox on my workstation. I've installed Ubuntu Server as a guest using host interface with a static IP.
The problem is that i can't ping, access the webserver or ssh to my gust från the host. No problem accessing it from my laptop.

Any solution?

---

### Post by shauvik on 2009-02-05
Have you setup bridge networking as mentioned here:
[https://help.ubuntu.com/community/VirtualBox#Networking](https://help.ubuntu.com/community/VirtualBox#Networking)

Also, it would be nice if you could paste your /etc/network/interfaces file

---

### Post by breakman on 2009-02-06
Nervermind... Now it suddenly just works. Strange!
Tried several times before and always get timed out.

---

### Post by markba on 2009-02-18
Have you upgraded you VBox setup? Because pinging from a guest (using ICMP) did not work by design until version 2.1.0.

See: [http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)
Search for ICMP.

---

