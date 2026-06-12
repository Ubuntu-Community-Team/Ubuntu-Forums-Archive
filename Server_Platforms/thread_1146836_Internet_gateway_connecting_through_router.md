---
title: "Internet gateway connecting through router?"
date: 2009-05-03
forum: Server Platforms
---

### Post by SamuelC on 2009-05-03
(Yeah, the title sounds weird, as may seem what I'm trying to do.)

I'm stuck on dial-up in the middle of the boonies. Fortunately, I do at least have a second phone line, which makes thins a bit easier. What I've been doing for the last eight months or so is having one Windows 2000 computer running 24/7 to maintain the Internet connection and then use Internet Connection Sharing to shove the connection through to my router (Linksys WRT54GL), running DD-WRT. From there, the rest of the computers in my house can connect to the network, either via Ethernet or Wi-Fi. Yes, it's as brutal as it sounds, but it's better than only being able to have the Internet connected to one computer at a time, or worse, only having one Internet-connected computer.

For a while now, I've been utterly fed up with the Windows 2000 gateway, largely due to the difficulties presented by trying to forward port ranges with ICS (easy answer: not possible). Anyway, last... Wednesday, I think, I bit the bullet and installed Ubuntu Server 9.04 on a machine (after spending about six days downloading it on and off). Got a Conexant winmodem in it working fine after a bit, and set up iptables to do basic connection forwarding and NAT as per the [Internet Connection Sharing wiki page](https://help.ubuntu.com/community/Internet/ConnectionSharing). So far, so awesome.

So, my question:

Because I am obsessive about statistics and like tracking my bandwidth consumption with the shiny WAN status in DD-WRT, but I'd also like to start using the new Linux gateway to download large files overnight or when I'm not using the connection to save me from having another computer powered on, I'd like to put a second network card in the machine and force all its Internet traffic to go through that card (presumably eth1), through the router, and then back out to eth0 on the gateway, then through the dial-up modem (ppp0). I.e., eth0 should only accept traffic between ppp0 and the router; anything else requesting an external connection should be forced out eth1, which goes into the router.

How can I go about this? iptables packet marking by the router or something? And how would I set it up? There's piles of tutorials on setting up a gateway, but I don't think many are crazy enough to try something like this.

Thanks very much,

   --- Samuel

P.S. Sorry about the length of this post. I wasn't trying to write prose, honest! ;)

---

### Post by SamuelC on 2009-05-06
Nobody has any suggestions? In a way, I'm not surprised...

   --- Samuel

---

