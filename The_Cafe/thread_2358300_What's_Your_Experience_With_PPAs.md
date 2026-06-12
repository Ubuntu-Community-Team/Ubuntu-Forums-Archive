---
title: "What's Your Experience With PPAs ?"
date: 2017-04-11
forum: The Cafe
---

### Post by Crimple on 2017-04-11
Have you had bad experiences in the form of instabilities, conflicts or whatever else ?

---

### Post by #&amp;thj^% on 2017-04-11
For myself ....Nope!
But the forums can be riddled at times with errors from PPA's
I research before adding them though...Look for current activity, Bugs reported, that sort of stuff.
_Lastly make sure it supports the Version of Ubuntu I'm using_..
EDIT: I also install PPA Purge....that way i can just revert back to stock, if problems arise from the said PPA.

---

### Post by &amp;KyT$0P# on 2017-04-11
> **1fallen said:**
> For myself ....Nope!
+1, same here.  But I too don't just add PPAs left and right.  I only add PPAs where the standard package repositories don't quite cut it for me, and I try to vet PPAs before using them.

Like 1fallen, I check that my version of Ubuntu is supported by the PPA.  I also check the complete list of packages in the PPA to make sure it doesn't look like it could be installing or overriding "too much" packages for what I want it for.

If the PPA passes both checks to my satisfaction, I sometimes then add it in a disposable VM to see what exactly will happen and how well the PPA's software works.


Crimple, do you have specific PPA(s) in mind?  If so maybe we can take a look and offer some more direct advice.

---

### Post by Crimple on 2017-04-12
> **halogen2 said:**
> Crimple, do you have specific PPA(s) in mind?

No, just curious about others experience in general.

---

### Post by linuxyogi on 2017-04-12
I only add a PPA if its maintained by the devs of the original project like [this one]("http://smplayer.sourceforge.net/en/downloads").

---

### Post by mastablasta on 2017-04-13
in some cases PPA is a must (e.g. the owncloud non patching issue)

otherwise it depends what kinds of PPA. the program ones shouldn't affect the overall system if they are made well. and i didn't have any issues with them.

the driver PPA's or similar ones are a different matter. they do affect the system. and can cause instabilities. particulary if you add some testing /experimental version.

---

### Post by izznogooood on 2017-04-13
My experience is rather good if you keep an eye on what it updates after you add it. Some PPA'a I cannot live without, especially when running LTS on a desktop.

I just checked and I have 19 active PPA's on my desktop. (16.04)

---

### Post by Frogs Hair on 2017-04-13
Currently use well known PPA's for installing themes and Icons not for applications. This was not always the case and most I did use are no longer supported on the Ubuntu release in use. Installing the latest release prohibits longterm use of a PPA in many cases unless the maintainer/s is like minded.

---

### Post by yetimon_64 on 2017-04-13
> **izznogooood said:**
> My experience is rather good if you keep an eye on what it updates after you add it...

Pretty much the same here. I made the mistake once of letting a PPA update the whole system as it wanted it (xorg-edgers ppa) and ended up having to do a re-install (probably could have been fixed but it was on a reasonably fresh install so I did a full new install to clean out any mess left). I soon learnt to use the PPA for what I needed at the time and then lock it out and occasionally manually check for any updates to the graphics driver I needed from it (on an intel/nvidia hybrid graphics laptop). 

I am happy this machine now can use the standard recommended drivers without the need for that PPA any more. Previously, with what was at the time very new hardware, the additional drivers utility did not even recognise the graphics hardware; nowadays there is no such problem.

I have used many PPAs over the years to get my desktop set up as I like it without any problems apart from the one just mentioned above.

---

### Post by kostkon on 2017-04-13
My experience has always been good due to the fact that I've always used official PPAs, but after (just recently) upgrading to 16.04 I've found myself using snaps more and more in place of PPAs. 
```
~$snap list
Name                        Version      Rev   Developer  Notes
blender-tpaw                2.78c-tpaw0  3     tpaw       -
canonical-livepatch         7            22    canonical  -
core                        16-2         1577  canonical  -
handbrake-jz                1.0.7-0      11    jz         -
hexchat                     2.12.4       17    tingping   -
scummvm                     1.9.0git     4     caldav     -
simplescreenrecorder-mardy  0.3.8-3      4     mardy      -
```

---

### Post by mooreted on 2017-04-13
Like others here I don't add a PPA unless it is well vetted first. I think the only one I have added at the moment is Handbrake (stebbins). My philosophy is to stick with official repositories as much as possible. In the past I have added other PPA's after vetting and have never had a problem.

---

### Post by wildmanne39 on 2017-04-15
> **1fallen said:**
> For myself ....Nope!
But the forums can be riddled at times with errors from PPA's
I research before adding them though...Look for current activity, Bugs reported, that sort of stuff.
_Lastly make sure it supports the Version of Ubuntu I'm using_..
EDIT: I also install PPA Purge....that way i can just revert back to stock, if problems arise from the said PPA.
+1 to all of these, I all most never use a ppa.

---

### Post by sp40140 on 2017-04-18
Generally no issues because of the simple fact that I do my research before installing them, which is just common sense and applies to any software you deal with.
I do remember Opera (browser) ppa giving trouble few years ago. Had to disable it for a while until Opera team fixed the issue.

---

### Post by Irihapeti on 2017-04-19
I use PPAs for things that aren't available in the standard repos. Or maybe they are in the standard repos, but I want a later version e.g. virtualbox. All of them are the developer's own repos.

I also install ppa-purge. If I decide that the software isn't doing what I want, I uninstall it and run ppa-purge to clean up afterwards.

Apart from a time several years ago when I was troubleshooting a bug using xorg-edgers, I've had no problems.

---

### Post by ChuangTzu on 2017-04-20
I don't use them, stick with whats in the official repos or compile from trusted sources only.

---

### Post by monkeybrain20122 on 2017-04-21
IMO it is one of the best features of Ubuntu (another one being unity, which unfortunately has just bitten the dust), it lets you selectively update your software without risking a system upgrade and it is usually reversible with ppa-purge should something go wrong. This is especially attractive for those who use LTS, open source moves quick especially for multimedia stuffs. To keep up to date I compile some software myself, but also use many ppas, but I always stick with the reputable ones like mc4man's and ppas from upstream developers. Also I only add ppas which do "target upgrades" in the sense that they don't upgrade a lot packages, only those required by the software. There are ppas on launchpad that have a lot of stuffs and want to upgrade a ton of libs, usually those are to avoid. Also avoid ppas for graphic drivers and the likes unless it is absolutely necessary (say official driver is buggy, or your hardware needs bleeding edge to work smoothly etc)

I have not had any problem with ppas. The only time am upgrade disaster hit me so hard that I had to re-install was from an official xorg-driver upgrade. After reinstallation I had it downgraded and pinned.

---

### Post by LastDino on 2017-04-22
Have used PPAS and never had an issue tbh.

Probably because I keep close eye on what is added and what is not, what needs to be updated or removed before something else is updated to avoid clash. 

PPA- PURGE IS pretty handy imo

---

