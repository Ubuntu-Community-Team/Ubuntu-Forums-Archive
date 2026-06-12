---
title: "Onboard LAN died, need to configure PCI nic"
date: 2009-02-12
forum: Server Platforms
---

### Post by lightningrod66 on 2009-02-12
I have been running ubuntu 8.10 server (LAMP server), using the onboard LAN for network.  The onboard LAN has died and **I have disabled it in BIOS **and inserted a PCI nic (Linksys) but the server won't recognize it now.  How to configure network for new card using command line?

EDIT:  I edited /etc/network/interfaces and changed eth0 to eth1, but that didn't work.  I changed eth1 back to eth0 and still don't work.  I have restarted the computer and even restarted the network from within the server [/etc/init.d/networking restart], but still does not recognize the PCI nic.

I know the PCI nic works because I also have a WinXP server on another hard drive that I swapped out and the nic works OK in WinXP. I am able to access the network, internet, etc from WinXP with this nic, but when I swap back the Ubuntu it does not recognize the nic.

SOLVED:  The NIC was named eth2 (why???)

---

