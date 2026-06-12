---
title: "Deluge 1.0 rc1"
date: 2008-07-14
forum: The Cafe
---

### Post by zachtib on 2008-07-14
After about a year of development, a new version of Deluge is nearing release.  This is a complete rewrite from the 0.5.x version of Deluge, and includes several new features, most noticeably the ability to run the frontend and backend on different computers.  However, as 1.0 uses a brand new plugin system, many of the plugins from 0.5 have yet to be ported over.

This branch was previously known as Deluge 0.6.

Packages are already available in my repository here: [http://launchpad.net/~zachtib/+archive](http://launchpad.net/~zachtib/+archive)

If you choose to test, please report any bugs you encounter at [http://dev.deluge-torrent.org](http://dev.deluge-torrent.org) so that this release can be as solid as possible.

(Deluge 0.9.x is the RC series for 1.0)

UPDATE 7/15: RC 2 is out, check out my announcement here: [http://collegegeek.org/2008/07/15/deluge-10-release-candidate-2/](http://collegegeek.org/2008/07/15/deluge-10-release-candidate-2/) (Lots of screens, hope my server is up to the task)

---

### Post by Lostincyberspace on 2008-07-14
Finally this has taken forever.

---

### Post by zachtib on 2008-07-14
> **Lostincyberspace said:**
> Finally this has taken forever.

Good things come to those who wait? :)

It's still a ways away from a final 1.0 release.  The client is pretty much there, but as I said, the plugins need to be ported (I'm trying to port over FlexRSS in my spare time).  This should also provide time to track down as many bugs as possible, so please help test it.

---

### Post by RiceMonster on 2008-07-14
Wow, that looks even better than before. I'm using Deluge 0.5x and I think it's already great :D. Going to try it out for sure.

---

### Post by zachtib on 2008-07-14
Just updated the package with a few changes from trunk, including a bugfix and webui improvements

---

### Post by Spike-X on 2008-07-14
I love this program. Thanks for all your hard work!

---

### Post by mustang on 2008-07-14
I will try it when I have time this weekend. In the meantime, I just wanted to thank you for your hard work and doing this for the community.

---

### Post by BluePlum on 2008-07-15
I'm a noob to ubuntu when it comes to installing stuff but i'm a deluge fan. How do i install this new version. There were like 20 differnt things to download o.o. And how to uninstall last version? Do i need to? help o.o

---

### Post by keiichidono on 2008-07-15
Thaks, i can't wait for 1.0 to come out. :D

---

### Post by zachtib on 2008-07-15
> **BluePlum said:**
> I'm a noob to ubuntu when it comes to installing stuff but i'm a deluge fan. How do i install this new version. There were like 20 differnt things to download o.o. And how to uninstall last version? Do i need to? help o.o

just add the repo I linked to (only hardy packages are available)

then 

sudo apt-get update

and 

sudo apt-get install deluge-torrent

the package is split up so you can install only the frontend or backend if you choose, but the deluge-torrent package will install both.

You don't need to uninstall the previous version, but note that your current torrents won't necessarily transfer over.

---

### Post by skip mcshwang on 2008-07-15
Seems to be working great, but it doesn't show my torrents from the old one?

*edit: Just read your last post about that :) Looking forward to getting the Graph plugin back!

---

### Post by smbm on 2008-07-15
Is there any chance you could build the version in your PPA with uPNP debugging enabled?

I filed this bug:

[http://dev.deluge-torrent.org/ticket/313#comment:6](http://dev.deluge-torrent.org/ticket/313#comment:6)

Which is also applicable to the version in your PPA and would like to provide the information needed but don't really know what I'm doing!

Hope you can help.

---

### Post by zachtib on 2008-07-15
RC 2 is up, plus more screenshots in my unofficial announcement on collegegeek,org

See first post

---

### Post by sotiriss on 2008-07-16
When i installed Deluge 1.0 rc2, i am having problems with my cpu usage. With the 0.5.9.3 version everything was ok (about 4-5% of my cpu  steadily), but now i have sudden increasings of my cpu, which may reach 100% . (I use Hardy)
Thank you, Sotiris

---

### Post by zachtib on 2008-07-16
> **sotiriss said:**
> When i installed Deluge 1.0 rc2, i am having problems with my cpu usage. With the 0.5.9.3 version everything was ok (about 4-5% of my cpu  steadily), but now i have sudden increasings of my cpu, which may reach 100% . (I use Hardy)
Thank you, Sotiris

Then report a bug :)

[http://dev.deluge-torrent.org/newticket](http://dev.deluge-torrent.org/newticket)

Thanks for testing

---

### Post by Masoris on 2008-07-17
Oh, it's quite better than before, new interface is very nice. Only one thing what I missed is there are no number for how many torrents are downloading / seeding now.

---

### Post by adityakavoor on 2008-07-17
looks impressive

---

### Post by FuturePilot on 2008-07-17
Wow, RC2 is amazing. I really love the new interface. Great job to the Deluge devs. It's one of if not the best bittorrent client for Linux. :guitar:

The only thing I kind of miss but it's not a huge deal, is the progress bar that showed the pieces of the file.

---

### Post by zachtib on 2008-07-17
> **FuturePilot said:**
> The only thing I kind of miss but it's not a huge deal, is the progress bar that showed the pieces of the file.

I imagine it will return by 1.1 or 1.2 :)

---

### Post by FuturePilot on 2008-07-17
> **zachtib said:**
> I imagine it will return by 1.1 or 1.2 :)

Awesome! :D

---

### Post by keiichidono on 2008-07-17
RC2 is nice, I hope you guys write up a very extensive change log, I'd like to know what's changed.

---

### Post by zachtib on 2008-07-17
> **CalvinB said:**
> RC2 is nice, I hope you guys write up a very extensive change log, I'd like to know what's changed.

There's [http://dev.deluge-torrent.org/browser/trunk/ChangeLog](http://dev.deluge-torrent.org/browser/trunk/ChangeLog)
and [http://dev.deluge-torrent.org/wiki/Development](http://dev.deluge-torrent.org/wiki/Development)

at the moment

---

### Post by myusername on 2008-07-17
sweet. it looks like utorrent

---

### Post by keiichidono on 2008-07-17
> **zachtib said:**
> There's [http://dev.deluge-torrent.org/browser/trunk/ChangeLog](http://dev.deluge-torrent.org/browser/trunk/ChangeLog)
and [http://dev.deluge-torrent.org/wiki/Development](http://dev.deluge-torrent.org/wiki/Development)

at the moment
I saw that, I wanted to know the change from previous updates though, such as RC1.

---

### Post by tomcheng76 on 2008-08-08
Is it multilanguage like 0.5x in Ubuntu repository ?

---

### Post by keiichidono on 2008-08-08
Using RC5 here and it's sweet, and perfectly stable too. I love the new look and new features. This is definitely going head to head with uTorrent, if it worked as well in the Windows build I would use this in Windows if I had it. ^_^

---

### Post by etnlIcarus on 2008-08-27
I'm using RC7. Are there any plans to bring back the network graph and the old progress bar which showed which chunks have been downloaded?

---

