---
title: "ISO will increase to 750MB"
date: 2011-11-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ubername on 2011-11-06
[http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html](http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html) from [http://ubuntuforums.org/showpost.php?p=11427715&postcount=5](http://ubuntuforums.org/showpost.php?p=11427715&postcount=5)

> The reason only 50MB were added is to make sure there's not too much stuff added on the ISO just because it's possible.

Does this make sense to anybody? I would have thought that as soon as you abandon the previous constraint (CD size), you might as well move up to the next constraint (1Gb USB stick ? 4GB DVD ?)

It seems akin to saying 'There's no point making the ISO 700 MB just because we can fit that on a CD - we should be going for 550MB'

---

### Post by dino99 on 2011-11-06
no sense to me, use & will use mini-iso as long as they dont drop it (hope so :))

---

### Post by lucazade on 2011-11-06
why not purge esotic fonts, multi language locales, legacy gtk2 themes, tons of old and useless small utilities in the ubuntu-meta package and install them if necessary via internet?

I think they can find more than 50mb with a good cleaning up instead of breaking the cd size.

---

### Post by Matti L on 2011-11-06
No sense especially with LTS 'cause that's the only image I might burn (others I boot from USB).

---

### Post by MacUntu on 2011-11-06
Minimal: < ? MiB,
Small: << CD size,
Normal: < 1 GiB.

Where's the problem?

I guess 750 MiB gives enough room due to the removal of Mono, but I don't know why they couldn't have added back some goodies like GIMP and gone for a 1 GiB limit. I know, the goal is to make it easy for users to install their stuff on their own, but I choose Ubuntu in the first place because I **hadn't** to install tons of stuff after setting up the OS. :-/

---

### Post by kaldor on 2011-11-06
> **ubername said:**
> Does this make sense to anybody? I would have thought that as soon as you abandon the previous constraint (CD size), you might as well move up to the next constraint (1Gb USB stick ? 4GB DVD ?)

It seems akin to saying 'There's no point making the ISO 700 MB just because we can fit that on a CD - we should be going for 550MB'

Well, 750 mb is enough to fit in a lot more stuff without going overboard. In some places with slow download speeds, 750 vs 1 GB is a huge difference and could be a problem. 

As far as materials go, DVDs are the same price as CDs are in my area and both are equally attainable. Either way, I always use a liveUSB. It'll take me just an extra couple of minutes to download.

I can't really imagine it being a problem for the vast majority of Ubuntu users.

---

### Post by MacUntu on 2011-11-06
> **kaldor said:**
> In some places with slow download speeds, 750 vs 1 GB
If you have trouble downloading 1 GiB, then you almost certainly have trouble downloading 750 MiB - IMHO. That's an argument I'm not willing to buy.

---

### Post by Matti L on 2011-11-06
Here's a thought:
[Use xz compression (lzma)]("http://linux.slashdot.org/comments.pl?sid=2510526&cid=37956482")

---

### Post by kaldor on 2011-11-06
> **MacUntu said:**
> If you have trouble downloading 1 GiB, then you almost certainly have trouble downloading 750 MiB - IMHO. That's an argument I'm not willing to buy.

When I had a much slower internet connection, the difference between ~700 MB and ~1 GB was about 45 minutes.

---

### Post by kansasnoob on 2011-11-06
For the most part I think this is OK, but ............

What about those who don't have a DVD drive and can't afford hardware upgrades or a USB flash drive?

Or has Ubuntu become victim to so much "bloat" that we assume those with older hardware with resort to either Xubuntu or Lubuntu?

And, if we must cross that boundary why limit things to 750MB?

I'd think it would make sense to go "balls-to-the-wall" and install all of the stuff that's been left off of the iso's over the past few dev cycles.

I particularly remember SABDFL arguing against a GUI to adjust 'notify-osd' because it would create "bloat", but now we've accepted "bloat" to intro Unity/Gnome3 :confused:

Seems odd to my simple mind, but I'm simple minded :)

---

### Post by philinux on 2011-11-06
Stop the press there is an update to this.

 [http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/](http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/)

---

### Post by effenberg0x0 on 2011-11-06
I gave up using burned CDs a while ago. It's slow to burn the ISOs, I had many problems with badly burned disks (depending on the writer quality), got tired of having to take a bunch of CDs everywhere, etc. Not to mention CDs tend to get scratched easy, I had to burn images again, it was a pain in the ***.

I find DVDs even worse to burn, carry, protect, use, etc. 

A 4GB USB costs peanuts, it's faster to read/write, lighter to carry, don't get scratched, etc, can hold more ISOs, etc. You can have a persistent partition like 1GB, etc. Many, many advantages over traditional media. Not to mention nowadays one can get USB Sticks even for free in promotional gifts, etc. I have a drawer full of them. Even portable USB HDD is incredibly cheap now considering what they used to cost 1 or 2 years ago. One can get a 120/160/250GB unit very cheap. Some mobiles, like mine, also act as USB units when plugged to USB port and use the SDCARD as the media. 

I usually keep my ISOs in dedicated partitions, to eliminate the need for any external media.

Also, most netbooks and tablets already dropped ODD units. ODD is dead technology IMHO...

**EDIT: **Another relevant point is that gnomes love to steal optic media as much as they love pens and lighters. I could never find ODD media when I needed it. I think they use it as mirrors, etc.

---

### Post by jerrylamos on 2011-11-06
Oink, oink.  

The CD size helped keep Ubuntu's weight down.  Now I'm looking at a 4 GB pen drive - and even larger ones are coming.

Oink, oink.

Jerry

---

### Post by cariboo on 2011-11-06
@jerrylamos, currently 4GiB thumb drives are selling locally for $8.00, you cn buy at least 2 for the price of a 100 disc spindle of writable DVDs, and they are reusable, so you are  actually saving money with the move to a larger than CD image. :)

---

### Post by dniMretsaM on 2011-11-06
I don't have a DVD burner (old computer), but I was planning starting to use LiveUSB's anyway (found out I actually CAN boot from USB's. Yay!)

> **Matti L said:**
> Here's a thought:
[Use xz compression (lzma)]("http://linux.slashdot.org/comments.pl?sid=2510526&cid=37956482")

+1 I can honestly see this format taking over the GNU/Linux compression world. I'm starting to use it for all my compression needs.

---

### Post by ranch hand on 2011-11-06
> **MacUntu said:**
> If you have trouble downloading 1 GiB, then you almost certainly have trouble downloading 750 MiB - IMHO. That's an argument I'm not willing to buy.
Having only recently come from 4.4kb/sec to 320kb/sec DSL I have no trouble agreeing with you at all.  That is just a lame excuse.

I have no trouble with the Mandriva LiveDVD and it has 3 DEs on it so you can install one or any combination of the 3.  Has always seemed like a smart way to go.

You can boot to any of the 3 for a Live Session.  Great for showing off an OS.

---

### Post by sartic on 2011-11-07
Stupid idea. CD or DVD size for optical media. Even 4GB usb stick are cheap today! What I am angry in Ubuntu must stuff as example samba is not included in cd size! Even new DVD RW is cheap. I think it is time to put as much software on DVD media (cca 4.2GB). Even in dial up era I had in my country volunteers that records media and sent u by mail.

---

### Post by jerrylamos on 2011-11-07
Ubuntu is right on Microsoft's heels,

Bigger, faster, newer hardware only.

Won't boot from USB or DVD like my IBM Thinkpad T40?  Simple, go buy a new notebook for several hundred dollars and throw the T40 in the trash.  

The T40 comfortably runs Oneiric Ocelot flash videos and multiboots Lynx, Narwhal, Ocelot but won't boot USB or DVD. Pangolin says trash it. 

Jerry

---

### Post by effenberg0x0 on 2011-11-07
> **jerrylamos said:**
> Ubuntu is right on Microsoft's heels,

Bigger, faster, newer hardware only.

Won't boot from USB or DVD like my IBM Thinkpad T40?  Simple, go buy a new notebook for several hundred dollars and throw the T40 in the trash.  

The T40 comfortably runs Oneiric Ocelot flash videos and multiboots Lynx, Narwhal, Ocelot but won't boot USB or DVD. Pangolin says trash it. 

Jerry

I use Plop ([http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)) on machines that, for one reason or another, won't boot from USB. It boots from CD just enough to load a working USB driver. It's a nice piece of software.

I recently installed Windows 7 in a friend's (actually my boss) new netbook (a Lenovo). It has no ODD. The only possible Windows 7 installation, as recommended by Lenovo, was to use any available online tool to convert Windows 7 ISO to a USB or install via network. Many PC manufacturers have already dropped ODD and create a "Recovery Partition" in the HDD with the Windows ISO inside it. There's a recovery button or boot option that mounts this partition.

There are four factories (soon to be three) in the world for ODD, all other brands are simply OEMs/CMs. The global ODD business is down 40% from what it was 3 years ago. BluRay units for entertainment do grow, but over a small installed base and it simply is not giving the previously expected return. Investors are dropping Combo Drives completely and will try BluRay for a little more time. PC ODD is also not aligned with miniaturization of laptops, the freedom of movement of tablets and cloud storage / online applications, SaaS/ASP, which are the growing trends and where the money is.

The future is having an external (USB/FireWire, eSATA, etc) ODD at home, or share a network/nas ODD at SOHO segment. External cases for ODD, that adapt SATA/IDE to USB, are broadly available for very low money and do work ok. People with netbooks/tablets are buying them.

---

### Post by philinux on 2011-11-07
I think some may have missed the link I posted.

> Update: It&#8217;s not actually confirmed that the size of 12.04 will be 750mb. Rather, if it has to go over 700mb, then that&#8217;s okay &#8211; however the developers will still try to keep it under the CD-R limit.

Effenberg has a fair point re ODD's though. Although they will continue to be in use for quite some time yet.

I've now switched to usb stick for iso's now as both my "old" desktop and my newish netbook can both boot from usb. I also have a few dvd rw's for really old machines.

---

### Post by kansasnoob on 2011-11-07
> **effenberg0x0 said:**
> I gave up using burned CDs a while ago. It's slow to burn the ISOs, I had many problems with badly burned disks (depending on the writer quality), got tired of having to take a bunch of CDs everywhere, etc. Not to mention CDs tend to get scratched easy, I had to burn images again, it was a pain in the ***.

I find DVDs even worse to burn, carry, protect, use, etc. 

A 4GB USB costs peanuts, it's faster to read/write, lighter to carry, don't get scratched, etc, can hold more ISOs, etc. You can have a persistent partition like 1GB, etc. Many, many advantages over traditional media. Not to mention nowadays one can get USB Sticks even for free in promotional gifts, etc. I have a drawer full of them. Even portable USB HDD is incredibly cheap now considering what they used to cost 1 or 2 years ago. One can get a 120/160/250GB unit very cheap. Some mobiles, like mine, also act as USB units when plugged to USB port and use the SDCARD as the media. 

I usually keep my ISOs in dedicated partitions, to eliminate the need for any external media.

Also, most netbooks and tablets already dropped ODD units. ODD is dead technology IMHO...

**EDIT: **Another relevant point is that gnomes love to steal optic media as much as they love pens and lighters. I could never find ODD media when I needed it. I think they use it as mirrors, etc.

While there is a lot of truth in what you say I'm an iso-tester and I've frequently found it almost necessary to keep older images during a test cycle.

That is; it's not at all uncommon now to have testing begin about 4 days before each release, less so during alpha stage.

So once Beta 1 (or beyond) hits it would not be uncommon to have to burn 4 or 5 discs during testing. In fact Oneiric final was quite a disc burning sensation :)

There was a sort of "unofficial" release candidate followed shortly by the final testing and since I test both Ubuntu and Lubuntu (and some alternates) I burned through about 35 to 40 discs within 10 days :D

That's not really a problem for me, but I frequently find it helpful to keep older images/discs during iso-testing to provide info needed in bug reports.

The expense of keeping 40 or 50 small flash drives aside it would be a nightmare to keep track of them. I guess I could use baggies with labels, but what about static? I suppose there are anti-static baggies.

Please read this:

[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

But, for me, the cost of DVD's is not a problem. I think they cost about 1 to 2 cents more each than CD,s. It really won't effect me.

But my greatest concern is that it will effect a lot of folks that still don't have DVD drives :(

I'd guess that about 1/2 of the people I have running Ubuntu 10,04 have only CD drives, and many of them depend on public assistance just to survive. Hardware upgrades are totally out of their grasp financially.

Regardless I can certainly deal with their installation needs because I can install for them using either a USB flash drive or a USB DVD drive.

But we must remember that there are a lot of people much worse off than we are ;)

---

### Post by kansasnoob on 2011-11-07
I think I'm a bit more concerned about the 64bit version being offered by default. Will it be installable on 32bit hardware?

