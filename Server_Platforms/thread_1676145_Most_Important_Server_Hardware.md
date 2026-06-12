---
title: "Most Important Server Hardware?"
date: 2011-01-26
forum: Server Platforms
---

### Post by garfonzo on 2011-01-26
Hey Folks:

I plan on setting up a server for a small business to allow users to remotely log in to the server and carry on their work. There will be anywhere from 1 to 5 users logged in simultaneously. They will be performing tasks such as checking email, creating/editing MS Word documents, creating/editing MS Excel documents, and using a front end to an MS Access database. 

The location of the server is roughly 1,100 miles away from the office from which the users will be logging in from.

My question is, if I were to buy a new server for this purpose, what hardware should I focus on spending the most on? Should it have a fast CPU? Have as much RAM as possible? Super Fast Hard Drive RPM speeds? 

In a perfect world, the new server would have all of these attributes, however, I don't want to spend on something that won't be utilized. For example, I have a desktop acting as a server in my home LAN which simply serves files. It has a 2.9Ghz or something CPU which sits virtually idle all the time. It's like using a Corvette as a golf cart: sure the Corvette will work, but you only need a golf cart.

Your thoughts?

Thanks!

---

### Post by cariboo on 2011-01-26
Personally I'd with server hardware, as apposed to consumer hardware, and go with a fast cpu and lots of ram. Unless the users are connected via fiber, hard drive speed is irrelevant, as network speed is a bottle neck.

---

### Post by garfonzo on 2011-01-26
> **cariboo907 said:**
> Personally I'd with server hardware, as apposed to consumer hardware, and go with a fast cpu and lots of ram. Unless the users are connected via fiber, hard drive speed is irrelevant, as network speed is a bottle neck.

Are server specific CPUs better at handling multiple requests (such as several users working off the server remotely)? I mean, why not go with a consumer desktop with a smoking fast CPU and lots of RAM? What differences would there be?

---

### Post by wongo888 on 2011-01-27
Almost a decade ago, we were running a moderately busy website with retail grade Tyan mobos. The tale of the tape said that they were equivalent to a Compaq server - and significantly less costly. Of course, that wasn't the case at all. We went through at least three mobos because of the load stresses.

I would rather run old secondhand HP servers than build a new one out of consumer grade components. That's not to say that enterprise class machines don't fail - they do. All I'm saying is that if you go for cheap then you shouldn't be surprised when they fail at 2am on a Saturday - during a long weekend.

---

### Post by datamove on 2011-01-27
For the profile you have described, very moderate hardware will suffice. I.e. 8GB RAM, even single CPU socket. But think of the future expansion, and you'll probably want to by a modern server (dual CPU Xeon or Opteron, 24 GB RAM etc, since what is low end now will be trash in 3 years. Yuo can chose to get a low wattage CPU model to save some enegry and lower operational costs over the server's life time. For 5 users, I am not sure SDD would significantly help. What's better is to setup raid 1 from SAS or SATA drives for better uptime and performance.

---

### Post by SeijiSensei on 2011-01-27
CPU speeds are largely irrelevant for such a small number of users.  What's more important if you're trying to maintain a server a thousand miles away is hardware reliability.  You want to be using a RAID storage solution; "hot-swap" drives are a nice feature in this situation as well.  If your server has hardware RAID and hot-swap drives, when a drive dies you can remove it from the front panel and insert its replacement.  The RAID controller will rebuild the filesystem on the new drive automatically.  I've had customers do this for themselves without incident.

Another consideration is power.  You'll definitely want a pretty hefty uninterruptible power supply, and perhaps even a redundant power supply on the server.  Linux comes with a daemon called apcupsd which will monitor an [APC]("http://www.apc.com/products/category.cfm?id=13") power supply and take appropriate actions if problems arise.

Finally, if you're going to be maintaining this server remotely, you might want to read [this thread]("http://ubuntuforums.org/showthread.php?t=1651444") on using OpenVPN tunnels to connect with machines behind a remote firewall.

---

### Post by tgalati4 on 2011-01-27
Lots of used HP Prolient and Dell Poweredge servers have been dumped on the market.  Get dual power supplies and set up email/text hardware monitors.  Get a decent UPS.

---

