---
title: "I'm a from the beginning Ubuntu user, here are my comments."
date: 2008-01-28
forum: Testimonials &amp; Experiences
---

### Post by jmaryinchina on 2008-01-28
I have been using Linux OS since 1997. Let's say I'm not a newbie. Setting up Linux servers is my job, I administrate them from the command line, I'm writing scripts when I need, patch source when necessary.

I will be tough, but fair. 

Mark has given a new direction to Linux systems :  provide something running out of the box for everybody. The linux ready for your secretary, when she doesn't even know how to install an OS. It was easy to recognize the Debian touch, but everything was polished, providing only what was absolutely necessary to start working : Clean menus, Office suite, mail client client, web browser. Most of peoples needs this and only this. If you are reading that, you are not most of peoples, you made a step toward solving troubles. Something we fail and just accept things as they are : compiz will not be stable with my hardware. Ok I don't use it. That is a minus trouble.

Now the big trouble : upgrading.
The only smooth upgrade I have seen from 5.10 to 6.04LTS. All others have made such a mess that this the reason for which I AM NEVER INSTALLING UBUNTU ON ANY PRODUCTION SERVER. That would be like suicide. On production or (web) development machine I use Debian, that's all. With Debian I can make a remote *apt-get dist-upgrade* with ssh, this from 3.1 to 4.0, go to bed, sleep quietly and wake up with hands on the machine, running the new version.

Once this is said, how can I quietly install Ubuntu in my customer's office with his 50 employees, running heterogeneous hardware if an upgrade will put an *End of the World* with 2 weeks of crazy work to fix everything. That's not realistic. Beside of this I have never seen in 10 years a Debian upgrade putting the mess.

Also in some companies some peoples can have Apple PPC machines, running Linux, how will they upgrade to 8.04 ? They wish it. They are excited by a new version.  

On my own Desktop, I have Feisty right now, not Gutsy, the reason is simple, Gutsy has been the worst Ubuntu version ever made. I have 3 kinds of hardware at home. None of them could upgrade without messing everything. If an upgrade leads to a reinstall (at least, sometimes things simply can't work as they were working before), and as this is every 6 months, how Ubuntu is different than Windows in terms of safety and stability. I don't want an upgrade mess everything, that's not acceptable, because it's not usable.

I hope 8.04 can upgrade smoothly from any version >= 6.06. I guess it will not according to the past experiences. I guess focus will be on 7.10 -> 8.04 and 6.06 -> 8.04.

That will be a test for me, and If I see the same mess as before, I'll go back to Debian. I was running the testing version for years on Desktops without any worry. Debian release cycle is long, but you can be safe from fancy things : Those have been the rule with Ubuntu as I have explained. I'd like to see a NO JOKE at upgrading to 8.04, I'm a professional providing services to my customers they trust me. I prefer to see a perfect 8.06 or even 8.08 than the mess I have seen to any past upgrade except one. Of course some peoples might have a different experience, but the reality is seen at looking topics in forums when upgrade time has arrived.

In order to contribute, I installed 8.04 beta on my old PIIIx2, now I just can't use and test it, it's freezing randomly. It was working fine with Feisty, and was freezing also with Gutsy.

That's what I wanted to say : the concept is good, the base is good, the philosophy also, the softs also, just a lack in terms of quality and stability has appeared. If the boss for releasing is the calendar, we are seeing a policy which definitely can't lead to quality. Calendars are often silly at considering the serious issues.

---

### Post by Whiffle on 2008-01-28
I agree 100%.  I put gutsy on both my computers when it first came out, that was a mistake.  I ended up reinstalling both.  One of them ran okay, the other one got more screwed up with every update.  Now I've got feisty on the laptop and debian etch on the desktop and I'm a happy camper.  I hate to say it but Ubuntu is starting to sacrifice user friendliness in favor of more new software that doesn't always work the way it should, or doesn't work at all (the aumix bug).

---

### Post by forrestcupp on 2008-01-28
Well the good thing about computers is that you are free to use whatever compatible OS you want.  If you don't like or want Ubuntu, use whatever OS you wish.

The thing about all of this is that the small upgrades aren't necessarily meant to be rock solid and ultra-stable.  They are meant to be on the cutting edge, adding new things.  Hence the code names Edgy, Feisty, and Gutsy.  If you need stable, stick to the long term support versions and only LTS.  It's not really recommended to put the smaller, edgier upgrades on enterprise machines.

You say you tried Hardy on a P3 machine and it locked up?  The release isn't for another 2-3 months.  That's a long time in the development process of an OS upgrade.  You can't expect Hardy to be stable yet.

---

### Post by koenn on 2008-01-28
> **forrestcupp said:**
> Well the good thing about computers is that you are free to use whatever compatible OS you want.  If you don't like or want Ubuntu, use whatever OS you wish.

sure, but Canonical's goal is probably not to make people use any operating system but ubuntu. 

I agree with the OP. I stuck with LTS because I need my PC in working order - I can't afford the 6 month breakage cycle. So I don't have personal experience, but I've been reading the forums. Granted, in support forums, there's going to be more noice about trouble than about succesful upgrades, but when people start advising eachother to do a clean install rather than to attempt an upgrade, something's wrong with the upgrades. And having a bit of upgrade troubleshooting every 6 months may be OK for the geeky people, but if Ubuntu is to target 'ordinary' users or corporate environments (and they are, as LTS, paid support, etc suggests ...), 
it needs to be able to handle upgrades way better than this. 

Just like the OP, I have some experience with Debian - and upgrading to the next release in Debian really is painless. I wonder what upgrading to the next Ubuntu LTS is going to be like ...

---

### Post by Spr0k3t on 2008-01-28
Ubuntu is fantastic for a desktop system with multiple users.  Experience has shown that it is only mediocre when comparing the server version with other options in the field.

---

### Post by bobbybobington on 2008-01-28
I have to agree that software updates cause too much breakage. Normal users have to be confident that a small update isn't going to mess everything up. There has to be a more thorough and  careful system for testing updates before they show up on people's taskbar. I think ubuntu is still in the process of trying to find the right balance between features and stability. Perhaps the emphasis on LTS releases needs to be better communicated.

---

### Post by disturbed1 on 2008-01-28
I don't really see the comparsion between running Debian and Ubuntu as a server. Debian is updated, what once every 2-3 years? Ubuntu releases every 6 months. 

If you're running a server, there is absolutely no reason to update between non LTS releases, considering security updates are released.

Since you seem to want the benefits of desktop like computing with constant fresh software, perhaps moving to Debian Testing would be the best bet. This way you can have all the rolling updates you want.

Has anyone ever pondered the reason why so many government entities updated from Windows NT4.0 to linux in 2006? Notice they didn't do point updates between Windows NT 4.0 and 2003 server. A server is meant to be loaded with rock solid software, and kept running stable in the background with the occasional security update here and there. If you're wanting to upgrade your server every six months, you should rethink your policies.

Every *ENTERPRISE* I've ever dealt with always does a test case/trial run on backup machines to ensure there isn't any down time. No one in their right mind would blindly add a single piece of code to a running server without first testing it. This is a strong reason why virtual machines were created ;)