I'd almost bet we'll hear a gazillion complaints of people trying to install something that won't work with their hardware **because people don't bother to read** :(

---

### Post by philinux on 2011-11-07
> **kansasnoob said:**
> I think I'm a bit more concerned about the 64bit version being offered by default. Will it be installable on 32bit hardware?

I'd almost bet we'll hear a gazillion complaints of people trying to install something that won't work with their hardware **because people don't bother to read** :(

At least a bug got fixed.

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

---

### Post by kansasnoob on 2011-11-07
> **philinux said:**
> At least a bug got fixed.

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

But that may result in a bug titled:

I downloaded the default iso and it won't install ;)

Believe me, people do not bother to read, and I have 3 machines running - but only one will run 64bit :D

---

### Post by Derek Karpinski on 2011-11-07
+1 for "balls-to-the-wall" :D

---

### Post by kaldor on 2011-11-07
> **kansasnoob said:**
> I think I'm a bit more concerned about the 64bit version being offered by default. Will it be installable on 32bit hardware?

I'd almost bet we'll hear a gazillion complaints of people trying to install something that won't work with their hardware **because people don't bother to read** :(

If your PC was bought later than 2006, I am willing to bet it's 64-bit compatible. An old (2004ish) PC I have around is running the 64 bit version of Ubuntu. 

There should probably be a note on the website which will say "If you're running Windows Vista or Windows 7, choose 64 bit. If your PC came with Windows XP, choose 32 bit" or something to that nature.

Basically, I'm not worried at all. Most people have modern systems.

---

### Post by kansasnoob on 2011-11-07
> **kaldor said:**
> If your PC was bought later than 2006, I am willing to bet it's 64-bit compatible. An old (2004ish) PC I have around is running the 64 bit version of Ubuntu. 

There should probably be a note on the website which will say "If you're running Windows Vista or Windows 7, choose 64 bit. If your PC came with Windows XP, choose 32 bit" or something to that nature.

Basically, I'm not worried at all. Most people have modern systems.

I haven't bought a PC in many years, unless it's on a yard sale :)

I buy parts and pieces, usually budget priced "all-in-one" mobos, and the 64bit version is usually about $10.00 US higher than the 32bit version so I opt for 32bit.

That way I can make my mac-n-cheese with milk instead of water, or eat canned soup instead of Ramen noodles :D

What seems like only a few extra dollars to some is a huge difference to others.

---

### Post by effenberg0x0 on 2011-11-07
> **kansasnoob said:**
> While there is a lot of truth in what you say I'm an iso-tester and I've frequently found it almost necessary to keep older images during a test cycle.

That is; it's not at all uncommon now to have testing begin about 4 days before each release, less so during alpha stage.

So once Beta 1 (or beyond) hits it would not be uncommon to have to burn 4 or 5 discs during testing. In fact Oneiric final was quite a disc burning sensation :)

There was a sort of "unofficial" release candidate followed shortly by the final testing and since I test both Ubuntu and Lubuntu (and some alternates) I burned through about 35 to 40 discs within 10 days :D

That's not really a problem for me, but I frequently find it helpful to keep older images/discs during iso-testing to provide info needed in bug reports.

The expense of keeping 40 or 50 small flash drives aside it would be a nightmare to keep track of them. I guess I could use baggies with labels, but what about static? I suppose there are anti-static baggies.

Please read this:

[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

But, for me, the cost of DVD's is not a problem. I think they cost about 1 to 2 cents more each than CD,s. It really won't effect me.

But my greatest concern is that it will effect a lot of folks that still don't have DVD drives :(

I'd guess that about 1/2 of the people I have running Ubuntu 10,04 have only CD drives, and many of them depend on public assistance just to survive. Hardware upgrades are totally out of their grasp financially.

Regardless I can certainly deal with their installation needs because I can install for them using either a USB flash drive or a USB DVD drive.

But we must remember that there are a lot of people much worse off than we are ;)

Hey kansasnoob!

An ISO is an ISO. If md5 matches, it may or may not burn alright depending exclusively on end-user writer quality, but the ISO is right. But, if the iso was mounted and install works, there's no need to burn it to test it. And there's no need to burn it to store it. Any old 80GB HDD will do for a large bunch of ISOs. If you mdadm 4 to 5 80GB HDDs you can really feel more than safe about the ISO. Don't go through the process of burning every release man, it's inhumane :)

About statics and USBs. There's so much static here we give hands to each other and touch one rack to get chocked in group. It happens mostly everyday after the morning rotten coffee routine.  But I luckily never had a bad USB ISO. And in the case of gamma ray bursts we'd all die anyway, so, no worries.

I was looking at imports costs for 1GB USB from China to Miami and the price is 0,90USD with insurance. Add taxes and profit over it, but it shouldn't cost more than 6 USD in US including retail margin. Does it cost more than that there?

---

### Post by kansasnoob on 2011-11-07
> **effenberg0x0 said:**
> Hey kansasnoob!

An ISO is an ISO. If md5 matches, it may or may not burn alright depending exclusively on end-user writer quality, but the ISO is right. But, if the iso was mounted and install works, there's no need to burn it to test it. And there's no need to burn it to store it. Any old 80GB HDD will do for a large bunch of ISOs. If you mdadm 4 to 5 80GB HDDs you can really feel more than safe about the ISO. Don't go through the process of burning every release man, it's inhumane :)

About statics and USBs. There's so much static here we give hands to each other and touch one rack to get chocked in group. It happens mostly everyday after the morning rotten coffee routine.  But I luckily never had a bad USB ISO. And in the case of gamma ray bursts we'd all die anyway, so, no worries.

I was looking at imports costs for 1GB USB from China to Miami and the price is 0,90USD with insurance. Add taxes and profit over it, but it shouldn't cost more than 6 USD in US including retail margin. Does it cost more than that there?

You're wrong on so many levels I don't know where to begin, so I won't.

Well, one thing; if I've filed a bug report and a dev asks me to provide more info, having that disc in hand saves me having to burn a new one ;)

I do know quite well how to cp or mv any image so it can be used to zsync a new one, that's not the point.

---

### Post by buzzmandt on 2011-11-07
> **kansasnoob said:**
> i haven't bought a pc in many years, unless it's on a yard sale :)

i buy parts and pieces, usually budget priced "all-in-one" mobos, and the 64bit version is usually about $10.00 us higher than the 32bit version so i opt for 32bit.

That way i can make my mac-n-cheese with milk instead of water, or eat canned soup instead of ramen noodles :d

what seems like only a few extra dollars to some is a huge difference to others.

+1000

---

### Post by ranch hand on 2011-11-07
> **philinux said:**
> At least a bug got fixed.

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

I jumped right over to see that thinking you were talking a bug on people not reading.  Oh well, maybe next cycle.

---

### Post by effenberg0x0 on 2011-11-07
> **kansasnoob said:**
> You're wrong on so many levels I don't know where to begin, so I won't.

Well, one thing; if I've filed a bug report and a dev asks me to provide more info, having that disc in hand saves me having to burn a new one ;)

I do know quite well how to cp or mv any image so it can be used to zsync a new one, that's not the point.

Seriously? Let me explain. (not joking or anything)
I always looked at ISOs as simple data images, not much more than that. If MD5 matches, and the ISO can be mounted, and install goes OK, I never felt that burning could produce a different result unless the writer has some problem. Is there more to it than that? What I mentioned about storing the ISO in 3 or 4 cheap outdated RAID1 disks was just to be sure of ISO file integrity, since ISOs are large and something can happen to specific sectors in one disk, and using low budget structure, be able to store many ISOs.

About Static: AFAIK, USB Flash Memory does not rely on magnetism, but on small transistor holding up small electrical charge. I've always been told that, disconnected, there's little damage to be done to USB. While it is plugged, it is in more danger of altered charges, specially if the host hardware USB port/hub is in bad condition, putting out more charge then it should. So a stored USB should be pretty safe. Or at least that's what I've been told until now. Now the lame exception I posted about gamma ray burts, in the case of near supernovae events (just a joke), would create such distress in the earth as a whole that would likely end life for 80 to 90% of species according to scientists, and I imagine that probably includes USB gadgets (and everything else) :) (unbearable heat and radiation, etc)  

And the price of 1GB USB: I just went to the Internal Revenue Data site: USB <=1GB from Shenzen enters here for less than a dollar FOB in pallets of 5.000 units. It really is incredibly cheap. Check comex sites, not joking, the thing is almost free.

---

### Post by seeker5528 on 2011-11-07
> **kansasnoob said:**
> For the most part I think this is OK, but ............

What about those who don't have a DVD drive and can't afford hardware upgrades or a USB flash drive?

Should those of us with hardware produced in the last 8 years be held hostage by those who can't afford $10 for a flash drive or ~$30 give or take for a used DVD burner?

PATA drives are getting harder to find too, so availability of parts for these older systems will increasingly becoming an issue as well even for people who have the money to spend. How long should we continue to support hardware that the entire computer industry seems to be working on phasing out? 

Lubuntu is specifically designed to be a light weight option, I don't foresee it growing beyond 700 MB any time soon. And there is always the net/minimal install option.

Later, Seeker

---

### Post by kaldor on 2011-11-07
> **kansasnoob said:**
> I haven't bought a PC in many years, unless it's on a yard sale :)

I buy parts and pieces, usually budget priced "all-in-one" mobos, and the 64bit version is usually about $10.00 US higher than the 32bit version so I opt for 32bit.

That way I can make my mac-n-cheese with milk instead of water, or eat canned soup instead of Ramen noodles :D

What seems like only a few extra dollars to some is a huge difference to others.

And because of that, you know whether or not to use 64 bit or 32 bit OS :)

The average person doesn't do that. Pretty much everyone I know is on an HP or Dell, all of which shipped with Windows 64 bit. Therefore, they are most likely to have a 64 bit processor.

---

### Post by effenberg0x0 on 2011-11-07
Usually products in my country are a reflection of what is in stores in USA 4 to 6 months before. That has been the rule since forever, so I imagine this won't be news to any of you... I am currently looking for a new laptop and I've been browsing stores. The top-of-the-line models of the known brands here (like Lenovo, Sony, HP, etc), the ones that are SSD-Based, Sandy bridge, LED Screen, 8GB of RAM, Win64, etc are all small laptops (12, 13" screens), very thin and light units with no ODD. Some of the low/mid-end units (14", 15") still have ODD (not all of them), but they are very hidden in low shelves and it's not what people are buying. Even in desktops, you are not guaranteed to get an ODD in any HP/Dell, other brand models. I think we'll still see ODD drives for a couple years at most, in older machines and in external units, but that's pretty much it... I think it's ok for Ubuntu to start making the transition to other download sizes / media demands slowly. I don't think it's much of a choice. Seems unavoidable.

---

### Post by kansasnoob on 2011-11-08
> **seeker5528 said:**
> Should those of us with hardware produced in the last 8 years be held hostage by those who can't afford $10 for a flash drive or ~$30 give or take for a used DVD burner?

PATA drives are getting harder to find too, so availability of parts for these older systems will increasingly becoming an issue as well even for people who have the money to spend. How long should we continue to support hardware that the entire computer industry seems to be working on phasing out? 

Lubuntu is specifically designed to be a light weight option, I don't foresee it growing beyond 700 MB any time soon. And there is always the net/minimal install option.

Later, Seeker

I'm sort of thinking that a better idea would be keeping things CD size and then offering to install certain packages (like libre-office) either during installation or post installation.

I mean, for those of us who are not financially challenged, we're also likely to have blazing fast internet speeds so we could easily get everything we want without effecting those less fortunate :D

In my case I make certain sacrifices so I can have the fastest possible DSL - much faster (and cheaper) than cable here - because it's simply more important to me than such things as Cable TV.

BTW how are you now being "held hostage"?

---

### Post by kansasnoob on 2011-11-08
> **kaldor said:**
> And because of that, you know whether or not to use 64 bit or 32 bit OS :)

The average person doesn't do that. Pretty much everyone I know is on an HP or Dell, all of which shipped with Windows 64 bit. Therefore, they are most likely to have a 64 bit processor.

My sole point is that AFAIK the 64bit version will NOT work on 32bit hardware, and **people do not read** so we'll be besieged with people saying, "I DLed Ubuntu and can't get it to install".

Then we'll end up replying that they DLed the wrong version :(

Only time will tell. I'm not going to worry about it because I won't personally be effected, but I am the kind of guy to say, "I told you so", when things go wrong :D

---

### Post by yaji on 2011-11-08
Sup guys, just wanted to show you something:

[img]http://img253.imageshack.us/img253/8260/cdresperanza800mb52x25s.jpg[/img]

---

### Post by amjjawad on 2011-11-08
After going all the way with Unity, I'm not surprise of this NON-SENSE and I'm sure a lot more is coming on the way ... so hope they will keep it up :D

---

### Post by Lars Noodén on 2011-11-08
I would really rather see Precise slimmed down to 700 MB so that it fits on a CD RW.  

I guess it's necessary to look at how to do USB booting.

---

### Post by kansasnoob on 2011-11-08
> **effenberg0x0 said:**
> Seriously? Let me explain. (not joking or anything)
I always looked at ISOs as simple data images, not much more than that. If MD5 matches, and the ISO can be mounted, and install goes OK, I never felt that burning could produce a different result unless the writer has some problem. Is there more to it than that? What I mentioned about storing the ISO in 3 or 4 cheap outdated RAID1 disks was just to be sure of ISO file integrity, since ISOs are large and something can happen to specific sectors in one disk, and using low budget structure, be able to store many ISOs.

About Static: AFAIK, USB Flash Memory does not rely on magnetism, but on small transistor holding up small electrical charge. I've always been told that, disconnected, there's little damage to be done to USB. While it is plugged, it is in more danger of altered charges, specially if the host hardware USB port/hub is in bad condition, putting out more charge then it should. So a stored USB should be pretty safe. Or at least that's what I've been told until now. Now the lame exception I posted about gamma ray burts, in the case of near supernovae events (just a joke), would create such distress in the earth as a whole that would likely end life for 80 to 90% of species according to scientists, and I imagine that probably includes USB gadgets (and everything else) :) (unbearable heat and radiation, etc)  

And the price of 1GB USB: I just went to the Internal Revenue Data site: USB <=1GB from Shenzen enters here for less than a dollar FOB in pallets of 5.000 units. It really is incredibly cheap. Check comex sites, not joking, the thing is almost free.

Not sure where to begin, you said:

> I always looked at ISOs as simple data images, not much more than that. If MD5 matches, and the ISO can be mounted, and install goes OK, I never felt that burning could produce a different result unless the writer has some problem. Is there more to it than that

Installation problems, or other bugs, do appear. And you almost must have the older image to perform testing as newer images appear. IMHO one of the greatest causes of bugs getting through the dev process is the common use of virtual machines for testing. Only when testing on actual hardware do many bugs appear ;)

