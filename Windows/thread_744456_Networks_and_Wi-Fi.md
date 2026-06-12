---
title: "Networks and Wi-Fi"
date: 2008-04-03
forum: Windows
---

### Post by Living2007 on 2008-04-03
I'm getting a notebook with Wi-Fi built-in. And we are setting up a home network with Wi-Fi connection. Both the Wi-Fi are the same signal strength (802.11g).

I don't know how to accses shared folder and printers on the network from the laptop.

PS. Also, how do we make the network scecure enough so other laptops don't enter it?

---

### Post by superprash2003 on 2008-04-06
to access shared files you need to install a program called samba , you can install it through synaptic then to access any other pc's files go to places->computer and type smb://192.168.1.10 where 192.168.1.10 is the other pc's ip
.. to protect your wifi network.. you need to login to your router's settings([http://192.168.1.1](http://192.168.1.1) or 192.168.0.1 depending on your model) and you will find a wireless tab.. there you can enter a WEP key which is like a password to your network

---

### Post by Living2007 on 2008-04-06
I'm trying to SETUP the network through WINDOWS XP.

---

### Post by myusername on 2008-04-06
well the wifi modem should have an install cd which lets you secure the network through windows

---

### Post by superprash2003 on 2008-04-06
so you want to access files on the network from xp? if so go to windows explorer and type \\192.168.1.10 where 192.168.1.10 is the ip of the pc you want to access files from

---

### Post by Living2007 on 2008-04-07
I dont want to accses file, I can do that later, I want to know what steps to take to setup a network

---

### Post by superprash2003 on 2008-04-07
to setup a network, all your computers must be on the same subnet (like 255.255.255.0) and their ip should be almost same like if 1 pc has ip 192.168.1.10 then the other pc should get an ip as 192.168.1.x not 192.168.0.x ..make sure they can ping each other.. if they are successfully able to ping then you have a network..then you can use samba etc to share files

---

### Post by Living2007 on 2008-04-09
When I have my XP OS setup under the network, how do I add the second OS on my computer (ubuntu) accses the network.

---

