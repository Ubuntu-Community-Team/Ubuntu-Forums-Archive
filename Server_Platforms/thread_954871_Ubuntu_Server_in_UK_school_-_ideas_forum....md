---
title: "Ubuntu Server in UK school - ideas forum..."
date: 2008-10-21
forum: Server Platforms
---

### Post by recklessray on 2008-10-21
Hi there,

I'm a sys admin is a small high school in Bristol, UK. We use a Windows 2003 system with XP clients and  the traditional Windows Domain setup with HP Proliant domain controllers and a database server also running Windows 03.

Today was a fairly momentous day. I managed to talk my manager into spending £700 on a server, and the really interesting part was that he agreed I could put an OS other than a Microsfot one on it. This is a real turn around for him, he is very MS centric and thinks Open Source is "rubbish free stuff". Sigh.

Still, now I'll have a nice HP ProLiant DL160 G5 Intel Xeon E5405 Quad Core / 2GB / NHP SATA 160GB / DVD/CD-RW to play with. 

It'll be used for setting up a room booking application (not sure what yet) and some other applications to get staff using their laptops more and paperwork less. 

I have googled the above server a bit and it looks like there are issues with the NICs, and numerous people have suggested using Ubuntu instead. 

I'm more than happy with this. I have been a fan of this OS for a few years now, having used it on my home machines very successfully. 

What I want to throw out into the forum (aside from my joy at having made an opening for open source software in a major MS hogging environment!) is a request for ideas on how to get the most out of the server. Any ideas or experiences on using ubuntu server in a MS domain setting would be gratefully received. Also, I guess I will need a GUI so would it be better to install Ubuntu Server then use apt to fetch Gnome or just install the desktop edition?  Any other ideas or suggestions will be read and appreciated!

Ray

---

### Post by lykwydchykyn on 2008-10-22
Personally, I would start with the server edition, and if you must have a GUI install it piecemeal rather than the entire ubuntu desktop package.  Having a GUI on a server is acceptable in my book (though not everyone agrees), but frankly you don't need all the other nonsense that comes with a desktop (office suite, email client, RSS feed aggregator, photo management, blah blah blah).  It only means more stuff to download whenever you update.  

I put a GUI on my servers mostly because my coworkers get spooked if they have to do anything on a CLI-only box.  Put something simple like xfce or fluxbox on there.

Webmin is highly recommended for management if you want a GUI to manage your servers.

If this server is basically just going to serve web apps, I don't think you need to bother with a lot of domain integration or samba or whatever.  For starters, you might just want to read up on how to authenticate apache against the domain so you can secure your web apps that way. 

I've found that once you get a Linux box in the server room, and start to familiarize yourself with some standard server apps (apache, samba, bind, dhcpd, ftp, etc), it starts growing pretty quick; because Linux and FOSS have two advantages over (particularly Microsoft) alternatives:
 - It multitasks better and requires less resources
 - It's free and immediate: no waiting for licenses to be ordered, media to arrive, budget approvals, etc.

Sooner or later, every IT department experiences a need for some kind of server app.  Linux becomes the path of least resistance.  The only thing you need to follow that path is knowledge, so start tinkering now on some spare boxes in your spare time.

Finally, I recommend picking up a copy of O'Reilly's "Linux server hacks" volumes 1 and 2.  You can find them used online for about the price of lunch at a fast food place (and there's a lot more meat in the books).

---

### Post by jona7han on 2008-10-24
Hi Ray,

I work in a school in W.Yorks. We have the same setup as you but have 2 Linux servers running Ubuntu 8.04. I use 1 for a Web Server, Squid Proxy and Dans Guardian filter instead of Microsoft ISA. The other is used for backing up data and is also a room booking system (MRBS), I really recommend this to you as it's dead simple to use and teachers love it. We did have Moodle for our VLE but since moved on. I'm also considering using one of the servers for an NMS, maybe OpenNMS or Zenoss

---

### Post by teaker1s on 2008-10-25
webmin is a must-unless your hell bent on commandline.
superb that a schools are considering both a free and more reliable alternatives. how about some desktops with ubuntu for the students to try next.

---

