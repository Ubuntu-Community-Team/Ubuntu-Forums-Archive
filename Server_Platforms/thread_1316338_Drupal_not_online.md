---
title: "Drupal not online"
date: 2009-11-05
forum: Server Platforms
---

### Post by baltadt on 2009-11-05
I have installed and set up my website the way I want with Drupal 6.x. Why can't I find it when I type in my IP address? Please any help, This is my first time setting up a server and website on my own.

---

### Post by unamanic on 2009-11-05
My understanding of the problem is that you can get to it via [http://localhost/drupal6/](http://localhost/drupal6/) but want to get to it via [http://localhost](http://localhost)

---

### Post by baltadt on 2009-11-05
No when I type the full address it gives me address not found

---

### Post by unamanic on 2009-11-05
Can you ping the IP?  Are you trying to get to it from another box on your LAN, or from the same box it's hosted on by typing the IP?  Are there any routers between you and the server that might be NATing the connection?

---

### Post by baltadt on 2009-11-05
My desktop(server) is pluged in to modem and I am trying to type in ip as [http://127.0.0.1:8080](http://127.0.0.1:8080).   Is this wrong? I typed ip address into terminal and it said "inet 127.0.0.1/8 scope host lo.

---

### Post by unamanic on 2009-11-05
unless you specifically configured it to listen on port 8080, then just try [http://127.0.0.1](http://127.0.0.1) or [http://127.0.0.1/drupal6](http://127.0.0.1/drupal6)  Although 127.0.0.1 is not your IP address, it's the loop back interface (the equivalent of typing localhost).  you can get you IP address by either rt clicking on the network manager applet and selecting connection information or by typing ifconfig on the command line.

---

### Post by baltadt on 2009-11-05
ok that worked. ty so much

---

### Post by baltadt on 2009-11-06
ok so now I have a new problem to overcome. How do I allow people that are not connected to my network access my website?

---

### Post by unamanic on 2009-11-06
That depends a lot on your network set up and your internet service provider.  

First, if your are using a router or DSL modem, your machine likely does not have an external IP address.  You can check this by doing an ifconfig from the command line.  If it says that your IP is 192.168.something or 10.something, then you are on an internal network and you'll have to use your router's web interface to forward traffic on port 80 to your computer's IP (if it's not one of those two your're ok no port forwarding needed).  

Some of them have presets for this. Once you have this set up you'll be able to have your friend go to your website by typing in your external IP (the one your ISP gave your router or DSL modem).  Some ISPs block port 80 inbound so that people cannot run webservers from a residential connection, if this is the case, you'll have to move the service to an nonstandard port.

Once you've tested with your external IP from outside your LAN (you can use  [http://browsershots.org/](http://browsershots.org/) for this).  You can set up dyndns.org so that you have a url like baltadt.is-a-geek.com.  Some routers have configurations for dyndns, if yours doesn't you'll have to install a client on your computer.

---

### Post by baltadt on 2009-11-06
ok which ip should I use? this is from my modem ip address. 
System Type:	  	Gigaset SE567/8 Series
High Speed Internet Connection Information:	  	UP
Router IP Address:	
WAN IP Address:	  	
Firewall:	  	
Config Part #:	  	
Firmware Part #:

---

### Post by unamanic on 2009-11-06
Your external IP is your WAN IP address.  This is the IP that anyone outside your LAN must use.

BTW: you want to edit your post and mask that out so that you don't have a bunch of script kiddies trying to hack you.

---

### Post by baltadt on 2009-11-06
ok so when i access it from local I type 192.168.etc/drupal and it loads fine. but how do I get it redirected from external ip to website?

---

### Post by unamanic on 2009-11-06
Each router/modem is a little different, but most of them have you point your browser at router ip address.  You might be propted for a userid and password for the router.  If you don't know this already, either look throuogh your documentation or google for the default.  You'll then need to set up port forwarding.  If it's not obvious, google your router's model number + port forwarding and it should come up with something.

---

### Post by baltadt on 2009-11-07
ok ty for being pacient with me.

---

### Post by unamanic on 2009-11-07
No problem, but I'm out for the night I'm in FL and it's past midnight.

---

### Post by baltadt on 2009-12-20
Ok so I figured this out. I was typing /ctlscript.sh start when I should have been typing ./ctlscript.sh start. That was my problem.

---

