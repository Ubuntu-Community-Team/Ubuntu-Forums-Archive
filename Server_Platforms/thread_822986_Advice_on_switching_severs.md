---
title: "Advice on switching severs"
date: 2008-06-08
forum: Server Platforms
---

### Post by lsutiger on 2008-06-08
My office will be moving into a new building we built in about 6-8 months. When we do this move, I've already decided to change our email domain - we were loose on the rules of personal use we we started hosting out own email and now we are getting spammed to hell (but it is managed w/ Spamfighter).

I got some wild idea that it would be a good idea to also change the server over to Linux. It is for personal growth in knowledge of Linux and the experience it will give me.

Here is what we are running now. We have a single server that is running W2k3 . We are using it as a domain controller with active directory, web server with ASP, mail server, and file server. We also use the Mailbee program for webmail - we have a lot of mobile employees. Using the Virtual SMTP server in IIS.

I plan on building and hosting the server here at home to play with it until I have it ready to transfer to the new building.

So, what I would like from all of you?? Where are the best tutorials on administrating Ubuntu server? Setting up Apache with ASP? Best webmail program? Best spam/virus scanning solution? Remote Desktop solution?

Having 6-8 months, I believe I can do this if I put a couple of hours a day into it with the couple of years I have been playing with Ubuntu/Linux.

Thanx in advance!!

---

### Post by Wharf Rat on 2008-06-08
lsutiger,
I am not sure Ubuntu is ready for this yet.   Don't get me wrong, I am an advocate of Ubuntu. I use it at home and on a couple of work machines.   I do think Linux offers a very good platform. I use IBM Nitix at work. The same server has been running over 4 years and I have only had to reboot 3 or 4 times. Except for upgrades.  Solid as granite.

Of course, it mostly depends on your level of technical expertise.

I have been working on a home server using Ubuntu.  It is a frustrating experience at best.    I had it working pretty good under 7.10  but I just had to upgrade to 8.04.   Ugh.  

Whatever, you choose, be sure to have it running good before it goes into a production environment.

---

### Post by lsutiger on 2008-06-08
> Whatever, you choose, be sure to have it running good before it goes into a production environment.

Thanx for the reply! I have 6-8 months to get this done. If Ubuntu isn't the answer, would Debian be the answer with all of my Linux experience being in Ubuntu?

---

### Post by nix4me on 2008-06-08
you can do 90% of what you need with any linux distro.  The long pole i see, is replacing active directory.  The only way to replace AD that I'm aware of is either switching to LDAP or using Red Hat Directory.  I am no expert on either so I'll leave that to the experts.

Fileserver and mailserver are easy.

---

### Post by spike_strip on 2008-06-08
NIS [Network Information Services]  can be implemented as a directory service.

---

### Post by freebeer on 2008-06-08
For security reasons, I wouldn't run the domain controller on the same machine as the web server/mail server.  That strikes me as exposing your internal network to the outside.

I use Ubuntu as my PDC (without AD - I don't need/want it) without issue (it's more stable than my Win2k3 server).  That has been a good choice for me.

My mail and web server are hosted elsewhere - partly because that's how it was originally set up, but partly for security reasons, too. So I really can't say how easy it is to maintain this stuff yourself.

---

### Post by promodus on 2008-06-17
> **lsutiger said:**
> My office will be moving into a new building we built in about 6-8 months. When we do this move, I've already decided to change our email domain - we were loose on the rules of personal use we we started hosting out own email and now we are getting spammed to hell (but it is managed w/ Spamfighter).

I got some wild idea that it would be a good idea to also change the server over to Linux. It is for personal growth in knowledge of Linux and the experience it will give me.

Here is what we are running now. We have a single server that is running W2k3 . We are using it as a domain controller with active directory, web server with ASP, mail server, and file server. We also use the Mailbee program for webmail - we have a lot of mobile employees. Using the Virtual SMTP server in IIS.

I plan on building and hosting the server here at home to play with it until I have it ready to transfer to the new building.

So, what I would like from all of you?? Where are the best tutorials on administrating Ubuntu server? Setting up Apache with ASP? Best webmail program? Best spam/virus scanning solution? Remote Desktop solution?

Having 6-8 months, I believe I can do this if I put a couple of hours a day into it with the couple of years I have been playing with Ubuntu/Linux.

Thanx in advance!!

Depending on your organization, downtime can easily cost far more money than saving dollars on purchasing licenses.

Having said that: There may be howto's to set up and configure a server, but when it comes time to troubleshoot if you don't know it well enough to run a server without a howto then take a second to evaluate your options.

As for the comment about Ubuntu not being ready, above. I disagree. 

What are your desktops? What OS?
What applications?
Mobile users... with laptops, smart phones?
How many users both mobile an non.

For spam: [http://www.spamhelp.org](http://www.spamhelp.org)

I prefer postfix as an MTA.

Your mileage may vary... There isn't always one right answer.

---

### Post by windependence on 2008-06-18
I recommed Zimbra as your mail server/collaboration suite. They have an exchange connector, or you can just use the Outlook connector or even switch them all to Thunderbird. If it was me, I would run all this stuff virtually on separate VMs on the one box and maybe have a second box for failover. Zimbra wants to have it's own box, and there is a pre-built VMware appliance for it that could have you up and running with mail in minutes.

nix4me is right, replacing all the functionality of AD might be challenging but I don't think it's impossible.

-Tim

---

