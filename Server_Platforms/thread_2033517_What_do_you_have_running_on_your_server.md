---
title: "What do you have running on your server?"
date: 2012-07-26
forum: Server Platforms
---

### Post by Mr.Dee on 2012-07-26
What do you have running on your server?
 
I'm curious since I would like to do more with my home server.  So far some of the stuff I've been having fun with:
 
1) Logging in with putty from work.  I am able to get past the work firewall and use the lynx browser to browse the internet, lynx can be a bit weird at times, but most of the time it works just fine.
 
2) I also installed festival, so one day when my brother was staying at my place...  I made my computer talk from work and he was like WHAT THE WHAT....!  He thought the robot invasion had arrived.
 
3) dlna server that I start up if I want my bluray player to view some pictures.
 
4) Worked on asterisk, but not too much... might return to it.
 
5) installed terminal games, that's fun for remote stuff too.

---

### Post by LHammonds on 2012-07-26
> **Mr.Dee said:**
> What do you have running on your server?
Most all of my servers are virtualized on top of VMware ESXi servers.

Here are the ones I currently have up-and-running (see my sig for some step-by-step install dox for some of them):

MySQL server (Ubuntu 12.04 LTS, 64-bit)
MediaWiki server (connected to the MySQL server) (Ubuntu 12.04 LTS, 64-bit)
Nagios network monitoring server (Ubuntu 12.04 LTS, 64-bit)
Minecraft / CraftBukkit game server (Ubuntu 12.04 LTS, 64-bit)
Zimbra email server (and a test server) (Ubuntu 10.04 LTS, 64-bit)
Zentyal print server (Ubuntu Server 10.04 LTS, 64-bit)

I have one server that is installed directly onto a Dell PowerEdge 2950 server for the purpose of evaluating it as a potential virtual server (KVM, Xen, VirtualBox OSE)

My next personal home project will be a media server to replace my satellite DVR and DVD/BluRay Player.  I have chosen XBMC as the media server and currently researching what the best format (for me) to digitally store my movies, music and pictures.  I am also researching what machine will host all of it...like a low-energy and quiet netbook and some kind of mass storage system such as a RAID or mirror or something with the ability to store a decent amount of movies "online" and available and others in an archive state (sleeping drives) that can be retrieved and moved to the online storage.  It all depends on how the storage will be handled.

LHammonds

---

### Post by Mr.Dee on 2012-07-26
Oh man, that is a pretty sweet setup.  What hardware are you running vmware on?  I'm not sure my 1gig pentium IV can handle virtual machines, lol, and I would not want to run my main desktop nonstop, might be a power guzzler.

---

### Post by LHammonds on 2012-07-26
> **Mr.Dee said:**
> What hardware are you running vmware on
It is an IBM BladeCenter (H chassis).  The blades that are installed are 7870's which are 8 CPUs x 2.93 GHz with 100 GB of RAM for each blade (5 total).

Each blade easily handles about a dozen servers.  I have them spread out so that if any blade fails, the other blade(s) can take on the workload (which means none of them are running over 50% CPU or RAM.

LHammonds

---

### Post by Mr.Dee on 2012-07-26
So what you are saying is that it is slightly faster than my pentium IV?  :P

---

### Post by LHammonds on 2012-07-26
Just barely.:guitar:

---

### Post by ninadpchaudhari on 2012-07-26
> **LHammonds said:**
> Just barely.:guitar:

:D :D :D 

Btw, 
What is that powerful server needed/used  for  ??

I have my on a p IV and, used for ssh & most of the time  file sharing ( SMB, & FTP)

---

### Post by FatFrog on 2012-07-26
I got my mitts on a decomissioned PowerEdge 850. It's now running Precise with the following

*PLEX for my home media
*Oracle's VirtualBox (headless) with 12.04 running a few different distros as a test lab. (I don't run them all at the same time, usually just one or 2 for testing...)
*Samba for file server
*LAMP for studying/testing purposes

---

### Post by Mr.Dee on 2012-07-26
i guess it had not occured to me... the potential of running virtual box in a headless server. Thanks!

---

### Post by lisati on 2012-07-26
Mine's setup as a web host and email server, based around apache and postfix. 

I decided to host my own email server after growing dissatisfied with the way "free" email providers handled spam, helped on by my ISP deciding to use Yahoo (need I say more?) to provide its email services. 

A few years back I had some pages hosted on Geocities before the plug was pulled on the free version. Time and other priorities have taken precedence, so I haven't really kept up with them.

---

### Post by LHammonds on 2012-07-26
> **ninadpchaudhari said:**
> What is that powerful server needed/used  for  ??To run our business systems.  I won't go into detail as to what servers they are but there are a couple dozen specialized Windows servers.  We also have AIX.

The list of Linux servers I showed above are strictly non-critical systems that I brought up as an experiment to learn about and bring in Linux as potential business-class servers.

The more I get familiar with it, the more features I take away from Windows servers...if it works better.

LHammonds

---

### Post by psyllex on 2012-12-31
I only have two setup on as a web server and another as an email server.  I have a third server but haven't found anything cool to do with it yet....that Plex media server sounds like a good idea.  They are all pretty underpowered just P4's 2.8 Ghz (or something close to that) with 4GB of ram.

---

