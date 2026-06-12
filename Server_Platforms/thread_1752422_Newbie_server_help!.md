---
title: "Newbie server help!"
date: 2011-05-07
forum: Server Platforms
---

### Post by Jimbo999 on 2011-05-07
Hey guys, I'm trying to get a website up and running and have decided to host my own website from home as it will work out more cost effective for my business plan. I've got a lot of old hardware lying around, probably 4-5 pretty average computers computers and I'd like to link them all together into a web server. Could somehow please tell me how to do this? I'd like to be able to control it from one screen.

Thanks

---

### Post by kpholmes on 2011-05-07
how big of a website are you looking to post? unless your site is going to be doing **a lot** of database querys, or hosting a cool new crazy webapp, you are not going to need to link 4 computers together. even the people who do host that kind of stuff would rather get 1 decent machine. but none the less a webserver, which is jsut a program running on your machine, does not require much processing power. theres always exceptions, but i take it as this isnt a mission critical operation your doing here (because if you are you NEED to either purchase a dedicated hosting plan from a repeatable service provider, godaddy, at&t, etc.., or rent rack space at a data center and bring your own computer but let them make sure power is on 100%, and that your users are not getting bogged down by a slow internet connection.. like ur house probably unless u have fios or live in Sweden). anyways, just pick the best computer out of the 4, install ubuntu, install apache (sudo apt-get install apache), place all website files in /var/www/, assign the linux computer a static ip on your LOCAL network, forward port 80 to that linux's static ip. then thats it, go to whatsmyip.com or an equivalent site, find your external ip address, then put it into the address bar of your favorite browser and you should see your website (its not a bad idea either to check other browsers and see how your website looks) but that should be it. :popcorn:

---

### Post by stmiller on 2011-05-07
> **Jimbo999 said:**
> probably 4-5 pretty average computers computers and I'd like to link them all together into a web server. Could somehow please tell me how to do this? I'd like to be able to control it from one screen.

Thanks

I'd say keep it simple. Don't try to 'link' the computers together. Make one to be your dedicated web server. And leave it like that. :)

There is a web-based admin tool called webmin that is popular:

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by volkswagner on 2011-05-07
I would imagine your isp will be your bottleneck.  Most likely your uplink bandwidth would be the first to get saturated before modest cpu/ram specs.

Having 3 or 4 machines running 24/7 will consume considerable electric, especially if they are Pentium4.  Likely each box with hard drive will consume ~100Watts each (at idle).

If you really wanted this to expirement with, I'd recommend separating services, vs. trying to make your own cloud.

Perhaps use 3boxes, 1. Webserver, 2. MailServer, 3. DataBaseServer. 4. BackupServer.

Some reading if you like. 

[http://www.informationweek.com/news/software/infrastructure/221900737](http://www.informationweek.com/news/software/infrastructure/221900737)

[http://open.eucalyptus.com/](http://open.eucalyptus.com/)

---

### Post by Jimbo999 on 2011-05-07
Thanks for the advice. I have 10mbs upload speeds with my broadband, would that be enough for heavy traffic? Or am I going to have to get an upgrade?

Thanks again guys!

---

### Post by spy_1134 on 2011-05-07
My server is hosted on an eMonster 550
550Mhz processor, 64MB of RAM, etc.

It doesn't take a supercomputer.

---

### Post by tgalati4 on 2011-05-07
You can easily run all of those services on one machine.  Use one machine for Centos; one machine with Xen kernel master; one machine Lucid server; one machine open for what you learn from the other 3.

Many business/enterprise apps are configured for Red Hat/Centos.  Many neat/social apps are ready to run under Debian.  Learning Xen or other virtual machine can be helpful for running several distros on one box.  Running Lucid server allows you long-term support for those neat/social apps that are being developed.  The 4th box can either be a backup for one of the critical machines/services or something to experiment with after you have spent some time in the other three.

For power consumption, keep only one machine running 24/7 and set up the other machines as Wake-on-lan so you can boot them as you need them for development work.  

For instance, if your Xen machine is on 24/7, then it could be hosting:

Centos instance with its services
Lucid instance with its services

The other machines would only be powered when you are developing/testing Centos or Lucid services before migrating to "Live" mode.

You want to maximize RAM for the Xen machine, so you might have to cannibalize.

Once you've climbed that learning curve, go out and purchase some real server hardware.  Older Dell PowerEdge, HP Proliant servers can be found cheap.

---

### Post by kpholmes on 2011-05-08
> **Jimbo999 said:**
> Thanks for the advice. I have 10mbs upload speeds with my broadband, would that be enough for heavy traffic? Or am I going to have to get an upgrade?

Thanks again guys!

megabits or megabytes, 2 different things. is it cable or fiber? what is heavy traffic? do you have a specified amount of users, like organization or business might? or are you hosting a website where users can freely sign up? or where no logins are needed? all these things are important to know to find out what kind in internet connection and computer your going to need.

it really depends on what content your gonna be holding, a bunch of text and lo res pics with no logins, would be more then enough. if your consistently getting 10 megabytes up, and want to run a mediam size bulletin board with less then 1000 users, probably be good for that two, if your hosting a video streaming site you better look at some big bandwidth providers. 

also check out dyndns so you can point a domain name at your house.

---

### Post by Jimbo999 on 2011-05-08
After further deliberation I've decided to host the site through a hosting business with a dedicated server. 

However, for setting up and testing I'd still like to construct a "web server" at home. With a crossover cable, can I remotely control a second pc from my laptop and install server software on it and run it as my test web server? I don't have any keyboards, mice or monitors spare!

Thanks again guys.

---

### Post by volkswagner on 2011-05-08
You can install Ubuntu server edition with keyboard, and monitory attached.  Once the server is up and running you can have just the LAN and power cable connected and use SSH to administer the server.

How you connect the ethernet connection is up to you,  In my opinion it is best to have it connected directly to the router so no other PC's need to be on if you want the server up and running with network connection.

For the hour or so, you need the keyboard and monitor, I don't think you need to try and connect via a serial console or such.

I think you will find the majority of servers running by folks on this forum and elsewhere, the install of the operating system was the only time the PC was connected to a monitor and keyboard.

---

