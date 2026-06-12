---
title: "Webhosting Project"
date: 2009-05-21
forum: Server Platforms
---

### Post by Imamoomoocow on 2009-05-21
Hello everyone.

Myself and a few partners are in the process of starting a buisness, and we were hoping to create a website. While i know enough HTML and basic web design skills to produce a satisfactory page, I have absolutely no clue how i can host said page. Is it possible to host a website from my home? (i have a spare computer which would run well with the downloaded 9.04 Ubuntu Server iso i have. I also have a 15/15 mbps internet connection which i connect to through my router.)

If anyone knows how to go about this, or if it's even possible, the help would be greatly appreciated. Thanks

---

### Post by BkkBonanza on 2009-05-21
Just start with a simple hosting account. Doing it from your home is unreliable, will save barely any money, and is not the ay to go. Is it possible - yes, but there is a lot more configuring, your home line is not reliable, your home server likely doesn't have power backup, and you will have more heaadaches. Do you want to put your time into your business or into your web server admin?

Starting with an account hosted in a data center is very easy and cheap. You can use a shared hosting account for a few $/mo or if you need more control/functionality you cna go with a VPS account for $10-20/mo. If your site will just be a simple few pages of business info then use a shared account.

If you need specific hosting company recommendations then maybe check webhostingtalk.com - a well known popular forum aimed at these kind of issues and very good for help.

---

### Post by Imamoomoocow on 2009-05-21
Hmmmm...
But if I still wanted to do it from home, what would i have to do?

---

### Post by ad_267 on 2009-05-21
You'd have to get a static IP address from your web host, or use a dynamic DNS service like dyndns.com. You'd need to buy a domain name and set the domain name to point to your IP address. You'd have to install apache and php if you need it and forward port 80 from your router to your server. You'd need to install ssh or some way to transfer files to the server. I think that's about it.

---

### Post by BkkBonanza on 2009-05-21
Install and configure the server and LAMP packages.
Make sure that port 80 and/or 443 isn't blocked by your ISP.
Configure your router to port forward port 80 to your server. Maybe 443 as well if you need https.
Configure your DNS for your domain name to point to your public ip for your home account.
Setup a dynamic dns client (or config one on your router) to update your ip when it changes.
Install and configure other software like email server etc.
Upload relevant web site files and test.
Spend many hours learning about server hardening and security so that you don't accidentally have an open system and/or mail server.

Hope that your ISP isn't going to shut you down for running a server (that is generally against the policy of home type accounts).
Hope your power doesn't go down or someone doesn't pull the plug, as your site will be down too.
Hope your ISP doesn't have connection outages very often as your site will be down during those times.

Sounds relatively easy except if you haven't done it all before then it can take a long time and be quite frustrating. Decide your priorities, business or farting around with your home pet project.

---

### Post by Ittiger on 2009-05-21
Firstly check that you ISP will allow you to run a web server.  Some block Port 80 to prevent it.

Do you have a static or dynamic IP address?  Static is better but you can get around it by using a DNS service such as No-IP

Check that your router will allow you to set up a webserver in a DMZ zone.  This is a zone that is not connected to the internal network.

Then you have to set up the server - this should teach you a bit about setting up an ISP server: [http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3)

---

### Post by malikp on 2009-05-21
You have good advise how to setup web hosting at home. 

I did this and still I'm doing. But I move out all my important/ Heavy traffic websites to VPS and shared hosting accounts.
You have to spend hours/days learning to configure server and the network if you not    	 	 	 	 	 	  familiar with Linux, Networking, DNS etc.


If you going to setup mail server make sure you spend enough time learning and how to configure with mailservers. If you not you will end-up with millions of SPAM and you may become SPAM relay agent.

I think you could do this to develop your sites and show to others. 
Basically you will spend more time on Configuring Linux and other software, than  developing and promoting your website. 

My advice is go to cheap shared hoting account and same time set-up your server and learn about Linux and configuring Apache.
When you have lots of traffic you have enough skills to configure and mange a VPS.
Now days making a website very easy, but bring people very very hard.  So you need more time for other things than managing your server.

---

### Post by black_shadow on 2009-05-22
I have my own webserver. email and DNS at home running on Ubuntu 8.10, currently hosting 4 personal sites. as said before get a free dyndns account which allows 5 free domain names.

One major note as said previously most ISP will not allow you to run a Webserver if you have a home contract, some may allow if it is password protected.

Mike

---

