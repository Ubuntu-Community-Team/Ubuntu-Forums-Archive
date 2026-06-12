---
title: "deploying beautiful LINUX"
date: 2007-06-14
forum: Server Platforms
---

### Post by netlogic on 2007-06-14
How many of you pushed Linux in your companies and to your clients? I always try my best.  I really love Desktop Linux, but it always have been a difficult sell. It took me tons of convincing to deploy on a local cafe. I even offered a small discount on the machines. Suggesting Apache Linux as co-location servers have been easy too, but I am finding it difficult to sell to small companies who are looking for a LAN solution. Maybe, this is really difficult in America. America has been really tied into Microsoft Office suites. Even I remind them, they can save over $400 software licensing fees for each machine. I really want to hear others successful stories. Maybe, I need more convincing. Maybe, I am doing something wrong here. Thank you for reading.

---

### Post by MentholLite on 2007-06-14
> **netlogic said:**
> How many of you pushed Linux in your companies and to your clients? I always try my best.  I really love Desktop Linux, but it always have been a difficult sell. It took me tons of convincing to deploy on a local cafe. I even offered a small discount on the machines. Suggesting Apache Linux as co-location servers have been easy too, but I am finding it difficult to sell to small companies who are looking for a LAN solution. Maybe, this is really difficult in America. America has been really tied into Microsoft Office suites. Even I remind them, they can save over $400 software licensing fees for each machine. I really want to hear others successful stories. Maybe, I need more convincing. Maybe, I am doing something wrong here. Thank you for reading.

Not just in American ppl are tied into Microsoft Office suites, other parts of the world as well.

Is your company providing after sales support or maintenance for that cafe?
Maybe because they are too used to Microsoft products and switching to another product makes them uncomfortable.
Assuring them that there will be after sales support and end-users training will help to put their worries at ease.

Just my 2cents. ;)

---

### Post by netlogic on 2007-06-14
Yes, I offer after sales support. I charge them very high to prevent from a business intervention while I am doing implementation from other locations. I just can't pay to have a dedicated staff yet. I am an independent consultant. I was wondering if other small potato consultants are having great success selling Linux solutions. It would be nice, it there is a forum for Linux consultants to teach each other about the business sides.

---

### Post by pkarjala on 2007-06-14
The important thing is to show the buyers that the computer they are getting has the exact same functionality.  The main reason to emphasize this is that most people are worried that Linux is too different--that it won't let them do the things they want to without having to relearn a ton of things.  This is the first hurdle to clear.

Then show them that the cost is greatly reduced, while providing the same support.  That the software upgrades are cost free down the road.  That there are no hidden costs when a new version comes out.

These arguments help a lot to increase the marketability of a Linux install.

...no, I haven't had to make this argument before at all.  Really.  >_>

---

### Post by joe.turion64x2 on 2007-06-14
The security topic may help you to convince them as well.

---

### Post by BLTicklemonster on 2007-06-14
I service and repair computers for friends and family, and honestly, I rue the day someone comes up with an Ubuntu box and says, "I updated my kernel, now it doesn't work". 

You know, as bad as microsoft is, at least they don't leave you looking at a black screen when you do a service pack.

I love my Ubuntu. I really do, but heaven forbid any of my friends should get it on their machines!

---

### Post by dmizer on 2007-06-15
i didn't have too much trouble convincing my small company to replace their aging win 2000 server (400mhz pII, 128meg of ram) with a linux box.  the win2000 server was hosting an 8 gig external mirror device connected via a honking huge scsi cable.  that and two printers.  the printers were the most difficult, because it took me a long time to find the right driver for one of the printers.

anyway ... i told the boss that i could make a server out of any old computer they had laying around.  much to my dismay, the first box they pulled out of the storage locker was a 486.  i like a challenge but ...

he finally happened to think of an old sony desktop machine he had at his house.  it was a 700mhz pIII machine with 128meg of ram.  i had a couple of spare pc100 256meg ram sticks laying around so i contributed to the cause.  that plus adding a couple of new high quality 120gig drives, and some hdd coolers.  loaded up ubuntu server, and off we went.  new server for basically the cost of the hard drives and coolers.

