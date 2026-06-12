---
title: "Ubuntu 8.04"
date: 2008-09-10
forum: Testimonials &amp; Experiences
---

### Post by carusoswi on 2008-09-10
I've just about had it with this release.  My system has frozen three times in the last 60 minutes, and I cannot run Crossover or Wine applications (some but keeps applications from running in the new 8.04 version of Ubuntu).

I want to support Ubuntu, I would like to leave XP, but, what is one to do when the OS freezes repeatedly?

It's bad enough that we have no printer drivers (not the fault of Ubuntu developers, I know), but, if stuff that worked in previous versions no longer works because of a version upgrade, then, what should I make of the new version.

8.04 is no beta release. It should represent improvement to my computing experience.  Instead, key portions of my setup are rendered inoperable.  Most of my Wine/Crossover applications will simply not run... and this crashing business, my machine crashed twice within an hour during an important interview.

I know there are others who share similar frustrations.

Is something being worked on to fix this issue? I've seen others posting problems, no one posting fixes.

What is the deal?

Caruso

---

### Post by SunnyRabbiera on 2008-09-10
can you give us your specs?

---

### Post by Crafty Kisses on 2008-09-10
First what are your system specs? I run Ubuntu 8.04 Hardy on a laptop just fine.

---

### Post by kansasnoob on 2008-09-10
Well, I still dual boot rather than using Wine. I don't like it!

So I can't help you there, but I'd like to know what other things just don't work for you:confused:

If you're specific about what doesn't work maybe we can help.

---

### Post by Bradtek on 2008-09-10
Do you want help to fix the problem or are you just here to complain ?

If you want help then don't be vague.
Post your specs
Post detailed descriptions of the problem/s

Wine may work well for some but if you really are a slave to micro$oft
software then either dual boot or run XP in Virtual Box / VM Ware and 
save yourself some frustration.

For me 8.04 Hardy has been a generally pleasant experience
and an improvement over 7.10.

---

### Post by bodhi.zazen on 2008-09-10
Moved to testimonials and experiences. There are tons of fixes to problems posted here on an hourly basis. If you mean patches or fixes to the code, that is done in launchpad.

[https://launchpad.net/](https://launchpad.net/)

And yes there are bug reports and fixes on Launchpad all the time. Turn around is faster on LP then it was when I used to use Microsoft products, some bugs in Microsoft go un addressed for years, and years turn into decades ...

---

### Post by wolfen69 on 2008-09-10
it is impossible for ubuntu to work perfect on all computers in the world. i've installed it on many without issue. don't judge it on your limited experience with it. if it doesn't work, find something that does. good luck.

---

### Post by Crafty Kisses on 2008-09-10
> **wolfen69 said:**
> it is impossible for ubuntu to work perfect on all computers in the world. i've installed it on many without issue. don't judge it on your limited experience with it. if it doesn't work, find something that does. good luck.

That's exactly the whole point, some people have issues, some people don't if you have issues there's Documentation and Forums to help you.

---

### Post by tulen on 2008-09-11
maybe u have problem with u'r CD or computer.
so far so good.

---

### Post by zombrax on 2008-09-11
So the forum helpers supposed to read your mind? ask and it shall be given... 
all the best dude.

---

### Post by carusoswi on 2008-09-12
> **zombrax said:**
> So the forum helpers supposed to read your mind? ask and it shall be given... 
all the best dude.

Not asking you to read my mind.  I actually lost track of this thread - stumbled across it just now.

Running Ubuntu 7.10 and Crossover 6 and wine (whatever was in the repos), I could run all MS Office applications, share files between Ubuntu and XP, install a number of non-support, more dos-based or platform independent applications (Irfanview, for example) with no issues.  Everything worked fine.

As soon as I installed 8.10, Crossover and Wine stopped working properly.  As of now, only Photoshop 7 runs properly.  Word runs but cannot save anything to NTFS drives where I can get at it from XP (or another computer).  Access will not function properly.  It starts up, but I cannot open existing databases, cannot create new ones.

Excel runs, can't save (as in word).

None of my unsupported applications will install, in either crossover or Wine.

To correct the crossover problem, I paid for an upgrade to version 7 - have an open ticket on their website.

So far, no joy.

I'm not here just to complain.  Have worked through all previous issues with Ubuntu/linux since early versions 6x.

But, 8.04 has broken part of my system, forcing me to go back to XP in order to complete work that depends upon Access (Word and excel I can probably live without as OO will suffice . . . Access has features that are not replicated in oo).

My system is nothing out of the ordinary, an Shuttle XPC with an Intel processor, 3 gHz, 2gb ram, plenty of HD storage.

I've made several other posts here, have read that others have also experienced problems, just wonderin' out loud if they will be addressed.

Thanks for the replies.

Sorry to have been slow to respond.

Caruso

---

### Post by jaqie on 2008-09-12
Hm...
You upgrade a system which you need for everyday tasks when 7.x works for you, despite the warnings that upgrading to a new version may break a lot of things, and then complain about them being broken after the upgrade?
This makes no sense to me at all...

Perhaps you may want to reinstall 7.x to get things working, or try a clean install of 8.x? Just an idea.

Not defending ubuntu, but trying to figure out why you seem so angry that what the warnings you saw on upgrade said did happen to you...

---

### Post by bodhi.zazen on 2008-09-12
To be honest, it sounds as if you are running primarily windows applications. 

As you know windows applications are designed to run on , well windows.

I doubt the Ubuntu developers are working on your issues as they are all 3rd part applications, you would need to look at wine or crossover office.

In my experience with wine, it takes some time and experience to maintain. Sure simple applications such a utorrent will run without much problem, but you are expecting full functionality on a large number of diverse applications.

Once you get everything working, why upgrade ? By that I mean you have configured a complex system and gotten it working, *[b]congratulations*/b], be happy with what you have. Complex configurations of wine often suffer breakage with updates to the wine package, something termed "regression" in the wine community.

