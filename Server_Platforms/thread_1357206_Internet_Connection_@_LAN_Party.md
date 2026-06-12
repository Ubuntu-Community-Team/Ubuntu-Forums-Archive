---
title: "Internet Connection @ LAN Party"
date: 2009-12-17
forum: Server Platforms
---

### Post by fatslob222 on 2009-12-17
Hey Everyone,
 
I was wondering if someone could help me out here.
 
Basically, in jan next year i will be running a small LAN party, with a dedicated server.
 
The dedicated server currently is an installation of ubuntu 8.10, with all of the ubuntu desktop removed (all the gnome packages). I used the command found [here]("http://www.psychocats.net/ubuntu/purekdeintrepid") to do that, but i didnt install kubuntu packages after. I then installed gdm, xorg, xfce4, synaptic, xterm, firefox, gksu. So its a very lightweight system. On there is a LAMP installation, with a things like autominous lan party and tunez, plus srcds and cod4 servers etc.
 
The "dedicated server" is my laptop which has a gigabit network port on it. When i run the network, i will be connecting a cat6 cable from the laptops gigabit to a gigabit port on a cisco 48 port switch, which all the players will be connected to.
 
Obviously this means LAN will be working fine, but i also wish to introduce internet into this equation, which I would like to limit on the dedicated server (probably with squid?) so that people can only access certain sites+services. Onboard the laptop is a wlan card, which i would like to connect to a router in another room to provide incoming traffic for internet access.
 
How would i go about bridging these connections through squid or whatever it is i need to use?
 
I hope this makes sense!!
 
Thanks,
 
Harrison

---

### Post by holastickboy on 2009-12-17
makes sense to me!  I wish I could help you, but that's a little out of my league.  I think that the squid is a good idea though, I understand what it does, and it sounds like it fits the bill perfectly.  I am a regular at a website which has a substantial network orientation, particularly with Linux.  Check the documents there, it might have some stuff to do with squid in there: [http://linuxhomenetworking.com](http://linuxhomenetworking.com)

---

### Post by fatslob222 on 2009-12-17
Thanks,

I'll check it out and see what I can find, but so far not finding much.

It's confusing lol.

---

