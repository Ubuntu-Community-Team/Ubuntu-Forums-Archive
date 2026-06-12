---
title: "Detecting unauthorized access"
date: 2023-10-07
forum: Server Platforms
---

### Post by monkey-learns-linux on 2023-10-07
I have set up a vanilla **_public_ **ubuntu server 22.04.3 that will be running public Node.js APIs. How do I set up an automatic failproof notification system that notifies me in case of unauthorized access **_or_** unauthorized processes.

I have a crude plan to handle unauthorized processes and that is to record all base processes, and then have a cron job that runs every 10 seconds to recheck list of running processes and notify me of any differences via email from SMTP server. Now I do not know how fool-proof this method is because I keep hearing the term "kernel exploit" which I think means using kernel vulnerabilities to your advantage.

How do I proceed with this? I am very new to system admin but know high level language programming.

---

### Post by TheFu on 2023-10-07
failproof?  It doesn't exist.  Would you like to try again with more reasonable expectations?

Security isn't a checkbox. It is a process that requires decades to master.  

For someone new to Unix, just do as much as you can related to security.

#1 is to have daily, automatic, versioned, backups.  When you start out, you probably can't set that up in the most secure way. Start with simple backups, then add versioning. Then change to networked backups, then change to "pulled" network backups.  When you are all done, you should have daily, automatic, versioned backups that are pulled that retain at least 250 days of backups using less than 2x the source storage. How many versions to retain depends on the risk level/sensitivity for the system and data it has/handles.

#2 is to only run LTS, supported, releases and keep them maintained. I patch weekly. Patching too often is also a security risk. If a system is changing every day, it is hard to know what could be causing any issues experienced.  If it is patched every Saturday morning, then when issues happen later on Saturday, it is a good bet that something related to the patch is responsible.  Plus, "production" systems need to be stable and working most of the time. Patching on weekends limits mid-week issues/downtime.

#3 monitor all your system log files.  There are many ways to do this. For 1 system, something like logwatch is probably fine. Included in this is having all logs sent to a log server that isn't on the front line being hacked at all the time.  Having a remote log server is a best practice, so any hacked system logs can't be trivially modified by the attacker. They are remote already.

#4 is to have a secure network architecture.  If the network architecture is flawed, other things are like spitting into a hurricane.

#5 is to setup restrictive firewall rules that only allow what you need in and out.  Don't allow all outbound traffic, just allow outbound traffic you need.

#6 don't run/install anything extra on the system that isn't required.

#7 setup a server monitoring/alarming system that captures 40-100 pieces of data, constantly.  Monitor the graphs. Look for things that are odd.  As you get 2-6 months of data, patterns will become obvious.

That's probably enough for today.

And for a webserver, look into having remote NFS storage mounted read-only.  Pretty hard for a hacked web server that has read only storage for the website to be modified.  They'd need to hack both the web server AND the NFS server.

Certain software stacks are prone to more security flaws and buggy software. I think it has to do with the quality of the average programmer in those languages and the lack of serious effort by the teams providing centralized software for those languages to prevent bad actors.  node.js and php are two of the worst.  Now that everyone is mad at me for naming their favorite language, it isn't necessarily the language, it is that those 2 languages/environments have a history of hacked code AND of the core teams not taking steps to put security first.  No language is specifically good or bad. It is just the programmers who are and that can often be traced back to having a low barrier to entry.  If there are lots of new programmers coding in a specific language and releasing their code onto the public, it will almost always be crap.

For an email server, I use layered email processing systems.  One is just a gateway that mainly filters junk and blocks bad actors.  There's no email actually stored on that system.  The gateway system runs 20.04 and is patched weekly.  The 219 days of backups are using about ... let me check 30M (not GB!).  Backups can be really efficient if there's no data.```

    increments.2023-03-01T08:38:30-05:00.dir   Wed Mar  1 08:38:30 2023
    increments.2023-03-02T00:03:16-05:00.dir   Thu Mar  2 00:03:16 2023
...
    increments.2023-10-05T00:03:21-04:00.dir   Thu Oct  5 00:03:21 2023
    increments.2023-10-06T00:03:20-04:00.dir   Fri Oct  6 00:03:20 2023
Current mirror: Sat Oct  7 00:03:20 2023
```

I think it is set to hold 366 versions, so none will be removed until that happens.  I built the new gateway server last March, which is why there aren't more versions.  It was running on an 18.04 server and that needed to be upgraded to retain support.

