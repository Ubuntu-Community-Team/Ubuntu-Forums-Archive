---
title: "Is it wise for me to move from ubuntu 14.04 to ubuntu 12 or 13"
date: 2014-11-05
forum: Server Platforms
---

### Post by lightman2 on 2014-11-05
It seems the current ubuntu release has a lot of issues,i keep on running from one error to the next and my time to present a cloud demo is running out.Is a wise decision that i start all over again with a much stable release?

---

### Post by Bucky Ball on 2014-11-05
12.04 LTS, yes. 12.10 and 13 anything, no. Has reached EOL and is no longer supported by Canonical or these forums.

Your best option would be to post threads regarding the issues you're having with descriptive titles, all relevant information, and in the appropriate areas of the forum.

12.04 is supported until 2017, 14.04 until 2019.

Can you install 12.04 on another partition for the cloud demo and come back to 14.04 when you've got time? I often do this with the LTS versions and slowly migrate to the newer one over time. I only use 14.04 but if anything goes pear shaped I have two 12.04 installs to fall back on (and even an EOL 10.04 LTS!).

---

### Post by Jonathan L on 2014-11-05
Hi Lightman2

For my more conservative and downtime-averse clients, I recommend 'penultimate LTS', and so for example will be installing 12.04 LTS until after 16.04 LTS is released, then they'll go to 14.04.  Normally installing the last point release available: these clients are installing 12.04.5 on new systems at the present time.  These clients are obviously conservative on hardware too, and don't need, want, or use novelty in their machinery, and have uptimes often in years.

The reasoning is that old bugs are so much easier to find than new ones, and they're well documented and known about.  

I'd really never suggest using anything other that the LTS versions for production work unless a) there's an overwhelming reason for it, and b) there is adequate support in the client organisation for the sadly-inevitible surprises.

For innovation-hungry clients I usually suggest installing each X.04 release the following January.

Of course these are just two of the innumerable possible policies, which you have to fit to the individual client organisation, but wanted to let you know you certainly won't be alone if you adopt 12.04.

Hope that's of some use.

Kind regards,
Jonathan.

PS.  Of course I'm sure everyone reading this pays close attention to security updates, but it's worth repeating that some of the 12.04 releases are vulnerable to the Heartbleed bug see [http://www.ubuntu.com/usn/usn-2165-1/](http://www.ubuntu.com/usn/usn-2165-1/) which it would be extremely unwise to propagate.

---

### Post by lightman2 on 2014-11-06
Thanks trying out your advice.

---

### Post by houstonbofh on 2014-11-09
I too am using 12.04 for all production and servers, and only have 14.04 on testing desktops.  And I am still working out 14.04 bugs...

---

### Post by Jonathan L on 2014-11-12
Hi again Lightman2

Of course it isn't supposed to be this way, but it *is* this way: even going from a given release to the next 'point' release can render your system inoperable.  I had a recent rather sorry situation where my equipment worked perfectly on 12.04.2, but when I tried it on 12.04.3 it didn't work (no display on console).  Those responsible for live systems in the field have a very difficult juggling act between security improvements on the one hand and new bugs on the other.  This particular episode caused a deployment delay of about four weeks and cost about two intensive days of testing for me to satisfy myself entirely about what was happening.  The moral of this story is that if you have an important demonstration, try to control everything and change nothing between setup and demo.

Having said that, in my experience the various distributions vary a lot in this regard, and Ubuntu provides a pretty good compromise between the various forces, and in particular you can run basically the same system on laptops and servers, which helps with developers not being too far distant from the deployment systems.

Everybody's experience will vary, sometimes greatly depending on their application and environment.  I hope you'll have time to tell us how your progressed with your project.

Kind regards,
Jonathan.

---

### Post by houstonbofh on 2014-11-12
Jonathan,
So you got bit by [https://bugs.launchpad.net/bugs/1132736](https://bugs.launchpad.net/bugs/1132736) too, huh?  Amazing that it was a problem at all, and more so that it STILL is not fixed...

Yes, upgrades have risk.

---

### Post by Jonathan L on 2014-11-13
Hi Houstonbofh ... actually the problem that affected me recently was a different one, but the moral is the same: despite the best intentions and great efforts of developers, it's not remotely unusual for there to be unintended consequences.  And so, responsibility for functionality has to rest with the users and their helpers.  Indeed, it's my opinion that one of the most significant differences between open source and closed systems is that with open source we take responsibility for ourselves.  The original poster though had a mostly-technical question about versions to which the answer is "Might well be a good idea", and I'll stop here before I get completely off-topic.  Kind regards to all.  Jonathan.

---

### Post by houstonbofh on 2014-11-16
So, to stay with the off topic diversion, but bring it back around to on topic, this is what I do for many critical systems.

If you only do LTS releases you have to upgrade every 2 to 4 years.  Hard drive warrentees are also around 2-4 years. :)  And they double or more in size every 2-4 years. :)  So...

I buy a new drive and use dd (or clonezilla) to copy my existing install to a new and larger drive.  (Expanded to fill it)  Then I upgrade that copy.  If all goes well, I have a new system on a newer, larger and faster drive.  If not, I stick the old drive in while I figure out why things went wrong.

---

