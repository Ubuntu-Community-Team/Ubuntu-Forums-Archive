---
title: "Why set up a server?"
date: 2008-04-16
forum: Server Platforms
---

### Post by Aeph on 2008-04-16
I have recently become interested in servers, but lack even the most fundamental grasp of what a server can do. Due to the popularity of Linux in the server world, I figured this was as good a place as any to learn about them. My initial question is this: what can servers do? Can they only be implemented in a local environment or can they host globally? I suppose the best way to put my question is this: what do you use a server for?

---

### Post by dcast on 2008-04-16
You can make a server do tons of things, on the top of my head I can think of: backup server for backing up your data, file server, mp3 streamer, bittorrent downloader, host a web page, etc etc etc.

---

### Post by sillyxone on 2008-04-16
My answer is a little bit in reverse of what you are asking. We replaced our Filemaker Pro database with a 3-tier web application but didn't want to spend money to try a new idea, so at first I put Apache, PHP, and MySQL on an old iMac running 10.3 (workstation version). So that's our first server. Last year, our demands and the web application grew big, so a real server was purchased from HP (about $4000), running the same deal: Red Hat, Apache with PHP, SQL. It has been handed to central IT to put in their server farm so I guess you only touch the real server if you are a big IT guy.

My laptop also has Apache, PHP and MySQL on Ubuntu for development so you can call it a server if you want.

To help sharing files between staffs, I also have a Mac server that serve files and authentication. All the Mac workstations connect to this server, users authenticate against its directory and have their home folders on the server. It also serve share drives to Windows users. We have a small number of staffs and little demand so the server is just an iMac with an external HDD for backup. This server also works as a Netboot server, so I can netboot the lab machines directly from it for imaging.

Personally, I don't have a server at home (except my laptop). For backup, I  rsync daily to my flash drive and weekly to a USB HDD.

---

### Post by volkswagner on 2008-04-16
To learn linux, and the command line.  When you install and configure a headless server, it forces some learning of the CLI.  It can make use of an aging pc to function as an, ftp, file, web, backup, etc. server.  There is the cool factor of having a [www.frommyhouse.com](www.frommyhouse.com) web page for the world to see.

The short answer for some may be if you have to ask why, you don't need one.  I more often than not get things I don't need.  Some things I just want.  :wink:

Be warned.  The wealth of information is endless.  You can get caught in trying to do too much at once.  A healthy approach would to decide on one function and concentrate.  The security topic of a public web server can have you researching for a long time.  You can go off into many tangents.  Some people run there servers in a virtual machine.  With virtual machines on can have several servers on one physical machine.  Yet another thing to learn.  I have yet to dive into VM.

For me it is just a hobby.  My most functional server is my master backend Mythbuntu machine.  This had little configuration on my end.  It is not headless and runs a GUI, but it is a database and web server.

---

### Post by garfonzo on 2008-04-16
I am  in the process of collecting information and researching to set up my own server for my home LAN. I hope to be able to do the following with my server:

- share a large collection of files across 3-4 computers
- stream media to any computer attached to my LAN
- access my files anywhere in the world through a website
- access my music and stream it to anywhere in the world through a website style MP3 player
- share a printer
- backup all computers on the network to one location (the server)

The machine I will be using was given to me (was on its way to the dump) and has low specs, but that isn't a big deal with Linux. A server can do a LOT of things, it really is up to you what you'd like it to do for you. 


Cheers,

Garfonzo

---

### Post by HermanAB on 2008-04-16
Web sites, forums (like this one), email, music and video streaming...

The list goes on and on.

---

### Post by hyper_ch on 2008-04-17
what makes you interested in servers anyway?

---

### Post by Aeph on 2008-04-19
> **hyper_ch said:**
> what makes you interested in servers anyway?

Dunno, new hardware? Just wondering if I could make use of one.

---

### Post by Iowan on 2008-04-19
> **Aeph said:**
>  I suppose the best way to put my question is this: what do you use a server for?I have a 6.06  LAMP server that I hope to use to learn more about Apache, etc.  My main server handles DHCP and acts as a SAMBA fileserver.  I have visions of setting up an email server on it and maybe even using it as an LDAP server.  At this point, I'm REALLY hoping NOT to host globally.  I learn best through my fingertips, so actually DOING something makes the learning process easier.

---

### Post by Dr Small on 2008-04-19
> **Iowan said:**
> I have a 6.06  LAMP server that I hope to use to learn more about Apache, etc.  My main server handles DHCP and acts as a SAMBA fileserver.  I have visions of setting up an email server on it and maybe even using it as an LDAP server.  At this point, I'm REALLY hoping NOT to host globally.  I learn best through my fingertips, so actually DOING something makes the learning process easier.
+1 there. That is the best way to do it, too.
If you plan to setup an mailserver, while not having it accessible from the internet, consider setting up a DNS server too, with bind9, so you can at least have a domain and use the DNS server for the entire network.

Dr Small

---