i really  inherited a nightmare of a network.  3 win98 machines still in service, alongside a winNT?! machine.  the 20 or so clients were all served from two 5port 10baseT hubs (not switchs).  there were only 7 mainlines attached to the hubs, and 4 of those were directly serving single machines, so the rest of the machines in the network were split off some 5 or so pocket hubs ... unreal.

now the problem is ... that i'm switching jobs, and there is no one in the company who has even close to the server/computer knowledge as i do, so they're all panicking because no one can use the commandline to fix the server.  of course, my winning argument was that, if a windows server broke, no one could fix that either.

so now, perhaps i'll get to come back home to babysit now and again.

---

### Post by netlogic on 2007-06-15
I find Linux administration easier than Windows. I find Windows administration a complete nightmare. Long as you have setup the PCs yourself and know the environment, it is easier to send them an email of commands than wait until their computer boots, not knowing exactly what they are clicking on the computer screen. It is frustrating to do a phone support for someone who has no idea about their computer. Something you can fix yourself within two minutes, become three hour phone calls. Almost everything in Linux can be done by the command line and shell scripts. Once, we have more commercial vendor supports for drivers and better Active Directory support for the enterprise, or something better than OpenLDAP, I seriously believe everything can be replaced by Linux. I have maintained thousands of Windows servers in the past. You don't know how much work is involved. When you are maintaining 100s of servers by yourself, you can completely go insane. Windows servers are pointless to use until you install cygwin (unix command line shells). For administrators, command lines are essential, so you can automate your jobs. Also, Windows servers are known to have the worst server uptime in the history of all the servers. This also includes OS/2. 

Also, I seriously doubt a soccer mom will be compiling her own kernel. I tried over ten different Linux distros. I never had a kernel panic from a stocked kernel. Also, the fact that almost all modern Linux distros use grub, I doubt people have issues upgrading their kernels. I love Linux.

---

### Post by Chayak on 2007-06-15
I've been working with small linux networks for quite a while and it was never a problem to keep the boxes groomed and in working order.  I had quite a learning experience when someone I installed a linux file server for decided to shift their entire network over.  LDAP was easy enough after some reading but keeping all of those machines updated was a pain until I discovered a few apps to make the job easier. Linux really needs some good administration apps if we want widespread adoption.  I'd love something that would give me a list of machines on my network along with their status and give me the ability to select single, multiple, defined groups, or all to send commands to and control updates and other little admin niceties.  I'd be in bliss if I had an open source analog to Apple's remote desktop.  I'm all for using the command line but when you're talking 100+ machines to administer it's a huge timesaver to have good tools to work with.

---

### Post by elst on 2007-06-15
Three thoughts:

- Most people want solutions to whatever immediate problems they have, and price is often the second question (after, "will this actually fix my problem"). For a small business or workgroup, Linux often does not solve a specific problem that they couldn't address with the more familiar Windows. Worse, it may appear to add new issues - it's unfamiliar system that they don't know the capabilities or limits of, and they may not be sure how to get information or support.

- I read an interview with a Red Hat executive where he suggested that for people to switch to a new and unfamiliar product in large numbers, that product would have to be at least four times better at solving their problems than the existing product, and preferably *ten* times better. He also said that he would not personally spend time trying to sell Linux to a potential customer who would not receive this level of benefit.

That sounds harsh, but I agree with it. Some organizations can get such massive benefits from using Linux in particular roles that it's obviously the right thing for them to do. But current Linux distributions are not the easiest or best integrated solutions for running a small set of multi-role LAN servers, especially compared with the lastest versions of Windows Server, so at this point the rewards may simply not be enough to actually make a really strong case in many instances.

- "Show, don't tell". A lot of people aren't familiar with Linux, and it's hard to judge what you aren't familiar with on the basis of what someone says. Think about what features you can demonstrate that solve a clearly definable problem.

I've used the Linux LiveCDs to test systems where Windows is broken, and it always gets a good response, whilst people are much more cautious where I've just talked about Linux as a solution. I suspect because the LiveCD shows them something immediately useful, actually working to solve an immediate problem.

---