To be perfectly honest, IMO, if you wish to run windows applications you should either dual boot or, if you have the hardware, virtualization (VMWare, Virtual Box, or KVM).

Your other option is to migrate to linux applications such as open office, gimp, image magic, etc. These applications are likely to work just as well for you and are much much easier to maintain. They are open source and freely available, so no need to pay for windows license or license of CrossOver office, or buy applications.

Running window native applications on Linux makes as much sense as trying to port Linux binaries to windows, it is generally unsupported and difficult.

---

### Post by beniwtv on 2008-09-12
I think a possible explanation of your wine problem could be changes made to Ubuntu 8.04. I've read somewhere that Hardy is blocking for security a specific area of your memory, which is used by older (maybe not so old?) WIndows applications...

Maybe it's worth a try looking in this direction...

Cheers,

---

### Post by Sef on 2008-09-12
> As soon as I installed 8.10, Crossover and Wine stopped working properly.

Not surprised.  Intrepid Ibex, 8.10, is alpha phase now.  It is not recommended for use where you need a stable desktop.

---

### Post by zombrax on 2008-09-13
Why in the world would you install 8.10????????? its not even released as a stable ver!!!!!!!!!!!

Honestly, man I dont know how some ppl think... if it was me, i wouldnt install it in the first place, secondly since i know that its in alpha phase, i EXPECT it NOT to work properly with all my settings and apps.... geezzzz....

