---
title: "So, how can turning one of my computers into a server benefit me?"
date: 2008-12-05
forum: The Cafe
---

### Post by NintendoTogepi on 2008-12-05
...

---

### Post by CholericKoala on 2008-12-05
Well, I have not done it yet, but I will log all the traffic in and out of my house.  You can make it into a web proxy server too.  I will also make a file server for backups no matter what computer I'm on anywhere in the house, and it makes printing very, very easy since you just need to connect to the server to print anything.  Other than that, I do not know.

---

### Post by dannytatom on 2008-12-05
Web server for testing (if you're into that)
Seed box for torrents
File server for backups

---

### Post by AndyCooll on 2008-12-05
The world's your oyster as far as a server is concerned. A server can be anything from something as simple as a file server to a media server, web server, email server etc.

I have two NSLU2's as servers. One is a file server and also runs rtorrent, the other is a backup server.

It's a matter of preference. It might not benefit you in any way. However (for instance) having all your files in one location able to be accessed by multiple pc's can be a benefit of a file server, rather than having multiple copies of a file.

:cool:

---

### Post by magmon on 2008-12-05
Im interested in this too. A friend of mine has a Mac mini, which is kind of like a REALLY small desktop. He says he'd sell it to me for like 50 bucks, should I buy it and make it a server? I think it has like 20 gb storage space.

---

### Post by dannytatom on 2008-12-05
For $50, I'd buy it.

[http://www.apple.com/macmini/specs.html](http://www.apple.com/macmini/specs.html)

---

### Post by damis648 on 2008-12-05
> **magmon said:**
> Im interested in this too. A friend of mine has a Mac mini, which is kind of like a REALLY small desktop. He says he'd sell it to me for like 50 bucks, should I buy it and make it a server? I think it has like 20 gb storage space.

For 50 bucks that wouldn't be a bad backup desktop.

---

### Post by Ralex1098 on 2008-12-05
I'm actually in the process of setting up a home server (old comp, has Xubuntu on it), but I don't know how to connect it all up. Does my internet run from the box to the server, and then the server connects to the hub which connects to the other computers? Has anyone does this before?

---

### Post by kindofabuzz on 2008-12-05
> **Ralex1098 said:**
> I'm actually in the process of setting up a home server (old comp, has Xubuntu on it), but I don't know how to connect it all up. Does my internet run from the box to the server, and then the server connects to the hub which connects to the other computers? Has anyone does this before?

Just connect your server to your router just like any other computer. No need for a monitor or keyboard, except to install the server OS. After it's installed, you can control it with ssh from any computer on the network. Or if proper ports are open, anywhere from the internet. Here's a good guide to get you started: [http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

---

### Post by Daveski on 2008-12-05
> **Ralex1098 said:**
> I'm actually in the process of setting up a home server (old comp, has Xubuntu on it), but I don't know how to connect it all up. Does my internet run from the box to the server, and then the server connects to the hub which connects to the other computers? Has anyone does this before?

I have this exact setup, and as I have a router I just connect the server to the router like any other machine. You would only put it between the internet and your home network if you wanted to use the server as a filter, a firewall and a router for the home network (note that the machine would need 2 network cards to perform this as 1 is connected to the internet and the other to your switch/hub for your home network).

For the original setup, to enable services accessible from the internet (such as a web server or ftp server) you need to find out how to configure 'port forwarding' on your router so that when a specific request comes in from the internet, the router knows to forward it to the server machine.

Does any of this make sense?

---

### Post by Ralex1098 on 2008-12-07
Yeah I think I understand it. Commands run from the other computers to the server within the network.

---

### Post by backupdevice on 2008-12-07
I use it as a Usenetbox and i host all my music on it

---

### Post by handy on 2008-12-07
I bought a couple of boxes from the local recyclers for $5- each early last week, one a Dell Optiplex GX150 - PIII 700/256Mb RAM/10Gb HDD, with a CD & floppy drive; the other a Cyrix 200Mhz/128Mb RAM/2.75 HDD, with CD & floppy.

Anyway I am using the Dell as a firewall & caching web proxy.  It has been a great learning experience for me, I've still got a lot more to learn as far as installing add-ons via SSH/scp & configuring them, but really if I never did another thing to it, it has already been worth it.

I am using [***_IPCop_***]("http://www.ipcop.org/"), it is a very mature distro' that is a dedicated firewall, it is really small, about 35k before any add-ons.  It uses squid for web proxy, but there is an add-on called [***_Advanced Proxy_***]("http://www.advproxy.net/") which is more configurable in that department, I have not installed that yet.

I have a thread going on this one if anyone is interested:

***_[http://ubuntuforums.org/showthread.php?t=998490](http://ubuntuforums.org/showthread.php?t=998490) _***

---

### Post by FuturePilot on 2008-12-07
> **AndyCooll said:**
> The world's your oyster as far as a server is concerned. A server can be anything from something as simple as a file server to a media server, web server, email server etc.

I have two NSLU2's as servers. One is a file server and also runs rtorrent, the other is a backup server.

It's a matter of preference. It might not benefit you in any way. However (for instance) having all your files in one location able to be accessed by multiple pc's can be a benefit of a file server, rather than having multiple copies of a file.

:cool:

I find this so handy. I go between a few different computers in my home and it's very convenient to have some of my files accessible from all computers via an NFS share that I have set up on a dedicated server. I also use it for backups of all the computers. The possibilities are endless when it comes to a server. There's so so many things you can do with one.

---

### Post by handy on 2008-12-07
I could spend $100- at the recyclers & get to work making a cluster of 20! :lolflag:

---

### Post by smoker on 2008-12-07
> **handy said:**
> I could spend $100- at the recyclers & get to work making a cluster of 20! :lolflag:

i love recycling centers, always bargains to be had, i'd advise everyone to find their nearest;)

---

### Post by RandomJoe on 2008-12-07
My favorite advantage of a server is that you can locate it anywhere - like in a back room, spare closet, what-have-you.  So you can make a behemoth with lots of drive space, good cooling, maybe lots of extra cabling (say for a couple of tuner cards for MythTV) and have it out of the way, where it's not annoying you.  Then on your desk you can have a small, quiet, unobtrusive system that simply accesses all the horsepower in the other room via network.  Or use a laptop wirelessly from the back yard to do the same thing! :biggrin:

I have a mini-server room in the walk-in closet of my back bedroom.  Poweredge server (gawd, those are noisy!) with 1TB RAID5 array (not so spectacular nowadays! :rolleyes: ), another desktop system with two tuner cards for MythTV, and an ancient castoff that is now my firewall - it has three NICs, I have my wired and wireless LANs segregated.

The server holds all my media - movies and music - so any computer in the house can watch.  It also provides backup storage via rsync, a central file store for things I work on from multiple machines, and runs ZoneMinder with a few network cameras around the house to watch over things.

---

### Post by billgoldberg on 2008-12-07
> **NintendoTogepi said:**
> ...

A media and file server are the most obvious uses for a server at home.

Stream media from your server to any network attached device (ps3, xbox 360, other computers, appletv, ...).

Put a file on the server and all computers can use it, thus you don't need to use usb sticks anymore to transfer data.

[I]I use my desktop as a media (mediatomb) and file server (samba and ssh), because it's on 24/7. 

You don't need to have a dedicated box for this if you don't have a spare.[/I]

---

### Post by Luke has no name on 2008-12-07
I use my server in my dorm as a backup for all my data, a testbed for other OSes (soon), a number cruncher when I don't want to bog my laptop, and a Samba server so I can access all my files from both Windows and Linux (soon).

---

