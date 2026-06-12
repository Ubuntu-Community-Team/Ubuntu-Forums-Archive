---
title: "FreeNAS. Openfiler. What is optimal?"
date: 2011-05-04
forum: Server Platforms
---

### Post by Roasted on 2011-05-04
I've been tinkering with both recently to see what can suit my needs as a simple raid1 mirrored backup server. I used FreeNAS for all but minutes before I had a raid1 array running and shares set up through CIFS. Using Ubuntu on my laptop I was able to see them as well. I had some more figuring out to do, as I wanted each share to be blocked off from the other. aka - I didn't want "fred" to be able to access "bob's" share. 

So then I move on to Openfiler to check it out. I hear it's simpler. It's web interface, while no doubt much slower than FreeNAS, was easy to mingle around. At first glance, I thought I'd like it more.

I began to set up my raid1 array. After realizing the final release I was dealing with had a bug, I found some commands to run in a root shell to fix. Okay, so now we're moving along... raid1 array created. Then I had to create a volume group. Then a volume. Then shares. And I still don't have it running over cifs.

So I'm a little confused now, because guides I read comparing the two said they were both VERY easy to use.

Has anybody here used both that they can fill in some blanks for me? I'm curious if FreeNAS by nature is truly simpler to set up raid array's with, or if maybe I'm just totally misunderstanding Openfiler and that be the reason why I'm thinking this.

If anybody can fill in the blanks, I'd greatly appreciate it. Thanks!

---

### Post by tgalati4 on 2011-05-05
I've used freenas over the past year.  I have it running on a Pentium 1 white box, overclocked to 188 MHz.  It has 256 MB of RAM (maxed out).  I'm running version 0.7.2  Version 0.8 is in beta and it's a complete rewrite using a database model to store settings instead of configuration files.  So I would stick with 0.7.2 if you want full functionality.  0.8 may take a year or so to catch up.

I haven't used Openfiler so I can't comment.  Freenas is rock solid.  It has built-in UPS support so you can plug in an UPS and it will shutdown when the power goes out--gracefully.  It also has a mini package system that allows you to install packages for more functionality.  I haven't done that yet, but it's there for tinkering.

Freenas does the file sharing quite well.  Easy to use is relative.  It's easier to set up than a full-blown Ubuntu server.  It's easy to migrate between computers.  You can load your freenas configuration onto a USB disk, move it to another computer (built the same way) and restart it and all your shares and services continue as before.  

You can also run off of a USB disk or CD and run in RAM and store your configuration on a USB disk or floppy.  One less disk to fail.

Freenas is a BSD/Unix variant--stripped down to the bare minimum.  So there are subtle differences between linux and freenas commands and procedures.  There's an extensive freenas forum and several guides and blogs on the web on how to set it up.  You have to spend some time reading to really appreciate how compact freenas is for its functionality.

Any aftermarket NAS that you buy will have braindead firmware in it. Unless it's running freenas.

So, yes it's easy, but you have to spend some time to learn it.

---

### Post by Roasted on 2011-05-05
FYI, version 8 was just released. That's what I'm using. I'm unsure of what's different between 7 and 8 but I just stuck with the most recent stable.

I think I may be sticking with FreeNAS, but I just want to hear more about Openfiler because I don't want to choose FreeNAS because I can't get Openfiler working. I want to get them both working and choose accordingly.

So far I just feel like Openfiler is a bit heavy, cumbersome, and has a lot of extra layers with setting up basic settings... moreso than what's needed. But on the flip side, I'm far from an expert, so I'm also taking into account maybe it's just me not understanding what it's underlying reasoning is. Hence, me asking here. :)

---

### Post by tgalati4 on 2011-05-05
You should use 0.7.2 to get full functionality.  8 is pretty, but a lot of stuff still doesn't work or hasn't been added back.  It's a complete rewrite, so it's not ripe yet.

---

### Post by Roasted on 2011-05-06
> **tgalati4 said:**
> You should use 0.7.2 to get full functionality.  8 is pretty, but a lot of stuff still doesn't work or hasn't been added back.  It's a complete rewrite, so it's not ripe yet.

