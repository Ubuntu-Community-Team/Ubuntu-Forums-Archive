---
title: "FTP Issue"
date: 2010-12-21
forum: Server Platforms
---

### Post by PHANTOM X on 2010-12-21
I setup a ftp server with Apache Tomcat and Webmin, but I'm having some problems with people connecting to it. It works fine on my end, but others are getting "This page cannot be displayed.". Checked my phone(needed something outside the home network)and comes up with Not Found The requested url at [http://192.168.1.43/](http://192.168.1.43/) was not found on this server. Apache Server at 192.168.1.43 Port 8090. Disabled ufw which didn't fix the problem.

---

### Post by wojox on 2010-12-21
Do you have a router and have you set up port forwarding?

---

### Post by slooow on 2010-12-21
Have you checked if your router has the corresponding port open to connect from the internet?

---

### Post by amauk on 2010-12-21
192.168 is your LAN IP address (internal only)

You need to use your external (ISP provided) IP address
You also need to set your router to forward ports 20 & 21 to the correct internal IP

---

### Post by PHANTOM X on 2010-12-21
Our router is isp owned. I think it has port 80 open. Not sure on 8090. :) I'll call in the morning.:)
 
Edit: Port 80 is opened. Shields up shows up to 10055 so it's probably closed. Most are closed

---

### Post by amauk on 2010-12-21
you can find your external IP address in a number of ways, but one easy one is here
[http://www.whatismyip.org/](http://www.whatismyip.org/)

---

### Post by PHANTOM X on 2010-12-21
Just made a quick decsion on getting a router Thursday/Friday as I don't want to have any problems with our ISP on enabling ports and would like control in my hands. I'll check back around then on my status.:)

---

### Post by PHANTOM X on 2010-12-28
Think I got it. Can I get someone to check this on their end? Thanks!:D


Edit Now it's not working on my end.](*,)

Edit: Link removed. PC going in the Recycle Bin....

---

### Post by amauk on 2010-12-28
A reverse DNS lookup on that IP indicates that it's a dynamic IP (meaning it changes, based on a rota)

If you want to run a server on your home connection, either get a static IP or use one of those hostname routing things (dyndns / noip / etc.)

---

### Post by PHANTOM X on 2010-12-28
I gave up on that pc. Old and seemed to have a lot of issues. Changed the new one to static(haven't got the external ip yet).

> 
#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.100
broadcast 255.255.255.255
gateway 192.168.1.1


---

### Post by PHANTOM X on 2010-12-29
External IP is [http://66.207.24.35](http://66.207.24.35)

---

