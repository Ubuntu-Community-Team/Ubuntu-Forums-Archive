---
title: "WAN IP Address Wont Resolve"
date: 2010-02-18
forum: Server Platforms
---

### Post by terrapin893 on 2010-02-18
I will make this as short and to the point as I can.  I am experiencing, what I can only describe as . . . pure chaos when trying to resolve my WAN IP address. 

Brief explanation of my setup. 

Ubuntu Server 9.10, with apache, proftpd, mysql and the goodies. 

I have wordpress installed and setup under /var/www/

The LAN IP address resolves perfectly to the index.php 

However I can not get my WAN IP to resolve.  My ISP blocks port 80, so I have my router setup to forward port 81 externally to port 80 of my server.  I know the port forwarding is setup correctly and working, because I can go to websites like [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) and test that port 81 is indeed open.  

I also have DynDNS setup on my router and through an account with them, to update my IP address with any changes, to a host name.  But because port 80 is blocked I have to access it with, host.name.org:81.  Ive had this system up and running before with no issues.  Now I can not get the host.name.org:81 to resolve.  

Neither can I get my ip address xx.xxx.xx.xxx:81 to resolve.  

What the hell is going on here?

---

### Post by cdenley on 2010-02-18
Does it work from outside your LAN? Some routers will only port forward traffic received on its WAN interface. Also, establishing a connection is not "resolving" an IP. A hostname or domain name resolves to an IP. "Resolve" implies some sort of translation. It sounds like your domain resolves to your WAN IP fine, but you fail to establish a connection to the WAN IP from within your LAN. I don't mean to be a smart-***, just trying to avoid confusion.

---

### Post by rturner on 2010-02-18
Just a wild guess here, but do you have your hosts and interfaces files set up with the dyndns domain?  I have the exact setup as you and tried to connect from an external shell account using lynx and it worked on both ports 80 and 81.  Unless your router isn't forwarding somehow.

---

### Post by terrapin893 on 2010-02-18
cdenley --- you hit the nail on the head, thanks for the clarification.  It is resolving to the IP address but it wont make a connection. And I have tested this from outside my LAN, and no, it does not appear to be forwarding to the server.

rturner --- The setup was working . . . so I know Im going about it the right way.  But something just isnt jiving right now.  Im going to reset my router and re-configure that . . . and if that doesnt work I am going to check into  the hosts and interfaces on the server.  I was just too exhausted last night to do anything about it.

---

### Post by cdenley on 2010-02-18
You never answered if it works outside your LAN. Connecting to your LAN's web server using a WAN address from within your LAN simply will not work with many routers.

Since the port is apparently "open", this is the case. If you post your IP, I can verify that.

---

### Post by terrapin893 on 2010-02-18
You're right.  I thought I used to be able to do that with my router, but no. I can access everything from my blackberry.  Weird, I mean I can access it internally with my LAN ip, so there is no need, but just weird, I thought I used to be able to do that.

---

### Post by terrapin893 on 2010-02-18
OK, so an update.  

I had a html index page that loaded fine when viewed outside of my LAN.  But when I put a php page up (wordpress install) I could view it inside my LAN but when trying to connect outside of my LAN, I get a "Could Not Locate Remote Server" error . . . . . 

Im assuming this isnt an apache problem because I can view it on my LAN.  Any ideas?

Edit:  phpinfo file works, so I must have goofed somewhere on wordpress install.

---

