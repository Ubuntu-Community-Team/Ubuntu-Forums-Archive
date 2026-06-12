---
title: "Quitting Compositing"
date: 2007-04-27
forum: The Cafe
---

### Post by TheMono on 2007-04-27
Normally, I am quite a positive person. I don't complain over bugs and the like, because I understand that in general, free software developers are trying hard to produce a decent product, and nobody leaves bugs in on purpose, only ever for lack of time or funds or the like.

However, there is one giant exception in the free software community at the moment.

Compositing window managers are the free software community's real chance to excel in a way that is most visible to the average end user. The two largest projects with respect to this (beryl and compiz) a while ago announced a merge.

What, you might ask, is the biggest thing holding this up? The answer is the egos of developers. Don't get me wrong, this isn't blanket leveled at every compositor developer. Nor is it to single anyone out. However, after reading the forums for both the beryl project and the compiz project, the one recurring though from compiz developers seems to be 'you forked from us in the first place, we are not changing just to accommodate you in a merge'. And Beryl developers seem to be flogging 'we became more popular and got all the press, we looked cooler, we don't want to just be swallowed up by compiz, the name must change'.

It disappoints me to see this happening. My personal stance on it is more one of not caring what they call it. To be honest, if it represented the combined efforts of Beryl and Compiz, I would download and install steaming_pile_of_crap-1.01-ubuntu5.deb. It doesn't matter what it is called.

What is everyone else's stance on what is going on? And those who don't use compositing window managers because they think they are a stupid idea - please don't post that, your point is valid for you, and this isn't the place.

---

### Post by maniacmusician on 2007-04-27
I agree with you. Egos like that are ridiculous. But unlike you, I'm actually completely against the merge. Beryl and Compiz are different projects with different goals. Compiz is more solid, uses resources better, has neater code, and is gnome-centric. Beryl is DE-independent, focuses on churning out tons of features first, and worries about stability later. Two different aims, two different target audiences. 

But I wish that the Beryl and Compiz projects would share resources. Their developers should occasionally get together, look at each other's code, and talk about how each project could get a little better. They should have teams for porting plugins back and forth, and stuff like that. The best way to do that, I think, would be to unite them under a common name. Linux Compositing Project? I dunno. But if they were under the umbrella of an organization, it would make it easier for them to share code and ideas. However, I feel like they should be separate branches of the same tree. 

I'm not getting my idea across very well right now, not reallly thinking straight for some reason. But I hope you get the basic idea.

Since I've given my impartial opinion, I'll provide my biased and very personal opinion as well; Beryl is, in most regards, the superior compositing manager. It has better config tools, it's DE independent, and it has a lot more features in it. But, it is not as stable as Compiz, and a lot of users think it's too bloated. So for me, the ideal solution would be for the Beryl devs to concentrate more on beryl-core and stabilize it. [/personal opinion]

---

### Post by TheMono on 2007-04-27
I agree that Beryl is superior for me. But I like the fact that compiz is, in theory, stabler. So I am in favour of the merge and hoping that we will end up with only the core developed by the compiz people, and the plugins, the settings managers, the sort of stuff that made it DE independent, etc, still done by the Beryl people - under whatever name they like.

---

### Post by maniacmusician on 2007-04-27
> **TheMono said:**
> I agree that Beryl is superior for me. But I like the fact that compiz is, in theory, stabler. So I am in favour of the merge and hoping that we will end up with only the core developed by the compiz people, and the plugins, the settings managers, the sort of stuff that made it DE independent, etc, still done by the Beryl people - under whatever name they like.
It's not that simple...the part that makes it DE-independent is in beryl-core. So the compiz people would have to work all of that into their core, and stop  using gconf. That's a tall order. It'd be easier to stick with beryl-core, and start making it more stable by importing some aspects of compiz-core.

---

### Post by TheMono on 2007-04-27
Compiz already supports a flat file backend for configuration as far as I can tell. And I wasn't aware that anything in the core depended on GNOME... By that, I don't mean you are wrong, I literally mean I am not aware.

---

