---
title: "Need Help With Getting Server to Work as a Firewall/Router"
date: 2011-09-30
forum: Server Platforms
---

### Post by TheGuvernor on 2011-09-30
Let me start by saying I've tried doing research before posting here but everything I find is incomplete or dated. If I can figure out how to do this I will be more than happy to contribute a step-by-step how-to for Ubuntus support wiki.

I have a home network. The problem I have is my utility room is located in the basement which is two stories down from where I need wireless access. I've purchased several off the shelf wireless n routers. I've tried OpenWRT. I've tried sending my connection through the power outlets but for some reason I have MAJOR speed drops. 

On top of that I want apache (with dyndns), samba, openvpn, port forwarding and ssh. So my next best bet is to build a server with all of the above. I've purchased two nics and a multi antenna wireless card.  

I'm trying to figure out what packages I need to just get the basic router/firewall working with Ubuntu and let network machines log on. I know I could install gnome and the network manager then just tick share this connect but that doesn't give me the flex I need for the other servers and configuration.

All I've gathered so far is I need:
dhcp - to assign ip's to the machines on the network
ufw - for easy firewall config

What else am I missing?

I asked in the linux irc channels and it must have been Ubuntu hater day because I got no answers just a bunch of "Why are you using Ubuntu?" and on and on.

---

### Post by Dangertux on 2011-09-30
I would completely skip UFW all together, go with iptables for this, it ends up being a lot more intuitive if that is believable. You are correct you need dhcp if you want it to assign ip's to anything.  You seem to know where you're going with this I would really just suggest using iptables this is a decent and very explanatory guide, it's older but iptables hasn't changed that much so it should still be valid for your purposes.  [http://www.aboutdebian.com/firewall.htm](http://www.aboutdebian.com/firewall.htm)

---