Really? 8 sure does work well, though. It seems very feature packed. I wonder what's missing from version 7...

---

### Post by tgalati4 on 2011-05-06
Media streaming.

---

### Post by Roasted on 2011-05-11
Does anybody have anything else to offer about OpenFiler? I've got my FreeNAS box set up in its final stage but now I want to make sure I can get OpenFiler running, as the fact it's Linux based and up my alley really intrigues me to want to use it even more. Can anybody offer some insight with OpenFiler?

---

### Post by spynappels on 2011-05-11
I found that Openfiler was a good start, but it really did not like multiple GbE NICs on different subnets and gave me a lot of trouble when I tried to set it up as an iSCSI SAN.

Using FreeNAS as an iSCSI SAN was also problematic but I knew it probably would be as it did not claim to have a native implementation of iSCSI but it emulates it IIRC.

FreeNAS was definitely easier to set up for Samba and NFS shares though.

---

### Post by Roasted on 2011-05-13
After some further tinkering, I am sticking with FreeNAS. I feel like I had to fight extensively to make OpenFiler work, and even then I wasn't able to get it working. My frustration began when I found some very well thought out how-to guides and videos. Even following on a fresh install with step by step instructions I wasn't able to duplicate the same results. This was true for the latest 2.99 version as well as their "stable" 2.3 version. Frustrated, I found someone who did manage to use both FreeNAS and OpenFiler extensively, and their opinion was shared by me, that they had to re-do their steps (yet, the same exact steps) 3 or 4 times to get it to play nice. At least by then I felt it wasn't a complete user error. I liked using OpenFiler. Very clean gui, laid out nicely, etc. I just couldn't get the job done with it.

FreeNAS was easier to set up, easier to manage, the web GUI was quicker, and it was more versatile for my needs. The more I use it, the more I love it.

Kudos to OpenFiler's dev team, though. I'm sure they put a lot of work into it. It just wasn't able to produce predictable results for my instance.

---

### Post by SteveHillier on 2011-06-14
Hi Roasted, didn't know I would find you here as well.
We have had a production machine out with a client running FreeNAS for about 18 months now without any problem.  We can get remote access to the Web GUI, we can ftp into it.  It is configured as a single shared directory for Windows Users and I would recommend it.
Now, Openfiler.  We have recently launched a new site called Linuxcomputinguk.co.uk where we are specifically trying to promote Linux products so I thought I really should try and find a Linux NAS server rather than a FreeBSD base and I came across OpenFiler.
So today I got an install going.  
Using 2.99.1, after doing all the network setup, password etc the system spends 3 minutes (well 2.42 actually) to do the install and then goes away for 10-15 minutes seemingly doing nothing before eventually saying it is ready for a reboot.
After the reboot I get the web GUI and type in root and my password and get presented with a user account quota page.
I tried the UK support desk.  They were all out at lunch, oh and by the way they do not take phone calls unless you have paid for a support contract.  I spoke with sales who said they would put me in touch with the Partner support team.  6 hours later I am still waiting for a response.
Think I had a bum install I reinstalled.  No change.  I have now tried 4 installs of 2.99.1 and 2 installs of 2.3.  And where am I now, nowhere forward from lunchtime.  I even put in a call to the States but still have had no response (except to ask for my contact details which had been at the foot of every email I  have sent them).
In the end I had a look at the install guide on their webpage.  I do not expect that after more Linux installs than I care to remember that I should need to look at the install guide.  What is it they say, manuals are for those who just can't hack it themselves.  Something like that anyway.  But right at the bottom of the guide is the gem.  Log on as user openfiler, password password.  Boy, why can't that be displayed on one of the install screens?
So I got in to the web gui to set up the system.  Can I set up a volume?  Can I, hell as like!  No volume, no share, no usable system.:(
For me it is back to FreeNAS.:D  And just as a final thought.  The FreeNAS server we have out in the field has the operating system on a 1 GB memory stick not using up valuable disk space.
Wait til I get going on our Blog site!

---

### Post by rubylaser on 2011-06-14
I normally just roll my own NAS, but if I had to choose between FreeNAS and Openfiler, I'd always go with FreeNAS in this case.  I would never spend 6 hours waiting for an answer like the default user name and password though.  Google really is a system admin's friend :)