---

### Post by koenn on 2008-01-28
No one in his right mind wantss to update a server every 6 months. But if a new release has something you've been waiting for (support for newer hardware, a feature that can help you get rid of an ugly workaround, ...), you might just consider it, and it would be comforting to know you have a reasonable chance of upgrading withou much trouble. 
And Ubuntu hasn't proven yet that it can handle LTS to LTS upgrades either. I guess we'll see in 3 months or so ?

It's also not just about servers. An enterprise running ubuntu desktops might be interested in a clean upgrade path as well. 

As for testing before installing - of course. But you'd really expect things to go smoothly and test mainly for confimation that it actually will, and to check that any exotic config or 3th party software will survive the upgrade. With Ubuntu, I have the impression that it's not always that simple.

---

### Post by disturbed1 on 2008-01-28
> As for testing before installing - of course. But you'd really expect things to go smoothly and test mainly for confimation that it actually will, and to check that any exotic config or 3th party software will survive the upgrade. With Ubuntu, I have the impression that it's not always that simple.No doubt there. It would be nice to have my cake and eat it too :D

The reality is, in the real world I can never see this happening. Now, if you were to only use the main repo, and have nothing from (multi)universe installed, an upgrade would (should ;) ) go smooth as silk. Even Debian can not handle an upgrade perfectly. It was a nightmare to upgrade from Sarge to Etch. Then again, we moved from xfree to xorg, and 2.4 kernel to 2.6 kernel, plus it was 2 years in between, so that's not a fair comparison :D

I can attest that an Ubuntu upgrade goes one hell of alot smoother than upgrading from Windows 98 to XP. Or even XP (1st release) to XP service pack 2.

You should take a stroll through the RHEL and/or CENTOS forums. Even though these ARE enterprise class system, the upgrades are still not foolproof.

[http://wiki.centos.org/HowTos/MigrationGuide/ServerCD_4.4_to_5](http://wiki.centos.org/HowTos/MigrationGuide/ServerCD_4.4_to_5)

That's a how-to upgrade from a fresh blank install of 4.5 to  5. Now grab a release of 7.04 do a fresh install, then directly reboot into recovery mode, change the apt-sources list with nano, apt-get update && apt-get upgrade.

---

### Post by koenn on 2008-01-28
well, actually, at work I've never upgraded  a server (apart from security patches). We just get a newer OS with a new machine when the old machine is decommisioned - so we only have to worry (and test) that all apps will run on the newer system, and figure out how to migrate data, configuration, etc. MS service packs can be troublesome - sp2 for XP was notorious - but that's not an excuse for Ubuntu to do moething similar, is it ? 

I did, painlessly, upgrade from Debian 3.1 to 4.0 on 3 servers I have at home (but they were already running a 2.6 kernel)
A for Ubuntu, I'll have to see it first. So far, I'm not impressed (by how their upgrades go).

---

