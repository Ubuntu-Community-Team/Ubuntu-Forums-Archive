---
title: "Storage space for a web server"
date: 2012-11-18
forum: Server Platforms
---

### Post by satimis on 2012-11-18
Hi all,

I'm prepared purchasing a 10G plan running a simple website advertising company service.  Following software will be upload to web hosting provider.

OS - Linux server
Web server - Apache2 or Lighttpd
Security - iptables
Web admin - Webmin
other relevant software for running a basic website.

User emails account limited to 10.

My question is whether 10G space will be sufficient?  Please advise.  TIA

B.R.
satimis

---

### Post by pkadeel on 2012-11-18
OS and softwares might occupy upto 4G. you have the rest of 6G for site content and email storage.

---

### Post by hawkmage on 2012-11-18
One thing that cane eat up space real fast are log files.  You should make sure log rotate is archiving/removing old logs.

---

### Post by Habitual on 2012-11-18
> **satimis said:**
> ...whether 10G space will be sufficient...

Not enough.

---

### Post by satimis on 2012-11-18
Hi all,

Thanks for your advice.

The storage space may not be a problem now.  Because I'm prepared to subscribe the 150G plan (instead of 10G plan).  The difference in fee is very small with only about USD3 per month increase.

I have following questions:

1)  The OS to run my website will be either Fedora 64bit or Ubuntu 64bit (both latest version).  Can I upload it to the service provider's website?  OR they alread provide the OS?

2)  Can I upload other applications(software) to their server for running my website?

Actually I no experience to upload applications (software) to Service provider server running my own website.  Where can I find relevant document to follow?

For remote access a server the experience I have:
Have the server installed completed and tested.  Then send the server to the datacenter

Please help.  Thanks in advance

Actually I'm able to run my own server at home.  I'm subscribing static IP with 8M/8M up and down speed.  Also I can upgrade to 100M/100M, fiber optic connection.  The difference in fee is only about USD35 per month without installation fees.  But considering the safety measure I cease the idea running a home server.  Because the server is running 7x24.  What about if there is no body at home and/or at night the server gets overheated and catching fire?  Therefore I stop running the server at home unless I solve the safety problem.

B.R.
satimis

---

### Post by Wim Sturkenboom on 2012-11-19
1)
Do NOT use Fedora; life cycle is too short. Far better to go for 5 year life cycle of Ubuntu

2)
A plan doesn't have to involve putting up your own server. In which case the 10GB is pure data storage (mail / database / files) and should be plenty.
I (co)host my site on a server with 250MB space.

---

### Post by satimis on 2012-11-19
The plan which I'm now considering is Deluxe on GoDaddy
[http://www.godaddy.com/hosting/web-hosting.aspx?ci=76393](http://www.godaddy.com/hosting/web-hosting.aspx?ci=76393)

Whether it is VPS plan or a dedicated server plan?

> **Wim Sturkenboom said:**
> 1)
Do NOT use Fedora; life cycle is too short. Far better to go for 5 year life cycle of Ubuntu

- snip -
Advice noted.

At the beginning with only 10G storage space I have been considering building my own Linux server OS, Harden Linux From Scratch.  Now with 150G space I'll install the ready-to-work Ubuntu Server, not to inject time building OS.  But I must clarify with GoDaddy whether they provide the server platform?  Or I can upload the platform to their server?

---

### Post by Wim Sturkenboom on 2012-11-19
Looks like this is co-hosting. You get a number of MySql databases while, if this was your own server, that number would be limited by MySql and not by the hosting provider.

So the only thing that you get in this case (economy, deluxe, ...) is space to 'store' your website / files, the option to create a few databases and store info in there and storage space for emails.

If they use apache, you get apache; if they use something else, you get something else. They take care of security (hopefully) when it omes to iptables, not you. They provide you with an interface for maintenance of your stuff (e.g. file upload, creation of databases and emailaccounts etc), not you.

Note that I did not go into the details that they might provide but that is how co-hosting works; for the website part of things, it's just another virtual host for apache. It's neither a virtual server nor a dedicated server.

---

### Post by satimis on 2012-11-19
Hi all,

After contacting GoDaddy it has been confirmed that Economy/Deluxe is Virtual Hosting plan. They're running Apache 2.2.13. I have been using GoDaddy registering Domain for 4 years.

I'll subscribe Deluxe, one month plan, to test. The max number of websites allowed on Economy is 10 and Deluxe 25 respectively. 10 websites is more than enough to me. Also 10G will be sufficient at the beginning. But Economy doesn't offer monthly plan, min 3 months.

I only have 2 simple website, one for advertising my company still running and another for my son advertising his knowhow on derivative, He is working in the stock department of a multinational bank. There is no online business

Actually it looks quite funny to me looking for web hosting service. I have all facility here capable for web hosting, fixed IP, 8M/8M up/down and 2 server boxes for testing. One box is running Oracle VirtualBox with 30 VMs installed and another box running RedHat KVM with 20 VMs installed. The VMs are Fedora/Debian/Ubuntu/Windows2008 servers, all working.

The problem faced by me is the heat generated on running the server 7x24. Even though they are headless server without display and graphic cards. Unless running the air conditioner round the clock I can't keep my server working 7x24. Therefore it would be better for me spending a few dollars per month looking for some place to host my websites.

---

### Post by marks_linux on 2012-11-19
> **Habitual said:**
> Not enough.

On what basis? Care to reason to allow the OP chance to make an educated choice

---

### Post by cariboo on 2012-11-20
I agree 10GB should be enough for what the op plans on doing. My 12.04 server uses about 2GB of hard drive space, this includes running mediawiki. I don't need a gui to administer the server, so I save a little over 2GB by not running one.

---

### Post by george897 on 2012-12-03
yes this web space and configuration is good enough to run your website properly, you can go with this configuration and getting out maximum from that for website result

---

### Post by satimis on 2012-12-03
> **george897 said:**
> yes this web space and configuration is good enough to run your website properly, you can go with this configuration and getting out maximum from that for website result
Thanks for your advice.

I'm now subcribing the Economy plan for 3 months.  It is a little bid funny to me.  I have to learning how to setup my website on their server with clicking around on screen, seemingly going back to MSWindows time.

On my server it is quite simple just loading all stuffs on /var/www/mywebsite/ after having Apache2 and relevant software configured.

B.R.
satimis

---

### Post by satimis on 2012-12-06
Hi all,

Thanks for your advice

I just found out that the Economy Plan of GoDaddy doesn't allow multi-hosting.  GoDaddy requested me upgrade to Deluxe Plan.  But I won't do that for the time being because;

1) Already prepaid 3 month subcsription.
2) I'm a little bid tire of clicking around on screen with mouse pointer without finding my solution.
3) GoDaddy support only provided reply not to my request, having exchanged numerous emails without result.
4) I have requested GoDaddy support about;
4a) I have 2 domains registered with GoDaddy say;
aaa.com (registered about 4 years ago)
bbb.com (newly registered)

The website is now created on aaa.com.  Now I want to delete it and recreate a new website for bbb.com because multi-hosting not allowed.  How to do it?  Up to now I still haven't received a sticking-to-point answer.

4b) If I retain aaa.com website, then how to point bbb.com to aaa.com.  So that when clicking bbb.com on browser it'll be directed to aaa.com

No YES or NO answer received from GoDaddy Support.


GoDaddy has a community forum but all questions have to be approved by the moderator before they can be posted.  Therefore I have no idea whether my technical questions can go through the moderator barrier or NOT.  Neither I have any reply received.

Any folk on this forum has experience on hosting website on GoDaddy please shed me some light?

TIA

B.R.
satimis

---

