---
title: "Windows 7 google chrome cannot connect to LAMP server"
date: 2012-05-05
forum: Server Platforms
---

### Post by LinuxLi on 2012-05-05
Hi all, just made a LAMP server on Ubuntu 11.10 which works fine. I can connect to it on a computer running windows XP but not on a computer running windows 7. Can someone please help explain some reasons for this?

---

### Post by darkod on 2012-05-05
By connect you mean open a website hosted on that server, or something else?

Did you try to ping the server IP first? Does it reach the server?

---

### Post by LinuxLi on 2012-05-05
I mean that when I try to open the website (brand new so its the default page) google chrome comes up saying connection was reset (Error 101) and I take that to mean it didn't reach the server. By the way the server is at home and running through the same router which the windows 7 machine is.

---

### Post by darkod on 2012-05-05
I assume you are trying to open it with the server IP address, right?

Otherwise, to work with a domain name you need DNS setup correctly.

And did you try to ping the server IP? doesn't matter that it's on the same network, something might be wrong. Try to ping it.

---

### Post by LinuxLi on 2012-05-05
I am using the IP address to connect to the server.

And sorry for being a bit of a noob, but how would I go about pinging the server?

---

### Post by LinuxLi on 2012-05-05
Nevermind, figured it out. 

Comes up saying Request Timed Out.

---

### Post by darkod on 2012-05-05
You don't have network connection to the server from that machine. Check the cable, check any firewall running on that machine.

Until you see a successful ping, no webpage will open of course.

---

### Post by LinuxLi on 2012-05-05
Ok, I've figured out what went wrong.

Somehow the ip address of the server changed, used to be 192.168.0.7 and is now 192.168.0.6. Any idea how that managed to occur?

---

### Post by darkod on 2012-05-05
If you have allowed the server to use dhcp the IP can change. That's why it's best to configure servers with static (fixed) IP. In case you want to, change it. I find the nano editor easiest to use on ubuntu server:
sudo nano /etc/network/interfaces

The syntax of a static IP is:
auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask x.x.x.x
   gateway x.x.x.x
   dns-nameservers x.x.x.x y.y.y.y (optional, but better to set manual DNSs)

Restart the server or the networking to apply the change:
sudo /etc/init.d/networking restart

---

### Post by LinuxLi on 2012-05-05
Thanks Darko

---

