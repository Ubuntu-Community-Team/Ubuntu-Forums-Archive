---
title: "Jeos in VirtualBox on Vista: Connect problem"
date: 2009-09-06
forum: Virtualisation
---

### Post by john_van_v on 2009-09-06
Hi all,

I have the Ubuntu JeOS within VirtualBox on Vista.

I can initiate an X window in the guest JeOS that attaches to an Xming server on the Vista laptop, but I cannot reach the guest JeOS from the laptop, either by pinging or to the www server on the JeOS.

Since there is two-way communication between the X server and client, then there is two-way communication between the two operating systems.

I am guessing that all I need is a "route" command on the vista host laptop to be able to connect to the JeOS in the VirtualBox.

Some of what I have read online implies that you cannot get from host to guest with VirtualBox, which makes no sense because the X server and ping, or ICMP, response are doing just that.

I tried to create a static IP address in the guest JeOS, and it worked, but only for a while.  When took my laptop to another network, that failed, and the guest JeOS connection has been unreliable since then with that address.  (I can't really make conclusions as to why, but that is the situation.)

I should mention that I have vmware and virtual box installed and running sometimes simultaneously.  

Any windoze routing advice gratefully appreciated.

---

