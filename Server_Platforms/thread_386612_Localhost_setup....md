---
title: "Localhost setup..."
date: 2007-03-17
forum: Server Platforms
---

### Post by nevsie on 2007-03-17
new to all this linux server stuff... but working my way through reasonably well thanks to google.
However this one ha me stumped...

Setup server for static IP 192.168.0.13  everything is fine there, and when typing this address into browser or putty i the webserver or command line.

However, i now wanted to configure 'localhost' to equal 192.168.0.13
Therefore i edited /etc/hosts to do this... restarted networking... and hoped for the best!!!

However no surprises... nothing, still tries to get to 127.0.0.1. I am accessing command through putty from my laptop on the network, so i am assuming that dns is currently being handled by my broadband router... and hence why it is ingnoring the server setup... is his correct or am i really missing the point?

Any help gratefully received. explanations would help as well.
Thanks, N

---

### Post by nevsie on 2007-03-17
okay... getting closer... the /etc/hosts will only work for the relivant local machine... logically and kind of what i assumed. therefore i coul set this up on each network machine... pointless and time wasting... or i could setup a local DNS to resolve these things.... something i will inevitably do, just not yet... please say if i am right, wrong, missing the point

---

### Post by kidders on 2007-03-17
Hi there and welcome,

> **nevsie said:**
> However, i now wanted to configure 'localhost' to equal 192.168.0.13You shouldn't try to force "localhost" to resolve to an IP outside the 127.0.0.0/8 range. Almost every network-aware program ever written will take it for granted that "localhost" is on a loopback interface.

What are you trying to do exactly?

---

### Post by nevsie on 2007-03-18
thanks for the reply...
In short i am trying to learn as i have little experience in this side of things...

I run a normal PC network so when setting up the server it used DHCP and picked up an IP that matched our network range in the 192.168.0.###

Therefore i was looking to find a tidy way of addressing the server other than by typing an IP address. It is not critical, and i do not even know if it is bad practise to do something like this.

As i say above i am trying to get some experience in linux and running a server as currently i am a web designer and my hosting requirements are stretching beyond simple reseller hosting. Therefore if i go for a managed dedicated server i will need to be able to configure to my requirements, not matter how basic the changes i will need to make after the box has been setup for me...

===========================
on a seperate note, i am also trying to understand the best ways of setting up things like virtual hosting, ftp for each account, etc, etc. There is a lot of documentation telling you exactly what to do, when you want to make a change... however there is very little explanation of best practises (for security) and explanation of why you do something... So i worry that i might get soemthing working, but in a very bad way!!!

Look forward to advice, help, links t useful info. thanks, N

---

### Post by Mr. C. on 2007-03-18
Start leaning the basics of network and administration on *nix systems.  Having a solid grasp of the fundamentals is required before moving onto larger projects.

Review the course notes, and perform the lab work when possible:

[http://cis68a.mikecappella.com](http://cis68a.mikecappella.com)
[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)
[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by kidders on 2007-03-19
> **nevsie said:**
> i was looking to find a tidy way of addressing the server other than by typing an IP address.

Strictly, you should use a DNS/DHCP server combination to control addressing and resolution on your network. The trouble with that is that it takes quite a bit of work to set up, so people often prefer to add lines like "192.168.123.456 server" to every machine's /etc/hosts instead.

The word "localhost" is intended to be a name with which you can always address a machine from itself only, so it usually resolves to 127.0.0.1. Everything on a network tends to have a second IP, accessible from within the LAN (eg 192.168.123.456), with which you are free to associate a different hostname.

> **nevsie said:**
> i am also trying to understand the best ways of setting up things like virtual hosting, ftp for each account, etc, etc. There is a lot of documentation telling you exactly what to do, when you want to make a change... however there is very little explanation of best practises (for security) and explanation of why you do something.I know what you mean... too many options, and no real way of choosing between them!

If by "virtual hosting" you mean virtual *web* hosting, then Apache can handle this for you nice & cleanly. The setup is easy, and well documented. On the other hand, are you referring to hosting entire virtual server boxes?

My advice with FTP is *don't*. It's insecure, and not very featureful. Personally, I would suggest the SSH protocol instead.

If there's a specific decision you're having trouble making, or something in particular that won't work properly for you, let us know ... Mr. C. and I will be happy to help you.

---

### Post by Mr. C. on 2007-03-19
> **nevsie said:**
> ... i am also trying to understand the best ways of setting up things like virtual hosting, ftp for each account, etc, etc. There is a lot of documentation telling you exactly what to do, when you want to make a change... however there is very little explanation of best practises (for security) and explanation of why you do something... So i worry that i might get soemthing working, but in a very bad way!!!

The reason I gave you those links is that you seemed to be interested in ensuring that your systems are configured correctly and securely.  Many want simple cookbook recipes, and are flummoxed when things go wrong, or their systems are compromised.  You don't seem like this type.

There is very little explanation of "best practices" because it is not possible to do so without assuming the reader has a solid understanding of the fundamentals.  When one tries to write a best practices, the result is often another cookbook recipe that readers blindly follow.  On the opposite end, when one tries to explain *why*, the result ends up being a book.  The bottom line is that configuring and maintaining a server or any complex computer system requires a vast amount of knowledge.  I entirely reject the cookbook recipe mentality (they are good to get ideas, but that's it), and whole-heartedly embrace and teach the fundamentals.

Take it one step at a time, and build upon your knowledge.  Resist the temptation to try to install and configure everything all at once.

I hear the frustration; unfortunately, in today's computer world, the complexity cannot be avoided.

MrC

---

