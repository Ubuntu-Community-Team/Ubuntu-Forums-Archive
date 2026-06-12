---
title: "1 static IP. Can I host a web site?"
date: 2007-12-07
forum: Server Platforms
---

### Post by cendant on 2007-12-07
There is one static IP address available from ISP

ISP  ->  DSL router -> Linux

The router takes the IP address, but gives dynamic addresses to LAN lile 192.168.1.x

Can I host a web site? 

I want to to type xxx.xxx.xxx.xxx in web browser and get into my server.

I set port forwarding and assigned static IP to the server, so when I type xxx.xxx.xxx.xxx from external machine, I get the web site.

However, ideally I want to setup up DNs for [www.mysite.com](www.mysite.com) and here is where I am stuck.

The server has LAN address. How can I type [www.mywebsite.com](www.mywebsite.com) and get to it?

---

### Post by az on 2007-12-07
> **cendant said:**
> There is one static IP address available from ISP

ISP  ->  DSL router -> Linux

The router takes the IP address, but gives dynamic addresses to LAN lile 192.168.1.x

Can I host a web site? 

I want to to type xxx.xxx.xxx.xxx in web browser and get into my server.

I set port forwarding and assigned static IP to the server, so when I type xxx.xxx.xxx.xxx from external machine, I get the web site.

However, ideally I want to setup up DNs for [www.mysite.com](www.mysite.com) and here is where I am stuck.

The server has LAN address. How can I type [www.mywebsite.com](www.mywebsite.com) and get to it?

You give DNS the ip address of the router.  You let the router forward the port to your machine in the internal network (lan)

---

### Post by mellowd on 2007-12-07
You sure can. As az said above, you need to forward port 80 to your webserver (or whichever port you choose, depending if you want this public or not)

DNS then needs to point to your external IP address. Forward the port on your router ([www.portforward.com](www.portforward.com)) to your internal webserver. Now anything that comes to your ip port 80 will go straight to your webserver

---

### Post by cendant on 2007-12-07
> **mellowd said:**
> You sure can. As az said above, you need to forward port 80 to your webserver (or whichever port you choose, depending if you want this public or not)

DNS then needs to point to your external IP address. Forward the port on your router ([www.portforward.com](www.portforward.com)) to your internal webserver. Now anything that comes to your ip port 80 will go straight to your webserver


Wow, that was quick! Thank you.

---

### Post by umattu on 2007-12-07
Heck, you can have multiple websites on 1 static IP!!!!

---

### Post by mellowd on 2007-12-07
Yeah, that would depend on the host headers, but you can run multiple different websites on the same server/port

---

### Post by cendant on 2007-12-08
My provider (MyDomain.com) allows to manage DNS, so I can enter A and CName records there

Do I need to run my DNS server or I can skip it?

---

### Post by cendant on 2007-12-08
How do you host your own web site?

I have done this:

1) Installed LAMP
2) Installed ISPconfig
3) The web site answers to the correct address: [http://86.43.126.137](http://86.43.126.137)
4) The web site does not answer to the   [www.drynov.com](www.drynov.com)

What am I doing wrong?

---

### Post by cendant on 2007-12-08
I am looking at [http://www.boutell.com/newfaq/creating/domainathome.html](http://www.boutell.com/newfaq/creating/domainathome.html) 

Maybe, it will help...

---

### Post by mellowd on 2007-12-10
> **cendant said:**
> My provider (MyDomain.com) allows to manage DNS, so I can enter A and CName records there

Do I need to run my DNS server or I can skip it?


You dont need to run it. DNS will be done to your ISP. Just make sure they update the A record to point to your external IP address

---

