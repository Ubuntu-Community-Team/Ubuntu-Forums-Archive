---
title: "Make Ubuntu Server reachable through DSL Internet connection"
date: 2007-10-29
forum: Server Platforms
---

### Post by cendant on 2007-10-29
Hello, friends.

My PC has Ubuntu Server 7.10 installed and it has dual Gigabit Ethernet.

To one Ethernet I connect Ethernet connection of a DSL modem which connect to the Internet.

The Internet => DSL modem => Ubuntu Server

I want to run a web server on the Server and I want to create a small home network so the Server will also run a file server, mail server (that is what the second Ethernet connection for)

The DSL modem has DHCP, etc, and it provides one static address. 

How can I reach the Server from the Internet by typing that static IP?

Thanks a million

---

### Post by twistedtwig on 2007-10-29
you will need to open ports to which ever service you want to be publicly accessable.

i.e. web server port 80

ssh 22

mail 25

if you want dhcp for your computers INSIDE your home network you should look at dhcp and bind (there are other less complicated things to replace bind but I cant remember their names).

hope that starts you off

---

### Post by daengbo on 2007-10-29
Is the IP handed out by your DSL modem on a private or public subnet? Please post your IP here. You can leave off the numbers after the last "." if you like.

If your IP is on a private subnet, then you will need to figure out if your ISP gives private IPs and the DSL modem is forwarding the IP to your computer, or if the DSL modem gives out a number unrelated to your outside address. Either way, you're probably out of luck.

If your IP address is on a public subnet, then you need to get a dynamic DNS service and install a program to update it for you. I'd suggest dyndns.org and ez-ipupdate, respectively.

If you do this, you'll NEED a firewall, rootkit detection, and probably an intrusion detector like Snort and maybe Portsentry. Good luck.

This setup is great and convenient, and I've used it before, but it requires a lot of looking through logs to make sure someone hasn't rooted your box. My SSH logs were constatnly full of attempts to break in. My Apache logs were full, too, but with exploits for that "other" web server.

---

### Post by cendant on 2007-10-29
OK so

IP statistics:

IP WAN address: 86.43.126.xxx
IP Gateway:        159.134.155.21
Primary DNS:       213.94.190.194
Secondary DNS:  213.94.190.236

---

### Post by cendant on 2007-10-29
General
IP WAN Address: 	86.43.126.XXX
IP Gateway: 	159.134.155.21
Primary DNS: 	213.94.190.194
Primary DNS Name: 	dns1.cwm.dublin.eircom.net
Secondary DNS: 	213.94.190.236
Secondary DNS Name: 	dns2.cra.dublin.eircom.net

IP interfaces
Address 	Netmask 	Name
192.168.1.254 	255.255.255.0 	Ethernet 100BT
86.43.126.XXX 	0.0.0.0 	WAN vcc1

Network Routing Table
Destination 	Netmask 	Gateway 	Interface
0.0.0.0 	0.0.0.0 	159.134.155.21 	WAN vcc1
192.168.1.0 	255.255.255.0 	192.168.1.254 	Ethernet 100BT

Host Routing Table
Destination 	Netmask 	Gateway 	Interface
127.0.0.1 	255.255.255.255 	127.0.0.1 	Loopback
159.134.155.21 	255.255.255.255 	159.134.155.21 	WAN vcc1
192.168.1.254 	255.255.255.255 	192.168.1.254 	Ethernet 100BT
192.168.1.255 	255.255.255.255 	255.255.255.255 	Ethernet 100BT

---

### Post by cendant on 2007-10-29
[[IMG]http://img218.imageshack.us/img218/8251/screenshotnj0.th.png[/IMG]](http://img218.imageshack.us/my.php?image=screenshotnj0.png)

---

