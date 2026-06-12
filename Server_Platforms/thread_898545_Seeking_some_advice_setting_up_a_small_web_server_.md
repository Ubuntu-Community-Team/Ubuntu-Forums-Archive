---
title: "Seeking some advice setting up a small web server ..."
date: 2008-08-23
forum: Server Platforms
---

### Post by mikey5555 on 2008-08-23
Hello all, 
I have loaded Ubuntu 8.04 server platform for the purpose of hosting about 10-15 domains.  These domains are very small, have limited activity and are "private", meaning they are the property of small fraternal organizations, clubs or "guilds".  They are mostly accessed only by members of said organization.  This is all hosted on a system using a DSL connection with a dedicated IP address. and my ISP providing DNS services for me.  

A little history: 
I currently host these sites on Red Hat Enterprise Linux "ES" 4.  It costs around $350.00/yr to keep the RH up to date and for "email-only" support, which is very slow, often no actual help, and quite often "off subject" suggesting alternatives which only cost more money, or looking elsewhere for assistance.  So.., I am moving on to a product I am using successfully in my desktop environment and getting very good support from it's user community - UBUNTU !!  I currently run Ubuntu Ultimate Edition 1.8 64-bit (based on Ubuntu 8.04 64-bit), and have almost completely abandoned Windows ( still needed for a couple of apps, and running in Virtualbox (VM software from SUN) on my UUE system).  

Now for my needs:
1: I want to host several small domains on Ubuntu 8.04 server.
2: I only have ONE dedicated IP address for the server.
3: I have been running these domains as "many-to-one", meaning they use  different NAT addresses on my server, but all requests and responses are sent via the ONE "real" IP address of the server.

Now, when I set this up on Redhat, I had all the "utilities" I needed to configure and setup this system available via a GUI which were installed by default.  I am only slightly familiar with the CLI of *nix systems.  At one time I ran a full service ISP using BSDI, which was CLI only, with the exception of a "new thing called Web Admin which was introduced just before I sold that business, so I have no experience with that interface.  I had LOTS of help in getting this system up and running, and kept meticulous notes ( which I can no longer locate)  on how to accomplish daily tasks, updates/upgrades, kernel configurations and compiles, backups, remote administration, etc.  I sold that business in 1999, and have not used any favor of unix again until about a year ago, when I discovered Ubuntu.  I do not have lots of experience in using CLI, and therefore was very pleased to find that Ubuntu has a very good GUI, excellent support community, a very good quality OS which seems to be very stable, and just about anything you could want/need to configure and run the system your way.  All that said, I need assistance with getting all the various parts of Ubuntu Server configured and running as soon as possible.  The current system is DOWN due to a minor drive problem, and the hosted domains are willing to wait for a few days, while I get a new system built, installed and configured, and back up and running.  
The 'new" system is built (Elitegroup PT800CE-A Motherboard, P4 2.4GHz processor, 1GB RAM, 160GB drive, nVidia AGP graphics card), Ubuntu 8.04 is installed, Ubuntu-desktop is installed (maybe something smaller or more appropriate for a web server should have been used for the GUI...??)

Now if someone could point me to some good documentation for accomplishing this task, I'd be very grateful. 
NOTE:  I was torn between using CentOS, a RH "clone" (?) that is supposed to be a direct replacement for RHEL (the commercial version) without the "branding", and using UBUNTU Server Edition.  I chose UBUNTU for many reasons, not the least of which is the support community associated with the product.  I can always go with CentOS if necessary, but would prefer to use UBUNTU, if I can get everything going pretty quickly.  

Sorry for the long, wordy post...  just trying to get all my bases covered....

Regards....

mikey5555

---

### Post by Iowan on 2008-08-23
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a starting point.
An [installation]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100") article.
A [serverguide]("dl2.foss-id.web.id/dokumen/ubuntu/serverguide.pdf") PDF.
Help on [WebMin]("https://help.ubuntu.com/community/WebMin")

---