Sorry I still cant comprehend this stuff.... :(

---

### Post by carusoswi on 2008-09-13
> **zombrax said:**
> Why in the world would you install 8.10????????? its not even released as a stable ver!!!!!!!!!!!

Honestly, man I dont know how some ppl think... if it was me, i wouldnt install it in the first place, secondly since i know that its in alpha phase, i EXPECT it NOT to work properly with all my settings and apps.... geezzzz....

Sorry I still cant comprehend this stuff.... :(

Ah, so sorry to offend such a stodgy community.  I should leave all trail blazing to you guys/gals who obviously have spare machines sitting around on which they can install this six or so month old LTS release.  I should then sit back and wait until you declare it ready for an old fart like me to try on my own machine.

As for getting my windows work completed, it still gets done, I just have to hit the down arrow during my dual boot so that XP, not Ubuntu comes up.

When I'm not working on money-making stuff, I joyfully spend my time in Ubuntu, doing my little bit to discover for myself how I might one day be free of some of the little aggravating nooks, crannies, and underlying philosophy of MS which I find disagreeable to my personal outlook.

While I definitely didn't come here just to complain, I also didn't come here just so that some of you smug types could confirm that I should go back to XP (or 7.10 or 7.04 or 6.10, etc.) from whence I came.

Honestly, some of us "ppl" are just as willing (and as competent) to try cutting edge releases as you.

To those of you who tried to offer helpful replies, I apologize for this rant.  Helpful replies (not condescending ones) are what I have found to be the norm in this community.

As for the subject version of Ubuntu, like releases before it, I am neither dismayed nor surprised that, along with great progress, come some problems.  But, I, and others as well, have been asking about this wine/crossover problem for some time now, and I am coming to the conclusion that either most in the community do not use wine/crossover or they must not be experiencing this problem in their 8.04 setups.

If the fact is as simple as 8.04 being incompatible with wine/crossover, fine, I'll drop back to 7.10 and wait for 8.10.  If the problem is somehow specific only to a minority of us who are experiencing it, then, I'd like to probe, via this forum and any other reliable source of information, for its cause and correction.

It would suit me fine to swear off of applications like MS Access or Steinberg's Wavelab or Sony Vegas or Adobe InDesign, but their counterparts either do not yet exist in Linux or they are not up to speed in terms of features/functionality . . . and, before someone rants that this or that linux ap is sort of like this or that Windows ap and does "everything he or she needs to do", I assure you that I am glad to be feature-specific concerning my need for the cited Windows aps, but that would be the topic for another thread.

I have not 'about had it with Linux or Ubuntu', but, unless I see more community activity on 8.04 and this wine/crossover problem, I may, indeed, need to give up on 8.04.

I do appreciate the unique nature of Ubuntu's development as I have waited patiently through successive releases for wants, desires, needs to be implemented.  There was a day when all my wireless surfing had to be performed via XP as no amount of calisthenics could get my Belkin N1 adapter to work with the Ubuntu version of the day.  Fortunately, those days are far behind me.

. . . printing photos or assembling video and/or sound on a professional level seem to yet be years away.

I have faith that all these will come (hopefully in my lifetime (not kidding, unfortunately)), but they are not here, yet.

While it is not my intention to rant, I do take exception to the superior tone in some of the replies that have been posted to this thread.

Having upgraded through the versions like the rest of you, I would not expect functionality as basic as wine/crossover to be broken to the point of not being quickly fixable in a new version at this point in Ubuntu's development.  I paid for Crossover 6, it worked until 8.04.  I ran Wine along side it, it worked until 8.04.  I checked this forum and the Codeweavers forum, was advised that Crossover 7 would fix the problem.  I paid for it, but it had no effect on my problem.  I continue to accept updates (some of which are wine specific), but, so far, nothing has fixed my problem.

So, one more time, is it really just a few of us, or is this area of Ubuntu simply broken in 8.04.  

I'd like to hear from someone who actually uses (or has tried to use) MS Access, for example, in Wine on 8.04, not from someone who wants to belittle me for upgrading, or for needing a Windows Ap, or for being so stupid as to put Ubuntu 8.04 on [one of my] key work machines.

Thanks.

Caruso

---

### Post by armandh on 2008-09-13
even updating from 7.10 to 8.04 I found VLC that had worked no longer worked. so I reloaded 8.04 and VLC and everything worked.

pushing the envelope with wine and 8.10 pre release [release = wider testing] one should expect big un-fixable trouble.

I do not trust the upgrade process to work unless the install being upgraded is just an out of the box one. none of mine qualify.

mission critical boxes are no place for first day issue, much less alpha & beta.
early adopters will always have trouble.

8.10 a month B4 release.....? your expectations are unreasonable.

---

### Post by carusoswi on 2008-09-13
> **armandh said:**
> even updating from 7.10 to 8.04 I found VLC that had worked no longer worked. so I reloaded 8.04 and VLC and everything worked.

pushing the envelope with wine and 8.10 pre release [release = wider testing] one should expect big un-fixable trouble.

I do not trust the upgrade process to work unless the install being upgraded is just an out of the box one. none of mine qualify.

mission critical boxes are no place for first day issue, much less alpha & beta.
early adopters will always have trouble.

8.10 a month B4 release.....? your expectations are unreasonable.

Where do I say anything about 8.10 a month B4 release?  Is it unreasonable to expect 8.04 to work with Wine/Crossover?

Did you misread my post?

Caruso

---

### Post by bodhi.zazen on 2008-09-13
No one is belittling your problem, but i do think your posting style is not conducive to a solution to your problem.

You are spending a lot of time and energy ranting about how Ubuntu is "broken", but your are :


[LIST=1]
[*]Using a third party application (Crossover Office).
[*]To run windows applications
[*]On a version on Ubuntu that is in alpha release
[/LIST]


Starting with Ubuntu, while you are free to use an alpha release, and debug it, you need to understand the responsibility YOU have when running an alpha release.

Have you filed a single bug report with Launchapd ? If so link please. if not, why not ?

Second, alpha releases are in development and change rapidly. The expectation that they will "just work" is unreasonable and ranting that Ubuntu is broken on the Ubuntu forums somehow seems like a fundamental misunderstanding on your part and frankly inappropriate. If you run alpha software , expect bugs and file bug reports. Ubuntu is not broken simply because you are having problems with an alpha release.

In response to your problem with crossover office, why may I ask are you ranting on the Ubuntu forums that a commercial product you bought is broken ? This application is not developed by the Ubuntu Developers and this is not a support forum for crossover office.  

Wine is also a third party application. If you wish assistance with wine please refer to WineHQ. WineHQ is simply the best source of information on wine.

Last, you are ranting about windows products. Why may I ask are your ranting about these issues on the Ubuntu forums? Did you file a bug report with Microsoft ?

I am sure you will be told by Microsoft that they do not support Linux. This simple fact is somehow acceptable to you. Ubuntu is not broken because your windows applications do not run , Windows applications are broken because they do not run in Linux.

Please direct your rants at Microsoft, not Ubuntu.

If you want to run Linux, try Linux applications. You may find they work well and are better supported.

I am going to close this thread now as it is going no where. If you wish you are free to file a bug report and ask for assistance in a more appropriate mannor in a support thread.

---