> What I mentioned about storing the ISO in 3 or 4 cheap outdated RAID1 disks was just to be sure of ISO file integrity, since ISOs are large and something can happen to specific sectors in one disk, and using low budget structure, be able to store many ISOs.

What's **cheap** to you may be quite expensive to those in a different demographic. Quite possibly the difference between being able to eat or not :)

Beyond that the argument about "static" causing flash drive failure seems pointless. More and more flash drives lack a true "cap", but defer to a silly swivel cover of sorts, or some retraction device which leaves the connective end of the device exposed to static charge. I know static can damage such devices, so 'nuff said. You're free to disagree as much as you'd like :D

I think my concerns are valid, and I may decide to bring these up with the Canonical devs (or not) but I'm thinking this is not a discussion to be had at Ayatana, maybe something to bring up with the release team .............. I'm not sure.

I have a plate full right now so I'll just be thinking about it. But I'm also considering the fact that Ubuntu stopped "ShipIt", so maybe they've decided the poor don't matter :(

---

### Post by kansasnoob on 2011-11-08
> **yaji said:**
> Sup guys, just wanted to show you something:

[img]http://img253.imageshack.us/img253/8260/cdresperanza800mb52x25s.jpg[/img]

Generally outdated and cost prohibitive :)

---

### Post by yaji on 2011-11-08
> **kansasnoob said:**
> Generally outdated and cost prohibitive :)

Yeah, you can buy them for 0,3$ where I live.

---

### Post by kansasnoob on 2011-11-08
> **yaji said:**
> Yeah, you can buy them for 0,3$ where I live.

Try to find them on line :)

I can buy 100 DVD's, either DVD+R or DVD-R, for about $16 or $17. And I can easily find 100 CD-R's for about $14 to $15.

What exactly is "0,3$" and where do find them?

---

### Post by effenberg0x0 on 2011-11-08
> **kansasnoob said:**
> Not sure where to begin, you said:
Installation problems, or other bugs, do appear. And you almost must have the older image to perform testing as newer images appear. IMHO one of the greatest causes of bugs getting through the dev process is the common use of virtual machines for testing. Only when testing on actual hardware do many bugs appear ;)

What's **cheap** to you may be quite expensive to those in a different demographic. Quite possibly the difference between being able to eat or not :)

Beyond that the argument about "static" causing flash drive failure seems pointless. More and more flash drives lack a true "cap", but defer to a silly swivel cover of sorts, or some retraction device which leaves the connective end of the device exposed to static charge. I know static can damage such devices, so 'nuff said. You're free to disagree as much as you'd like :D

I think my concerns are valid, and I may decide to bring these up with the Canonical devs (or not) but I'm thinking this is not a discussion to be had at Ayatana, maybe something to bring up with the release team .............. I'm not sure.

