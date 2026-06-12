---
title: "Need help with creating network in virtualbox"
date: 2009-10-02
forum: Virtualisation
---

### Post by daybreak on 2009-10-02
Here is my question to those of you having experience with setting up network with virtualbox
Is it possible to create a LAN between lets say 2 virtual machines, that are running simultaneously?
Network should have dns and dhcp services available.
Thats it

BTW:It is for a project and I chose to do it with kubuntu:KS
I have tried both, to adjust network settings in virtual box and kubuntu, still no luck.

---

### Post by Perryg on 2009-10-02
If there is a router in the mix you can select bridged mode to make this happen.  I you don't have a router in the mix you can select one of two ways to make this happen.
(1) use host-only mode to make the connection to the host and add a second adapter as NAT to allow the guest to get to the Internet.
(2) use Internal mode on the guests if they need to connect to each other but not the host.  Still adding a second adapter as NAT if they need to get to the Internet.

---

### Post by daybreak on 2009-10-03
By giving a separate virtual NIC to each machine they were able to communicate and share some files
However there was still no internet connection, so I gave 2 NICs for both machines(one NAT and the other host-only), and that did the trick.
Thanks for your help

---

