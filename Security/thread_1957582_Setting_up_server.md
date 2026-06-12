---
title: "Setting up server"
date: 2012-04-12
forum: Security
---

### Post by iceshaft07 on 2012-04-12
Hey! This password still works! :-)


I have been tasked with setting up a server and deploying it out on AWS. This will be my first.

We are using an AMI (an image) to start our server in the cloud. We were warned that no security measures have been taken in securing the server.

As such, I am soaking up information like a sponge. I've run through the basic security guides on the community documentation.

I have:
disabled root access on SSH, 20 sec timeout, only allow 1 user, and using a .PEM file to login.

Configured AppArmor to monitor Nexus, which will be locked down after using it.

Installed emacs :-)

Configured ipv4 tables (Is there anyway someone can update the community docs? it wasn't apparent to me that I had two ip tables to manage, and that would have been a major security concern had I not noticed)

I ran Bastille and came out alive (is this actually a good tool?)

I installed RKHunter and ClamAV.

I skipped encrypting my home folder because theoretically nothing should be on it.  I also skipped encrypting the disk. We are on the cloud hosting repos, so I don't think we need to encrypt. CORRECT ME IF I'M WRONG!



Questions:

What else can I do? What is too much? (I know I need to install monitoring tools)

I was wondering if installing OSSec or Snort is really worth it?

How about Tiger?

How can I be absolutely sure that httpd, telnet, ftp, and mail are all disabled? (I checked netstat, they aren't running, is there anything else I can do?)



Any help is MUCH appreciated. I really just want this all to go smoothely.

---

### Post by kevdog on 2012-04-12
You can be sure they are disabled since out of the box Ubuntu installs no running services.  If you are super paranoid, you could configure your iptables to block outgoing or incoming packets for these listening processes.

---

### Post by iceshaft07 on 2012-04-13
Unfortunately, I did not set up this machine, so I don't know what was done to it ;-).



Any suggestions on Tiger / OSSec? Have these worked for you? How about Bastille and APpArmor?


It's one thing for me to run through the scripts on the community docs, but its another thing for someone to say "yes these work".

Thanks again!
-Rob

---

