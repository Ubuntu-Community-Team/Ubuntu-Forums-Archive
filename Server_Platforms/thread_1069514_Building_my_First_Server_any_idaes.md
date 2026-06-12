---
title: "Building my First Server any idaes?????"
date: 2009-02-14
forum: Server Platforms
---

### Post by Dr Zin on 2009-02-14
So i thinking about building a "Home server".  (wait and here me out i know you are thinking ahead).  I want to have a chat service, file share, web page and a vlan.  I am clueless on where to start.

I know that I can setup an IRC channel off site.  But I would like to share files over the network with postings and to have a super privet network work and play on.  Oh yeah, i want access and have other user to access the network or web page or chat form out side the network.

Hardware I am looking to build a server box to do this with in the end.  I would like some direction on this as well.

Well its like a company's Network on way small scale. A nano site?

---

### Post by jimv on 2009-02-14
For what you're doing you don't need much firepower.  An old Dell Optiplex off eBay would be just fine.  I use one of their micro-towers for a server...1ghz and 512 MB of ram, though Ubuntu server rarely uses more than 100 mb.  Cost: less than $100.

Something like this would work great:

[http://cgi.ebay.com/Dell-Optiplex-GX260-Desktop-Pentium-4-2-26GHz-40Gb_W0QQitemZ120346931316QQcmdZViewItemQQptZDesktop_PCs?hash=item120346931316&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A0|293%3A1|294%3A50](http://cgi.ebay.com/Dell-Optiplex-GX260-Desktop-Pentium-4-2-26GHz-40Gb_W0QQitemZ120346931316QQcmdZViewItemQQptZDesktop_PCs?hash=item120346931316&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A0|293%3A1|294%3A50)

---

### Post by ugm6hr on 2009-02-14
EBox is bundled with Ubuntu in a single install CD:
[http://ebox-platform.com/product/use-cases/](http://ebox-platform.com/product/use-cases/)

---

### Post by hyper_ch on 2009-02-14
what do you mean by "chat service"?

---

### Post by ByteJuggler on 2009-02-14
For what it's worth, I run a server with:
- Teamspeak server for voice chat
- Trackmania game server
- MYSQL for hosting databases, primarily the records for the Trackmania server
- Apache web server + PHP for hosting websites 
- Several web interfaces to the other services (Teamspeak, Trackmania, MYSQL)
- SAMBA server for filesharing on my local network. 
- SSH server for remote access.
- NX server for terminal services type functionality from other local LAN clients
- Local MTA (mail server, in my case I use "postfix") which can send/receive email.  Set up to not relay obviously.  :)
- Various other bits n bobs (for example VMWare for hosting/testing XP and other Linux distro's)

Have been wanting to set up a VPN but haven't gotten so far as I've not really needed it - usually just use SSH or NX (which also tunnels via uses SSH).

As for hardware I use a Dell Vostro with 2.33Ghz Core2 E6550 and 4GB of DDR2/667 with 320GB 7200RPM disk as server box, it's way overspecced as it is for what it does, so that should give you an idea.

If you're looking for something similar then I'll try to help where I can.

---

### Post by Dr Zin on 2009-02-14
ByteJuggler 
>   Have been wanting to set up a VPN but haven't gotten so far as I've not really needed it - usually just use SSH or NX (which also tunnels via uses SSH).

Question is just having ssh as the remote client would work for Windows and MAC environments.

ugm6hr
 >  EBox is bundled with Ubuntu in a single install CD:
[http://ebox-platform.com/product/use-cases/](http://ebox-platform.com/product/use-cases/) iliky-------^

Well the dell seems to be some what a good idea. i needing lots of disk space for the movies and music other files indeed. 

The OS? Duh! Ubuntu But one the server build or the desktop. I think at less one of the 8.04 or 8.10.  you know I think 8.10 would be better.

So the Vlan part i have a router that "kicks ***" and could be set up for that but i guess there is no need for software on the server.

---

### Post by Dr Zin on 2009-02-14
OH Ebox! Nice :-)

---

### Post by ByteJuggler on 2009-02-16
> **Dr Zin said:**
> ByteJuggler 


Question is just having ssh as the remote client would work for Windows and MAC environments.



Not sure what you mean by this.  I access my Linux box from Windows using SSH (putty) and Macos will have not problem there.  Alternatively I use NX (for a GUI session) from Windows.  I don't know what you'd do there from Mac OS/X.  Can't remember if they have a client or not.  There are however alternatives.

---

### Post by wlraider70 on 2009-02-16
I don't know about you, but my first Linux project was a server. I started with the server version, but that doesn't have a GUI built in. After some frustration i reinstalled the desktop version, all networking programs will run on both.

---

### Post by R.Bucky on 2009-02-16
Well, I bought a new eMachines (I know they suck) for $468 including tax last year and have hosted a streaming media server (Jinzora2), WP blog, and Concrete5 CMS, SSH, VNC, Samba, Proxy server (Glype), and other cool stuff when I get curious, for the last year and a half. I have never had problems with memory, performance, or anything remotely close to hardware issues. Not to say that I have not made my fair share of stupid configuration errors (another story). You really do not need much. 

Upgrade the RAM to 2GB or so, but I rarely use more than 550MB even when streaming. I would advise that you create 2 partitions on your drive if no RAID. Use one for the OS and the other for your files. Trust me!

---

### Post by unixeducation on 2009-02-17
You could build a box yourself (buy the parts at Newegg or a similar source) and run something like VMware Server on it. This is what I do, as it allows me to run multiple operating systems concurrently on one machine. Different VPS nodes are for different purposes (one reverse proxy server, a couple of Debian web servers, an Ubuntu server instance that does various things, etc).

For a home network server designed to host VPS nodes, I'd get a dual-core processor, 4 GB RAM, and a beefy hard drive or two. Good luck!

---

### Post by Dr Zin on 2009-02-19
I have an idea what I am going to build it out of. I have installed ebox and working on the configuration of that. I have it installed on a virtual box ubuntu 8.10. Yup a fun learning curve. I have already screwed that up. I had internet and now I don't know why. I think once I have it configured to my liking I will share. 

But for the other parts on want it to will take some time. But I think about make a distro fork for a complete Home Server package. I am sure there are a few out there. I want make more useful to average Joe that that wants all his toys at his lazy figure tips. But just think a all-in-one box with roaming profiles, music and movies any where he or she goes. They can pull up there desktop form any in the home and any where they go. I know I grow in my pant a little to fast. But hey, I am dreamer.

---