My real email server is an "enterprise communications server" ... which is an easy way to say it is a _bloated crapload of 20 F/LOSS projects_ that are tightly integrated together and likely full of security issues.  The more complex any software is, the more likely it is to have bugs and security flaws.  I keep that ECS away from the internet, which might seem counter intuitive.  Backups for it take a long time ~ 20 minutes and I only keep ... let me check 180 days.  System patching is weekly, but the ECS package has 3-4 updates a year and applying them is non-trivial.  I'm at a point where it is time to build a completely new server and do a fresh install, with data migration for all the users' data.  This won't be fun and I'm not looking forward to it.  It will probably take about 2 weeks of effort to test out everything and fix issues.  Then I'll pick a Saturday and spend 4+ hrs doing everything for real.  My email gateway will be storing inbound emails most of that time. User's won't have any access to their email that day.

cron is 1 min resolution, not 1 second.  Better to run a daemon that does what you want all the time.  Do you really want an email every 10 seconds?  Doubtful.

There are many different system tools for security. They generally come as **IDS** and **IPS**.  Sadly, running these will often eat more storage, network, and CPU than most admins are willing to give up for monitoring.  
In the old days, I remember running **cops**.  It would take a list of all the files on the system and create a checksum for each file.  The file checksums could be tested as desired to see what changed.  For old or new program binaries, you would need to know which had been updated via normal patching on your schedule and new binaries would need to be added to the "golden" list.  I think cops went commercial, but there is probably a new tool that does the same thing.  Or you could create a script to do it. I doubt it would be more than 30 lines, but it probably wouldn't be too efficient.  I'd create a time-stamp-named file for when the checksums are built, then use diff/sdiff or meld to see which actually changed.  Don't forget to gpg-sign each of the created checksum files so you know no tampering occurred. 

Don't put extra stuff on your router.  More code means more bugs and more security issues.  Do you really want the router to be a hacker magnet?  Just because a router CAN do 20 things, that doesn't make it a good idea.  Avoid consumer routers. Use router hardware and software that gets updated at least monthly.  This will typically mean running on low-powered x86-64 hardware with pfsense, OPNSense or OpenWRT. Yep, those are about the only choices. Keep the wire hardware outside the router.  A router like described should last 10+ yrs and run $100-$150.  Wifi standards change faster, so having an external wifi-AP means you can swap that part out as standards change and flaws that can't be fixed in software occur.  I avoid wifi myself and only have it provided for guests. Any wifi access sits outside my real networks and is considered "untrusted".  Wifi devices need to run a VPN client to access internal LAN resources.  IoT devices can't do that and are stuck on an ISP-controlled LAN that isn't internal, nor external.  This an FBI recommendation.

I've been cracked 3 times since the early 1990s.  
Once, I prepared the system specifically for that expectation, but also did a fresh install and patched it before entering a hazardous environment.  I didn't really expect to be hacked, but was.  
The other 2 times were in 1994 and 2002, both were related to my ignorance as an admin.  
The first time, I really deserved it. I left the root account enabled and with a default password.  
In 2002, a network daemon was hacked. I was a few months behind on my patches - it was a different time.  Anyway, a script got in and was trying to get root access, but that never happened. I was able to compare the most recent backup against all the files that were currently on the system and found the crackers had been trapped into a low-privilege account that could only write/create files under /tmp/.  I was able to see how they tried to hide their tools and how they were attempting to get root access using a timing bug in a scripting language ... that I used and had patched. Basically, every attempt sent me an email. I saw their multi-thousand attempts and failures because my email was full of unread messages.  You've probably seen where people say never to use 777 permissions.  If I'd use that, the hacker(s) could have found all those files/directories and done some real damage.  

**Don't use 777 permissions.** Don't know how to say that any clearer. 777 is for lazy people.

---

### Post by ian-weisser on 2023-10-07
Hot dog.

That's a whole semester course in practical security ... in a single post.

Gonna print that one.

Thank you.

---

### Post by TheFu on 2023-10-08
Check out Bob Toxen's book "Practical Linux Security" - I think that's the name (could be slightly wrong).  Bob's retired now, but he shows up at our LUG meetings from time to time.

I'm gonna fix some grammar and add a little to my post #2. Nothing material. Just clarifications.

---

