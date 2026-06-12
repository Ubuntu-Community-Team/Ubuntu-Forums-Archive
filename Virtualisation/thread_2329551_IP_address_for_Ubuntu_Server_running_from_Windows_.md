---
title: "IP address for Ubuntu Server running from Windows 7"
date: 2016-07-02
forum: Virtualisation
---

### Post by warren55 on 2016-07-02
I have Ubuntu 14.04 running in a virtual box from my Windows 7 computer.  When I run ifconfig from a terminal windows it shows an IP address of 10.0.2.15.  The IP of the windows 7 computer is 192.168.1.5.  If I want to access the nginx server from another computer on the same network do I type 10.0.2.15?  For some reason it doesn't seem to work even though I have nginx setup for 10.0.2.15.  Thanks for the help.

---

### Post by TheFu on 2016-07-03
Make the network connection settings inside the VM settings "bridged." There is a **checkbox** for this. That will make the VM work like it was a real machine on the main network. It will ask the DHCP server for the network to provide the network settings - should get something like 192.168.1.10.  

If you want it to get the same IP every time, there are 2 ways, both methods require the "bridged" network setting, regardless.

[https://www.virtualbox.org/manual/ch06.html#network_bridged](https://www.virtualbox.org/manual/ch06.html#network_bridged) as more details.

Oh - and welcome to the forums.

---

### Post by MAFoElffen on 2016-07-03
TheFu is correct, but just in case you need a more basic explanation--

The 2 addresses you noted in your post: 10.0.2.15 & 192.168.1.5 are on Networks NID 10.0.0.0 & NUD 192.168.1.0, respectfully. Networks with different network ID's would need a bridge or route to talk with each other. If you tried to ping your VM Guest from your host, it would fail, saying "No route."


If you use a bridge connection, you will be on the same network as your host and should be able to talk with each other. Understanding that, the TheFu's post will should make more sense to you.

---

### Post by warren55 on 2016-07-03
Thanks so much for pointing me in the correct direction.

---

