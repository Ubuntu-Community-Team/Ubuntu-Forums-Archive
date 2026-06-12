---
title: "Network Monitoring Choices"
date: 2008-04-19
forum: Server Platforms
---

### Post by Xiuh on 2008-04-19
I've recently downloaded Ubuntu Server 7.10. Although, I'm pretty much a Windows server guy, I really enjoy the open source packages in the Ubuntu community. In particular, I have an interest in network monitoring utilities. I originally intended to setup a small network monitoring lab using Zenoss. However, I saw Ubuntu server comes with Nagios 2.11. I've seen Nagios around, but I've never used it. Just looking for some feedback as to which title (you) prefer. 

Although, I'm looking for something that will provide good info back, I don't particiarly want to spend hours finding and tweaking MIBs. This is just a goof off project for me. I've never worked with either package, can anyone give me a heads up?

---

### Post by TuckLive on 2008-04-19
OSSIM is a good open source monitoring program.  Although it does or might take some tweaking it comes with nagios, snort, acid/base, nmap, and some others.  I was looking for something to goof off with also and found this.  It was cool to find an all-in-one deal.  Easy to get installed and running also.

---

### Post by geertn on 2008-04-19
Check out munin, really easy to install.

---

### Post by Xiuh on 2008-04-20
Just a follow up note on this. I pretty much spent all of yesterday attempting to get Zenoss setup. Although, I did get it setup successfully, I had a few things go wrong. Well to be honest, I think I was plagued by more than a few problems. For example, I had issues with daemons, Zenoss discovery services, setting up proper rights for the Zenoss user, mysql database build problems, and Python issues. I think I wiped the system and did a number of fresh OS installs, while following two or three different recommendations for installation I found on the web (including instructions found on the Zenoss Website). Never did get it working properly, pretty frustrating. I guess, I'll check out some of these other packages, as I'm pretty disappointed in the difficulty of setting up a very simple Zenoss core system.

Figured I'd be having a hell of a time configuring the reporting with this software, note the installation of it :|

---

### Post by Xiuh on 2008-04-20
I was starting out with Munin and Nagios. Can anyone point me to a "best practice" setup guide for Ubuntu Gutsy?

---

### Post by geertn on 2008-04-21
There is not much difficulty into setting up munin. Install it with its suggested packages and it will start polling localhost. Configure your webserver to be able to access its output directory and you're set!

Google shows up a lot of hits for munin+ubuntu.

As far as nagios goes, just read the docs and try to set up a simple ping test and you'll get started fast enough.

---