### Post by tehkain on 2007-04-27
Yes compiz's direction was different then that of beryl's but compiz is not what beryl is merging with. People are so confused about this merge. Compiz is not really going to be effected by beryl(very little). It is compiz-community that it is going to join with beryl. They were already  using so many of the modifications that beryl was using, so the project were very close. You will still have the solid core compiz but now you have a merged compiz-community with alot more development potential. Plus compiz community was going in the same direction as beryl.

---

### Post by Tundro Walker on 2007-04-28
I think what you're seeing -- the ego's, the bickering, the forking, etc -- is actually good and productive, because it promotes evolution.  Lots of good things started because folks couldn't get along.  People had a difference of opinion, so they parted ways and pursued their own goals...Great!  What's even better is that now they seem to be coming back together to share ideas, and merge, because they've each done their thing, and think that coming back together would be good.  Instead of sharing common resources, which ManiacMusician said, it's more common for folks to do like they did...start together, split over differences, work alone, then come back together when curiosity gets the best of them, work together for a while more, wash rinse repeat.

While it may seem petty, it's actually one of the things that makes Open Source stronger.  It may take longer to develop things over time, due to squabling or what-not, you get a wider range of evolutionary ideas coming into the fold as people get tired or curious and want to try something a different way.

Look at it this way.  In the past, when innovative ideas came along, Microsoft usually just bought up the company that dreamt it up, and either scrapped the idea, or forced it into their own strict, evolutionary path.  I'd much rather have some egotistical programmers squabble over their work (which means they're passionate about their work), then to see them both get squelched by a buy-out or a "cease and desist" court order.

Also, sometimes squabbling can lead to a halt in productivity, because folks get so tied up in fighting they forget about working on their project.  But, it can also lead to great leaps in productivity, as one person, fed up with others saying something is "impossible" or "is stupid", diligently codes away just to prove folks wrong.  It used to be hard for a single programmer to make really awesome stuff, but with the advanced lib's and IDE's out today, one programmer with lots of determination (and caffeine!) can make some wondrous things.

---

### Post by igknighted on 2007-04-28
"Compositing window manager" is kind of a blanket term encompassing more than beryl and compiz.  Xfce is a "compositing window manager" as well, check out its transparencies and fading/shadows.  KDE (kwin) also has some of this.  So while Beryl/Compiz are the big names here with the most 3d features, they are just (and in the end will remain) test platforms.  Wobbly windows (a KDE4 feature I am told, in a toned down way), true transparency, shadows and other effects are making their way into the common WM's.

---

### Post by TheMono on 2007-04-28
igknighted, yes, you are right, my apologies for generalising.

Tundro Walker, I agree with you in general, but it is the fact that they are no longer bickering over an approach, or a way to solve a problem, but rather they are bickering over a name. I had no objections at all to the fork, for the reasons you give. It is the wasted time and effort arguing over names that I object to.

---

### Post by sorcererx84 on 2007-04-28
> **maniacmusician said:**
> It's not that simple...the part that makes it DE-independent is in beryl-core. So the compiz people would have to work all of that into their core, and stop  using gconf. That's a tall order. It'd be easier to stick with beryl-core, and start making it more stable by importing some aspects of compiz-core.

There are NO changes in beryl-core that make it more DE-neutral. The core only has patches for some plugins to work (transparent cube, 3d etc), libberylsettings (which is being rewrittent for Compiz) and new features from Compiz's core were already included. If the projects wouldn't have decided to merge, Beryl would still have used Compiz as beryl-core, it was already decided and at that point the developers saw that the goals were almost identical and started to talk about the merge. Compiz now has ini plugin for storing settings and AFAIK has absolutely NO Gnome dependancies.
Please, do not spread bs among the community, there have been more than enough misunderstandings regarding this topic.

---

### Post by TheMono on 2007-04-28
Yes, what sorcerer has said was basically what I believed to be the case, but I can't say I'm any authority on the subject.

EDIT: except for one part - compiz does require gnome to compile, but not to run. Strange but true.

---

### Post by sorcererx84 on 2007-04-28
AFAIK Gnome is only needed when you compile gtk-window-decorator. Dependancies for core (in Feisty) should be:
```
build-essential libxcomposite-dev libpng-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgl1-mesa-dev libglu1-mesa-dev
```
More info on compiling is [here]("http://forum.compiz.org/viewtopic.php?t=827")

---

