---
title: "Cutting off access to anything but the Internet"
date: 2010-02-07
forum: Security
---

### Post by noobeh on 2010-02-07
I have a small network, a common setup, consisting of a cable modem, a wireless router, 2 desktops and 1 wireless laptop.  I am running Ubuntu in a virtual machine via VirtualBox on my Windows 7 desktop.  I want to do all my websurfing through the Virtual Machine which is setup to use NAT in VirtualBox.  I have everything working so far and it is really nice.  This is a safer way to use the web, but it could be even better if my Virtual Machine could not access any device on my network besides the router.  Even better than that would be if it could only receive and send HTTP and HTTPS traffic via the router and not be able to access any other device on my little network.  I installed Firestarter and set it to restrictive outbound, allowing only those two things i.e. HTTP and HTTPS, but I can still ping devices on the network.  I would like to block it all.  I have delved into the iptables firewall and came up with the following commands:

(My router is 192.168.1.1)

sudo iptables -I INPUT -m iprange --src-range 192.168.1.2-192.168.1.255 -j DROP
sudo iptables -I OUTPUT -m iprange --dst-range 192.168.1.2-192.168.1.255 -j DROP

I am no networking expert, so could anyone please tell me if that is sufficient?  Do I need to add anything else?

---

### Post by noobeh on 2010-02-07
I found the ICMP blocking rules in the preferences of Firestarter, so I guess the commands I was entering were not really necessary.  :popcorn:

---

