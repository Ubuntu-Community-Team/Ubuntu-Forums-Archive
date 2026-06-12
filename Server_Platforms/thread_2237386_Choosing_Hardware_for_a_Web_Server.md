---
title: "Choosing Hardware for a Web Server"
date: 2014-08-01
forum: Server Platforms
---

### Post by baudouin-laloy on 2014-08-01
Hello,

I have a web server hosting 20 small sites. It is an old Dell XPS hardware running Ubuntu server 12.04 LTS.
All my sites are made with Drupal (PHP) + Apache.
As you can imagine, this setup becomes slow.
I am planning to add 20 other sites and I would like to invest in a more robust solution.
Unfortunatly, I am a complete noob in this matter.
I have a budget from 2 000€ ($ 2 700) up to 5 000€ ($6.700).
I would love a scalable solution where I can add (a card? a processor? ...) when needed... In this case, I would be happy to start around 2000€
Hereafter my questions:
-Tower or Rack? (could I start with a rack without the frame?)
-Which vendor/product solution are the most Ubuntu compliant?
=>I just read the[ Ubuntu Server certified hardware]("http://www.ubuntu.com/certification/server/") page, but I am lost, because if I look at the vendor sites, there is no mention of Ubuntu (or very few)
=>I really don't want to spend too much time into compiling driver... I would like to be able to install Ubuntu nearly out of the box
-Should I invest into memory or into the number of processors (or number of kernel)?
-Should I go into SSD?
-Is there anything else I should think about.

I am sorry by advance if my questions seems a little bit stupid; I assume I will fine tune my requests in the future.

---

### Post by TheFu on 2014-08-01
These are all very smart questions and you want the answers, but you've left off all the data anyone would need to know to begin making any recommendations. Things like:
* transaction rates (web and DB)
* transaction sizes (web and DB)
* concurrent access
* total data storage
* total DB sizes
* count of DBs
* disaster recovery plan
* backup plan
* failover plan
* load balancing plan
* upgrade plan

Start by providing 3 months of data monitoring - CPU, RAM, files, disk I/O, network I/O, and all sorts of dupal/DB specific things.
Then start documenting the other things.

I'm a huge fan of deploying 2-3 servers per location and at least 2 locations to prevent downtime.

Oh ... and buying a server that supports adding CPUs never pays off in this price range.  Add a zero to the budget first before thinking that way.  20 websites is really a trivial amount. I'd be shocked if a $700 "server" couldn't easily handle 5x that number.  

SSD or not?  Perhaps, but only in RAID1 or RAID10.  Buy enterprise-grade SSDs, not the cheap "home" versions. I don't use SSDs - the devil I know vs the devil I don't know.  I know many companies with high transaction rates that use SSDs - for a small DB, you can pin actively used tables into RAM - which will blow away SSD performance.

---

### Post by baudouin-laloy on 2014-08-01
Hello TheFu,

Many thanks for your answers.
Unfortunatly, I couldn't answer all of your questions, but here are some data:
Number of DB: 50
Avrg size of DB: 100Mb
Total db size= 5 GB
Total data storage= 20 GB
Concurent access= 10 (max 20)

Backup plan: For now, I have a personal backup plan (some scripts I have made to backup [in 3 locations] and restore websites)
disaster recovery plan: For now, I have a second computer with the same setup 

* transaction rates (web and DB)=>I don't know how to calculate this
* transaction sizes (web and DB)=>I don't know how to calculate this

As you can see, a lot of things needs improvements... This is why I am here (I am not an IT guy, but I have to do it...)

