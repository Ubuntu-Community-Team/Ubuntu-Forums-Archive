---
title: "Live Daily, daily upgrade, final Beta"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-06
This is sort of a procedural question as I'm pretty comfortable with the technology atm.

I've been testing for a couple of weeks and now I'm a bit confused about terminology.
Is there a benefit to a 'fresh install' of the new Beta2 release if I've done a daily apt-get [update upgrade dist-upgrade] on 13.04 daily install on a daily basis? 
This is a testing environment for me, I've kept 12.10 on a different physical device.;)

The reason I ask is because I did some testing on the laptop forum and submitted results; during the testing the system had a number of apport warnings and reports and I'm curious if my procedure was flawed.:confused:

[LIST]
[*]Fresh boot to 13.04
[*]apt-get [update upgrade dist-upgrade]
[*]log out of gnome session fall back
[*]log back into unity for purpose of testing
[*]create and enter my hardware profile for Ubuntu Friendly
[*]run subscribed tests, report results after each test
[*]follow through with apport when the warning appeared (none of the failures here were associated with tests being run - totally different module, they just occurred during the test)
[/LIST]

TIA
Pete

---

### Post by grahammechanical on 2013-04-06
I cannot find fault with your method of testing. How we test is very much a personal thing, in my opinion. There is a need to test

1) the Ubuntu live session
2) the Ubuntu install process
3) the upgrade process from earlier versions
4) running Ubuntu under daily work load (smoke testing)
5) under specific tests asked for by QA
6) the development branch as it develops into the next version of Ubuntu (daily updating)
7) Major new code before it is accepted as stable. Such as Unity 7, Unity Next, Mir, etc., over the next 12 months.

How far we get involved is our choice. We may want to run more than one install of the development branch. Some tests are better done with a default installation that we may put in just for that purpose. I have spare partitions where I can put in fresh installs to test the installation process or the upgrade process.

Personally, I see little point of testing an ISO image day after day. Especially, if I find nothing wrong or if what I find wrong does not get fixed. A few months ago I could not get a live session working without using F6 options. What was the point of testing every day? Once a week should be enough. But why test unless it is to test a fix to a bug?

Sometimes people get into a routine or a process of doing things and they never stop to think if there is another way to do things. They never notice things not working as they should. The process takes over.

Just some of my thoughts. Regards and keep testing. Automated tests are very useful but the ultimate tester is the user and things should be put right so the user does not become the tester. This is where real people as testers come in useful.

Regards.

---

### Post by pfeiffep on 2013-04-06
Thanks for the response.

I'm quite comfortable from a personal level about testing - my questions were directed about the 'official' methods. Additionally is there really a difference between the beta2 release and my method? 
stated another way - do I essentially have the beta2 by following my procedure?

I ask because if not I want to officially comment, or invalidate them!

---

### Post by grahammechanical on 2013-04-06
Sorry, I misunderstood.

The ISO images are snapshots of the development code base. I guess that the daily image will be a little bit behind the daily update installation because updates are being put into the repositories during the period the image is being built. The code base of milestone images (betas) are fixed at that date the image was built. So, if we download and install a beta image then run Update Manager there will be updates available.

By doing daily updates we arrive at the same place as the release image. It is difficult to prove that we are running 13.04 beta 2. ```
uname -a
``` and ```
lsb_release -a
``` will only tell us the Linux kernel and 13.04 but not that it is beta.

Regards.

---

### Post by pfeiffep on 2013-04-06
Thanks, I needed to confirm my suspicions
> [COLOR=#000000]By doing daily updates we arrive at the same place as the release image. It is difficult to prove that we are running 13.04 beta 2.[/COLOR]

So, according to that my testing for the laptop team should be VALID.
The instructions I read about official community testing seemed ambiguous!

---

### Post by jerrylamos on 2013-04-07
> **grahammechanical said:**
> 
By doing daily updates we arrive at the same place as the release image.
Not quite.  Doing daily updates esp. amd64 (less so i386) winds up with fatter and fatter ubuntu as seen from df.  I do apt-get clean, autoclean, autoremoves, linux-image purges, header purges, you name it and no matter what the df shows ubuntu getting fatter and fatter with daily updates.

So I re-install, fairly automated with exec's.  Surprise, df shows much less space being used.  Can also show up bugs to report to launchpad. that weren't there on the daily updates.
 
Also in particular the Beta image is frozen in time with the bugs as of that date.  Daily images were at 2 April for a while now 7 April so I'll likely give that a try - I've a bunch of partitions.  Just did an update and sure enough, ubuntu is fatter in spite of cleans & removes.  No new linux-image tho.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"
Linux Aspire1 3.8.0-16-generic #26-Ubuntu SMP Mon Apr 1 19:52:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

so this doesn't show the 7 April update.  Time for another install.

---

### Post by pfeiffep on 2013-04-07
OK now I'm confused ... my intent for this questioning was to validate my testing from an official standpoint. I really don't want to go through the procedure only to find out that the method used was 'flawed' wrt the community testing. 

I'm really comfortable with my personal testing!
 
Yes I know I'm only one person reporting vs results from hundreds or thousands; but if I'm going to perform tests that are part of the community effort I'd like to insure compliance to their standards. I cannot find this on the QA sites. I can't imagine doing a daily install!

---

### Post by ronacc on 2013-04-07
as long as your install is up to date any bugs you find will be valid . As stated by grahammechanical the daily's are just snapshots of the repo's at the time they were built . That said a fresh install from time to time is good ( some do do it daily ) because most of us add desired non/default software and customizations and its good to start fresh from time to time .

---

### Post by Gyokuro on 2013-04-07
I think you have downloaded it and updated it - as long the lsb package get not updated to the final release I think development branch get issued and therefore no need for another install.

---

### Post by jerrylamos on 2013-04-08
> **jerrylamos said:**
> Not quite.  Doing daily updates esp. amd64 (less so i386) winds up with fatter and fatter ubuntu as seen from df.  
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"
Linux Aspire1 3.8.0-16-generic #26-Ubuntu SMP Mon Apr 1 19:52:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

From df:

Installed April 2 updated daily: 
Used: 3231244
Fresh install April 7 including update:
Used: 2977068

After update I do:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

And of course after a new linux image I do apt-get purge linux-image, purge linux-headers, and the apt-get commands  In this case there wasn't any linux image change.

Now in the days of gigabyte drives an 8.5% growth may not matter - just indicates to me 8.5% of "dead" code has accumulated in just a few days..  My experience over Raring U+1 df shows fatter and fatter.

---

### Post by pfeiffep on 2013-04-08
Thanks to all for the responses - I'm pretty satisfied that my test submissions are within reasonable expected guidlines!

---

### Post by ventrical on 2013-04-08
Usually SDC will read the flags on the .iso.  I am not sure if they no longer use that convention.

---

