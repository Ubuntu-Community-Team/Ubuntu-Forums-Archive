---
title: "Help setting up a simple webserver"
date: 2012-07-28
forum: Server Platforms
---

### Post by gudushen on 2012-07-28
Hi, this weekend I set out to make a simple webserver that is accessible from the internet. 
So far, I can only access it through LAN, so I have come here in hope of some help.
Using ubuntu desktop( i know :( ) with virtualbox, I install apache2 and run it.
I also made an account on [www.no-ip.org](www.no-ip.org) for ddns service and installed noip2 on ubuntu.
I port forwarded port 80 / 8080, also set DMZ for virtual machine.

Unfortunately, while the website name resolves correctly to my external IP, I get a 
"Grandstream Device Configuration" page instead of the default "It works!" page. 
Using the internal ip however goes to the "It works!" page correctly.

My ISP is rogers, so port 80 is probably blocked, I haven't found an open port so far 
with canyouseeme.org....

Any help would be greatly appreciated.:D

---

### Post by hesson on 2012-07-29
You may need to open up port 80 on your webserver. Try going to your router's page on your browser, and open up port 80. If you need to set up FTP or SSH, or some other service on your webserver, make sure to open up that port as well (i.e. 21 for FTP, 22 for SSH). If you don't know how to set up port forwarding on your router try [portforward.com]("http://portforward.com") to help you. Also, what is your domain name/IP?

**Edit:** I just realized you said you've already set up port-forwarding. Could you still provide us with more info on your domain name? Are you sure you have set up port forwarding correctly? You should be able to see that the port is free if in fact you have it set up correctly.
> 
port 80 is probably blocked

Not sure how that's possible considering most HTTP requests go through port 80.

---

### Post by BkkBonanza on 2012-07-29
What is this "Grandstream Device Configuration" page? Is that your router or not anything you own? Is it something your ISP perhaps owns? What port is that on?

OTOH, if you cannot find an open port with canyouseeme.org then you'll have a tough time getting thru to your server. Even in that case you can use a reverse tunnel but it kinda defeats the purpose since that requires an outside server to connect thru.

Many ISP's block port 80 but usually you'll find others open. It doesn't have to be 8080. You can use 1234 if you like. Try some random ones.

BTW you probably don't want DMZ for your server even if virtualbox. The point of DMZ is pass everything thru, hence the server becomes "open" demilitarised. You're safer just forwarding one port for http and leaving other traffic blocked at the router.

---

### Post by volkswagner on 2012-07-29
In order for canyouseeme.org port checker to work, not only do you need to have the test port open by your isp, it needs to be open on your router _and_ have a device/service listening on that port within your network.

---

### Post by sandyd on 2012-07-29
> **gudushen said:**
> Hi, this weekend I set out to make a simple webserver that is accessible from the internet. 
So far, I can only access it through LAN, so I have come here in hope of some help.
Using ubuntu desktop( i know :( ) with virtualbox, I install apache2 and run it.
I also made an account on [www.no-ip.org]("http://www.no-ip.org") for ddns service and installed noip2 on ubuntu.
I port forwarded port 80 / 8080, also set DMZ for virtual machine.

Unfortunately, while the website name resolves correctly to my external IP, I get a 
"Grandstream Device Configuration" page instead of the default "It works!" page. 
Using the internal ip however goes to the "It works!" page correctly.

My ISP is rogers, so port 80 is probably blocked, I haven't found an open port so far 
with canyouseeme.org....

Any help would be greatly appreciated.:D
You need to turn off your modem's remote interface

---

### Post by Cheesemill on 2012-07-29
Check this thread, especially my reply in post #14.

[http://ubuntuforums.org/showthread.php?t=2033584](http://ubuntuforums.org/showthread.php?t=2033584)

---

