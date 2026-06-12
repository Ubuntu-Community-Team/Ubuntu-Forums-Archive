---
title: "Apache2 Serve unaccesible from public IP"
date: 2011-07-10
forum: Server Platforms
---

### Post by snype360 on 2011-07-10
Hello, I know this is probably a simple fix, but I cannot seem to find any fixes through google.  Any help would be greatly appreciated.

I installed apache, PHP, and mysql on ubuntu 11.04 and the webpage that I set up is accessible from within my home network, but when I try to access the server with the public IP address.  An authentication prompt pops up.  I have set up port forwarding for my router to the webserver.  I even tried setting the server as DMZ to troubleshoot and the password prompt still pops up when I try to use the public IP.  

Does anyone have any suggestions on how to fix this issue?  I never set up a password and username to access the server.

---

### Post by NZReaction on 2011-07-10
You can't usually access your public IP address from home without tweaking a few things.  If you want to test whether or not you can access your website from the web try open a proxy site and enter your IP address. :P

---

### Post by rswitzer on 2011-07-10
First, make sure the problem is not your router not letting a query reach the server from outside. If that is not the problem, type: " gksudo nautilus " in a terminal window. This command will let you have root admin privileges  for your file system. Go to usr/www and examine the read /write privileges of your web file you are trying to open. Make sure that it at least has read privileges for others. 

I set up a new 11.04 server last week, that's all I remember doing to get it going.

Good Luck!

---

### Post by NZReaction on 2011-07-10
> **snype360 said:**
> Hello, I know this is probably a simple fix, but I cannot seem to find any fixes through google.  Any help would be greatly appreciated.

I installed apache, PHP, and mysql on ubuntu 11.04 and the webpage that I set up is accessible from within my home network, but when I try to access the server with the public IP address.  An authentication prompt pops up.  I have set up port forwarding for my router to the webserver.  I even tried setting the server as DMZ to troubleshoot and the password prompt still pops up when I try to use the public IP.  

Does anyone have any suggestions on how to fix this issue?  I never set up a password and username to access the server.

The authentication prompt is most likely your modem/router responding to your http request.

---

### Post by ian dobson on 2011-07-11
Hi,

If you can change the port used by the router for its admin interface (For example 81) and then forward port 80 to port 80 of your server.

Regards
Ian Dobson

---

### Post by snype360 on 2011-07-11
How can I change the port my router uses for it's admin interface?  

After looking at it more, I believe it is the router/modem responding to the HTTP request.  Because when I click cancel to not enter a username and password, the denied access page is the same layout for the denied access of my routers admin page.  Is there a way to get around this?

---

### Post by ian dobson on 2011-07-11
Hi,

Just log into your routers web interface and look for the option something like admin interface port, at the moment it's 80 change it to something else (81). After changing it you need to use [http://ip_address_of_router:81](http://ip_address_of_router:81) to access the admin interface of the router.

Once thats done you need to go to the port forwarding screen and configure port 80 so that it's forwarded to the ip address of your server.

Regards
Ian Dobson

---