[http://lmgtfy.com/?q=openfiler+username+password]("http://lmgtfy.com/?q=openfiler+username+password")

Almost all of those link have the username and password right in the synopsis, without even opening up the page.

---

### Post by tgalati4 on 2011-06-14
I think a big plus of FreeNAS over OpenFiler is being able to use the ZFS file system for enterprise applications.  I just set up 2 x 1 TB drives in a ZFS mirror configuration to play around with.  ZFS gives extra data integrity by computing and comparing stored checksums for each file stored.

---

### Post by Roasted on 2011-06-15
I ended up ditching FreeNAS. FreeNAS seems to have a bug with CIFS shares, as I was not able to write more than 574 files to my CIFS share before getting invalid argument. 575 and it would tank.

FreeNAS in general makes me a little shakey. You have version 0.7.2 and version 8. It seems as if it's almost forked. FreeNAS 8 is pushed heavily by IX Systems, which is all well and good. Then you have the 0.7.2 team which are mostly FreeBSD developers. But they tend to work semi independently.

Likewise, you have Oracle, who absolutely sucks. Oracle owns ZFS now since they took over Sun Microsystems, and is closing the ZFS code. So now that's forking ZFS to be closed ZFS and open ZFS, with open ZFS being backed by Illumos, which came up after Oracle killed OpenSolaris. Illumos is backed by a few small companies, but nothing substantial.

So you have OpenSolaris which died. Then came Illumos to replace. Then you have ZFS split between closed/open forks. Then you have FreeNAS being split as well. While the web gui for FreeNAS was sweet to use, it didn't take away from the fact I have thousands of files to back up. 574 won't cut it. Sure, it's a bug that could be fixed, but seeing all of this forking in this area of the community makes me shakey to rely on it.

That said, I put Ubuntu on my file server with a software RAID mirror, and it's been running 100% flawlessly ever since. Zero complaints. I should have just done this from the get-go...

---

### Post by SteveHillier on 2011-06-15
> **Roasted said:**
> I ended up ditching FreeNAS. FreeNAS seems to have a bug with CIFS shares, as I was not able to write more than 574 files to my CIFS share before getting invalid argument. 575 and it would tank.

I find that odd.  Our client has a lot more that that number of files on FreeNAS.  They have over 100GB of data - mostly photos of around 300KB each.

---

### Post by SteveHillier on 2011-06-15
> **rubylaser said:**
> I normally just roll my own NAS, but if I had to choose between FreeNAS and Openfiler, I'd always go with FreeNAS in this case.  I would never spend 6 hours waiting for an answer like the default user name and password though.  Google really is a system admin's friend.
Thanks rubylaser.  It was not as if I was doing nothing while I was waiting.
As to the comment about Google, You are right. but you also need a couple of other things in your mind,
1.  You need to make sure you have not got a bum install.
2.  You have to know that what you are looking at is not what you are supposed to be looking at.
3.  And you have to know that user 'root' will not get you where you want to be.
When I first installed ClearOS back end of last year.  I installed it, setting the root password and when I logged on I used root and made the rest of the configuration changes.  Is there something wrong with that approach?
Steve

---

### Post by tgalati4 on 2011-06-15
I agree, there are a lot of unsettling changes in the open source world.  If you want an enterprise-ready zfs solution, then Oracle will gladly sell you a solution.  If you want an open source zfs solution, then, yes you are taking your chances.  Dell bought Compellent storage solutions in February.  They had a ZFS SAN that looked pretty cool and had a lot of enterprise goodness.  With the wonky ZFS licensing, I can see Dell dropping that technology like a hot potato.  No answers from a Compellent employee that I spoke to recently (who now works for Dell).  

FreeNAS 8 was a complete rewrite (using AJAX and Ruby-on-Rails) versus the MoNoWall GUI, and the parameters are now stored in a database instead of several different configuration files.  This makes web-based modifications easier than committing changes to config files then restarting services.  And yes, FreeNAS is being pulled in different directions, that is the nature of open source.

I would only put FreeNAS on a box that can't or won't run Ubuntu server.  I have mine running on a 188 MHz whitebox PC from 1997.  I'm just playing with it.  It's not an enterprise solution, but it's low-voltage and it works.  Ubuntu server would run on the same box, but it's not as lightweight as FreeNAS.

I'm not aware of the CIFS bug that you speak of.  I haven't seen it in 0.7.2 and I've moved a lot of files around, but only mac and linux, no Windows machines on my network.

---

### Post by Roasted on 2011-06-16
> **tgalati4 said:**
> I agree, there are a lot of unsettling changes in the open source world.  If you want an enterprise-ready zfs solution, then Oracle will gladly sell you a solution.  If you want an open source zfs solution, then, yes you are taking your chances.  Dell bought Compellent storage solutions in February.  They had a ZFS SAN that looked pretty cool and had a lot of enterprise goodness.  With the wonky ZFS licensing, I can see Dell dropping that technology like a hot potato.  No answers from a Compellent employee that I spoke to recently (who now works for Dell).  

FreeNAS 8 was a complete rewrite (using AJAX and Ruby-on-Rails) versus the MoNoWall GUI, and the parameters are now stored in a database instead of several different configuration files.  This makes web-based modifications easier than committing changes to config files then restarting services.  And yes, FreeNAS is being pulled in different directions, that is the nature of open source.

I would only put FreeNAS on a box that can't or won't run Ubuntu server.  I have mine running on a 188 MHz whitebox PC from 1997.  I'm just playing with it.  It's not an enterprise solution, but it's low-voltage and it works.  Ubuntu server would run on the same box, but it's not as lightweight as FreeNAS.

I'm not aware of the CIFS bug that you speak of.  I haven't seen it in 0.7.2 and I've moved a lot of files around, but only mac and linux, no Windows machines on my network.

It is a known bug. I've seen it posted on LaunchPad because the original poster of it thought it was an Ubuntu bug, because he only had this issue with Ubuntu and not Windows. The user who posted the bug had a cap of 627 though, unlike my 575. I ended up doing it one file at a time to find that exact number.

But I talked to Samba developers extensively. They walked me through doing a ton of command line testing to confirm it was indeed a bug on FreeNAS's end. And yes, it was only with FreeNAS 8, but it didn't matter if it was UFS or ZFS, which kind of took away ZFS as being the culprit, which I originally thought it may be. So it's a bug in regard to the way Linux/CIFS talks to FreeNAS, but oddly, it's not a Samba/Linux bug. It's something on the FreeNAS end. Very weird, but whatever.

FreeNAS is awesome when it comes to running it on old hardware - assuming you're not using ZFS. They boast about ZFS and how great it is, yet they also boast about how FreeNAS is so easy to run on old hardware. Both things are very true, but both things cannot be had *together*. If you want ZFS you need considerably more horsepower to handle it. I had FreeNAS running on a Pentium 2 box with complete ease. But at the end of the day, I can run a tiny Linux distro or a Linux server variant to do the same job too.

I agree, the nature of open source warrants potential changes being had. It's not that I have a problem with the two FreeNAS variants, as they seem to co-exist just fine. What bothers me is what Oracle is doing with ZFS and how it killed OpenSolaris. So it's nothing against ZFS in particular or FreeNAS, but more so there's just a ton of tension in the air right now and I'm curious to see what the outcome will be. I'm just glad the nature of open source didn't let OpenSolaris die, thanks to the Illumos project.

But like I said, at the end of the day I just need a server that works, and Ubuntu does the job just fine and my mdadm software raid is working without issue. It also helps in my case to keep Linux because I also run ZoneMinder with a wireless IP camera, which is Linux based CCTV for video surveillance. That way my camera feed is being backed up on the file server as well.

So overall, all fingers just pointed to this direction, and I'm glad I stuck with it.

---

### Post by SteveHillier on 2011-06-17
Roasted, I take my comment about file limits back.  Our client is running 0.7.2 not the version you have got.

Just for others there is another thread running along using ubuntu as a NAS server.  The OP might benefit from our combined wisdom (or perhaps I mean experience).

[http://ubuntuforums.org/showthread.php?t=1773695]("http://ubuntuforums.org/showthread.php?t=1773695")

---

