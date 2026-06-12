---
title: "help with web page setup"
date: 2007-05-01
forum: Server Platforms
---

### Post by daugheg on 2007-05-01
hi all
I'm kinda new to linux but I can get around in it.I would like to know if any one kand help with setting up aweb site I just went to godaddy and got a domain name I have feisty server with gnome (I like to see what I'm doing)and I woulld like to set up a web site for just family so I can post pics nothing fancy but I would like to host it on my comp.
I have NVu for web page, I'm on lan ,comp is 2gig with 2gig ram
and I would like to know how to find out my ip address. ipchicken shows one thing and ip addr in terminal shows something else .
any help or links to step by step would be great
thank you for your time

---

### Post by jakev383 on 2007-05-01
> **daugheg said:**
> hi all
I'm kinda new to linux but I can get around in it.I would like to know if any one kand help with setting up aweb site I just went to godaddy and got a domain name I have feisty server with gnome (I like to see what I'm doing)and I woulld like to set up a web site for just family so I can post pics nothing fancy but I would like to host it on my comp.
I have NVu for web page, I'm on lan ,comp is 2gig with 2gig ram
and I would like to know how to find out my ip address. ipchicken shows one thing and ip addr in terminal shows something else .
any help or links to step by step would be great
thank you for your time
Are you behind a Linksys router or something similar? If the terminal is howing something like 192.168.1.101 then you're behind a router.
You'll want to use something like DynDNS.org then so when your IP changes your DNS name will update.
Lets get that all straightened out, then we can move to the actual; web page itself.

---

### Post by daugheg on 2007-05-01
I/m just on a direct lan line our internet pervider is ussonet ,like charter (tv phone internet ) all on fiber line
ipchicken shows 67.135.62.119
terminal shows smaller number 10.0.51.86
I got my web page made just dont know how to host it 
like I said I'm kinda new so I know it 's something simple that I'm not doing
thank for the lead will look in to it

---

### Post by jakev383 on 2007-05-02
Your provider is routing your IP address. You have the public IP (67.135....), but your cable modem/DSL/whatever is giving you a private IP (10.....). Private IPs are not what you want. If you have access to the router/cable modem/DSL and can do a port forward then you'll be good. Just open port 80 to point at your Linux machine. Otherwise you'll need to either get routing turned off or see what other options they offer. 
If you can't get any of that for whatever reason (price usually being the biggest) then you won't be able to run a web server from home that others can access.

---

### Post by daugheg on 2007-05-02
that just it I only have one box on side of the house were phone/internet/tv come out 
thanks for your help .I will call my provider an see if they can do anything

---

### Post by jakev383 on 2007-05-05
No problem. If they can offer some help by either dropping NAT so your PC gets  a public IP address or can tell you how to forward a port from the outside to the inside PC post here again (it's in my watchlist) and we can work on getting a photo site up for you. I do the same thing here at my house so this will be an easy one.

---