You say that a $700 server can do the job... Could you give me the configuration you are thinking (amount of memory, the type of the processor, vendor...)
You say that you are a huge fan of deploying 2-3 servers per location: it was also my idea: one web server and one mysql server... or do you think it is better to have only one server but more powerfull (in other words, is it correct to say that 2 "small" servers are better than one "big" server")

And finally, in 2 years, the number of sites/db/... could be the double... This is why I was searching for a scalable solution.
(ans sorry for my poor english)

Baudouin

ps: You say: for a small DB, you can pin actively used tables into RAM... I will look into this [Is it a feature that exists in mysql?]

---

### Post by SeijiSensei on 2014-08-01
Have you considered cloud-based solutions like [Linode](http://www.linode.com/)?  I no longer have any interest in running services on my own hardware.  I'm much happier letting a third-party worry about air conditioning, uninterrupted power, and big Internet pipes.

---

### Post by TheFu on 2014-08-02
> **SeijiSensei said:**
> Have you considered cloud-based solutions like [Linode](http://www.linode.com/)?  I no longer have any interest in running services on my own hardware.  I'm much happier letting a third-party worry about air conditioning, uninterrupted power, and big Internet pipes.

There's a point where cloud makes sense, but there are also some workloads that do not make sense for cloud deployments.  I'm responsible for about 20 systems - most have proprietary customer data on them and intercommunicated, so we'd need a cage with the equipment at a colo data center to have any hope of security.  $1200/month - min.  OTOH, a few $700 machines running these VMs easily handle the loads, plus $100/month for business connectivity - which is the right answer?   3 months of "leased" systems is a year of "owned" systems costs.  If we needed higher bandwidth and metro ethernet was the only way to get it, then the colo-solution would look more attractive.

I'm looking at a GIS system this week that needs lots of CPU, RAM and IO - nothing special or proprietary about that data, so it could be deployed in the cloud.  Linode's plan for the estimated server size is $320/month - thats 1 VM. I haven't priced systems with similar capabilities. We may just pay a service provider by the transaction instead. I need to run some numbers for the transaction rates where it makes more business sense to run the service ourselves.  Even in the first month, the free services (google, MS, others) aren't anywhere near enough.  I've deployed GIS before, but had huge budget ($10M+) back then.  Doing it for under $5K will be impressive, if successful.

---

### Post by baudouin-laloy on 2014-08-02
Hi [B]SeijiSensei,
[/B]Thank you for your answer, but I don't wantto have my sites in the cloud (I am creating web site starting at 99€; everything is automatized...)

Hi TheFu,
I know that my questions aren't enough specific... but could you provide an estimate with the small data I could provide?
(especially for the vendor: do you know a vendor which is Ubuntu friendly)

---

### Post by TheFu on 2014-08-02
> **baudouin-laloy said:**
> 
Hi TheFu,
I know that my questions aren't enough specific... but could you provide an estimate with the small data I could provide?
(especially for the vendor: do you know a vendor which is Ubuntu friendly)

No, I cannot. Sorry.

I haven't purchased a "server" in 7 yrs.  We're running our business on home-built desktop-class equipment - in a redundant setup. If/when I need server-class equipment, it will probably be Dell, but don't take that as an endorsement.  The idea of redundant PSU, redundant NICs, redundant SAN connections just doesn't make as much sense today as it did 8 yrs ago.  I'd rather have 2x the desktop-hardware than have a single server at 4x the price. It is hard for anyone to argue that 1 "highly redundant" server matches the redundancy of 2 desktops in a load balanced situation.  Plus those desktops can still run 10-40 VMs. ;)

Plus desktops will use much less power, create less noise, less heat, and use less expensive components when upgrades are desired. The only thing I'd spend server-class money on is the RAID card - and only if I need HW-RAID for performance. Buy a spare with the first HW card (so when it fails, the data isn't gone). A pair of quality LSI cards would be at the top of my list.  SW-RAID is so much more flexible that I'd much, much, much rather use that, if possible.

---

### Post by SeijiSensei on 2014-08-02
The last Linux server I built is running on a Dell PowerEdge R410 with dual Xeons and hardware RAID1.   I successfully installed a number of different distributions on this box including Ubuntu Server.  We're running CentOS 6 on it, since I prefer RedHat flavors for servers.  It runs a couple of web sites, but mostly it is scanning inbound mail with MailScanner and handling outbound web traffic via Squid.

> I am creating web site starting at 99&#8364;

I hope that's an annual figure considering standard web hosting plans often cost just a few bucks a month.

---

### Post by baudouin-laloy on 2014-08-02
> **SeijiSensei said:**
> I hope that's an annual figure considering standard web hosting plans often cost just a few bucks a month.

No, it is not... This kind of sites are generated automatically (based on a form filled by the client)... I call them "business card" sites


Many thanks for your answer... I think I will go with PowerEdge... Do you think I should have 2 "smal" servers (one for Apache and one for MySQL) or one "big" server?

---

### Post by SeijiSensei on 2014-08-04
I started building Linux servers around 1995-96 when the cost of hardware was an order of magnitude greater than it is today.  (Desktop PCs could easily cost $2,500; servers twice that or more.) That provided a big incentive for running multiple services on a single box.  I continue to do so today unless the application requires multiple machines.  For instance, I built an application for a health provider which has a publicly-visible server, but the (PostgreSQL) database resides on a separate machine behind the firewall to insure the privacy of patient records.  (All the information in the database is also encrypted for the same reason.)  The publicly-visible server also runs a database that contains only the website's dynamic content, but no patient information.

---

### Post by gordintoronto on 2014-08-05
There are probably computer shops near you who would be delighted to assemble a system for you. Here's my starting point for a pretty beefy server (US $):
 i5 4590 quad-core processor $200
 ASUS Z87-A mid-range motherboard $125
 16 GB DDR3 $175
 2x1TB WD "black" hard drives in RAID 1 $170
 Antec Sonata case $70
 Antec EA-650 power supply $90 (Don't go cheap on the power supply!)
 Optical drive $20

Oops, I went past the $700 target, it's an $850 configuration.

As you add web sites, you might want to add memory, and that's possible. If you run out of processing power, add another computer and split the web sites over the two computers. By starting with "best of breed" components, the computer should last a long time. Just make sure you run it in a dust-free environment; when the CPU heat sink fills with dust, it becomes a big problem.

---

