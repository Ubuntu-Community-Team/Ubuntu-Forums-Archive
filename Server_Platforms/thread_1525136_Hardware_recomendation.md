---
title: "Hardware recomendation"
date: 2010-07-06
forum: Server Platforms
---

### Post by epsolon77 on 2010-07-06
Alright I can't take it anymore!  I've been running around and around on what hardware I should pick up for my wife's church.  They want to move their Email, Website and have onsite data storage and I can't decide on hardware.  There are maybe 25 email users and pretty low traffic on the website. Should I do something like an I5 with external sata raid tower?  Does this seem a bit skimpy?

---

### Post by doogy2004 on 2010-07-06
Ever think of a hosted VPS (Virtual Private Server) solution, like Linode? Or even something like Google Apps, I think Google has stuff for non-profits (but I'm not 100% sure).

Links:
[http://www.linode.com/](http://www.linode.com/)
[http://www.google.com/apps/intl/en/nonprofit/index.html](http://www.google.com/apps/intl/en/nonprofit/index.html)

---

### Post by epsolon77 on 2010-07-07
Doogy that is a great suggestion.  I will look at those solutions, but the desire on the part of the church is two fold.  They are not at all happy with their current hosts, and want to be able to control the system.  Now the VPS does fix that issue, however they also don't want to pay someone else to host these services.  They've had REALLY bad experiences.  I will most defiantly bring both those options up again.

---

### Post by HermanAB on 2010-07-07
I don't think you should bother buying a server.  You could rent a dedicated server at GoDaddy or Rackspace for about $80 per month.  Shared virtual servers cost much less.  So rather invest in fast internet access and use a machine elsewhere in a data centre.

---

### Post by doogy2004 on 2010-07-07
> **epsolon77 said:**
> Doogy that is a great suggestion.  I will look at those solutions, but the desire on the part of the church is two fold.  They are not at all happy with their current hosts, and want to be able to control the system.  Now the VPS does fix that issue, however they also don't want to pay someone else to host these services.  They've had REALLY bad experiences.  I will most defiantly bring both those options up again.

That is understandable.  If they are dead set on buying hardware, the quick answer is that anything will do (depending on the load and expectations of the users).  I'm running a 550Mhz Pentium 3 with 512MB of RAM with the following services with at most 2 concurrent users:
[LIST]
[*]Software Raid 5 (mdadm)
[*]Podcatcher (Mystic-Boa)
[*]Web server (apache)
[*]VPN (OpenVPN-AS)
[*]VMware Datastore (through NFS)
[*]Fileserver (SFTP & Samba)
[*]Repository Mirror (apt-mirror)
[*]Torrents (Transmission with X-forwarding SSH)
[*]Usenet (SABnzbd+)
[*]DNS (bind)
[*]etc.
[/LIST]

With your short list of requirements almost anything should work as far as hardware.

---

### Post by volkswagner on 2010-07-07
> **epsolon77 said:**
> Doogy that is a great suggestion.  I will look at those solutions, but the desire on the part of the church is two fold.  They are not at all happy with their current hosts, and want to be able to control the system.  Now the VPS does fix that issue, however they also don't want to pay someone else to host these services.  They've had REALLY bad experiences.  I will most defiantly bring both those options up again.

+1 for a VPS or a dedicated server on co-location such as godaddy.

A couple things to consider, reliability will be hard to match with a reputable VPS provider such as Linode.

Does the current ISP allow you to run a WebServer and or MailServer in the user agreement.  Does the church have a static IP from the ISP, or will that be an added charge?  What is the upload bandwidth of the current connection?

Server rooms have redundant power and Internet, along with battery backup, and hardware failover.

My two cents...go with a VPS and get a basic file server, maybe even a NAS device.

---

### Post by epsolon77 on 2010-07-08
One note I would like to bring up is a long term cost, which is why we were originally not looking at a VPS solution.

I found a CHEAP vps service for 50 per month.  However we aren't looking at spending more than 1000 on our system.  Having up time be THAT consistent is not really a requirement, the DSL package we are putting in is a business class, which allows servers and has a static.  So, 50 per month, would take 20 months to pay back the investment of buying the server.  If I buy a server that lasts less than 20 months I'm gonna be PISSED.

I just can't decide if I want to go one "beefy" server running an i5 or quivalent, or if I want to go with a few n330's or D510 atom's...  too many choices.

Doogy, I've got a few P3's and early P4's running some lite server stuff at my office, and I really am scared that I'm going to over tax them.  This will probably have about 10 concurrent users on email and file share, with an occasional burst on the MDADM for things like movies, so I am very hesitatnt to combine my MDADM, email and web hosting on one server.  Best to put the RAID on something seperate.

---

### Post by gordintoronto on 2010-07-08
The apps you describe have very low system requirements. An Atom 330 with 4 GB of memory and a 500 GB hard drive should completely overpower the problem. Add on a cheap monitor and nice UPS and you're talking $650.

What's the monthly cost of the business DSL package?

---

### Post by doogy2004 on 2010-07-08
> **epsolon77 said:**
> Doogy, I've got a few P3's and early P4's running some lite server stuff at my office, and I really am scared that I'm going to over tax them.  This will probably have about 10 concurrent users on email and file share, with an occasional burst on the MDADM for things like movies, so I am very hesitatnt to combine my MDADM, email and web hosting on one server.  Best to put the RAID on something seperate.

Point taken, in my setup the only bottleneck is MDADM during large write opperations.  The applications that you plan on running are generally not bound by CPU but memory.  As long as you have at least a 1Ghz single core processor and a bunch of RAM, you should be golden.

If you have a decent P4 with the ability to load it with RAM and donate it to start with.  If that isn't enough you could always upgrade to something else.  In my experience most non-profits can't/won't argue with FREE.

---

### Post by epsolon77 on 2010-07-08
> **gordintoronto said:**
> The apps you describe have very low system requirements. An Atom 330 with 4 GB of memory and a 500 GB hard drive should completely overpower the problem. Add on a cheap monitor and nice UPS and you're talking $650.

What's the monthly cost of the business DSL package?

We don't have the DSL package in place yet.  The church has a new building almost done the construction phase, so I don't have a cost on the DSL yet, but it seems to average between 80 and 100 around here.  This is considered free though, since they would need this DSL package to get internet access to the location anyway, so we are only adding about 5 bucks a month for a static IP.  

Doogy you hit my concern on the nose with the MDADM transactions.  They say they won't be streaming video from the storage disks, but you just know it's going to happen. 

What do you all think about an Atom 330 or D510  loaded on ram (depending on budget of course) with an esata or direct attached sata storage option?  

Thankfully the church has a budget for this, so I don't have to delve into my hardware stash.  I appriciate all your help!

---

### Post by doogy2004 on 2010-07-08
> **epsolon77 said:**
> Doogy you hit my concern on the nose with the MDADM transactions.  They say they won't be streaming video from the storage disks, but you just know it's going to happen.

The bottleneck that I have with MDADM is large write operations, read opperations such as streaming video off my server works perfectly.  I'm also running MDADM on IDE disks, again more adversity for my server to overcome.

> **epsolon77 said:**
> What do you all think about an Atom 330 or D510  loaded on ram (depending on budget of course) with an esata or direct attached sata storage option?

I've been out of the hardware game since they stopped incementing the number to show better performance (P3-->P4).  But what I do know is that almost any new computer will work, assuming it has enough RAM and storage.  As far as storage goes, SATA drives should have more than enough performance for what the server is going to be used for.  RAM is KEY, most server applications cache as much in RAM as possible.

---

### Post by volkswagner on 2010-07-10
If you are going to build, I would stick with the Atom 510 for a low watt solution implementing newer technology than the Atom 330.  Also the 510 Boards usually have better RAM acceptance with two slots and 4g max.  With the MiniITX boards readily available under $80, you should have an available PCI slot to add a SATA controller for your RAID setup.

---

