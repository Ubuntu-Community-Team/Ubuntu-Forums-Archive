---
title: "Starting a web forum. First server and first forum."
date: 2011-03-26
forum: Server Platforms
---

### Post by Cyrus11 on 2011-03-26
Hey everyone.

I'm really interested in starting a forum on the internet using a linux run server. Here's the catch...I have no serious programming skills and I know nothing about servers or how they work and crap like that. I'm a 20 yr old kid so that would explain a lot. 

Here's why I want to do this:

I have been pretty active on a forum on the internet. One major section is about the low activity on the forum. No newcomers and those that do come, quickly leave. They've suggested advertising through ads and digg and stuff and redesigning the site. Problem is, none of the mods can contact the site/admin/owner. He just renews the domain every year.

 Well I want to design a forum with the same thesis for discussions. But better than the one that is having problems. Then the active users from the other forum can come to my forum which I will design and advertise via social networking sites and ads and word of mouth and so on...you get the idea. But basically the other site isn't vague enough in topic to generate a lot of activity. And the design is pretty sad. So basically it's competition here. 

I just want some serious pointers in the right direction of what I need to learn what programming languages I need to learn and whatever else entails. Pretend I'm just plain stupid. Though I have been using linux for about a year now so I am somewhat familiar with the types of commands and I have customised the kernel on my laptop via copy and paste from other threads to get my hardware working on my laptop. But that's it. 

Also as a very first priority: how to get a decent server at a decent price to run a website forum? What is considered powerful enough as a beginner? 

Second: Buying a domain. Can someone explain it?

I will be checking and replying on this thread often once I get a server and buy a domain. At least once every two days because I work night shift. 

Please help guys. I'm really interested in this.

Cheers,
Cyrus
<email address removed>

---

### Post by lisati on 2011-03-26
There is free forum software available that requires little or no programming expertise. Examples include [PhpBB]("https://help.ubuntu.com/community/PhpBB3"), [mybb]("http://www.mybb.com/"), [xmb]("http://www.xmbforum.com/") and [punbb]("http://punbb.informer.com/").

I've never purchased a domain, someone else might be better equipped to answer that one. [DynDNS]("http://www.dyndns.com/") and [no-ip]("http://www.no-ip.com/") seem popular free domain name providers here.

---

### Post by Cyrus11 on 2011-03-26
Thanks for that advice. I appreciate it.

---

### Post by BkkBonanza on 2011-03-26
1. Don't buy a server. Either rent a VPS account or take advantage of the [Amazon EC2 first year free offer]("http://aws.amazon.com/free/"). You don't need to own a server to run a web site, and owning one just makes it harder to get it connected with a reliable high speed connection to the net. 

2. Using [Amazon]("http://aws.amazon.com/ec2/") you can start an [Ubuntu server]("http://alestic.com/") from the control panel and in less than a minute have a free server running connected in a data center to the net ready to customize to your needs. You do need a credit card though to get an account. Or some close family member perhaps. You will need to learn about ssh and installing the key Amazon gives you on your desktop machine. Read.

3. Login to the server you just started (using ssh) and install the needed web server software. Follow the [Ubuntu server guide here]("https://help.ubuntu.com/10.04/serverguide/C/index.html") (sections 10,11,12,18 only) to install Apache, PHP, Mysql as a minimum. I prefer Nginx web server but Apache is more well known and widespread. Read up on the steps you need to make a snapshot image of your server (create image) so you have a customized AMI. Of course, there is a lot more to learn about managing a web server. No programming, just linux admin steps here, editing config files etc.

4. Go to a name registrar like [name.com]("http://www.name.com/") (my fave, but many exist) and search for and find a domain name. Buy it with a credit card. About $8 with coupon. Use their free DNS control panel to create a CNAME entry that points your domain to the Amazon web server (to the address it gives you on the Amazon control panel). This enables people to use your name to visit the server. There is more to learn about domains and DNS and you need to understand how it works, but you do NOT need to run your own DNS server. Use google to find a primer on the DNS system (not on running a DNS server though) and read up.

5. Install a free PHP BBS system like phpBB or others as suggested in posts above. There are several well known ones but do some research first as some are pigs and ideally you want one that puts less load on the server but also has the features you need. Customize it to your needs, banner images, color choices, options for users and admin etc. No programming needed.

6. Test it all out and keep reading about server admin topics. Set up a backup script to keep automated backups of the mysql database for the BBS. You can either use ready made scripts or do a bit of coding to customize your own. Just make sure data is backed up often. On Amazon you can backup to S3, fast, cheap (free first year), and safe. This allows you to restore the site if a problem occurs.

7. Relax. Just don't get hung up on running a physical server from home. That is not the best way to get a busy site going on the cheap. If your site is popular and you grow beyond what a micro size instance can handle (it slows down too much) then you can upgrade to bigger server sizes very easily. I'd suggest using the "spot price" instances to cut costs but even normal fees are reasonable.

---

