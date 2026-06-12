---
title: "Linux gains backup utility"
date: 2008-08-21
forum: The Cafe
---

### Post by newbie2 on 2008-08-21
> Memopal announced a free trial download of a Linux version of its online backup utility. The public beta of Memopal supports Ubuntu 8.04 and Debian Etch, says the company, which says it may release an open source version in the future.

Memopal offers "automatic and continuous" backup to a remote server via a secure internet connection, says the company.
[http://www.desktoplinux.com/news/NS2461279608.html](http://www.desktoplinux.com/news/NS2461279608.html)
[http://betatest.memopal.com/index.php/Main_Page](http://betatest.memopal.com/index.php/Main_Page)

---

### Post by billgoldberg on 2008-08-21
> **newbie2 said:**
> [http://www.desktoplinux.com/news/NS2461279608.html](http://www.desktoplinux.com/news/NS2461279608.html)
[http://betatest.memopal.com/index.php/Main_Page](http://betatest.memopal.com/index.php/Main_Page)

Any kind of software that has a trial version has not even the slightest change of being used by me.

---

### Post by Boelcke on 2008-08-25
Ah, they're in beta testing on the Linux version.  The Windows version is actually quite slick.  Plus, you can't beat the pricing for online backup.  $49/year for 150gb.

The Linux version isn't quite up to par with the Windows version yet.  It's just CLI, and doesn't have all the options yet.  It's not as far along, but it's somewhat functional.  Hopefully, they'll get it finished soon.

To their credit, they do call it a beta version.  Remember when beta meant it was a product that's still in testing, not meant for general consumption?  As opposed to, say, Gmail, which will probably say beta for a decade.

I'm a bit enthralled with the Windows version, which I've played with on an XP box.  They've made some decent choices in the design.

---

### Post by Vitamin-Carrot on 2008-08-25
I would prefer to back up my data to a source that i can manage myself both hardware and privacy

---

### Post by SunnyRabbiera on 2008-08-25
> **billgoldberg said:**
> Any kind of software that has a trial version has not even the slightest change of being used by me.

well they said that the possibility of a open source client is there, so thats good.

---

### Post by MaxIBoy on 2008-08-25
All we need is for someone to create an alternative server, recompile the code to use it, and we get the service for free!

---

### Post by Boelcke on 2008-08-27
You know, the problem is, I don't think I can run a server that cheaply.

I mean, if I just buy an external HD to do backup, that's going to be $100-150, and I'm probably going to need a new one every two or three years.  Not to sound like a salesman for them, but it seems like an external HD costs more, and gives me less functionality (no online file access, no offsite backup).

I admit, the privacy issues are a concern.  I was thinking of writing my own backup system/scripts using [rsync.net]("http://www.rsync.net/"), but the pricing to store 80gb of backup is just astronomical anywhere else.

The server economics are also difficult, though that does address some of the security concerns.  If I spend a measly $500 on hardware (a weak server, to be sure), and it lasts me 5 years, call it $100 a year.  Leave the thing on, burning say 100W at $0.10/kWhr, and that's $87.60/yr in electricity to leave the thing on 24/7.  All that assumes nothing ever breaks.

So, to your point MaxIBoy, I'm sure a couple of us could create some code that does this functionality.  I've thought through a lot of the algorithms and choices that I'd want.  However, if we want to host a server for this stuff, that isn't free.  It costs money.  And frankly, I haven't seen server space anywhere else this cheap.

That's my biggest question, which only time will tell: can they afford to do this long-term at this price structure?  It's no good to run my backup with them if they disappear!

---

### Post by Warpnow on 2008-08-27
> **Boelcke said:**
> You know, the problem is, I don't think I can run a server that cheaply.

I mean, if I just buy an external HD to do backup, that's going to be $100-150, and I'm probably going to need a new one every two or three years.  Not to sound like a salesman for them, but it seems like an external HD costs more, and gives me less functionality (no online file access, no offsite backup).

I admit, the privacy issues are a concern.  I was thinking of writing my own backup system/scripts using [rsync.net]("http://www.rsync.net/"), but the pricing to store 80gb of backup is just astronomical anywhere else.

The server economics are also difficult, though that does address some of the security concerns.  If I spend a measly $500 on hardware (a weak server, to be sure), and it lasts me 5 years, call it $100 a year.  Leave the thing on, burning say 100W at $0.10/kWhr, and that's $87.60/yr in electricity to leave the thing on 24/7.  All that assumes nothing ever breaks.

So, to your point MaxIBoy, I'm sure a couple of us could create some code that does this functionality.  I've thought through a lot of the algorithms and choices that I'd want.  However, if we want to host a server for this stuff, that isn't free.  It costs money.  And frankly, I haven't seen server space anywhere else this cheap.

That's my biggest question, which only time will tell: can they afford to do this long-term at this price structure?  It's no good to run my backup with them if they disappear!


Right now, 500gb HDs are $100. Put Five of those suckers in there for 
2tbs in a raid 5.

750 + 87 a year for five years = $1185

$237 a year.

2tbs of space. Give everyone 150gbs like that place does, and you've got room for 13 users.

$18 per year per user is the operating cost.

Now take that and apply it on a massive scale. The price per user would fall to cents eventually.

There is definitely room to undercut their business if someone developed an open source alternative. Let anyone run a server for the app, and suddenly, people will be offering this service at BARE MINIMUM to draw a profit (like is done with webhosting now).

If someone wrote a good open source server/client, they wouldn't have to worry about the servers. The industry is profitable enough to draw its own users.

-Warpnow, your resident Economics student. :-p

---

### Post by oldsoundguy on 2008-08-27
If you are just looking for a simple backup utility that works and want to keep your data HOME and not on line .. Easy Gig II is the first self booting disk copy utility I have found that does the job on Windows, Mac and LINUX.  
I had a drive that was going south and I just copied it to a larger drive and swapped it.  Booted right up without a hitch.

---

### Post by slavik on 2008-08-28
> **Warpnow said:**
> Right now, 500gb HDs are $100. Put Five of those suckers in there for 
2tbs in a raid 5.

750 + 87 a year for five years = $1185

$237 a year.

2tbs of space. Give everyone 150gbs like that place does, and you've got room for 13 users.

$18 per year per user is the operating cost.

Now take that and apply it on a massive scale. The price per user would fall to cents eventually.

There is definitely room to undercut their business if someone developed an open source alternative. Let anyone run a server for the app, and suddenly, people will be offering this service at BARE MINIMUM to draw a profit (like is done with webhosting now).

If someone wrote a good open source server/client, they wouldn't have to worry about the servers. The industry is profitable enough to draw its own users.

-Warpnow, your resident Economics student. :-p

you forgot the co-location cost of your equipment (because your home cable/dsl isn't fast enough).

---

### Post by Boelcke on 2008-08-28
As you scale up, you'll have to pay for the things that break, too.  That'll cost.  The costs don't go down on a massive scale today.  Plus you'll have to charge a small profit, as payment for the risk you're assuming.  So, rounding up, turn the $18/yr into $25.  Plus, my rule of thumb for developing products and getting them to market is that it always takes at least twice as much as you think when you're excited and drawing it up on a napkin, and put it to $50.  Interesting.

BTW, according to that recent Google study on HD failures, over half will give no warning at all.  You don't always get signs that it's going south.  So no matter what backup solution you pick, it should really be automatic, and constantly updating without your intervention.

---

### Post by LateNiteTV on 2008-08-28
dump and restore works wonders for me.

---

### Post by toupeiro on 2008-08-28
If you're and end user looking for a backup utility and dont have enterprise needs, then I have three words for you:

1. cpio
2. tar
3. cron

Want something a bit more GUI, try sbackup (in repositories)

If you are saying Linux has no enterprise agents, I beg you to google things like Legato Networker and NetBackup..

There is very little room for try and buy for backup solutions in end user linux space.  That better be one revolutionary product, since most tools are using some sort of tar/cpio combination under the hood anyways.

---

### Post by Warpnow on 2008-08-28
> **Boelcke said:**
> As you scale up, you'll have to pay for the things that break, too.  That'll cost.  The costs don't go down on a massive scale today.  Plus you'll have to charge a small profit, as payment for the risk you're assuming.  So, rounding up, turn the $18/yr into $25.  Plus, my rule of thumb for developing products and getting them to market is that it always takes at least twice as much as you think when you're excited and drawing it up on a napkin, and put it to $50.  Interesting.

BTW, according to that recent Google study on HD failures, over half will give no warning at all.  You don't always get signs that it's going south.  So no matter what backup solution you pick, it should really be automatic, and constantly updating without your intervention.

But that number falls DRASTICALLY when rather than serving 13 members you are serving hundreds or thousands.

It is a profitable industry, and so if an open source alternative exists, I am confident people will find ways to drive price drown as low as possible, to be competitive.

---

### Post by Boelcke on 2008-08-28
Warpnow, I think I disagree.  Here's why.

This isn't software we're talking about.  It's hardware, and the management of it.  It's also about organizations, and structure.  The larger you get, you'll have to pay something for the overhead of managing it.

If you just have the one server box, you might do it in your spare time as a hobby for a dozen of your friends.  If you're going to make a go of it, and run, say, several hundred servers, for a few thousand users, it isn't a free open source project.  It's a job.  You'll have to pay yourself a salary.

So, sure, when you get 10,000 users, you'll get some economies of scale.  But you'll have to add your $50,000/yr salary to it, which presumably you're not giving away for free.  That's $5/yr per user.  A real number.

Plus, you've got rent on a place to house and cool those servers.  All this stuff costs money.  So, to setup a 3rd party place, it just plain costs.  Frankly, I'm not sure how they're doing it for $50/yr.

More to your point, though, what's the open source alternative?  If we're driving for free, I hope you'll see that paying somebody to house and maintain a bunch of servers never approaches zero cost.  We'll have to backup our files on each other's PCs.  There are a few solutions out there that already do this.  [http://www.cucku.com/](http://www.cucku.com/).  There are a few others I have looked at, some of which look really good.

The only drawback is, if you want to have good availability of your backups, you and your friend have to leave your computers on all the time.  Yes, I know some folks do this anyway.  I don't.  The way I figure it, that costs me about $7-8 per month to keep one PC on 24/7.  Plus, we might each buy external USB drives to store the backup on (another $100).  So, it isn't really free.  As long as I'm paying that, why not have the greater stability and up-time of a company?

I have tried to imagine a distributed network for file backup, so that you'd have greater redundancy and availability.  Before going too far down that idea, though, I asked myself:  Would I give up, say, 50 gigs of my space (to share as encrypted storage for other users) to have 10 gigs of my own backed up in a distributed network?  Ignoring all the problems of up-time, and having users stay on the network, you'd have to answer yes to that question, I think.  I'm not sure I would.  What do you think?

Something along those lines would be an open source app, with community support for running it.  We'd be trusting the programmers and the open source community at large to make sure we had decent encryption protecting our data.  As opposed to trusting a company.  It's a bit of a philosophical choice.

Toupeiro, everything from tar to NetBackup that you mention are great software tools.  They're not a service.  I'm not sure I see your point.

I've used tar before, and still do.  It, by itself, is not a backup scheme.

---

