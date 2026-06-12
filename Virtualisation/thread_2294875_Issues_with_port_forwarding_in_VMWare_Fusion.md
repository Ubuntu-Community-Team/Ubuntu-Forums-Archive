---
title: "Issues with port forwarding in VMWare Fusion"
date: 2015-09-14
forum: Virtualisation
---

### Post by Mirko_Wiese on 2015-09-14
I'm running Ubuntu 15.04 in VMWare Fusion and trying to forward two ports for a software in the VM Ubuntu.

In Fusion shared networking is active and the VM is recognized in my router as the same machine as my Mac. So it seems that shared networking is ok.

But the software in Ubuntu still claims that the two ports (701/702 TCP) are both closed.

Is there something special i have to configure in Ubuntu for port forwarding?

I have already tried bridged networking, changed the ports for testing, nothing works. On my host the ports are open and working, only in the VM they are not.

---

### Post by Mirko_Wiese on 2015-09-18
After some further testing and experimenting, i have gained some ground, but found an odd issue in the end, which still needs solving.

I forgot that the software also needs Port 703 UDP for working. The host and the Ubuntu VM have both the same IP address and are both recognized by the router as the same machine. After adding Port 703 to my router rules, this port was open for the Ubuntu VM, but both TCP remained closed. I already deleted the TCP ports from the router and added them again, but to no avail. Is there a difference in Ubuntu between TCP and UDP in regards to port forwarding? I just don't understand, why the UDP port is open and TCP ports are not. For the host all 3 ports are open, so the router configuration is surely fine.

---

