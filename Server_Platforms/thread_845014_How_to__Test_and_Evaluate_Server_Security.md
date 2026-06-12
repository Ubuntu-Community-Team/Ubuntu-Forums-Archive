---
title: "How to  Test and Evaluate Server Security"
date: 2008-06-30
forum: Server Platforms
---

### Post by Exception06 on 2008-06-30
Hi, I am currently undertaking a project for which I have to test, evaluate and compare the security of 3 different Linux Server Distributions.

I am new to Linux so any advice would be greatly appreciated.

I need to know how to best test these servers equally, using the same criteria for each - or as close as.  I have started by installing each of the servers and performing Nessus and Nmap scans on the default security of each of the servers which are;

Ubuntu Server, SuSE Linux Enterprise and RHEL.

these scans gave me mixed results..... anyone got any suggestions?  thanks in advance.

Exception06

---

### Post by mac133 on 2008-06-30
Hi! Here are some suggestions for you.
Using the power of virtualization, you can now quickly evaluate Microsoft and partner solutions through a series of pre-configured Virtual Hard Disks (VHDs). You can download the VHDs and evaluate them for free in your own environment without the need for dedicated servers or complex installations. Start now by selecting an item from the VHD catalog below.

Mac
____________________________________________________________
[http://fenderbluesjunioramps.com](http://fenderbluesjunioramps.com)

---

### Post by Exception06 on 2008-06-30
thanks but i dont think thats quite what i'm looking for.  I have a pyhsical network set up for which i have one server machine with hard drive caddy with all three servers distro's on seperate hard drives, i have a PC with Ubunutu 8.04 desktop on it, and a touch screen Kiosk with OpenSuSE10 on it (i need openSuSE10 as it supports the touch screen whereas 11 does not as of yet).

Exception06

---

### Post by calraith on 2008-06-30
Nessus and nmap would've been my recommendations.  You might also check out [http://sectools.org/](http://sectools.org/) -- specifically the sections for [vulnerability scanners]("http://sectools.org/vuln-scanners.html"), [web vulnerability scanners]("http://sectools.org/web-scanners.html"), and [vulnerability exploitation tools]("http://sectools.org/sploits.html").

I'm a little curious, though.  Weren't you expecting mixed results from the scans you performed?  Why compare and contrast different distros if they don't provide different results?

---

### Post by Exception06 on 2008-06-30
firstly, thanks for the reply, 

yes i was expecting mixed results, when scanning the same distros with different tools i got different results which is what i was expecting, for example, Nmap discovered the O/S of the Ubuntu server whereas Nessus did not.  I am just looking for some advice from someone who has performed a similar task in evaluating the different security aspects of different Linux operating systems.

I have been on sectools.org a number of times - its a great site but i couldnt find a guide for performing such things as penetration tests.  As i said, i am new to this so any help is greatly appreciated.

Thanks.  Exception06

after reading my first post I can see why you questioned my mention of mixed results.  just ignore my grammar, i wasnt meaning that my mixed results were an issue.

---

### Post by promodus on 2008-06-30
It all depends...

Are you looking for default configuration?
Is the system patched, how often is it patched?
What applications are involved, what services are offered?
What is the environment that this machine is situated?
How is the physical security?
What is the technical background of the administrator? Do you trust the administrator?

If you're looking for something to plug in and forget, then the machine will have to be unplugged. Security evolves on a variety of levels.

The main ones to focus on, if you're asking this question:
Check for an Active firewall to detect intrusion attempts. If someone port scans will that IP be blocked or null routed? If someone hammers a login to SSH, FTP, or any other service will they also be blocked after so many failed attempts.

Second, active configuration monitoring of some sort. Like Tripwire. Say, for example, that someone was able to change a file either by an undocumented exploit or by physical access the machine. Will you know that configuration has been changed?

Lastly if security is serious, audit's have to be done at some point. Every hack leaves a trail.

---

### Post by Exception06 on 2008-07-01
I am wanting to evaluate the security level of these servers in their default state and then again upon enhancing the security by using applications such as AppArmor and FireStarter.  As I am new to Linux there may be other, better security options that I have not yet sourced, also, as this will eventually become a penetration test I am looking for tools, preferably with a GUI to start, that I would use to perform such tests and possibly a guide of steps to take and how to go about each one - a kind of walk through guide if such a thing exists.

thanks in advance.
Exception06

---

