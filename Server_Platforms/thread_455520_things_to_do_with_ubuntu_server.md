---
title: "things to do with ubuntu server"
date: 2007-05-26
forum: Server Platforms
---

### Post by conanm4 on 2007-05-26
I'm going to be taking a networking class in college and then IT in university and have downloaded Ubuntu Feisty Server. Can I have some ideas on what to do to prepare me, I wanna go into this class knowing my stuff.

---

### Post by johnman145 on 2007-05-26
You wont learn anything usable for that class from just downloading an ubuntu distro and installing it. There is a lot of difference between the theory you get in class and how stuff really works. Unless the class is specifically about linux i wouldn't waste my time with linux if you are already very much familiar with windows or any other os.

---

### Post by dbott67 on 2007-05-26
> **conanm4 said:**
> I'm going to be taking a networking class in college and then IT in university and have downloaded Ubuntu Feisty Server. Can I have some ideas on what to do to prepare me, I wanna go into this class knowing my stuff.

I can speak from experience on this one: I taught networking at our local college for 5 years.  Of course, I was teaching when Windows NT 4.0 was just released & Netware 4.x was still king of the hill.

There are a few things to keep in mind about the program you're taking:

1. What is the objective of the course?  Is it to teach basic admin stuff for a specific OS (like Windows 2003 server & XP clients)?  Or is it more general?

2. What level of depth is the course teaching?  Is it a multi-year program that will focus on various aspects of networking (routing, security/firewalls, clients, servers, permissions, DHCP, Active Directory, Group Policy, applications (SQL, www, mail, etc.)

You can see that it can get quite complex and to become proficient you need to spend a fair amount of time in each area to familiarize yourself with the technologies involved.

Having said that, I would focus on the "bread & butter" of most networks:  file & printer sharing.

Setup a samba server with DHCP services, and configure the server as a router so that you can share a single internet connection with each client PC:
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Then, get a couple of PCs (Windows, MAC, Linux) and pop them on the network (set their networking config to auto/DHCP so that they request an IP from your server).

Setup some shared folders and a shared printer and see if you can get the clients connected & using the network resources.  If you can accomplish the above & have an understanding of what is happening, you should be able to apply that knowledge to whatever your instructors teach you.

-Dave

---

### Post by envis on 2007-05-26
the things that are fun to do with Ubuntu that i know of are:
run a website easily! [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)
enjoy a much more comfortable desktop system than windows.
have fun beeing a geek!!

---

### Post by conanm4 on 2007-05-27
Thanks for the suggestions.

---

### Post by dmizer on 2007-05-27
yes ... the problem with the term "networking" is that it's far too broad.

simply by connecting your ubuntu computer to the internet is networking.
working with bittorrent is networking.
using a router to connect multiple computers to the internet through one external ip ... is also networking.
configuring those computers to talk to one another is networking.
then there's domains, and directories, and services ... different architectures and protocols ... it just goes on and on.  and i haven't even mentioned security yet ... ugh.

i'll echo dbott67, if you want something to do that will help you get ahead of the game, set up a dedicated gui free file server to host shares to both ubuntu and windows.  that task alone should lay down the groundwork for a fundamental knowledge of networking.

---

### Post by elst on 2007-05-27
If you are trying to learn networking, be aware that Samba/Windows file sharing/CIFS was historically based on a different protocol to TCP/IP, and hence doesn't quite work like other stuff. For example, WINS was designed to do for CIFS what DNS does for the all the other network services. 

One other thing to watch out for with networking classes is that some still use the obsolete "OSI Seven Layer model", which purports to describe how networking operates. TCP/IP does not work like the systems that the OSI model was meant to describe, and since everything is now based on TCP/IP, the OSI model won't match up with the technologies that you actually use.

---

### Post by Alterax on 2007-05-30
Fun things to do with an Ubuntu Server.  (If your idea of fun is similar to mine).

1.  Create a file server.  Will come in handy.  If boring, use Apache, MySQL, and PHP to give a web interface.
2.  Create an inline firewall device.  Always good to do with cheap hardware
3.  Create a proxy server using Squid.
4.  Create a Network Intrusion Detection System using Snort, Base, and MySQL. (advanced but not hard)
5.  Make an application server, so you can use lower-power PCs and stream the application windows across the network.
6.  Set up a Jabber server
7.  MythTV.  Hardware investment but worth the fun.
8.  Get a couple of SIP-based IP phones and set up an asterisk phone system.
9.  Create a thin-client system. (bout the same as 5, really)

These should be a few fun projects, and trust me, you will learn a TON of stuff for your networking class.

--Alterax

---

### Post by misfitpierce on 2007-05-30
Friend of mine just took networking and programming and they taught him some Ubuntu and mainly windows things... Still surprised me that they gave him Ubuntu though... In fact I was so amazed I was baffled.... :)

---

### Post by Alterax on 2007-05-30
Baffles me too.  It's a good feeling, though...

---