I have a plate full right now so I'll just be thinking about it. But I'm also considering the fact that Ubuntu stopped "ShipIt", so maybe they've decided the poor don't matter :(

I agree with you, all the points. I think the thing is that there are many differences between the countries and currencies / prices dynamics. Just to give you an idea: A used 80GB SATA HDD here costs about BRL20, which is about USD12. And you can probably negotiate and take two for BRL20, 3 for BRL25, etc from the guys that sell used IT. They buy tons of it from companies that are gonna throw old IT stuff away and resell online. With the same money (12USD), one goes to McDonalds and eats a BigMac, a Medium Coke and Medium Fries, but one time only and there's no change. 

If I go buy a 50CD-R Box (cheap one, not known brands like verbatim, tdk, sony, etc - unknown Chinese brand), it costs about BRL50. With the same money, one can buy a Kingston 8GB USB Stick or two Kingston 4GB Sticks, or 4 4GB Pendrives from unknown brand. So people are buying less and less CDR. DVD-R is even more expensive and people are not buying much of it either. 

The most sold PCs here, bought by people from what the government and economists calls the C/D classes (A are the rich, middle class is B, C is lower middle class, D is poor, E is miserable) are netbooks (13", Atom CPUs, 2GB, running Linux, no HDD, 32GB flash internal memory) from Acer, Asus, etc. These units have no ODD. 

Maybe this dynamic is very different from USA.

---

### Post by kansasnoob on 2011-11-08
Half a buck each:

[http://www.burnsmart.com/Prodisc-90min-CD-R-10pack-p/100.htm](http://www.burnsmart.com/Prodisc-90min-CD-R-10pack-p/100.htm)

Testing both Ubuntu and Lubuntu, both Desktop and Alternate images, that adds up fast :(

They're no longer a popular option and not all CD drives will work, nasty work-around :(

---

### Post by Dragonbite on 2011-11-08
If they are going to make it larger than a CD, why not make it a full DVD with a copy of the official repositories so you can install the DE and applications you want, like openSUSE and Fedora does?

---

### Post by andrewabc on 2011-11-08
> **Dragonbite said:**
> If they are going to make it larger than a CD, why not make it a full DVD with a copy of the official repositories so you can install the DE and applications you want, like openSUSE and Fedora does?

If made full size of DVD 4.4gb, it would not fit on 1gb, 2gb or 4gb USB sticks. So no liveusb for those devices. Yes I know larger sizes are available for cheap, but I got lots of older devices that I use for liveusb.

---

### Post by jerrylamos on 2011-11-08
> **effenberg0x0 said:**
> I agree with you, all the points. I think the thing is that there are many differences between the countries and currencies / prices dynamics. Just to give you an idea: A used 80GB SATA HDD here costs about BRL20, which is about USD12. 

The most sold PCs here, bought by people from what the government and economists calls the C/D classes (A are the rich, middle class is B, C is lower middle class, D is poor, E is miserable) are netbooks (13", Atom CPUs, 2GB, running Linux, no HDD, 32GB flash internal memory) from Acer, Asus, etc. These units have no ODD. 

Maybe this dynamic is very different from USA.

I've got a perfectly good IBM Thinkpad T40, 1.5 GHZ Pentium, 784 MB memory, 40 GB IDE hard drive, CD Read/Write.  Running Oneiric Ocelot fine, Unity-2D.

No it won't boot USB.  No it won't boot DVD.  

Looks like Oneiric Ocelot is the end of the line for Ubuntu for the T40, unless they are interested in a two CD version.  

Maybe an alternate might work.  Last time I tried alternate it worked, but it was a bear getting all the usual default apps installed and running.

I just tried Lubuntu 11.10, and it booted to command line.  No desktop.

Jerry

---

### Post by cariboo on 2011-11-08
@jerrylamos, you've had a couple of suggestion to get around that fact that your system can't boot from usb, another thing you can look at is upgrading you cd drive to a dvd drive, a quick look on ebay shows you can get new atapi ide drives for the cost of a couple of 100 dvd spindles.

---

### Post by crdlb on 2011-11-08
> **jerrylamos said:**
> I've got a perfectly good IBM Thinkpad T40, 1.5 GHZ Pentium, 784 MB memory, 40 GB IDE hard drive, CD Read/Write.  Running Oneiric Ocelot fine, Unity-2D.

No it won't boot USB.

Jerry

I don't understand, your T40 won't boot from a USB drive? My T42 could. [According to ThinkWiki]("http://www.thinkwiki.org/wiki/Supported_Boot_Devices#T_Series"), it should be the same for the T40.

---

### Post by effenberg0x0 on 2011-11-08
Jerry, I am interested in the issue of the Lenovo T40 not booting from USB. I've seen it happen and I've also seen a person fixing it the most stupid way. I'd like to understand what the real issue is, which is far from clear to me.

I'm assuming that, as you're no newbie, you have tried playing with BIOS settings, changing boot order priority, etc. And that, at boot, you have pressed F12 to select the boot device. Also, that you performed BIOS updates - The T40 (and 41, 42) had problems with USB speeds that were fixed in BIOS revisions.

Now comes the weird part: I have seen a T40 detect the name of the USB volume in the F12 screen and boot successfully to Win7 setup from it when the USB Stick is reformatted using **HP USB Format Tool** (check Google, any software download site has it). And the same same USB failed when it was reformatted using Windows 7 explorer (wouldn't boot). 

It got me thinking that, like a standard HDD, we should consider different ways to format a USB stick (not only FS, but geometry, sector size, heads, etc), and that softwares most likely do it differently.

I would suggest that you can try to use something like ubuntu fdisk -l to compare the structure of a USB Stick when formatted with Windows 7, HP USB Format Tool and Ubuntu Startup Disk Creator. Maybe you'll spot the difference and manage to solve this known problem, which would help many users.

**EDIT: **A guy went ahead of us (in 2005!) and made tests proving that different tools create very different (and sometimes wrong) USB geometries, and that some of these won't boot. He also informs what would be the way to do it correctly. Amazing effort. See here: [http://jaclaz.altervista.org/Projects/USB/USBstick.html](http://jaclaz.altervista.org/Projects/USB/USBstick.html)

---

### Post by Starks on 2011-11-08
I have zero respect for those that seek to undermine the bump to 750MB by advocating crappy, fault-intolerant high-capacity CDs.

If you can't boot from USB due to BIOS restrictions, go DVD or don't bother.

I also don't want to hear how you don't have a DVD drive either.

It's 2011. Grow up.

---

### Post by dext on 2011-11-09
> **Starks said:**
> I have zero respect for those that seek to undermine the bump to 750MB by advocating crappy, fault-intolerant high-capacity CDs.

If you can't boot from USB due to BIOS restrictions, go DVD or don't bother.

I also don't want to hear how [B] you don't have a DVD drive either.

It's 2011. Grow up.   [/B]
i agree, there not that expensive either. if one can afford the net, one can afford a DVD drive

---

### Post by Dragonbite on 2011-11-09
> **MacUntu said:**
> If you have trouble downloading 1 GiB, then you almost certainly have trouble downloading 750 MiB - IMHO. That's an argument I'm not willing to buy.

Depending on your internet speed that can make a difference.  For me, 1GB vs 750 MB = +1+/- additional hour (yes, it takes about 2 hours to download a CD, and 15 to download a DVD).

I am more than willing to send my ISP bill to you if you want, just give me your address... :D

> **seeker5528 said:**
> Should those of us with hardware produced in the last 8 years be held hostage by those who can't afford $10 for a flash drive or ~$30 give or take for a used DVD burner?

If the image fits on a CD, then it doesn't matter if you choose to use USB, DVD or CDs, it is available for all.  Take out the CD option and you reduce the ease and availability for some people.

It's laziness to not take into consideration that not everybody is in the same financial situation as a number of posters here.  Not everybody can afford, or have available, fast internet, newer computers or external peripherals.  And to say **** them is very self-centered.

Will Ubuntu, Linux for humans, become polarized between people with money and resource and exclude those without?

---

### Post by Lars Noodén on 2011-11-09
> **Dragonbite said:**
> If the image fits on a CD, then it doesn't matter if you choose to use USB, DVD or CDs, it is available for all.  Take out the CD option and you reduce the ease and availability for some people.

It's laziness to not take into consideration that not everybody is in the same financial situation as a number of posters here.  Not everybody can afford, or have available, fast internet, newer computers or external peripherals.  And to say **** them is very self-centered.

Will Ubuntu, Linux for humans, become polarized between people with money and resource and exclude those without?

+1

700 MB will also fit on a CD RW which means being able to reuse resources instead of burning coaster after coaster.

---

### Post by seeker5528 on 2011-11-09
> **kansasnoob said:**
> Half a buck each:

[http://www.burnsmart.com/Prodisc-90min-CD-R-10pack-p/100.htm](http://www.burnsmart.com/Prodisc-90min-CD-R-10pack-p/100.htm)

Testing both Ubuntu and Lubuntu, both Desktop and Alternate images, that adds up fast :(

That's why I use RW disks.

> **Dragonbite said:**
> It's laziness to not take into consideration that not everybody is in the same financial situation as a number of posters here.

At worst it's not any more lazy/inconsiderate than insisting others be limited by your outdated hardware when you have other options. 

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Lubuntu is a good desktop.

> **Lars Noodén said:**
> 700 MB will also fit on a CD RW which means being able to reuse resources instead of burning coaster after coaster.

4.3 GB will fit on a DVD RW, also being able to reuse resources instead of burning coaster after coaster.

> **kansasnoob said:**
> BTW how are you now being "held hostage"?

Not me personally, since I don't use some of the default applications and have to install ones that I do use, no matter which *buntu disk I install from. 

But from the standpoint of providing a good range of default selections the different desktops and relevant application software and/or the things those desktops and software depend on grow in size all the time, if people are looking at Linux to be the 'Extender of life for older machines' they should accept that what is provided by the default install may not be the right choice for them depending on how far behind the curve they are and that the hardware they have may not continue to be supported for the length of time it takes their hardware to die a natural death.

As far as old hardware goes, I'm not totally unsympathetic, both of my home machines run AMD 939 socket chips, one old enough to still have an AGP slot and an early SATA I implementation that has problems with SATA II HDDs. So the premature phasing out of PATA drives is of some concern to me on that machine.

My computers are mostly scrapped together from used/hand-me-down parts and old enough that someone bringing equivalent machines into my place of work wouldn't be offered any money/trade-in for them because they would be too hard to re-sell.

Later, Seeker

---

### Post by kansasnoob on 2011-11-09
> **jerrylamos said:**
> I've got a perfectly good IBM Thinkpad T40, 1.5 GHZ Pentium, 784 MB memory, 40 GB IDE hard drive, CD Read/Write.  Running Oneiric Ocelot fine, Unity-2D.

No it won't boot USB.  No it won't boot DVD.  

Looks like Oneiric Ocelot is the end of the line for Ubuntu for the T40, unless they are interested in a two CD version.  

Maybe an alternate might work.  Last time I tried alternate it worked, but it was a bear getting all the usual default apps installed and running.

I just tried Lubuntu 11.10, and it booted to command line.  No desktop.

Jerry

The alternate image is basically the Debian installer, and I can almost guarantee you that you'd be able to install using the Alternate image :D

During the late stages of the Precise cycle I'll try to provide some updates here:

[http://members.iinet.net/%7Eherman546/index.html](http://members.iinet.net/%7Eherman546/index.html)

It's been far too long since I've talked to Herman anyway :D

---

### Post by kansasnoob on 2011-11-09
> **Dragonbite said:**
> Depending on your internet speed that can make a difference.  For me, 1GB vs 750 MB = +1+/- additional hour (yes, it takes about 2 hours to download a CD, and 15 to download a DVD).

I am more than willing to send my ISP bill to you if you want, just give me your address... :D



If the image fits on a CD, then it doesn't matter if you choose to use USB, DVD or CDs, it is available for all.  Take out the CD option and you reduce the ease and availability for some people.

It's laziness to not take into consideration that not everybody is in the same financial situation as a number of posters here.  Not everybody can afford, or have available, fast internet, newer computers or external peripherals.  And to say **** them is very self-centered.

Will Ubuntu, Linux for humans, become polarized between people with money and resource and exclude those without?

+1!

It will not directly effect me, even though I install for about 35 to 40 other users, because I have a good USB DVD drive, and also have two USB flash drives that could be used.

BUT some people will not have that kind of access :(

---

### Post by buzzmandt on 2011-11-09
> **Starks said:**
> I have zero respect for those that seek to undermine the bump to 750MB by advocating crappy, fault-intolerant high-capacity CDs.

If you can't boot from USB due to BIOS restrictions, go DVD or don't bother.

I also don't want to hear how you don't have a DVD drive either.

It's 2011. Grow up.

pfft, speaking of growing up.....

Not everyone has the financial means to upgrade their computer just because the os demands it.  Great example is microsoft.  Win XP is still in great use because so many people don't have the money to get a computer that will run win7.  Now the same demands will be placed on the users of ubuntu as well.  And we have arses on here saying if you can't afford it like I can then you need to grow up.  

wow....

---

### Post by Starks on 2011-11-09
The foolish people that stick with the now 10-year-old Windows XP instead of using a modern Linux distro on that old computer are a problem unto themselves.

---

### Post by kansasnoob on 2011-11-09
> **seeker5528 said:**
> That's why I use RW disks.



At worst it's not any more lazy/inconsiderate than insisting others be limited by your outdated hardware when you have other options. 

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Lubuntu is a good desktop.



4.3 GB will fit on a DVD RW, also being able to reuse resources instead of burning coaster after coaster.



Not me personally, since I don't use some of the default applications and have to install ones that I do use, no matter which *buntu disk I install from. 

But from the standpoint of providing a good range of default selections the different desktops and relevant application software and/or the things those desktops and software depend on grow in size all the time, if people are looking at Linux to be the 'Extender of life for older machines' they should accept that what is provided by the default install may not be the right choice for them depending on how far behind the curve they are and that the hardware they have may not continue to be supported for the length of time it takes their hardware to die a natural death.

As far as old hardware goes, I'm not totally unsympathetic, both of my home machines run AMD 939 socket chips, one old enough to still have an AGP slot and an early SATA I implementation that has problems with SATA II HDDs. So the premature phasing out of PATA drives is of some concern to me on that machine.

My computers are mostly scrapped together from used/hand-me-down parts and old enough that someone bringing equivalent machines into my place of work wouldn't be offered any money/trade-in for them because they would be too hard to re-sell.

Later, Seeker

No real problems between you and I that I can see, I know you've helped me out a gazillion times :)

In fact I don't see a real problem with anyone posting here, it's all a matter of opinion, but as things transpire I think it's fair to think one of us should mention the worst of our concerns to SABDFL through whatever means possible.

I really do have a full plate but unless someone else steps up to the plate I'll do it. Must I?

Everyone should be aware that, if I pursue this, iso size will take a backseat to the decision to default to 64bit ;)

Both concern me, but it's simply not possible to burn an image to a disc that's too small, whereas downloading the wrong image will have much more catastrophic effects :(

I'd really appreciate someone else taking on this challenge,

---

### Post by buzzmandt on 2011-11-09
> **Starks said:**
> The foolish people that stick with the now 10-year-old Windows XP instead of using a modern Linux distro on that old computer are a problem unto themselves.

again.... wow
lmao





Personally i don't care, i have burners and usb sticks galore, and all the computers i techy in the neighborhood and family are in good shape.  I almost always use a usb to install and test anyway. I'm not going to comment you anymore starks, you obviously feel ubuntu should only cater to those who can afford it (Great way to advocate free software).  I'll keep this in mind in our future encounters.

---

### Post by tekstr1der on 2011-11-09
> **kansasnoob said:**
> I really do have a full plate but unless someone else steps up to the plate I'll do it.

Multiple distinct plate idioms in a single sentence. Impressive!

---

### Post by kansasnoob on 2011-11-09
> **buzzmandt said:**
> pfft, speaking of growing up.....

Not everyone has the financial means to upgrade their computer just because the os demands it.  Great example is microsoft.  Win XP is still in great use because so many people don't have the money to get a computer that will run win7.  Now the same demands will be placed on the users of ubuntu as well.  And we have arses on here saying if you can't afford it like I can then you need to grow up.  

wow....

+1!

These changes won't actually effect me. I can buy 100 DVD's at about 1 to 2 cents higher cost each than CD's. That ain't gonna break the bank :)

But it will effect others. And I do care!

Maybe I should just mention this at Ayatana. They won't shoot me :)

---

### Post by kansasnoob on 2011-11-09
> **tekstr1der said:**
> Multiple distinct plate idioms in a single sentence. Impressive!

Idioms are easy for idiots, and I belong to that club :lolflag:

---

### Post by jerrylamos on 2011-11-09
> **Starks said:**
> The foolish people that stick with the now 10-year-old Windows XP instead of using a modern Linux distro on that old computer are a problem unto themselves.
O.K., I do linux preferably, even unstable most of the time.

My wife supports a couple web sites that are coded to use Dreamweaver.

No Dreamweaver on Linux.  Not available, not even being worked on.

Dreamweaver works on XP.  Haven't tried Windoze XX yet, because the only way we get Windoze XX is if it comes on a new computer.  She's got 2 GHZ Pentium's that are running fine (given XP's slow response).  (Only matched by Windoze 7's slow response on the same speed pc's.)

Jerry

---

### Post by cariboo on 2011-11-09
Actually, it hasn't been written in stone yet, that the size of the image will increase, it was just said, that if there was a need, it would be expanded up 750MiB and no larger.

Earlier on in this thread it was suggested that [plop]("http://www.plop.at/en/bootmanager.html"), would be a good solution, for those that don't have a dvd drive, or can't boot from  usb device. I intend on testing plop boot manager on three systems I have here that won't boot from a usb thumb drive. I'll post the results tomorrow.

The plop boot managers zipped size is just 2.1MiB, included in the archive is an iso file, that is only 492kb in size, so it would quite easily fit on a floopy if needed.

---

### Post by kansasnoob on 2011-11-09
> **cariboo907 said:**
> Actually, it hasn't been written in stone yet, that the size of the image will increase, it was just said, that if there was a need, it would be expanded up 750MiB and no larger.

Earlier on in this thread it was suggested that [plop]("http://www.plop.at/en/bootmanager.html"), would be a good solution, for those that don't have a dvd drive, or can't boot from  usb device. I intend on testing plop boot manager on three systems I have here that won't boot from a usb thumb drive. I'll post the results tomorrow.

The plop boot managers zipped size is just 2.1MiB, included in the archive is an iso file, that is only 492kb in size, so it would quite easily fit on a floopy if needed.

Plop is a bit ridiculous as a true alternative to an oversize live image, the Ubuntu alternate image is a much better choice :D

Regardless I just got a cali that my youngest son is back in the hospital so I may be tied up for a little while.

What we really need is some verification from Canonical about the path they intend to follow ;)

---

### Post by effenberg0x0 on 2011-11-10
> **cariboo907 said:**
> Actually, it hasn't been written in stone yet, that the size of the image will increase, it was just said, that if there was a need, it would be expanded up 750MiB and no larger.

Earlier on in this thread it was suggested that [plop]("http://www.plop.at/en/bootmanager.html"), would be a good solution, for those that don't have a dvd drive, or can't boot from  usb device. I intend on testing plop boot manager on three systems I have here that won't boot from a usb thumb drive. I'll post the results tomorrow.

The plop boot managers zipped size is just 2.1MiB, included in the archive is an iso file, that is only 492kb in size, so it would quite easily fit on a floopy if needed.

I suggested it at [#19]("http://ubuntuforums.org/showpost.php?p=11434102&postcount=19") and thought no one had even checked it. IMHO, plop is a very decent workaround for those with boot limitations. There are many options available, the thing is very well thought.  

I also urge people that have problems booting from USB to read the document I posted at [#52]("http://ubuntuforums.org/showpost.php?p=11439494&postcount=52"). Having read that, I managed to test the explained concepts in two machines that NEVER booted from USB. And it worked perfectly. The creator of that document did an amazing job.

Additionally: I talked to a friend of mine that works doing foreign trade between asian countries and latam/north america. He said Chinese manufacturers can make 1GB USB 1.1 USB sticks, _printed with Ubuntu logo and already burned with any image previously provided_, for about **USD2** each (FOB), if anyone buys at least 1.000 units. I though this would make a nice idea for anyone that wants to kick off a small home business and make some bucks on eBay and local IT stores :) Selling each for **USD4** or **USD5** would make a **100%** profit and help Ubuntu users with no functional ODD available. Just go to alibaba.com, get a list of Shenzen manufacturers, send them an e-mail and you can have a small business rolling in no time :) Idea: Have your LoCo team fund the impost costs, donate the units to any new user that shows up at LoCo events.

---

### Post by cariboo on 2011-11-10
@effenberg0x0, thanks for reposting both links, I'll have a look at the link from post #52 in the morning, it is currently 23:54 in my time zone, and I've been up for close to 30 hours, so it's time to get some sleep.

---

### Post by TenPlus1 on 2011-11-10
Wait, wont removing Mono, Banshee and Tomboy save an additional 20mb of space to use for better things, rather than upping the iso limit to 750mb ?

Remove old themes that arent gtk3 ready, only keep one's like radiance and ambiance that work on both gtk2 and gtk3...

Keep icon sets for those themes only and of course default gnome, remove the others...

gcalctool (2mb) ... galculator (800k)  just saying...

Lots of space can be saved and still have it on a single cd folks...

---

### Post by moldaviax on 2011-11-10
well I'm not too concerned about the changed size, its also good th 64bit option will be available on media in the shop - I have always thought it would be handy if they offered both 

M.

---

### Post by Seb71 on 2011-11-10
One of my PC's (the one with Ubuntu) is not capable to boot from USB and only has a CD-RW IDE drive. I bought a S-ATA DVD-Writer drive, but had to return it because for some reason the PC would not boot with the S-ATA DVD drive connected. It would be pointless to spend money on an obsolete DVD IDE drive.

> **Starks said:**
> I have zero respect for those that seek to undermine the bump to 750MB by advocating crappy, fault-intolerant high-capacity CDs.

If you can't boot from USB due to BIOS restrictions, go DVD or don't bother.

I also don't want to hear how you don't have a DVD drive either.

It's 2011. Grow up.

You are so old fashioned. DVD in 2011? It's Blu-ray decade. On a 25GB single layer disc you could fit all Ubuntu versions (Ubuntu, Kubuntu, Xubuntu, Lubuntu) and still have room to spare. I can download 25GB in a few hours so the size would no be a problem.

---

### Post by Quackers on 2011-11-10
I haven't read all previous pages of this thread, so if it's been mentioned previously, I apologise.

I can see why the extra download time may be an issue on very slow connections, but I've been there too. It just means you have a bit longer to wait.

On another note, if you've already got grub2 installed you can boot the downloaded iso directly from the grub menu. The size of the iso then becomes irrelevant together with the CD/DVD issue - as you don't need one.

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

Just my 2 cents worth :-)

---

### Post by Seb71 on 2011-11-10
> **Quackers said:**
> I can see why the extra download time may be an issue on very slow connections, but I've been there too. It just means you have a bit longer to wait.

In some cases, it could also mean that you have more to pay.

---

### Post by Dragonbite on 2011-11-10
> **Quackers said:**
> On another note, if you've already got grub2 installed you can boot the downloaded iso directly from the grub menu. The size of the iso then becomes irrelevant together with the CD/DVD issue - as you don't need one.

That sounds like an interesting work-around the lack of CD/DVD drive issue.  Do you have a link for that?

I don't see it being something a newbie will use, but sounds like an interesting practice!

---

### Post by Quackers on 2011-11-10
I put a link in my post. It is a very quick way to boot an iso - about 45 seconds quick! It just needs the /etc/grub.d/40_custom file to be edited accordingly. Admittedly it is something that a beginner may have some difficulty with - but I managed it ;)

---

### Post by philinux on 2011-11-10
> **Dragonbite said:**
> That sounds like an interesting work-around the lack of CD/DVD drive issue.  Do you have a link for that?

I don't see it being something a newbie will use, but sounds like an interesting practice!

The easy way. Well sort of lol.

[http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html](http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html)

---

### Post by irv on 2011-11-10
> **kansasnoob said:**
> For the most part I think this is OK, but ............

What about those who don't have a DVD drive and can't afford hardware upgrades or a USB flash drive?

Or has Ubuntu become victim to so much "bloat" that we assume those with older hardware with resort to either Xubuntu or Lubuntu?

And, if we must cross that boundary why limit things to 750MB?

I'd think it would make sense to go "balls-to-the-wall" and install all of the stuff that's been left off of the iso's over the past few dev cycles.

I particularly remember SABDFL arguing against a GUI to adjust 'notify-osd' because it would create "bloat", but now we've accepted "bloat" to intro Unity/Gnome3 :confused:

Seems odd to my simple mind, but I'm simple minded :)
Is $4 too much for a 2 gig USB stick? That's the price of 2 cups of coffee in the coffee shop I am sitting in.

---

### Post by Dragonbite on 2011-11-10
> **irv said:**
> Is $4 too much for a 2 gig USB stick? That's the price of 2 cups of coffee in the coffee shop I am sitting in.

$2 for coffee?  All the more reason to make coffee at home and bring it along. I'd be spending $10-20 a day at that rate!
:lolflag:
When it comes time to pass out for people to be introduced to Ubuntu and Linux, I can give out a lot more CDs at $0.70 per CD and case than I can $4 USB sticks.

---

### Post by irv on 2011-11-10
> **Dragonbite said:**
> $2 for coffee?  All the more reason to make coffee at home and bring it along. I'd be spending $10-20 a day at that rate!
:lolflag:
When it comes time to pass out for people to be introduced to Ubuntu and Linux, I can give out a lot more CDs at $0.70 per CD and case than I can $4 USB sticks.

Refills are free!!!! and when I am on the road I need the INTERNET!

EDIT:  OH YA, when giving out Ubuntu ask them for a USB stick so you can put Ubuntu on it for them. Works for me. (at $0 cost).

---

### Post by Dragonbite on 2011-11-10
> **irv said:**
> Refills are free!!!! and when I am on the road I need the INTERNET!

EDIT:  OH YA, when giving out Ubuntu ask them for a USB stick so you can put Ubuntu on it for them. Works for me. (at $0 cost).
Free Refills! Gotta love that!

Most people I know aren't walking around with a USB they are ready to have wiped out for putting a Live Linux distro on it, in their pockets.

---

### Post by effenberg0x0 on 2011-11-10
When I hear those that are speaking in defense of the people that can't afford a 1GB USB (which seems to cost less than US$4 mostly everywhere, just see the export prices of China for this product in sites like alibaba.com, etc) I get divided:

- One side of me thinks that, if I was worried about spending US$4, I shouldn't be using Ubuntu anyway: I should be doing anything else to make enough money to live instead of worrying about installing the latest Ubuntu. I doubt I would have broadband. And if I even had a PC, etc  I would sell it, buy a suit and a tie and start seriously looking for a job. Or trade it for drugs, alcohol, a gun, etc. At any rate, my last concern would be liking or disliking Unity.

- Another side of me thinks of some places in Africa, poor countries and communities in which there are no opportunities, people don't even have water, etc. And even miserable people in developed countries, who survive from government and donations. Sometimes they can't get a job because they have no formal education and/or skills or were born with some physical condition, etc. Maybe they would benefit from using Ubuntu (Windows is expensive) and some dollars do make a difference in this case. My country had many miserable communities until 15/20 years ago and it was a very sad situation.

So it's hard to choose a side... Maybe there should be two ISOs, with some differences in the packages included.

---

### Post by Dragonbite on 2011-11-10
> **effenberg0x0 said:**
> When I hear those that are speaking in defense of the people that can't afford a 1GB USB (which seems to cost less than US$4 mostly everywhere, just see the export prices of China for this product in sites like alibaba.com, etc) I get divided:

- One side of me thinks that, if I was worried about spending US$4, I shouldn't be using Ubuntu anyway: I should be doing anything else to make enough money to live instead of worrying about installing the latest Ubuntu. I doubt I would have broadband. And if I even had a PC, etc  I would sell it, buy a suit and a tie and start seriously looking for a job. Or trade it for drugs, alcohol, a gun, etc. At any rate, my last concern would be liking or disliking Unity.

- Another side of me thinks of some places in Africa, poor countries and communities in which there are no opportunities, people don't even have water, etc. And even miserable people in developed countries, who survive from government and donations. Sometimes they can't get a job because they have no formal education and/or skills or were born with some physical condition, etc. Maybe they would benefit from using Ubuntu (Windows is expensive) and some dollars do make a difference in this case. My country had many miserable communities until 15/20 years ago and it was a very sad situation.

So it's hard to choose a side... Maybe there should be two ISOs, with some differences in the packages included.

So you're going to ship me 100 USBs for handing out?  Thanks!

---

### Post by effenberg0x0 on 2011-11-10
> **Dragonbite said:**
> So you're going to ship me 100 USBs for handing out?  Thanks!

LOL... How can I know that you don't have 20 5-port USB hubs and that you'll use the 100 USBs to make a ultrafast 98GB mdadm RAID6?

If anyone start a serious fund to provide USBs with Ubuntu to people  that REALLY need it, I wouldn't mind paying for 100 of them. 

I was thinking about my country, which is in the "3rd world": Popular broadband (dsl-based 1Mbps) from the government is free and from carriers is about US$7/month in my country now. And every family that is under "average household wage" receives a salary from the government (about US$400). They pay a little more for every children in school in the household. "Popular PCs" are sold to them with 35% discount, no taxes, discount and can be paid in 40 fixed monthly installments... And, as the government has a policy to only use FOSS in all public PCs (schools, libraries, agencies, hospitals, etc), everyone can get Linux everywhere. 

So, if things are like this here (3rd world) can we really say that there are people who can't afford a USB in north-america, asia, europe, etc? 

Maybe they also had this line of thought when ship-it was discontinued?

---

### Post by irv on 2011-11-10
> **Dragonbite said:**
> Free Refills! Gotta love that!

Most people I know aren't walking around with a USB they are ready to have wiped out for putting a Live Linux distro on it, in their pockets.

I have two in my pocket and I always have my computer with me. (laptop), and can wipe one after copying the files off it. But you are right, not everyone is like me.

---

### Post by irv on 2011-11-10
> **effenberg0x0 said:**
> When I hear those that are speaking in defense of the people that can't afford a 1GB USB (which seems to cost less than US$4 mostly everywhere, just see the export prices of China for this product in sites like alibaba.com, etc) I get divided:

- One side of me thinks that, if I was worried about spending US$4, I shouldn't be using Ubuntu anyway: I should be doing anything else to make enough money to live instead of worrying about installing the latest Ubuntu. I doubt I would have broadband. And if I even had a PC, etc  I would sell it, buy a suit and a tie and start seriously looking for a job. Or trade it for drugs, alcohol, a gun, etc. At any rate, my last concern would be liking or disliking Unity.

- Another side of me thinks of some places in Africa, poor countries and communities in which there are no opportunities, people don't even have water, etc. And even miserable people in developed countries, who survive from government and donations. Sometimes they can't get a job because they have no formal education and/or skills or were born with some physical condition, etc. Maybe they would benefit from using Ubuntu (Windows is expensive) and some dollars do make a difference in this case. My country had many miserable communities until 15/20 years ago and it was a very sad situation.

So it's hard to choose a side... Maybe there should be two ISOs, with some differences in the packages included.
Just a little side note on the poor. I was in Nigeria a couple of years ago, and I couldn't believe that people so poor they were living in boxes under bridges but everyone everywhere had a cell phone. Of course the wire phone service never did work while I was there. The first thing I did was run out and bough a cell phone for that area. They cost more then a USB stick.

---

### Post by Dragonbite on 2011-11-10
> **effenberg0x0 said:**
> LOL... How can I know that you don't have 20 5-port USB hubs and that you'll use the 100 USBs to make a ultrafast 98GB mdadm RAID6?

If anyone start a serious fund to provide USBs with Ubuntu to people  that REALLY need it, I wouldn't mind paying for 100 of them. 

I was thinking about my country, which is in the "3rd world": Popular broadband (dsl-based 1Mbps) from the government is free and from carriers is about US$7/month in my country now. And every family that is under "average household wage" receives a salary from the government (about US$400). They pay a little more for every children in school in the household. "Popular PCs" are sold to them with 35% discount, no taxes, discount and can be paid in 40 fixed monthly installments... And, as the government has a policy to only use FOSS in all public PCs (schools, libraries, agencies, hospitals, etc), everyone can get Linux everywhere. 

So, if things are like this here (3rd world) can we really say that there are people who can't afford a USB in north-america, asia, europe, etc? 

Maybe they also had this line of thought when ship-it was discontinued?

Wow, even your pay-for DSL costs less and is faster than mine here in the USA! There is no government salary (unless you are hired by them) and computers are sold at full price unless it "falls off the truck".  I'm lucky to find people who know what Linux is (hence, the interest in being able to hand out cheap CDs to people as I run across the opportunities).

Yes, there are people where $4 is a more significant number than it is to you or I to put into a piece of plastic that is largely seen as a luxury item but who can benefit from the possibilities Linux can provide (safe & secure system, educational software, email, printing resume, etc.).  

The kinds of people that would likely be most effected by this are the people that don't frequent these forums, but does that mean they are any less important?

---

### Post by Starks on 2011-11-10
I'd like to see Samba back in the image and not an addon download.

---

### Post by effenberg0x0 on 2011-11-11
> **Dragonbite said:**
> Wow, even your pay-for DSL costs less and is faster than mine here in the USA! There is no government salary (unless you are hired by them) and computers are sold at full price unless it "falls off the truck".  I'm lucky to find people who know what Linux is (hence, the interest in being able to hand out cheap CDs to people as I run across the opportunities).

Yes, there are people where $4 is a more significant number than it is to you or I to put into a piece of plastic that is largely seen as a luxury item but who can benefit from the possibilities Linux can provide (safe & secure system, educational software, email, printing resume, etc.).  

The kinds of people that would likely be most effected by this are the people that don't frequent these forums, but does that mean they are any less important?

Technology-wise the country is doing significant efforts in the last years. I have 40Mbps Internet at home for a decent price, etc. Free 1Mbps Internet and tax cuts to local PC manufacturers, to PCs with Linux, the popular PCs, etc projects are somewhat seen as a very effective way of populism too... And don't think for a second that because people have free Internet and cheap access to IT the rest of the country works - people die in hospital lines waiting for treatment, etc. But (in government's point of view) they do have a PC, so it's all good right? :)

Back to the issue at hand: Popular PCs do not have ODD. People rely on USB, which is why you can find a cheap-brandless USB stick at any corner anywhere for almost no money.

---

### Post by irv on 2011-11-11
I just downloaded Mint 12 64bit, and I had to burn a DVD it would not fit on a CD. No big deal.

EDIT: The size of the iso file was 1014.2 MB (1063479296 bytes)

---

### Post by ubername on 2011-11-12
> **kaldor said:**
> Well, 750 mb is enough to fit in a lot more stuff without going overboard. In some places with slow download speeds, 750 vs 1 GB is a huge difference and could be a problem. 

As far as materials go, DVDs are the same price as CDs are in my area and both are equally attainable. Either way, I always use a liveUSB. It'll take me just an extra couple of minutes to download.

I can't really imagine it being a problem for the vast majority of Ubuntu users.

This is my problem. Why is 50Mb 'not going overboard'? The proposition (whether it comes to pass or not) is that the physical CD limit should be exceeded, but not to the extent of any other physical limit. Yet it seems very clear to me that that previous size constraint was precisely because of the physical limit (Imagine what the responses to a thread with the title 'Why is the ISO restricted to 700MB?' would have looked like prior to this).

As for the argument 

> In some places with slow download speeds, 750 vs 1 GB is a huge difference

I'm afraid no matter where you are and no matter what your download speed, the difference is always 250Mb. If the size of the image is a concern that should be a reason for arguing for a reduction in the ISO size, not justifying increasing it by 'only 50Mb'.

Likewise, the price of the media is irrelevant. If you are going to use a DVD, even if it costs the same as a CD, why not use as much of it as possible?

Anyway, sorry for frothing, and sorry to Kaldor who just happened to be the first of many posters who brought up these issues. I just can't get my head around why anyone would propose a new limit of 750Mb.

---

### Post by jerrylamos on 2011-11-12
Personal opinion, going from CD size up, opens the floodgates and then DVD size is the limit.  Blue Ray next.

There's still optional stuff in the CD image that's readily downloaded over the internet, example Libre Office which I use quite a lot.

Alternate image is a solution.  Last time I tried it, was a bear to get the standard default functions and programs loaded.

Alternate image + a one click "download the rest" would solve the obese Pangolin iso for me.

Another still is Lubuntu.  I've got 12.04 Lubuntu on my Thinkpad T40, thanks to Lucazade on the Lubuntu thread in this forum.

Jerry

---

### Post by Dragonbite on 2011-11-12
I think there already is an Ubuntu DVD available though I cannot remember if it was "official" or something somebody put together.

Fedora Live CD does not include LibreOffice and I think they've kept it down into the 600mb's.  Then they offer a DVD with all of the RPM packages in the official repositories included.

OpenSUSE, after installing from the LiveCD has a huge number of packages automatically flagged for installing at first update (including Flash, MP3, etc.).  There was supposedly an option somewhere to choose to install or not install but it didn't bite me.

---

### Post by effenberg0x0 on 2011-11-12
[http://www.usbforfree.com/](http://www.usbforfree.com/)

Anyone is the countries they operate (see FAQ) wants to give it a shot and report back

---

### Post by jerrylamos on 2011-11-17
Images from development tend (always?) to be oversized.  How about a Precise Pangolin development image that will fit on CD like Ubuntu-mini-remix 11.10 (180 MB) or even one without LibreOffice, etc. (which I can install from synaptic) and games? What else is big in the .iso that can be readily downloaded?

Even if I'm using a USB drive, on my test pc's that will boot from USB, would save download time and server time.

Thanks, Jerry

---

### Post by cariboo on 2011-11-17
@jerrylamos, use [zsync]("https://help.ubuntu.com/community/ZsyncCdImage") to update your daily images instead of downloading the whole thing.

---

### Post by kansasnoob on 2011-11-17
> **cariboo907 said:**
> @jerrylamos, use [zsync]("https://help.ubuntu.com/community/ZsyncCdImage") to update your daily images instead of downloading the whole thing.

+1!

I started something during Oneiric final iso-testing very hurriedly and sloppily:

[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

That needs a major rewrite but I think we do need a long term sticky for Ubuntu +1 regarding the ability to sync images.

Zsync is so easy I can use it :lolflag:

---

### Post by dniMretsaM on 2011-11-17
> **irv said:**
> I just downloaded Mint 12 64bit, and I had to burn a DVD it would not fit on a CD. No big deal.

EDIT: The size of the iso file was 1014.2 MB (1063479296 bytes)

They also have a CD sized one (as of Mint 11 32 bit). But anyway, I think they should keep one around. I'll use myself as an example. When I first decided to install Ubuntu, I had no access to a DVD burner and at the time, I didn't know my computer could boot from USB (I only found out that it could like a month ago). So if there had been no CD image, I would still be using Windows XP. Obviously not everyone has the same experience as me, but I still thought it was worth bringing up. Now I carry around an 8GiB USB drive with the live images of K/L/X/Ubuntu 10.04 and 11.04, Mint 11 (DVD), Memtest86+, Clonezilla, BitDefender, and GParted. I also carry around a 2GiB SD card that I'm going to put a Puppy install on  (and maybe some other small live distro).

---

### Post by irv on 2011-11-17
I have never tried this, but you can setup a pxe server if you are on a network and install from there. 
[http://www.howtoforge.com/ubuntu_pxe_install_server]("http://www.howtoforge.com/ubuntu_pxe_install_server")
This is a howto Setting Up A PXE Install Server For Multiple Linux Distributions With Ubuntu Edgy Eft. It is a old post from back in 2006, but I believe it will work for a newer install also.
This is a great way to install if you have a lot of PC's on a network and you want to do multi-install.

---

### Post by ranch hand on 2011-11-18
> **cariboo907 said:**
> @jerrylamos, use [zsync]("https://help.ubuntu.com/community/ZsyncCdImage") to update your daily images instead of downloading the whole thing.
Zsync is nice but the image still won't fit on a CD.  That is what the guy is asking about.

Answers for questions asked are nice.  Even if it is "It ain't gonna happen".

---

### Post by tghe-retford on 2011-11-18
> **effenberg0x0 said:**
> [http://www.usbforfree.com/](http://www.usbforfree.com/)

Anyone is the countries they operate (see FAQ) wants to give it a shot and report back
The Web of Trust addon for Chrome was screaming at me to get out of there the second I clicked that link:

[http://www.mywot.com/en/scorecard/usbforfree.com](http://www.mywot.com/en/scorecard/usbforfree.com)

---

### Post by tlcstat on 2011-11-18
It ain't gonna happen!

---

### Post by effenberg0x0 on 2011-11-18
It could be risky depending on the connection quality, but I was thinking one can possibly mount a remote iso using samba over wlan. Would be fun to try, but considering usb dvd-rw drives can be found in the 25-30 usd range, it's not worth the risk: [http://www.amazon.com/AmazonBasics-Writer-External-Optical-Drive/dp/B003M0NT1M/ref=pd_cp_e_2](http://www.amazon.com/AmazonBasics-Writer-External-Optical-Drive/dp/B003M0NT1M/ref=pd_cp_e_2)

---

### Post by cariboo on 2011-11-18
> **ranch hand said:**
> Zsync is nice but the image still won't fit on a CD.  That is what the guy is asking about.

Answers for questions asked are nice.  Even if it is "It ain't gonna happen".

The person I suggested zsync to, has stated during Oneiric testing that he mounts the iso via grub, so size shouldn't make a difference.

All this is just speculation any how, as it was stated that the iso would be a maximum size of 750MiB if needed, it may never even happen.

The testing isos are always oversize, due to the extra debugging libraries installed during the testing phase.

---

### Post by keithpeter on 2011-12-02
Hello All

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

All sounds great to me. I've downloaded the Desktop CD iso and booted a couple of computers from the live image ok. 

Is the plan to release 12.04 as a 1.5 Gb DVD as well as smaller isos? 

Where do I find lists of the application software to be included on the DVD image? Is there a final list at this early stage?

---

### Post by OrangeCrate on 2011-12-02
^,

Here's the last news I saw on what's coming up in Precise:

[http://www.junauza.com/2011/11/ubuntu-1204-precise-pangolin-features.html](http://www.junauza.com/2011/11/ubuntu-1204-precise-pangolin-features.html)

---

### Post by keithpeter on 2011-12-02
> **OrangeCrate said:**
> ^,

Here's the last news I saw on what's coming up in Precise:

[http://www.junauza.com/2011/11/ubuntu-1204-precise-pangolin-features.html](http://www.junauza.com/2011/11/ubuntu-1204-precise-pangolin-features.html)

Thanks OrangeCrate

Quoting your page

> Since Pangolin's ISO will be 750 MB in size, it won't fit on your standard CDs. So, you'll either have to burn a DVD or use a USB thumb drive to install the update.

...but I'm seeing a 1.5Gb dvd image and a slightly oversized CD image. 

Does anyone know if there is an Ubuntu/Canonical page or source where they explain what images will be released?

A 1.5Gb dvd image will allow a wider range of application software (GIMP, Inkscape, video editor &c) and could then lead to a much more interesting range of software available out of the box so to speak.

Imagine a free e-book along the lines "Do almost everything with Ubuntu 12.04".

PS: I used to sit on orange crates when I first started work in a warehouse in Liverpool. Not quite half a century ago...

---

### Post by MG&amp;TL on 2011-12-02
Better still; just have a DVD image; there's not much point in a over-700MB cd ISO.

---

### Post by OrangeCrate on 2011-12-02
> **keithpeter said:**
> Thanks OrangeCrate

Quoting your page



...but I'm seeing a 1.5Gb dvd image and a slightly oversized CD image. 

Does anyone know if there is an Ubuntu/Canonical page or source where they explain what images will be released?

A 1.5Gb dvd image will allow a wider range of application software (GIMP, Inkscape, video editor &c) and could then lead to a much more interesting range of software available out of the box so to speak.

Imagine a free e-book along the lines "Do almost everything with Ubuntu 12.04".

PS: **I used to sit on orange crates when I first started work in a warehouse in Liverpool. Not quite half a century ago...**

The original OrangeCrate was a tricked out, bright orange, 1975 Dodge Van (think "surfer" van). The current OrangeCrate is a custom painted, burnt orange Harley Davidson Fat Boy (that sits in my garage).

Edit: 

> ...first started work...not quite a half a century ago...

I would expect we're about the same age.

---

### Post by keithpeter on 2011-12-02
> **MG&TL said:**
> Better still; just have a DVD image; there's not much point in a over-700MB cd ISO.

Exactly my feeling. A 4Mb usb stick is the 'optimum' value for money size here in the UK (maybe different outside US/Europe) so an image of around 1.5Gb still leaves plenty of persistent storage space and might provide a good range of applications.

The 'pound shops' sell 5 dvd +r discs for, well, a pound. 

> **OrangeCrate said:**
> The original OrangeCrate was a tricked out, bright orange, 1975 Dodge Van (think "surfer" van). 

Excellent! 

I teach in a Further Education College (Community College in the states) and the art and design students are all growing afros and wearing dark orange and chocolate brown. It's quite funny. I'm expecting to see loons next :twisted:

---

### Post by cariboo on 2011-12-02
This has already been discussed, two threads merged.

---

### Post by keithpeter on 2011-12-02
> **cariboo907 said:**
> This has already been discussed, two threads merged.

Hello cariboo907

I'm very sorry, but I can't see any answer to my question in the thread you have merged my post into.

To restate the question:

**There is a 1.5Gb DVD image available from the 12.04 Alpha download page. Will this image remain available when 12.04 is released?**

The **1.5Gb image** contains applications that are not in the 703Mb image including: GIMP, Gnu Emacs, Inkscape, Pitivi

It would be helpful to know if there will be a release of this **much larger image** alongside an iso that is a little larger than a standard 700Mb CD. The extra applications mentioned, if available in a released DVD image, would *significantly expand the range of activities* that could be explored in a beginners guide.

I can't find any trace of a discussion of the **1.5Gb iso image that now exists and is not a vague possibility** in the thread that you have merged my distinct question into.

Apologies if we drifted off into nostalgia and colour schemes.

Cheers

---

### Post by cariboo on 2011-12-02
> **keithpeter said:**
> Hello cariboo907

I'm very sorry, but I can't see any answer to my question in the thread you have merged my post into.

To restate the question:

**There is a 1.5Gb DVD image available from the 12.04 Alpha download page. Will this image remain available when 12.04 is released?**

The **1.5Gb image** contains applications that are not in the 703Mb image including: GIMP, Gnu Emacs, Inkscape, Pitivi

It would be helpful to know if there will be a release of this **much larger image** alongside an iso that is a little larger than a standard 700Mb CD. The extra applications mentioned, if available in a released DVD image, would *significantly expand the range of activities* that could be explored in a beginners guide.

I can't find any trace of a discussion of the **1.5Gb iso image that now exists and is not a vague possibility** in the thread that you have merged my distinct question into.

Apologies if we drifted off into nostalgia and colour schemes.

Cheers

There has always been a DVD image available, it has both the Live and Alternate install images on it.

---

### Post by keithpeter on 2011-12-02
> **cariboo907 said:**
> There has always been a DVD image available, it has both the Live and Alternate install images on it.

Hello cariboo907

Then you have answered my (original) question :twisted:

I have observed that the 1.5Gb DVD has **additional applications** (GIMP, Inkscape, Pitivi) compared to the 'a bit more than 700Mb' iso. It is therefore *not* simply a duplication of the live and alternate images, but provides significant extra affordances.

I shall now attempt to make a bootable usb stick from the DVD live image and then boot the thinkpad. If I succeed then this will be very helpful to me within an educational setting where students / trainees are limited to working from a live image for institutional reasons. 

See [this interview]("http://www.furtherfield.org/interviews/puredyne-discussion-netbehaviour") for the logic and limitations of institutional training. You have no idea unless you have been there.

Cheers & good luck

---

### Post by jerrylamos on 2011-12-03
lubuntu CD Live and alternate still both fit in a CD.  I've installed lubuntu on a Thinkpad T40 which runs lubuntu just fine, also running precise as upgraded from an ocelot .iso which did fit on a CD.

It's a 1.5 GHz pentium with 750 MB memory runs internet videos full speed just fine.  Nice notebook.  Quick and responsive.  No it doesn't run unity-3D which I don't use anyway on my latest pc.  I don't like fuzzy edges and foggy windows and Compiz overhead churning away even when it doesn't have anything to do.  As a tester I briefly use -3D, switch to -2D and at the moment gnome-session-fallback which with F11 gets more on this netbook screen than Unity does and no launcher forever overlaying when I didn't want it to.

No the T40 will not boot from USB.  Period.

The way ubuntu is headed with fatter and fatter .iso's only way I'll be able to install precise is with a minimal .iso plus downloading the rest from the internet.

As it is, after install, I put in a bunch of useful stuff ubuntu development kicked out of the .iso such as aptitude, synaptic, gparted, full samba, And of course flashplayer.

Ubuntu's direction is clear, just like Microsoft, only for the latest and greatest pc's.  Throw the nice fast usable older pc's on the dump.  Hopefully ubuntu will still be the base for distro's like lubuntu, mint, bodhi, etc.

Jerry

---

### Post by keithpeter on 2011-12-03
> **jerrylamos said:**
> Ubuntu's direction is clear, just like Microsoft, only for the latest and greatest pc's.  Throw the nice fast usable older pc's on the dump.  Hopefully ubuntu will still be the base for distro's like lubuntu, mint, bodhi, etc.

Jerry

Lubuntu seems to be the ideal use case for older kit as you say. Still has up to date repositories, kernel and drivers, and nice fonts. DON'T put the old kit on the dump, pump it up with Lubuntu add some sound applications (see puredyne.org) and put it in the hands of teenagers!

My interest is in Ubuntu Unity 2d as a system in its own right well suited to educational environments and runnable with a good range of applications from a USB stick with persistent storage. I've 'discovered' the DVD - which apparently has always existed - and am very interested in the extra apps in that image including GIMP, Pitivi video editor and Inkscape.

My target machines in the P4 1Gb ram class but probably blacklisted video hence the tutorials I'm developing for Unity 2d. They will boot from USB if admin sets the bios permissions.

---

### Post by tlcstat on 2011-12-03
Greetings,
> Ubuntu's direction is clear, just like Microsoft, only for the latest  and greatest pc's.  Throw the nice fast usable older pc's on the dump.   Hopefully ubuntu will still be the base for distro's like lubuntu, mint,  bodhi, etc.
 

IBM always was an arrogant bunch. Why would you possibly need to boot from USB since they put a real nice OS on the machine at the factory. Be happy! 
tlcstat

---

### Post by irv on 2011-12-03
I downloaded an installed the 12.04 Alpha version of Ubuntu this morning and had to put it on a DVD because this warning was on the download site.
> [COLOR="Red"]Warning: This image is oversized (which is a bug) and will not fit onto a standard 700MiB CD. However, you may still test it using a DVD, a USB drive, or a virtual machine.[/COLOR]
The release of 12.04 should be sized to fit on a CD because they are saying this is just a bug. Who knows?

---

### Post by cariboo on 2011-12-03
> **irv said:**
> I downloaded an installed the 12.04 Alpha version of Ubuntu this morning and had to put it on a DVD because this warning was on the download site.

The release of 12.04 should be sized to fit on a CD because they are saying this is just a bug. Who knows?

The dailies are always oversize, usually until the beta release, this has nothing to do with the proposed increase in iso size if needed.

---

### Post by teh603 on 2011-12-05
> **jerrylamos said:**
> Ubuntu's direction is clear, just like Microsoft, only for the latest and greatest pc's.  Throw the nice fast usable older pc's on the dump.  Hopefully ubuntu will still be the base for distro's like lubuntu, mint, bodhi, etc.
You entirely sure about that? I was able to install Kubuntu Ocelot on the Winbook from '02 using the Alternate Install CD. It runs great, and I'm pretty sure if I'd put Lubuntu on it that it'd run even faster.

---

### Post by CryptAck on 2011-12-05
In all honesty, I have not read all the replies to this thread. In so, this may have already been discussed, but its my thoughts on the subject at this point. 

I can understand how this could affect some with older hardware. I could also see how this could affect those who do not have a broadband connection with an older PC, and rely on a friend (or cheap purchase) of a CD.  

Nevertheless, to the masses, I don't understand why this--if actually true--would cause any problems? In the event that your system is unable to boot from USB, why not use a minimal? You can still burn this ISO to CD and the download time of the install should be comparable to the download of the standard 700MB ISO + install. 

Additionally, if you have GRUB already installed, you don't even need to create a media to boot from, you can boot the ISO directly from the hard drive. 

Finally, a USB install should be quite faster anyways (assuming USB2.0).

I don't see this being all that shocking if true. Years ago people installed applications and even operating systems from floppy disks. Times changed and CDs became the norm due to data increases.

---

### Post by jerrylamos on 2011-12-05
> **cariboo907 said:**
> The dailies are always oversize, usually until the beta release, this has nothing to do with the proposed increase in iso size if needed.

Imitation "tablet" eye candy code is famously obese and will drive ubuntu fatter and fatter.  Already losing stuff I use like synaptic, gparted, aptitude which I do add in later.  

I'm also testing lubuntu which still fits on a CD so far partly because 
it doesn't do unity and abiword is a lot smaller in size and function than libre office.  I frequently use libre office write and calc so I can add them from internet.  

At the moment this is from a netbook which will run fuzzy foggy overheady huge hieroglyphic Unity-3D and clearer but still huge hieroglyphic Unity-2D but I'm trying gnome-session-fallback likely to disappear in the future.

Now I do run a tablet from time to time which is sharply limited in function and information density by having to accommodate big fat fingers - compared to a mouse pointer.  O.K. for reading books and listening to music.  Just try to do a write document with embedded graphics and pictures, or manage finances....

Choices...

Jerry
Jerry

---

### Post by tlcstat on 2011-12-05
Greetings,
Hey! Wouldn't it be a shocker to convert the iso to 1450 720k floppies to install on my Tandy 1000 and then get a "kernel panic error"?
:)
tlcstat

---

### Post by cariboo on 2011-12-05
> **jerrylamos said:**
> Imitation "tablet" eye candy code is famously obese and will drive ubuntu fatter and fatter.  Already losing stuff I use like synaptic, gparted, aptitude which I do add in later.  

I'm also testing lubuntu which still fits on a CD so far partly because 
it doesn't do unity and abiword is a lot smaller in size and function than libre office.  I frequently use libre office write and calc so I can add them from internet.  

At the moment this is from a netbook which will run fuzzy foggy overheady huge hieroglyphic Unity-3D and clearer but still huge hieroglyphic Unity-2D but I'm trying gnome-session-fallback likely to disappear in the future.

Now I do run a tablet from time to time which is sharply limited in function and information density by having to accommodate big fat fingers - compared to a mouse pointer.  O.K. for reading books and listening to music.  Just try to do a write document with embedded graphics and pictures, or manage finances....

Choices...

Jerry
Jerry

I'm getting seriously tired of your continuing statement that Unity was designed as a tablet interface. I'd suggest if you dislike Unity, stop testing it, there are plenty of other versions that need testing as well. We don't get near enough feedback on Xubuntu, Edubuntu and Kubuntu, why not try to one of those.

---

### Post by MG&amp;TL on 2011-12-05
> **tlcstat said:**
> Greetings,
Hey! Wouldn't it be a shocker to convert the iso to 1450 720k floppies to install on my Tandy 1000 and then get a "kernel panic error"?
:)
tlcstat

Yeah!

Or "Unity failed to load"

---

### Post by Dragonbite on 2011-12-05
They've removed Gimp. I think they've removed PiTiVi and are removing Mono and programs Banshee and Tomboy.  While Banshee is replaced by Rythmbox, I don't think they are replacing Tomboy initially.

Yet they are increasing the size of the CD?  What is it taking up all the extra space?  Unity? LibreOffice? UbuntuOne? Software Center?  Either they are adding a whole new collection of things or what is staying is getting larger and larger.

Three out of those 4 are Ubuntu-focused products that while they look good, they aren't really so good, IMHO, to warrant moving from CD to DVD! I find Unity and Software Center good, but pretty slow and questionably an "improvement".

OpenSUSE 11.4 DVD includes a Live session of 2 choices (KDE and Gnome), as well as the RPMs for picking and choosing applications during installation.  The DVD provides a number of beneficial reasons to warrant using, while still having CDs available for download.  That is a smart utilization of the DVD.


This is starting to smell like moving the buttons to the left side; a controversial but good idea when there is a plan to take advantage of that move, and here we are still with no planned use of the right-side being implemented.

Why not bump it up to to a DVD that includes extra add-ons that the user can include during installation such as Gimp, Open Shot, optional Language Packs, etc. which are free, distributable but not part of the Live image.  Kind of like how Gparted is included in the Live image, but isn't installed by default.

---

### Post by thatguruguy on 2011-12-05
> **cariboo907 said:**
> I'm getting seriously tired of your continuing statement that Unity was designed as a tablet interface. I'd suggest if you dislike Unity, stop testing it, there are plenty of other versions that need testing as well. We don't get near enough feedback on Xubuntu, Edubuntu and Kubuntu, why not try to one of those.

Thank you for posting that.

---

### Post by thatguruguy on 2011-12-05
> **Dragonbite said:**
> They've removed Gimp. I think they've removed PiTiVi and are removing Mono and programs Banshee and Tomboy.  While Banshee is replaced by Rythmbox, I don't think they are replacing Tomboy initially.

Yet they are increasing the size of the CD?  What is it taking up all the extra space?  Unity? LibreOffice? UbuntuOne? Software Center?  Either they are adding a whole new collection of things or what is staying is getting larger and larger.

Three out of those 4 are Ubuntu-focused products that while they look good, they aren't really so good, IMHO, to warrant moving from CD to DVD! I find Unity and Software Center good, but pretty slow and questionably an "improvement".

OpenSUSE 11.4 DVD includes a Live session of 2 choices (KDE and Gnome), as well as the RPMs for picking and choosing applications during installation.  The DVD provides a number of beneficial reasons to warrant using, while still having CDs available for download.  That is a smart utilization of the DVD.


This is starting to smell like moving the buttons to the left side; a controversial but good idea when there is a plan to take advantage of that move, and here we are still with no planned use of the right-side being implemented.

Why not bump it up to to a DVD that includes extra add-ons that the user can include during installation such as Gimp, Open Shot, optional Language Packs, etc. which are free, distributable but not part of the Live image.  Kind of like how Gparted is included in the Live image, but isn't installed by default.

I still haven't seen confirmation that the default .iso ***will*** be 750 MB; I've only seen the discussion of the agreement to increase the size if necessary.  Presumably, if it's not necessary to increase the size of the .iso, it won't be increased.

---

### Post by Dragonbite on 2011-12-05
> **thatguruguy said:**
> I still haven't seen confirmation that the default .iso ***will*** be 750 MB; I've only seen the discussion of the agreement to increase the size if necessary.  Presumably, if it's not necessary to increase the size of the .iso, it won't be increased.

Of course everything is speculation at this point.  So far it is an "idea" that just came up, but it came up for a reason.

---

### Post by tlcstat on 2011-12-05
Greetings,
 					Originally Posted by **jerrylamos** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11514345#post11514345") 				
 				> Imitation "tablet" eye candy code is famously obese and will drive ubuntu fatter and fatter.

The reason the installation is getting bigger and no doubt will be moved to a DVD or multiple CDs is the demand that users have for functional software. After all synaptic, gparted and the like are tiny utilities that are easy to install by anyone that needs them. Here's a suggestion, leave out Libre Office and include Abiword instead. That will make a lot of space available. 

If you check out the newest Debian installation, it is up to 9 4.4Gig DVDs which equal 53 CDs.  There is no question that Ubuntu will eventually move to a DVD installation. Only a person that thinks that Unity is tablet eye candy would think otherwise. 

If you have a demand for tiny, I suggest that you give Puppy Linux a try. Its only 130 Meg and can be installed in any partition format. It even includes a flash drive installer. 

The 1.2 Gig DVD that we have seen in the Ubuntu Downloads are just a teaser.  Or maybe history doesn't just move forward!

---

### Post by jbicha on 2011-12-07
Ubuntu developers are generally well aware of Abiword. While it's a nice simple app, LibreOffice has better support for Microsoft Office documents. The ability to open spreadsheets and PowerPoint presentations from the default CD is a huge advantage Linux has over Windows nor OS X and makes LibreOffice unlikely to be removed from the Ubuntu CD any year soon.

---

### Post by lolpenguin on 2011-12-07
Well, how 'bout we use BitTorrent, there'll be so many downloads and so many seeds. Perfect!

---

### Post by teh603 on 2011-12-07
> **tlcstat said:**
> 

If you have a demand for tiny, I suggest that you give Puppy Linux a try. Its only 130 Meg and can be installed in any partition format. It even includes a flash drive installer. 

Unless something massive has changed, don't use Puppy for anything but a USB or CD/DVD install. Puppy won't properly integrate .sfs files on a hard drive install and has no package management system at all.

---

### Post by tlcstat on 2011-12-07
Greetings,
original by teh603
> Unless something massive has changed, don't use Puppy for anything but a USB or CD/DVD install. Puppy won't properly integrate .sfs files and has no package management system at all.

Actually Puppy Lucid has a very good package system.  However I was only offering it as an alternative to those that fear a transition to DVD.  Should be a long time before Puppy gets up to 700MB.  Also Abiword would most definitely eliminate the bloat of Libre Office.  Plus you can do desktop graphics with Abiword by arranging a bunch of a's on the page to create a desired graphic. I've seen it done before.  
The concern of the OP was a greater than CD sized release. I'm just grabbing for a few alternatives given the publics addiction to large software. Heck the kernel itself is twice the size that it once was plus a whole cadre of firmware for device support that keeps getting bigger.  
Nice thing about Puppy Linux is you don't even have to worry about having bluetooth. They just leave it out which in turn makes the release even smaller. It's a miracle! So who needs a great big bloated distro like Ubuntu that will ultimately lead to a release on a DVD or two?  Answer: I do!

tlcstat

---

### Post by teh603 on 2011-12-07
> **tlcstat said:**
> Actually Puppy Lucid has a very good package system.Really? When did they get that? Last time I tried using it, they were still expecting everyone to use .sfs files.

---

### Post by tlcstat on 2011-12-07
Greetings,

original post by teh603
> Really? When did they get that? Last time I tried using it, they were still expecting everyone to use .sfs files.
They make sfs packages available. I guess that does imply an expectation. I've installed the full version of Open Office in Puppy with no problems. Same with Google Chrome and others.  Kind of like saying that Ubuntu expects everyone to work from the Terminal just because they have a terminal.  The sfs files keep the Puppy distribution small but easy to expand.  I don't have any problem understanding that concept. Its like .deb vs .rpm, just a choice of method. But hey thats what you have to settle for when you demand a CD sized distribution.  Remember this thread was started by someone that thinks Ubuntu needs to be on a CD for millions just because his IBM computer won't boot from USB. Just plain silly! 
tlcstat

---

### Post by cariboo on 2011-12-07
Again to add to what tlcstat said, the devs can increase the size of the iso to 750MiB **if needed**, they are still working on keeping the size small enough to fit on a CD.

---

### Post by ubername on 2011-12-07
> Remember this thread was started by someone that thinks Ubuntu needs to be on a CD for millions just because his IBM computer won't boot from USB.

Not really. This thread was started by someone who couldn't understand why, if you were going to make the image bigger than a CD, you would make it just a little bit bigger, rather than moving up to the next real constraint, whatever that was deemed to be.

---

### Post by teh603 on 2011-12-07
> **tlcstat said:**
> They make sfs packages available. I guess that does imply an expectation. I've installed the full version of Open Office in Puppy with no problems. Same with Google Chrome and others.  Kind of like saying that Ubuntu expects everyone to work from the Terminal just because they have a terminal.  The sfs files keep the Puppy distribution small but easy to expand.  I don't have any problem understanding that concept. Its like .deb vs .rpm, just a choice of method. But hey thats what you have to settle for when you demand a CD sized distribution.  Remember this thread was started by someone that thinks Ubuntu needs to be on a CD for millions just because his IBM computer won't boot from USB. Just plain silly! 
Depends on how recently you've used Puppy. As I said, the last time I'd used it, sfs files were the only form of package management available and they would specifically *not* integrate if you'd installed it on a hard drive.

Not all of us are leet enough to unpack a tarball and get everything into the right place the first time, y'know.

---

### Post by tlcstat on 2011-12-07
Greetings,
Originally posted by teh 603
> Depends on how recently you've used Puppy. As I said, the last time I'd  used it, sfs files were the only form of package management available  and they would specifically *not* integrate if you'd installed it on a  hard drive.

I have  a Puppy Installation installed all of the time. Currently Lucid 528. Evidentially your experience goes back to the good old days like when Ubuntu was still shipped on a 700MB CD:)

tlcstat

---

### Post by kuvanito on 2011-12-09
there must be at least 10 to 20 apps with no use or minimal use that comes in every ubuntu build,i am just going to mention a few,Games(all games),Libre Office can be installed later,Rhythmbox,Too many different settings,settings for this,settings for that,etc,etc,etc.I think the size could actully be down to 500 MB....Guys,There is a Software Center for all we need....

---

### Post by cariboo on 2011-12-09
> **kuvanito said:**
> there must be at least 10 to 20 apps with no use or minimal use that comes in every ubuntu build,i am just going to mention a few,Games(all games),Libre Office can be installed later,Rhythmbox,Too many different settings,settings for this,settings for that,etc,etc,etc.I think the size could actully be down to 500 MB....Guys,There is a Software Center for all we need....

What about the people that have no internet, or only dial-up available? They aren't going to to be able to download an iso, but there are plenty of other methods available to get a CD of the distribution.

---

### Post by PaulW2U on 2011-12-09
> **kuvanito said:**
> Libre Office can be installed later

Read post #133, LibreOffice is not going to be removed from the CD.

---

### Post by hakermania on 2011-12-09
My opinion: I think most of us out there use USB sticks up to 2GB in size so as to install e.g. Ubuntu, so what's the point? I wouldn't really care if the size of the iso was up to 1.5GB

---

### Post by irv on 2011-12-09
> **cariboo907 said:**
> What about the people that have no internet, or only dial-up available? They aren't going to to be able to download an iso, but there are plenty of other methods available to get a CD of the distribution.

I would think that most computer/Linux users know someone with an Internet fast enought to download a .iso image file. A few years ago I was in Africa and in an area where many did not have an Internet connection but they had coffee shops all over to get on the Internet and download files.

Just about anywhere I go I can find and Internet fast enough to do what I have to do. Airports Motels Resterants etc. And many places have computers available and all you need is a USB drive. Where there is a will there is a way.

---

### Post by cariboo on 2011-12-09
> **irv said:**
> I would think that most computer/Linux users know someone with an Internet fast enought to download a .iso image file. A few years ago I was in Africa and in an area where many did not have an Internet connection but they had coffee shops all over to get on the Internet and download files.

Just about anywhere I go I can find and Internet fast enough to do what I have to do. Airports Motels Resterants etc. And many places have computers available and all you need is a USB drive. Where there is a will there is a way.

You're assuming everyone that has no internet connection, or on dial-up has a laptop, I know several people that live in areas where dial-up, or satellite is the only option, and they don't own a laptop, it's pretty tough for them to bring their desktop system to a cafe in town to download an iso. :)

---

### Post by Dragonbite on 2011-12-09
> **cariboo907 said:**
> You're assuming everyone that has no internet connection, or on dial-up has a laptop, I know several people that live in areas where dial-up, or satellite is the only option, and they don't own a laptop, it's pretty tough for them to bring their desktop system to a cafe in town to download an iso. :)

The other possibility is people with a limited download amount and while a minimal CD may be feasible, not knowing beforehand if you are going to be able to fit the rest under your cap can be nerve-wracking!

---

### Post by kuvanito on 2011-12-09
hehehehe,cariboo907 you make it sound like ppl who use ubuntu are bushwacker and live in the middle of nowhere,hehehehe
who doesn't a neighbor with an open internet or better yet go to mcdonalds,now tell me that there are no mcdonalds in the bush...:D:D:D

---

### Post by irv on 2011-12-09
> **cariboo907 said:**
> You're assuming everyone that has no internet connection, or on dial-up has a laptop, I know several people that live in areas where dial-up, or satellite is the only option, and they don't own a laptop, it's pretty tough for them to bring their desktop system to a cafe in town to download an iso. :)

I carry two USB thumb drives in my pocket all the time, but most of the time I do have my laptop with me. The point I am making is if someone really needs to get a iso file there are ways to do it.

---

### Post by jerrylamos on 2011-12-10
> **irv said:**
> I carry two USB thumb drives in my pocket all the time, but most of the time I do have my laptop with me. The point I am making is if someone really needs to get a iso file there are ways to do it.

Sure, just buy a new pc or notebook that will boot from USB, even though the old pc or notebook is still nice and fast and responsive and runs internet videos just fine.  Trash it anyway.  Running Lubuntu on it right now.

Jerry

---

### Post by teh603 on 2011-12-10
> **jerrylamos said:**
> Sure, just buy a new pc or notebook that will boot from USB, even though the old pc or notebook is still nice and fast and responsive and runs internet videos just fine.  Trash it anyway.  Running Lubuntu on it right now.Just because it supports USB doesn't mean it can boot off USB. My Winbook has USB, but there's no boot menu and the BIOS doesn't support any kind of USB boot. No way, no how.

In case you're wondering, its BIOS *can* boot off a floppy drive...

---

### Post by cariboo on 2011-12-11
> **jerrylamos said:**
> Sure, just buy a new pc or notebook that will boot from USB, even though the old pc or notebook is still nice and fast and responsive and runs internet videos just fine.  Trash it anyway.  Running Lubuntu on it right now.

Jerry

If you're trashing hardware, because you can't find a work-a-round, which if I recall you have, by using grub to boot an iso, you're doing something wrong, For desktop systems, dvd burners, are quite inexpensive, and with a little searching you can find dvd burners for older laptops that don't cost a lot of money. Just because you've owned a piece of hardware for a numbers of years, doesn't mean it isn't upgradable. That's how many people keep older hardware running longer.

---

### Post by jerrylamos on 2011-12-11
> **cariboo907 said:**
> ....if I recall you have, by using grub to boot an iso,....

A few releases ago, I could boot a .iso from a hard drive and do an install on the same hard drive.  My laptops typically have just one hard drive.

No more. "Someone" put a check in install and won't allow installing into a different partition on the same hard drive that the boot .iso is on.

When ubuntu images exceed 700 mb I get to try lubuntu, and when that won't fit I'll have to learn how to do some minimal install plus internet package download. Last couple times I tried that I went down in flames missing some libraries that I didn't know what packages they were in.

Jerry

---

### Post by effenberg0x0 on 2011-12-11
Can anyone move this to the cafe? Or prove me that this topic content is relevant to PP in the way it has developed? All I see is pathetic sobbing about a couple MB and the fury of inanimate USBs that in some magic way choose when to boot or not.

I can't stand reading this anymore. It's been the same yada yada about laptops that don't boot from USB myths, how jumps from 640 to 750MB are evil, etc.  

And no one cared that about 2 weeks (or more) ago I posted a link to an amazing technical guide explaining why **some** PCs won't boot from **some** USBs and how to make **any** PC boot from **any** USB. Then I took a week of this forum (to avoid being banned from it by saying what I really want to say right now) just to come back and find the same **ridiculous** discussion still going on in circles. And apparently not a single individual managed to invest one hour of their life to read the document, try something, discuss ways, ask for help, etc and finally fix their boot issue. Sure they didn't: It's easier to blame the evil Ubuntu Corporation for adding a couple MBs to the ISO than to put some effort into anything productive.  

This thread, and everything in it, is not about ISO size and "How to install new ISOs of Ubuntu whatever the size they are" or "lets find out how to make the ISO+USB/CD thing easier for the community". It never was. It hardly relates to PP. It's just about how lazy people are to try to learn and accomplish something, or at the very least show some interest and ask for help. It's about how easily people choose to fall into the "poor me and my USB-less-PC" approach just to get some attention. 

It doesn't matter if the ISO is 600MB, 700, 800, 1GB, 4GB. Any individual has one (1) friend that has broadband and a CD/DVD Burner. Or than can lend you a USB Stick. Or dload/burn it at school. Or at work. Or go to a cybercafe and do it. If any of these sounds too complicated, then don't update, don't use a PC, go do other thing, be happy with anything else.

EDIT: I can understand how were now supposed to re-do General Help typical activities, that is, keep repeating over and over the same things (black screen=update VGA, no boot=fix grub, crashes=don't partial update, I can't do xyz=this is alpha, so it's broken/will not be in the future, etc) now that Alpha users existence was acknowledged, instead of actually investing our time to testing U+1, as crazy and unnecessary as it seems. But this thread, in particular, is useless.

---

### Post by cariboo on 2011-12-11
@effenberg0x0, it's always easier to complain about something, than it is to actually do something about it. 

I agree, that this thread seems to have run it's course, and the thread has turned circular. I'll leave it open for another 24 hours for anyone that wants to get their final comments in, then close it.

---

### Post by effenberg0x0 on 2011-12-12
Thanks Cariboo. If anyone wants to start a thread to discuss viable things like:

- Help me boot from USB
- How to make USB boot more reliable
- How to install ISO to partition and boot from it
- Etc

I will be the first to try to help.

---

### Post by ronacc on 2011-12-12
I think that one of the reasons that many are complaining is that in the past when we have suggested going to a larger size .iso to allow more ( or larger ) applications on the install disk , we were told that such an increase in size was absolutely impossible because a CD sized install was sacred and that the world would end if we exceeded it , so it sort of sticks in our craw that it is cavalierly exceeded when it is convenient for the dev's ( or whoever decided that 700mb was no longer a "magic number" ).

---

### Post by kansasnoob on 2011-12-12
One possible need comes to mind here, improving either the official or community documentation for using the alternate images. Any thoughts on that?

---

### Post by ventrical on 2011-12-12
Just reading through and noticed that no one had mentioned the PLOP bootloader (which I just recently used on a PIII 600MHz system with 1999 Award BIOS and no USB support) and it booted the  Precise alpha USB 1 just fine !!

  It takes a little work  to learn how to do this but once you get the hang of it  you can then learn to bring back older systems from the boneyard ! :)

thanks everybody for sharing..

---

### Post by jerrylamos on 2011-12-12
> **kansasnoob said:**
> One possible need comes to mind here, improving either the official or community documentation for using the alternate images. Any thoughts on that?

Glad you mentioned that.  Any pointers on how to use the alternate CD's?  I've seen some mention example 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Some of it looks a little out of date, example to grub hd0,1 is now hd1,1
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
but there's some info I didn't know to give it a try.

Jerry

---

### Post by Dragonbite on 2011-12-12
I am against it because it reduces the ease of distribution to individuals on a technical, and non-technical manner (pop cd into tray = easy, download and run from ISO = not easy, cds = cheap, pay for USBs to pass out = not-so-cheap).

*I* don't have a problem since I already use a USB for all my distribution trials (got one with Ubuntu in my pocket right now).  But for distributing, this is another matter.

---

### Post by jerrylamos on 2011-12-12
> **jerrylamos said:**
> Glad you mentioned that.  Any pointers on how to use the alternate CD's?  I've seen some mention example 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Some of it looks a little out of date, example to grub hd0,1 is now hd1,1
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
but there's some info I didn't know to give it a try.

Jerry

It works!  Copied the oversize .iso onto my Thinkpad T40's hard drive into /dev/sda1 new folder /boot/iso, previous experience /dev/sda1 is preferable.

and to /etc/grub.d/40_custom appended:

menuentry "Precise ISO sda1" {
set isofile="/boot/iso/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

then sudo update-grub.

Note I use gparted to prepare a target partition beforehand.

Rebooted selecting the above entry

In terminal issued magic incantation from wiki wizard:

sudo umount -l -r -f /dev/sda1

install started and away I went!

One slight curio, at the end of the successful install, it asked "continue or restart".  What it restarted was the .iso boot, not the expected new install??  Did manual restart O.K.

Anyway, off and running, oversize .iso, "won't boot pen drive", but will run and install from a big fat precise .iso file on the hard drive.

Thanks, Jerry

p.s. selected Unity-2D of course.  I don't depend on the automatic fallback from Unity-3D to something that works.

---

### Post by kansasnoob on 2011-12-13
> **jerrylamos said:**
> Glad you mentioned that.  Any pointers on how to use the alternate CD's?  I've seen some mention example 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Some of it looks a little out of date, example to grub hd0,1 is now hd1,1
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
but there's some info I didn't know to give it a try.

Jerry

I'm most concerned about the instructions for the actual Alternate CD:

[https://help.ubuntu.com/community/Installation#Alternate_Installation](https://help.ubuntu.com/community/Installation#Alternate_Installation)

In upcoming days I'll do one in a VM so I can grab some screenshots, then I'll open a discussion here ;)

It's easy for me to use because I've fiddled with Debian to some degree as far back as 2001 or 2002, just never fell in love with Linux until I ran Gutsy though :)

But the Alt iso really is just a slightly tweaked Debian installer.

---

### Post by jbicha on 2011-12-13
> **jerrylamos said:**
> A few releases ago, I could boot a .iso from a hard drive and do an install on the same hard drive.  My laptops typically have just one hard drive.

No more. "Someone" put a check in install and won't allow installing into a different partition on the same hard drive that the boot .iso is on.


Jerry, could you please report the bug about the inability to install to a different partition of the same disk that the .iso is booted from? I'm pretty sure that was an unintentional regression and it should be fixable. I can confirm that that trick used to work but it no longer works as of a release or two ago.

---

### Post by jerrylamos on 2011-12-14
> **jbicha said:**
> Jerry, could you please report the bug about the inability to install to a different partition of the same disk that the .iso is booted from? I'm pretty sure that was an unintentional regression and it should be fixable. I can confirm that that trick used to work but it no longer works as of a release or two ago.

The inability to install comes from the booted .iso mounting the cdrom/hard disk boot partition and ubiquity's usual fuss the user could decide to change the partition ubuntu is running from during the install creating a train wreck.  Once the Live ubuntu is running from memory it doesn't need the boot device any more but ubiquity doesn't know that.

So the work around of 

sudo umount -l -r -f /dev/sda1

suits me.  The user has to read the wiki to find out how to boot the .iso anyway so the user should see that instruction.

Jerry

---

### Post by cariboo on 2011-12-14
I've let everyone have their say for a little longer than I suggested earlier.Thread closed.

---

