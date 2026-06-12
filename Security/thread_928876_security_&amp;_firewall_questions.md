---
title: "security &amp; firewall questions"
date: 2008-09-24
forum: Security
---

### Post by brandon88tube on 2008-09-24
Well I have been searching the forums and reading up on security/firewall related posts trying to understand it to the best of my knowledge. This has been an ongoing task for about a week now and I am finding it hard to understand all of it. I was wondering if someone could help me with a few questions I had as I tend to be paranoid about things and would like to try and understand what I am doing rather than just doing it. I feel more comfortable understanding what is going on and what things do.

1.How do I know which ports to open up/are good? I know I can open up port80 because that is http, but the rest are a mystery to me.

2.Lets say I wanted to use Transmission to download torrents, how well protected would I be against people trying to get into my system?

3.Is there an easy way to check activity so that I know if anyone else has been doing stuff on my computer other than me? < I am not worried about physical stuff because I am the only that uses this computer.

4.Anything else that comes to mind

---

### Post by hyper_ch on 2008-09-24
> **brandon88tube said:**
> 1.How do I know which ports to open up/are good? I know I can open up port80 because that is http, but the rest are a mystery to me.
By default, no ports are open as no service is running. Only when you start installing services you will open ports. If you have two computers, just nmap yourself to see what is open.

> **brandon88tube said:**
> 2.Lets say I wanted to use Transmission to download torrents, how well protected would I be against people trying to get into my system?
You would be as secure as transmission is coded.

> **brandon88tube said:**
> 3.Is there an easy way to check activity so that I know if anyone else has been doing stuff on my computer other than me? < I am not worried about physical stuff because I am the only that uses this computer.
Check the auth.log (and maybe other logs also)

> **brandon88tube said:**
> 4.Anything else that comes to mind
A firewall per se does not add any security because if you run a service you mostly want it to be accessible by anyone on the net. A firewall can limit as to who may connect to a certain service. For example block all incoming requests originating from country X or allow only incoming requests from country Y.

---

### Post by The Cog on 2008-09-24
Any port can be opened. Ports are opened by an application listening for incoming conections on them. A port is closed if no application islistening for connections. Web servers listen on port 80 by convention but can be configured to listen on any other port. 65535 is the highest port number. On unix, opening ports below 1024 requires root priviledge.

People also sometimes refer to a firewall blocking or permitting packets for a given port as opening or closing the port, but this is entirely different and shouldn't really use the same words because it causes confusion.

If Transmission is listening for connections from the Big Bad World, you are depending on transmission not having bugs that can be exploited by sending it deliberately bad packets. This is true of any application.

There are log files in /var/log, but they can be edited by the hacker of course. A good script will cover its tracks by removing the log trail. Look up root kit hunters, chkrootkit and rkhunter. Also OSSEC, although that may be overkill for you. 

Use good passwords, and keep your publicly accessible applications to a minimum.

---

### Post by brandon88tube on 2008-09-24
Cog, why would you say a rookit hunter would be overkill? Also what I really want to do is just have an easy way to be safe because I have ubuntu installed on my Windows partition through Wubi.

---

### Post by rustybronco on 2008-09-24
My interpretation of what he said...
> **The Cog said:**
> 
Look up root kit hunters, chkrootkit and rkhunter. 
**Also "OSSEC", although that may be overkill for you.** 
not to put words in his/her mouth...

---

### Post by brandon88tube on 2008-09-24
> **rustybronco said:**
> My interpretation of what he said...
not to put words in his/her mouth...

Yeah I guess I read that wrong. I will check up on rootkit hunters again... Still hard to understand all of this stuff.

---

### Post by The Cog on 2008-09-24
Yes, OSSEC **may** be overkill. It's a log analysis server that looks a events from multiple clients and emails alerts to you, although you can run client and server on the same box as a standalone setup. 

Rootkit hunters are not overkill.

---

### Post by brandon88tube on 2008-09-24
Ok I got chkrootkit and ran it once, but do I always have to manually run it in terminal? If not and it automatically scans does it notify me? I checked around these forums and on their site and I completely lost... I almost couldn't figure out how to run the program, which turns out is really simple. sudo chkrootkit

---

### Post by The Cog on 2008-09-25
As far as I know, it's a manual run when you feel like it.

---

### Post by hyper_ch on 2008-09-25
you can add chkrootkit to a cronjob and have the output mailed to you.

---

