---
title: "How did you upgrade from Hoary to Breezy?"
date: 2006-02-26
forum: The Cafe
---

### Post by aysiu on 2006-02-26
It's still almost two months away, but I'm already thinking about Dapper.

I'm just curious as to what others' upgrade experience was like four months ago...

---

### Post by xequence on 2006-02-26
Downloaded the release canditate of breezy two days before the final release and did a clean install.

---

### Post by Sutekh on 2006-02-26
I waited until my local mirror wasn't so bogged down and when people started some real seeding, and downloaded the iso via torrent.

I will probably do the same for Dapper, I like to have something physical to install with.  I will definately get a LiveCD or two.


**Edit:** Can I take the *early* poll results to mean that you tried a dist-upgrade and it went pear-shaped aysiu?

---

### Post by PatrickMay16 on 2006-02-26
I did dist-upgrade and it worked fine. I guess I'm pretty lucky, since so far I've only installed Ubuntu once (no reinstalls) and the dist-upgrade I did went perfectly.

---

### Post by aysiu on 2006-02-26
[QUOTE=Sutekh]
**Edit:** Can I take the *early* poll results to mean that you tried a dist-upgrade and it went pear-shaped aysiu?[/QUOTE] Yeah. I'm just curious as to whether my situation was a freak accident or commonplace. 

Also, if this poll gets enough results, it'll be a good indicator for people whether they should upgrade or reinstall for Dapper.

---

### Post by Sutekh on 2006-02-26
To me the idea of a dist-upgrade sounded way off the planet, both in terms of technical cleverness (and coolness) and technical risk (and scariness).  I will be interested to see the results.

---

### Post by TechSonic on 2006-02-26
I wont do an upgrade.  I plan on downloading the Dapper ISO and burning a few copies and then backing up my files on my second hard disk and then installing a fresh copy, all nice and clean like.

Just like I did when I moved to Breezy.  I downloaded it on Hoary and did a clean install.

---

### Post by Iandefor on 2006-02-27
Dist-upgrade worked pretty well, and I got to keep all my documents and settings from Hoary.

---

### Post by Qrk on 2006-02-27
I always do a clean install, as I collect way too much junk in between the releases.

Its good to start with a clean slate.

---

### Post by vayu on 2006-02-27
I downloaded a pre-release and did a clean install on my desktop.  Had tons of problems.  Then downloaded the RC, clean install, tons of problems.  Downloaded the final, still had problems.  Waited a week did apt-get update, things started to get sorted out.  For my laptop I waited about three weeks after the final, then apt-get dist-upgrade, no problems whatsoever.  That machine is still running great.

For Dapper, I'm waiting 4 weeks then I'll dist-upgrade.

---

### Post by GreyFox503 on 2006-02-27
aysiu, what's up with all the polls?  You must be a statistician at heart.  :)

Oh yeah, and my upgrade to Breezy had a couple minor problems, but I re-installed anyway to check out the new installer/have fun.

---

### Post by frodon on 2006-02-27
I didn't have any problems at the time with the dist-upgrade, the only thing i had to do was to remove xcompmgr in the session startup programs to avoid a very long login.

So my dist-upgrade from hoary to breezy was really painless, so i will do the same thing to update my computer to drapper (after making a ghost of my partition obviously).

---

### Post by nocturn on 2006-02-27
I never had dist-upgrade fail on me (did it from Warty -> Hoary on 3 machines, from Hoary to breezy on 1).

What did happen regularly was that I had to run dist-upgrade more then once to get on the new release.

---

### Post by xmastree on 2006-02-27
Well, given that I had a new motherboard, so I therefore needed to reinstall XP,
plus the fact that this new mobo didn't have the 'select which disk to boot from' option which I was using to boot from hdb,
plus the fact that I needed to re-organise everything anyway,
plus the fact that the new unit came with a sata drive,
and the fact that my connection isn't reliable enough to attempt a live update...

I started over.

Seemed like the best option (although just for fun I tried to boot from my hoary/hdb install and it was fine).

---

### Post by Gustav on 2006-02-27
I installed Warty when it came and after that I've been dist-upgrading for every new release. It has always worked flawless.

(I'm by the way using the same /home partition that I used when I started with Linux maybe 4 years ago (with Mandrake 9.0) only side-effect is a lot of .*stuff*. It even kept all my theme settings from Debian :))

---

### Post by angkor on 2006-02-27
I dist-upgraded. 

Some things went wrong because I had a different version of OpenOffice installed with dpkg. Nothing a few 'apt-get -f installs' coudn't fix. 100 times better than my Debian dist-upgrading experiences in the past.

With Dapper I'll take the same route. If the dist-uprade really doesn't work I'll do a fresh install.

---

### Post by aysiu on 2006-02-27
[QUOTE=GreyFox503]aysiu, what's up with all the polls?  You must be a statistician at heart.  :)[/QUOTE] Who knows?

By the way, I've noticed that some people have had problems and others haven't. Does anyone know what makes it so that some can upgrade flawlessly while others have issues? Is it that they have different hardware?

---

### Post by GreyFox503 on 2006-02-27
I would imagine that the further away an Ubuntu install gets from the default, the higher the probability that the upgrade will fail.  Of course, the developers test it so it'll work flawlessly with a default Hoary install, probably with and without updates.  But they can only test so many combinations of software against their upgrades.

The more you install custom *.debs, force package versions in synaptic, install something important to the system from source, etc. the less predictable the upgrade will be.

That's just my idea, though.  It's possible that the upgrades have trouble differing with hardware.  But one would think that upgrading would only add support for hardware, not take away existing ones?

Also custom edited config files like xorg.conf may make it trickier.

---

### Post by aysiu on 2006-02-27
Thanks for the explanation, GreyFox.

That makes sense. It was just difficult for me to articulate it in my head.

---

### Post by FizDev on 2006-02-27
I downloaded the ISO and made a fresh install... that way, if I mess something real bad, than I will be able to "reset" everything without having to install an old version and then update everything else. :D

---

### Post by Lunixfanboy on 2006-02-27
I started with Warty, then dist-upgraded to Hoary, from thence to Breezy again via dist-upgrade a day before they announced the official release to beat the stampede on the servers, and will be doing a Breezy to Dapper when it hits. Had no great difficulties, but my machinery is almost five years old (1 GHz processor, 640 meg of ram, ATI 9250, Yamaha sound card) so doesn't really present any challenges.

---

### Post by raggamuffin on 2006-02-27
[QUOTE=Qrk]I always do a clean install, as I collect way too much junk in between the releases.

Its good to start with a clean slate.[/QUOTE]

I agree...

I originally did a dist-upgrade without problem...but I went ahead and did a clean install anyways because I figured in the end it'd be easier than manually going through my ~/ and removing unused/unwanted stuff...

---

### Post by DavidW2 on 2006-02-28
I started with Hoary on my laptop and wasn't familiar with repositories and apt-get (still learning more about apt) when Breezy came out.  So I downloaded the Breezy ISO and burned it to CD.  I planned on just starting over with Breezy but I put it in my drive with Hoary running.  It recognized it and asked if I wanted to upgrade.  I clicked a few buttons and I was running with Breezy.  No probs.  I did have to go through the upgrade manager a few times to get everything though.

---

