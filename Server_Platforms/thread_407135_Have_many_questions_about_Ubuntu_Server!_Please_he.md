---
title: "Have many questions about Ubuntu Server! Please help!"
date: 2007-04-11
forum: Server Platforms
---

### Post by wvcaudill2 on 2007-04-11
Hello, I am planning on starting up a small web hosting business from my home. I would like to use Ubuntu Server Edition, but first I need to know the answer to these questions:

1) Will the latest version work with this server: [http://h71016.www7.hp.com/dstore/MiddleFrame.asp?page=config&ProductLineId=431&FamilyId=2465&BaseId=20097&oi=E9CED&BEID=19701&SBLID=](http://h71016.www7.hp.com/dstore/MiddleFrame.asp?page=config&ProductLineId=431&FamilyId=2465&BaseId=20097&oi=E9CED&BEID=19701&SBLID=)

2) Is the Ubuntu Server Edition a good choice for beginners who are constantly worried about security?

3) How exactly does the Server Edition work? Will Ubuntu Server Edition just add an account for a client when they signup and have paid? Or will I have to use some code for it? Does Ubuntu give me tools to monitore disk usage, client accounts, bandwidth, CPU usage, etc?

4) If Ubuntu is a good choice for the computer shown in question #1, how much space and disk space would be left if I installed Ubuntu?


Well, thats all the questions I have right now, answer quickly, and thanks in advanced for all your help!

---

### Post by WesRatcliff on 2007-04-12
You may be better off renting a dedicated server from a vendor that has the machine in a co-lo with redundant power and Internet connectivity. Most will even install some sort of web-based management software for you such as Plesk. This software will come with your web, mail etc already installed and **secured**. You still are able to have root access to the server if you want to install any custom software. It's the best of both worlds.

As a beginner with this setup, you will get all of the benefits of having your own server and it will be hosted (and sometimes maintained) by professionals that do this sort of thing every day - leaving you to focus on your hosting business' marketing and client relations. What you don't get is the headaches and frustration caused by downtime as well as the costs of maintaining the hardware and connectivity yourself.

Hosts like Media Temple and Rackspace come to mind as a couple that are just what you are looking for.

Wes

---

### Post by wvcaudill2 on 2007-04-12
That sounds pretty good, Wes, but what is the price? Just for incase I dont decide to do this, please everybody else answer my questions!

Thanks in advanced :)

---

### Post by wvcaudill2 on 2007-04-12
Rackspace wont work. The basic plan there would cost me $383 a month! I would rather just startup my own server at that price. So please, someone answer my questions!

---

### Post by MilesZS on 2007-04-12
One you install Ubuntu server, you have very little.  If you go with a LAMP install, then you will have Apache, MySQL and PHP ready to go out of the box, but you won't have any graphic interface to administer anything.  You'll have a command line.  You'll have to start there.

More importantly, are you going to run this out of your home?  What kind of Internet connection will you have?  Can you guarantee fast service?  Can you guarantee at least 90% up-time?  Do you know how to administer a server from the command line?  

Although I could administer a box in my apartment, I know that I would not be able to guarantee a lot of things.  I am going with a virtual private server (VPS), hosted by [Slicehost]("http://slicehost.com").  For $70 per month, I get 40GB space, a guaranteed 1024 MB of RAM, and 400GB transfer.  You still have to setup everything yourself, but they have many avenues for support, and their network service is more reliable than my apartment by a factor of 10 (fuzzy math).  

Ubuntu server edition is not an automated system.  You can't just add water and get a simple hosting platform.  It's work.  You can find many HOWTOs in the forums that will help, but they won't make you a system administrator.  

Good luck!

---

### Post by WesRatcliff on 2007-04-12
> **wvcaudill2 said:**
> Rackspace wont work. The basic plan there would cost me $383 a month! I would rather just startup my own server at that price. So please, someone answer my questions!

What you'll find in hosting (whether you do it yourself or pay someone to do it) is that you always get what you pay for.

Also, if you are shooting to host entry-level sites you are up for some very stiff competition - look at the pricing at bluehost.com for example... they make their money by having thousands of low buck clients.

If you are aiming to host mid to higher end sites, hosting from your house won't work for the reasons mentioned above.

I'd recommend finding a host that offers reseller services if you are looking to do hosting.

