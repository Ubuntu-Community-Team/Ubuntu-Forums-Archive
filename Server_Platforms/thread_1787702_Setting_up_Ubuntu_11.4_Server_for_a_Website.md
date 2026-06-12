---
title: "Setting up Ubuntu 11.4 Server for a Website"
date: 2011-06-21
forum: Server Platforms
---

### Post by Greebe on 2011-06-21
Hello all.  I am new to the forum and was looking for some advice.

I was planning on buying a Dell Server to run Ubuntu 11.4 Server on for hosting my business website. It would be used on a cable modem through our home ISP. 

I have been using several hosting plans on the net and constantly have problems and pay a decent amount of money for poor limited service.

My website is small and fairly low traffic.  Most traffic is refereed or from Google product searches.  I need to be able to take payments through PayPal like I currently do, which directs payment to their site anyways.

I am not new to linux but I am new to Ubuntu and linux servers.  I had my MCSE back in early 2000 on the Windows 2000 OS.  I used Kubuntu for years both at work and at home up until a few years ago.

Any help getting set up would be greatly appreciate.  Things to consider, or guides would be welcome.

Thanks
Greebe

---

### Post by ruffEdgz on 2011-06-21
I wish there was just a single page you can go to to learn about setting up a website at your own descression but it isn't as easy as other would say it is. There is a lot of management not just on the website you are hosting but security concerns, future hardware replacements, etc... that will be different per user but here are some links that might be able to give you some ideas on web management:
---
[list]
[*]HowtoForge on setting up LAMP: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
[*]Ubuntu HTTPD: [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
[*]Ubuntu LAMP: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[*]Ubuntu Mysql: [https://help.ubuntu.com/10.04/serverguide/C/mysql.html](https://help.ubuntu.com/10.04/serverguide/C/mysql.html)
[*]Ubuntu Postgresql: [https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)
[*]Ubuntu Postfix (if you want to send and receive email?): [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[*]Ubuntu Firewall (for security): [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*]Ubuntu Amavis-new (more on security): [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)
[/list]
Sorry for the overwhelming number of links but I want to make sure you are aware of what make a 'good' local website happen.

**NOTE** You don't need to do everything mentioned above to make a web server. Just want to give you as much information about this as possible. **NOTE***

Cheers!

---

### Post by brettg on 2011-06-21
Use 10.04 LTS if this is a production server (unless you want to be restarting the server and doing dist-upgrades on a regular basis of course)

---

### Post by crispy_420 on 2011-06-22
I would use Windows Server 2008 R2 and IIS. Just kidding 10.04 would be my route and you have updates for another four years until April 2015.

---

### Post by Greebe on 2011-06-23
Haha... You said Windows:shock:

I started reading through some of the links that "ruff" linked too.  Thanks for those.  I still need to get through the rest of them and get some questions together to ask here.

Also the Dell server I was looking at was a PowerEdge T110 Tower Server.  I know that it is pretty basic but I would think for my requirements that it would be fine.  What do you guys think?

BTW.  Do you think it is too ambitious to want to set up my own server to host my website?  

Also I am downloading Ubuntu 10.04 as we speak.

Thanks
Greebe

---

### Post by Corlis on 2011-06-23
Heya, that server should be fine for a small website.

Technically, it's more than valid to use an own server that you have set up yourself, rather than a "websitehosting-thingie" (and we all at one point had one of those and gave up on it :P), especially Ubuntu Server is a good choice in doing so.

Where I think the problem lies, is the location. A full webserver running 24/7 at home, while possible, bears alot of risks. If it would be a normal webserver, an outtage of a few minutes probably won't destroy much, but when payments are involved, any failure can be quite a huge workload and problematic. Power-Failures, Modem corrupt, Hot/Cold temperature, Wife wanted to use that plug for the electric nailpolisher, ..., and of course environmental problems like dust, hairs and bugs.

Another solution might be a nearby data-center where co-location is offered (means you pay a little rent for the space your server uses up there, and it benefits greatly from perfect climatic conditions, reduntant power-supply, failsafe, ..., and of course a better connection).

It also would be possible, to rent a server somewhere and get Ubuntu 10.04 installed. It's usually quite a difference to the "websitehosting-thing".

---

### Post by haqking on 2011-06-23
> **Greebe said:**
> Haha... You said Windows:shock:

I started reading through some of the links that "ruff" linked too.  Thanks for those.  I still need to get through the rest of them and get some questions together to ask here.

Also the Dell server I was looking at was a PowerEdge T110 Tower Server.  I know that it is pretty basic but I would think for my requirements that it would be fine.  What do you guys think?

BTW.  Do you think it is too ambitious to want to set up my own server to host my website?  

Also I am downloading Ubuntu 10.04 as we speak.

Thanks
Greebe

10.4 not 11.4 for server IMO.

If you are MCSE then setting up servers and websites should be very easy as you should of done it before although with IIS, unless your MCSE was a paper one LOL ;-) so ambitious doesnt come into it, i prefer inquisitive to ambitious when it comes to Linux ;-)

The whys and wherefores are the same, just a different platform and how's.

Plenty of guides on LAMP out there (linux, apache, mysql and the 3 p's of programming)

---

### Post by craigcrawford114 on 2011-06-23
nginx + PHP5-FPM + MySQL. I do not agree with using Apache purely because of the terrible performance, resource demands and vulnerabilities. It's actually easier to setup than Apache too.

[http://www.howtoforge.com/installing-nginx-with-php5-and-php-fpm-and-mysql-support-on-ubuntu-11.04](http://www.howtoforge.com/installing-nginx-with-php5-and-php-fpm-and-mysql-support-on-ubuntu-11.04)

Also for the latest nginx version: [http://wiki.nginx.org/Install](http://wiki.nginx.org/Install)

---

### Post by Dangertux on 2011-06-23
For whomever mentioned accepting payments -- use paypal. 

You will not ever pass a PCI-DSS audit for a webserver in your home,  unless of course you build a concrete bunker for it in your back yard.  Just something to consider.

I also agree with what haqking said about 10.04 LTS as opposed to 11.04.

Ambition is good -- and Linux is a great place to have it. More importantly still is planning and preparation. With Linux anything can be made to work with the proper amount of forethought, perseverance and a little pfm.

Good luck!

---

### Post by garfonzo on 2011-06-24
I have a server setup to run a business website. The server sits in my garage running 10.4 LTS and is connected to a Business grade internet connection. I also have the whole thing attached to a UPS in the event of a power supply. 

Would I do it this way again? 

No. 

Were I to do it all again, I would go with Amazon's EC2 service, rent a Linux instance, and run the website from there. There are so many headaches I wouldn't have to deal with were the system running in Amazon's cloud. Sure, I haven't had any issues yet, but when they pop up (hardware failure, summer heat, extended power failures, someone breaking into my house and walking away with the server) I will always think, "I wish I set this up in the cloud". 

Of course, the cloud isn't perfect either, but for a small business it seems ideal. 

That's my tuppence.

---

### Post by Moneysworth on 2011-06-24
Also be aware that cable companies often monitor for and block server traffic on their networks. It is probably against their terms of service unless you buy a connection specifically for the purpose and that won't be cheap.

For less money/month I have my hosting with an almost local outfit that does it for a living. They all have English as a first language, I know them by first name, and if they lie to me I can drive over there and whoop hiney in the parking lot. The peace of mind is well worth it.

---

