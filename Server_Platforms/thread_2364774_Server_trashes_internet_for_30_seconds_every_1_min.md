---
title: "Server trashes internet for 30 seconds every 1 minute?"
date: 2017-06-27
forum: Server Platforms
---

### Post by capitalhitman38 on 2017-06-27
Hi ubuntu forums. I'm writing here for a problem i have. Whenever the ubuntu server starts my internet dies every minute for about 30 seconds. i've timed it and it happens like that every time.  It makes my internet crash completely as no page will load during the duration although voice chat data does get through but it is very choppy. im using the server to host games with friends and it disconnects everyone whenever the issue occurs, it doesn't always happen and on some reboots it works fine but i'd like to find out where the issue is coming from. Im a novice at ubuntu and even more of a novice at computer networking so i cant diagnose this myself. Thanks for any help. the version of ubuntu server i'm running is... 17.04

---

### Post by Michael_McKenney on 2017-06-28
A duplexing mismatch or speed mismatched can cause it.   Do you have the correct cable attached from the server to the network device?   What device is the server attached to?  What cable?

---

### Post by capitalhitman38 on 2017-06-28
> **Michael_McKenney said:**
> A duplexing mismatch or speed mismatched can cause it. Do you have the correct cable attached from the server to the network device? What device is the server attached to? What cable?

I currently have the server plugged into a 5 port netgear switch which is in turn plugged into my linksys main router which is connected to my ISP provided modem. not sure what you mean by what cable so im going to guess you mean what type of cable am i using to connect the server to the switch which is a cat6 ethernet cable. I tried plugging the ethernet cord into different ports on both the switch and server and i also tried replacing the cable with another of the same type but that did not help.

---

### Post by Michael_McKenney on 2017-06-28
Yes, the cat 6 cable.   That is perfect.  So you have your modem to the netgear to the server.    Is the netgear a gbps or 100 mbps switch?   Do you have the correct port on your modem connected to your network?  Does your modem do your DHCP for the server?   When I setup my AT&T modem as a pass through, I had to turn off settings in it.  My Fortinet 60E gets the IP of the modem on its WAN side via pass through.

---

### Post by Michael_McKenney on 2017-06-28
Do you have more than one IP address from your ISP or is everything NAT on your LAN side of the modem?

---

### Post by capitalhitman38 on 2017-06-28
> **Michael_McKenney said:**
> Yes, the cat 6 cable.   That is perfect.  So you have your modem to the netgear to the server.    Is the netgear a gbps or 100 mbps switch?   Do you have the correct port on your modem connected to your network?  Does your modem do your DHCP for the server?   When I setup my AT&T modem as a pass through, I had to turn off settings in it.  My Fortinet 60E gets the IP of the modem on its WAN side via pass through.

it goes ISP provided modem to linksys router to netgear switch to server, all of which are running at 100mb up&down. There is only one port on the modem which goes to the linksys router which is what does dhcp for the entire network. 

> **Michael_McKenney said:**
> Do you have more than one IP address from your ISP or is everything NAT on your LAN side of the modem?

I only have one IP address from my ISP and it is dynamic. Not sure what "NAT" means so i cant answer that.

---

### Post by Michael_McKenney on 2017-06-29
So you are running a 100 Mbps switch.   What is the server speed and duplex running?   Did you try setting them to 100 Mbps full duplex instead of auto / auto?   NAT is address translation from private IP to your public IP.   Does your server use DHCP or a static IP address?

---

