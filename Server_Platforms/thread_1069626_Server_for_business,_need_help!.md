---
title: "Server for business, need help!"
date: 2009-02-14
forum: Server Platforms
---

### Post by AICollector on 2009-02-14
Hey all.

Recently, a company my Father works for as been looking into getting a server up and running to deal with invoices.

The boss went to HP, they gave him paperwork denoting 'what they need':

Standard RAID setup

250gb SATA drive (non-hot-plug) 

Windows server 2003 (gah!)

AMD quad-core opteron. (double Gah!)

Price: £2000, plus £300 per callout. (oddly enough, they have listed 'Server Basic Operating System: £80')


Server's arnt my territory, so I need some help here.

Heres what they need:

Something that can run Sage Accounting software.

Hardware that won't fail if you sneeze at it.

Software that can take an email and turn it into an invoice (don't ask me how, but thats what they've got)

Also, duel hard-drive setup, one for use, one for backup.


It needs to be setup in such a way that it can run fairly autonomously. 


Any help would be appreciated.

---

### Post by hyper_ch on 2009-02-14
does this Sage software have run on linux?

---

### Post by theDaveTheRave on 2009-02-14
AIcollector.

It seems that SAGE software will run on Unix Linux platforms, a quick search of their web site gave me [=all&s=unix&x=0&y=0"]this page]("http://me.sage.com/index.php?search_modules[). I hope that helps.

Then it is just a matter of configuring a database (I would go for MySQL).

For "disaster" protection, double up on the system and run it as a "cluster"

As you are saying "money isn't the issue" then I would recomeng the MySQL Enterprise system, for the added support.

Either way if you are running a "business critical system" you should be recomending either a well qualified database / systems admin, or the acquisition of a full support network (hence the sugestion of MySQL enterprise.

Personally I have been setting up a mysql server (Master / Slave) setup, and I am begining to think that a cluster may be more effective for the potential of required disaster recovery / allways accessable databases systems etc.

Good luck with whatever you decide to go for.

David.

---

### Post by hyper_ch on 2009-02-14
if it's mission critical I'd first go with what you know. You don't want anything newly setup on a mission critical server. If you're unfamiliar with all that, go the route you've gone this far and learn how to do that on linux while you are under no pressure.

---

### Post by linux_tech on 2009-02-14
Best to setup in a test environment first (vm) before going live

---

### Post by PilotJLR on 2009-02-14
If you want uptime, use hot-plug drives in a RAID 1 or RAID 5 array; also verify you have redundant power supplies and add another NIC card for teaming.

If you use W2003, make sure you also purchase CALs for your users, or you won't be legal.

Remember that RAID is not a backup system, so choose your backup software and test it often!

Also - what is the problem with an Opteron processor? They are excellent.

---

### Post by AICollector on 2009-02-14
My experience with AMD chipsets has been less then terrific, I'm afraid.

This isnt something for a company with 50 employees, this is something to manage accounts and invoices for a company of 6 employees and around 12 customers at any one time. Not much in the way of workload or performance is needed, only uptime and a mostly autonomous system. The company dosent have the funds 

I'm glad SAGE will play nicely. I trust you all think HP's suggestion of Windows Server 2003 is a bit counterproductive in this sense?


Also understand I am in a tight spot here; this is a small company which dosent make that much money and which I feel could benefit from Ubuntu. On the other hand, I have little to no experience with databases or servers (my area of work is laptops and desktops)

---

### Post by hyper_ch on 2009-02-14
if it doesn't make much money then go first with what you know will work. When you have more time to test alternate things you can implement those at a later time. But rushing into something and then it won't work will in the end cause more harm.

---

### Post by etali on 2009-02-14
When do they want to have this new server by?  Could you ask them to wait a month or so, set something up on a spare machine and test it, then show it working and see what they think?

I'm in a similar position at the moment (moving over from standard shared hosting to a VPS, have some experience with Linux but not running a server on it), and I've been running the VPS for a while with some not-mission-critical stuff on it while I iron out any issues.  It's been three weeks so far, and I've 'broke' things several times.  I'm getting there, and I think by this time next month I'll be confident enough to move over the important things.

You may not have the luxury of doing that, but if they can hold off with buying the server for a while, I'd recommend it - learning how to fix something while you have the stress of lost business hours, and perhaps lost customers hanging over your head isn't fun.

Your test machine doesn't have to be as fancy as the real server, just show them the OS, the backup system, and the SAGE software working if they already have a license for it, work out what hardware they'll need, and show them the price difference.

---

### Post by PilotJLR on 2009-02-14
As the other posters have commented, go with what you know. If you feel up to managing a Linux server, then do it. Also see if you can try out Sage on Linux, to make sure managing Sage itself is something you're okay with on Linux.
A Windows Server license (for SMB) is something like a few hundred dollars... just get whatever works for YOU.

I think you may have misunderstood my comment about RAID. It doesn't matter if you have 1 employee or 1000; you need to put a price on your data.

If you buy a 1 disk server, then you WILL have data loss eventually. At that point, the integrity of your backups will be the only thing that can save your data.

If you really do want uptime, make a RAID 1 array. If you use Ubuntu, we're talking about a $200 hard drive here. Is your data not worth $200?

I work for a Fortune 500, but I also made a little server for a relative's 2 employee business. I think their needs are similar to yours. In my case, I'm using a 2 disk RAID 1, with nightly rsync backups to a 3rd disk and to an offsite rsync location, and then weekly backups to Amazon S3. I really don't think that is excessive; it's important data.

Remember... just because you're paranoid doesn't mean there isn't someone outside your house right now!

---

### Post by theDaveTheRave on 2009-02-19
AICollector

Seems to me like Pilot and hyper_ch are making sensible suggestions.

Good luck with your implementation.

One thing I would recomend.

Document everything you do.

Everytime to change a config file, make a copy of the old "working" file.

Document how you made a set up work (ie setup of the RAID device, and use of fstab for puting it in a easy to find location). If you get an error you will more easily be able to find out what has changed. Personal experience with fstab and disk UUID's being "dynamic" often caused me issues on a 3 HDD desktop I had (when experiencing electrical failures!), luckily nothing was critical or ever lost, it was just getting it working again. With the documentation in place it is much easier.

Strangely I tend to document how I do stuff onto the forums, as a thread with a problem and then a post for the solution.

this as saved my skin a couple of times in the last few weeks since my intrepid upgrade.

David

---

### Post by windependence on 2009-02-19
> **PilotJLR said:**
> As the other posters have commented, go with what you know. If you feel up to managing a Linux server, then do it. Also see if you can try out Sage on Linux, to make sure managing Sage itself is something you're okay with on Linux.
A Windows Server license (for SMB) is something like a few hundred dollars... just get whatever works for YOU.

I think you may have misunderstood my comment about RAID. It doesn't matter if you have 1 employee or 1000; you need to put a price on your data.

If you buy a 1 disk server, then you WILL have data loss eventually. At that point, the integrity of your backups will be the only thing that can save your data.

If you really do want uptime, make a RAID 1 array. If you use Ubuntu, we're talking about a $200 hard drive here. Is your data not worth $200?

I work for a Fortune 500, but I also made a little server for a relative's 2 employee business. I think their needs are similar to yours. In my case, I'm using a 2 disk RAID 1, with nightly rsync backups to a 3rd disk and to an offsite rsync location, and then weekly backups to Amazon S3. I really don't think that is excessive; it's important data.

Remember... just because you're paranoid doesn't mean there isn't someone outside your house right now!

I would agree here, and go one step further and say go with at least 3 drives in RAID 5. There are great SATA machines out there now from the major manufacturers including HP. RAID 1 is OK, but you will get a performance boost with RAID 5 and you can just pull a drive that fails and replace it without missing a beat.

IMHO it's a GREAT thing that the software supports Linux/Unix. This means that not only don't you have to worry about licensing costs, but once you set this thing up, it will most likely just run and run without intervention. Personally, for rock solid stability and very little disk usage, I would use FreeBSD with a Postgresql back end. MySQL is great, but if the software works with Postgres, it is as good as, if not better than Oracle, and as an added benefit, since it is less well known, it should be a bit more protection from script kiddies.

On processors, like PilotJLR, I have worked for several Fortune 500 companies, and currently run my own consulting business which is exclusively Unix/Linux. From my experience, AMD has a far superior product, and I currently run all my web hosting clients on a dual Opteron quad core box. It hasn't missed a beat, and seems much faster than the Intel boxes I have, as well as runs much cooler than they do. Some people just have a thing for certain brands. It's like the old saying: " No one ever got fired for buying IBM". Same applies with Intel. Absolutely good solid processors, but not necessarily the best.

-Tim

---

### Post by songshu on 2009-02-19
i usually stay away from server hardware because they always appear the same to me as "normal" pc hardware except that they cost double the price. (they say these parts have been tested better, i don't know)

what i personally do is expect anything to break and buy some good but cheap pc hardware and make sure i have everything double, this way i don't have to wait for new spare parts being delivered and no worries about this specific mobo being out of stock because they are not being produced anymore after 2 years.

always make back ups!!!!!!!

depending on your acceptable down-time you can have all the spare parts next to the machine and it will take you not so much time to replace the broken part.

alternatively you could go for a "live" back up system if you can't afford any down time.

i kept some notes about a high available setup that works really well, although not sure if you would feel comfortable with this.
[http://www.songshu.org/index.php/getting-high-with-lenny](http://www.songshu.org/index.php/getting-high-with-lenny)

all this said, you do need the expertise around in case anything goes down, if not you need to buy the support, and yes....this is expensive.

---

