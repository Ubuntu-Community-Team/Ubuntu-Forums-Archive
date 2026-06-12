---
title: "Ubuntu Server"
date: 2008-03-19
forum: Server Platforms
---

### Post by SuperMiguel on 2008-03-19
Got my server today and installed ubuntu server on it, my set up is:

Router --> Server --> Desktop

Now, i have two network cards on the server (integrated connected to the router and a linksys pci network card connected to my desktop), the question is how do i set up the server for it to give my desktop a connection or ip??? like my desktop its not able to connect to the internet, so how do i set up that funcion so my desktop will have internet... thanks

---

### Post by cdenley on 2008-03-19
You can set up your server as a router or a bridge. A router will let you have an isolated network for your desktop computer. A bridge will forward traffic between the router and desktop transparently, and the IP address can be assigned by the router if you use dhcp. Is there a reason you want to put the server in the middle?

---

### Post by SuperMiguel on 2008-03-19
the only reason is to learn how to it. And get more security on my desktop.so i guess i have to set it as a router right? How do i do that?

---

### Post by cdenley on 2008-03-19
You need to set up NAT rules in iptables. I think firestarter can do this if you are using the desktop version. If you want to do it the hard way, it shouldn't be too hard to find a guide.

---

### Post by mreynaga on 2008-03-19
if you are going to setup your server to be a "router" meaning a DHCP server then you can ditch the router altogether and i would recommend it. meaning ISP-->server-->desktop. if you are going to setup remote access to your server in any capacity (ftp, web server) having 2 dhcp servers may mess things up. or you can turn off the dhcp functions on your router. 

install DHCP server with the folowing command:

sudo apt-get install dhcp3-server

then off you go

---

