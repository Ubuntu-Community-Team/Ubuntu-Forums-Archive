---
title: "How Long Has Your Server Ran Without Crashing?"
date: 2011-01-10
forum: Server Platforms
---

### Post by garryconn on 2011-01-10
I have a few headless servers running in my home office and I can easily see how these machines could get lost or forgotten. Linux is such a beautiful operating system it often puzzles me why it isn't more popular. People say that Linux isn't user friendly, but honestly I think it's more user friendly than Windows. If you took two people who have never used a computer before and sat one down in front of a computer running Linux and the other person in front of a computer using Windows, I'd like to believe that the person using the Linux computer would excel much quicker. 

Anyway, if you have a server running out of your home, or office, how long has your server ran without it crashing? Secondly, compare that figure against how long a computer running Microsoft has run without crashing or forcing a restart.

---

### Post by aceofspades686 on 2011-01-10
Roughly a year, and then only because the hard drive went kaput.

---

### Post by Skadork on 2011-01-11
longest my ubuntu ran was around 100 days till there was a power outage and my battery ran out of juice :(

A Win2K server I administer has been up and running for over a year :)

---

### Post by Neo@Matrix on 2011-01-11
> **garryconn said:**
> 

Anyway, if you have a server running out of your home, or office, how long has your server ran without it crashing? Secondly, compare that figure against how long a computer running Microsoft has run without crashing or forcing a restart.

My servers on win worked for over 2 years without even restart.
Some of my servers on Linux with Apache are now running for : > **System uptime** 392 days, 12 hours, 05 minutes

---

### Post by kg4cna on 2011-01-11
Before I shut mine down for an upgrade/rebuild, it was up for 183 days. Old Red Hat 9 box.  Now sporting Ubuntu 10.04.1 LTS server :)

A~

---

### Post by Thirtysixway on 2011-01-11
> **aceofspades686 said:**
> Roughly a year, and then only because the hard drive went kaput.

Yeah I had mine for about 377 days, rebooted to do security updates and it never came back online.  After some hard work over the phone it was the drive that crashed.  It could have kept going if I didn't reboot.

But it's not a good idea to let your server go that long.  Unless you're using something like ksplice, you're going to be missing security updates in the kernel when you don't reboot.  So if your running your server for.. say 392 days, it's best not to advertise that :p

---

### Post by HermanAB on 2011-01-11
My previous home server ran for almost 5 years continuously till the PSU burned out.  The present one has been going just over a year now.

---

### Post by perspectoff on 2011-01-12
Have had a BSD DNS server running since 2003 without touching it (except to add new addresses).

---

### Post by James78 on 2011-01-12
I'm always restarting my server, so maybe 2 weeks or so. It didn't crash, but like I said, I restart too often. I hope to finally go all the way, and something like 377 days. Restarting the server after that would be IMPOSSIBLE as you don't want to loose your long record. :) Also, those kernel updates make you restart. :(

> **perspectoff said:**
> Have had a BSD DNS server running since 2003 without touching it (except to add new addresses).Insane!

---

### Post by chrislynch8 on 2011-01-12
Out of 30+ Ubuntu servers, only two have ever crashed in the last three years. But when they crash boy do they crash, required a full rebuild after days of trying to figure out what happen

But I also have a windows server, and that has never crashed on me, but it isn't doing much.

PCs will always crash more Windows/Linux/Mac as 99.999999999% of the time its the user using the PC that has caused the problem.

Rgds
Chris

---

### Post by bsntech on 2011-01-12
I typically reboot mine every now and then - usually the servers are rebooted once every three months or so.  This is done just to refresh them or when I do full system backups on a separate hard drive that is done remotely.

I actually had one of my servers fully lock up a few weeks ago.  Nothing in the logs showing the cause of it - but I can only think it was related to a memory issue.

Other than that, I've never once had any lockup on the servers.  With Windows servers, I was constantly having problems it seemed.  Makes it even harder when you remotely administer everything.

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

### Post by mathieu_ on 2011-01-13
I have a server that has been running Ubuntu 8.0.4 (server edition) for over two years now. I only reboot it when there's a kernel upgrade or when I have to replace a failing disk (I'm using software RAID 1 with automated notification of failure). It has never crashed.

If it wasn't for the kernel upgrades or the flakey disks, I suppose it could run forever.

---

### Post by James78 on 2011-01-13
> **mathieu_ said:**
> I have a server that has been running Ubuntu 8.0.4 (server edition) for over two years now. I only reboot it when there's a kernel upgrade or when I have to replace a failing disk (I'm using software RAID 1 with automated notification of failure). It has never crashed.

If it wasn't for the **kernel upgrades** or the flakey disks, I suppose it could run forever.
KSplice. :D

---

### Post by Thirtysixway on 2011-01-13
If your server is sitting on something more dependable than home electricity, or even on a UPS, I would imagine it's not too difficult to get your servers uptime way up there.  My issue was always small power outages at home.  Pretty much my server uptime used to indicate the time between outages :p

I have some winXP servers that we never reboot.  I imagine we could have put server on them but they're used to stream a radio station broadcast online using icecast.  Not sure what its uptime is, though I imagine windows update reboots it every once in a while.

---

### Post by JohnYYC on 2011-01-13
Where I work we have server's that have been up for 8+ years. :)

At home my record uptime is about 2 years.

---

### Post by darkhelmetchris on 2011-01-13
I have to say, I **really wish** I had known about Linux-based operating systems earlier in my life.  I have now had the pleasure of being Linux-based for about 6 years.  I suffered with "that other option" far too long just because (at the time) I didn't know any better.  The move to a Linux-based OS (both for servers and workstations) has provided me with far less maintenance costs, far less licensing costs, far less headaches, more speed, more options, more flexibility, and more money in my pocket for other things.

Thankfully, the power grid in my area is quite stable, and only suffers brief outages, so a small UPS has protected me from outages for years.

I am pleased to report that my own personal record for uptime is just over 2 full years:
> 16:00:50 up 741 days,  2:21,  1 user,  load average: 4.99, 5.01, 5.03 *and the only reason I had to power it down was to change a faulty CPU cooling fan.*  Being prudent, I took a brief pause to replace the hard drives at the same time (thanks dd) as they are moving parts and I care about my data.

I am also pleased to report that with "that other option" for an OS, I had been restarting that server at least once a month on that very same machine, that very same hardware, that very same UPS, that very same cabling, absolutely no other changes except the calendar date and the OS.  Once it was Linux-based, it was smooth sailing and my uptime just kept going up, the way it should be.  Thus, no one can convince me that it's the hardware that makes the difference.  I have seen the same type of scenario on many servers that I have converted for my customers; it just makes good sense.

I hope that millions, if not billions, of you have this same enlightening experience.

---