aitcom.net comes to mind as a cheaper host that does this, but remember you get what you pay for.

Wes

---

### Post by wvcaudill2 on 2007-04-12
Yes, I plan on running this out of my home. I looked at blluehost, and my prices would be much cheaper. My prices would be around $3 a month per customer. I plan on tailoring to the people who want a small package for their fansite or personal website. I would also offer plain image hosting for $3 too. I would only be planning on offering 100MB per account. I can offer customer support easily, since im online so much and I have a few friends that will help me. Here are my internet connection speeds:
• Incoming: 3008 kbps 
• Outgoing: 512 kbps 

I also have multiple firewalls ready to be installed for security too. As for the power, we hardly ever lose power, and if it gets to be a problem with too many power outages, i will buy a UPS. Unfortunatly, I know nothing about command line for Ubuntu. I know the cd for change directory though :P So, does this server work for Ubuntu: [http://h71016.www7.hp.com/dstore/MiddleFrame.asp?page=config&ProductLineId=431&FamilyId=2465&BaseId=20097&oi=E9CED&BEID=19701&SBLID=](http://h71016.www7.hp.com/dstore/MiddleFrame.asp?page=config&ProductLineId=431&FamilyId=2465&BaseId=20097&oi=E9CED&BEID=19701&SBLID=)


-------------------------------------------------------------------------------------------------


By the way, the ait.com site looks pretty good. Im nto sure what alot of the features are, but it is a definite option if I cant have my own server.

---

### Post by wvcaudill2 on 2007-04-15
hello, anybody there?

---

### Post by sheesh721 on 2007-04-15
Your connection is too slow to run a server and charge for it.  Also if you attempt to run a server on a home connection account you very often get your internet capped to dial-up speeds or dropped.  This of course depends on your host, but most out here would drop you.

a 512kps upload is practically nothing.  You won't be able to run a sufficient server from your box out of your house.  If you're serious about doing this I would do as suggested, either start with a VPS or get yourself a dedicated Box from a reliable host.

---

### Post by jorgerosa on 2007-04-15
For starting: (Only 1 PC, and just for tests)
**1** - Get any PC for server
**2** A - Get a static IP, and contract traffic, from your ADSL provider (Can be expensive here) or...
**2** B - Temporary static IP solution: [http://www.no-ip.com/](http://www.no-ip.com/) (ideal for tests or just fun - no costs - But a good 1st step) Example: [www.wvcaudill2.no-ip.com](www.wvcaudill2.no-ip.com) (Its a domain name pointing to your PC´s IP - You must configure it in their website)
**3** - Go!*****

***** Must configure Ubuntu server ( install desktop (to use firefox and web-based applications in that PC) just to learn). Start: serving HTTP (simple HTML pages: index.htm), then serving FTP (Try share contents with friends), then serving emails, then serving HTTP (dynamic pages: index.php with many MySQL databases), allways creating many different user accounts for each type of server, then be wild...

*"How exactly does the Server Edition work? Will Ubuntu Server Edition just add an account for a client when they signup and have paid? Or will I have to use some code for it? Does Ubuntu give me tools to monitore disk usage, client accounts, bandwidth, CPU usage, etc?"*

After Ubuntu server installed appears... Nothing!.. But its running in background. (You can install gnome or KDE on it - search for "server gui" on Ubuntu Forums) To configure your server with accounts, etc (without command lines) Try these web-based guis: [http://ubuntuforums.org/showthread.php?t=405574&highlight=server+guis](http://ubuntuforums.org/showthread.php?t=405574&highlight=server+guis) (read documentation on their sites)

Notes, just in case:
- Ubuntu (Apache) doesnt work with ASP***** and/or Visual Basic and/or MDB Databases (and other windows stuff)
*****There are "emulators" but none works 100%
- Ubuntu LAMP Server is: Linux + Apache + MySQL + PHP
**- Dont compromise yourself (in any way) with any clients, until you master the server itself! (Can took 2/3/more years, its your learning curve)**

Dont worry what others may say: Major hosts in the world started at home (or garage: Google) just for fun... 
About skills: Everything (how strange it may be) has a start.

---

### Post by wvcaudill2 on 2007-04-16
Im going with AIT, is this a good chouce, has anybody used them before?

---

