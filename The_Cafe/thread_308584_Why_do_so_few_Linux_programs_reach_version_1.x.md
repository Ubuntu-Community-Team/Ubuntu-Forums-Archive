---
title: "Why do so few Linux programs reach version 1.x?"
date: 2006-11-28
forum: The Cafe
---

### Post by urukrama on 2006-11-28
Why are there so many Linux programs that do not even reach version 1.x?

Most of the applications that I have installed are some version 0.3 or 0.2.1 etc, with a few that have an older version (2.x etc). Hardly any go as far up as Opera, for example, which is now at version 9. Why is that? 

Is it because there are (percentage wise) more programmers that use Linux than in Windows or MacOS? Or due to devlopers not cooperating and rather starting their own program than building on an existing one? Or because Linux (either the software or the community) evolved so much in the last few years that programs 'had to be' started froms scratch? Or is it because Linux programmers just use a different counting?

(This is not a criticsm. I like most of the apps I have installed. I was just wondering.)

---

### Post by mostwanted on 2006-11-28
You can't compare version numbers between applications, I don't see how you could think that. A version number is just something to let you know some version of program is more recent than another.

But! There is one key difference between proprietary software and open source software and that is the fact that proprietary software is usually released in major versions (1, 1.5, 2, etc.) while open source is usually developed doing small incremental updates in an open process.

There are several ways of using version numbers. Linux and Gnome use even decimals to mean stable version and uneven to mean unstable development versions. Other projects, like KDE, don't differentiate like this. In the case of libraries, 1.0 usually means coding interface freeze and 2.0 a coding interface overhaul. Ubuntu's version number has this format: "years since 2000".month, like 6.06 for 2006, june.

---

### Post by Brunellus on 2006-11-28
Versioning is a complicated question.  Proprietary software, as mostwanted notes, releases in major steps, and their development process is closed to the public.  So they tend not to release until 1.0 anyway. 

There were always "betas" (0.x) releases, as well.  The long intervals between "major" re-releases of proprietary software has stoked a particularly pernicious form of "beta fever" among Windows users...they scramble for untested software thinking they need the 'latest-and-greatest'---and then complain if that software isn't perfectly stable.  

When I was a little kid learning about software, I learned that a full-version-number increment usually meant a MAJOR revision or even a re-write of that program.  Point releases were minor tweaks.

Some Free software projects use a "major, minor, build" convention.  The Linux kernel, for instance, is in its second major revision (v.2).  the kernel also maintains an "even for stable, odd for development" convention.  current "stable" kernel is 2.6.18

The dots, by the way, are not decimal separators;  thus it is possible for gnome 2.2 to be a far earlier release than gnome 2.14--the former is the second minor revision, the latter the fourteenth.

It's all arbitrary anyway.  The conventional wisdom used to be never to jump on the 1.0 version of commercial, proprietary software, as there were going to be bugfixes in 1.1 and 1.2 anyway.  The same advice holds true for 0.9rc3 versus 1.0 in some other versioning systems.  

*shrug*

---

### Post by steevk on 2006-11-28
It also has to do with version names meaning different things to different people. Take Mac OSX for instance. 10.4 is a major revision from 10.3. 

Most programs don't reach 1.0 because they recognize that there are still tons of problems, and they just aren't at a point where they're willing to label thier software '1.0'. Generally 1.0 is percieved as an 'okay, it'll Just Work for most people, main featureset is done' and some developers just aren't ready to call it that yet...

That's how I see it, anyway. It's not really a big deal...

---

### Post by doobit on 2006-11-28
Some of them would reach 1.0 faster if people who find them useful would help support the developers.

---

### Post by bastiegast on 2006-11-28
> **Brunellus said:**
> Versioning is a complicated question.  Proprietary software, as mostwanted notes, releases in major steps, and their development process is closed to the public.  So they tend not to release until 1.0 anyway. 

There were always "betas" (0.x) releases, as well.  The long intervals between "major" re-releases of proprietary software has stoked a particularly pernicious form of "beta fever" among Windows users...they scramble for untested software thinking they need the 'latest-and-greatest'---and then complain if that software isn't perfectly stable.  

When I was a little kid learning about software, I learned that a full-version-number increment usually meant a MAJOR revision or even a re-write of that program.  Point releases were minor tweaks.

Some Free software projects use a "major, minor, build" convention.  The Linux kernel, for instance, is in its second major revision (v.2).  the kernel also maintains an "even for stable, odd for development" convention.  current "stable" kernel is 2.6.18

The dots, by the way, are not decimal separators;  thus it is possible for gnome 2.2 to be a far earlier release than gnome 2.14--the former is the second minor revision, the latter the fourteenth.

It's all arbitrary anyway.  The conventional wisdom used to be never to jump on the 1.0 version of commercial, proprietary software, as there were going to be bugfixes in 1.1 and 1.2 anyway.  The same advice holds true for 0.9rc3 versus 1.0 in some other versioning systems.  

*shrug*

Even though I kinda knew this already, still an interesting read Brunellus :-D

---

### Post by urukrama on 2006-11-28
> **mostwanted said:**
> You can't compare version numbers between applications, I don't see how you could think that. A version number is just something to let you know some version of program is more recent than another.

True, and I am aware of that. But the longer an application is around (and in active development), the more improvements will have been made to it, and hence the more it moves up on the "version number ladder" (whatever the conventions).

I always considered version numbers like Brunellus explained them: major releases go up one number, minor ones go up a dot number (.x). So one would expect that Linux applications would (a) go up, (b) do not go up because they are not longer actively developped (for whatever reason), (c) are so good from the start that they need fewer major revisions.

Again, it is not something that bothers me, just something that makes me wonder. I generally don't update an application unless something is fixed or added to that I really need/want.

---

### Post by zachtib on 2006-11-28
I think it has to do with the mentality of open source developers vs. that of closed source devs.

In the open source world, there isn't usually a deadline to meet, and as the devs are often doing it willingly and for free, they can take their time.  In the closed source world, when releases are done for money, they may have a deadline of 1.0 this year and 2.0 the next.

Also, OS devs tend to regard the 1.0 release as being 'done' that is, 1.0 only comes out once everything is perfect and as many bugs as humanly possible have been found and rooted out.  For example, when banshee was nearing the end of the 0.9.x cycle, the next cycle was 0.10.x to indicate that it still wasn't 'done' yet.

That said, you should never be concerned with using an open-source program with version number < 1.0, as they tend to be just as stable as closed-source equivalents with higher numbers.

This is just my opinion/take on the situation.  Obviously this doesn't hold true for everything.

---

### Post by prizrak on 2006-11-28
Numbers are completely made up. The first ever version of Windows NT was 4.5 didn't mean there were at least 4 version before it. Since then we had NT 5.0 (2000) and 5.1 (XP) Vista will be 6.0. The Linux kernel has been around for at least as long as NT (I think longer actually) and we are only on version 2 (well 2.6 really) with alot more incremental releases in between.

---

### Post by Henry Rayker on 2006-11-28
I think it has to do more with marketing. A higher number just sounds more stable. I think it goes both ways, from my experience.

When you're selling your product, you want as many people as possible to jump on and start paying you for it. The version number is almost like bragging rights, of a sort. When you're working on something as a work in progress, you're not getting anything in return except people whining and moaning about how feature x doesn't work like it does in some other app, or how you would REALLY love to donate money, but the app just isn't far enough alone etc. You want to make sure that people are VERY WELL aware that your application is far from finished.

---

### Post by B0rsuk on 2006-11-28
...because Linux developers are often more honest/modest, and use version numbers to indicate current state of the program.

format: 1.2.3

1 is for major changes
2 is for significant changes
3 is for little changes and bugfixes

There are no upper limits for these 'digits', so, for example, you can see linux kernel version 2.6.17 etc. Imagine how big this number would have to be if they were forbidden to use dots. (or even just 1 dot). 


In contrast, closed source/commercial developers are often tempted to artificially increase version number to make their program appear more mature, and get more profit from sales (ads, or whatever). Look at Winamp:

There was never, ever winamp4. To my disgust, they oficially said that new version of their program was too great to call it 'winamp4'. Instead, they jumped from winamp3 to winamp5. Talk about narcism...

---

### Post by Brunellus on 2006-11-28
> **B0rsuk said:**
> ...because Linux developers are often more honest/modest, and use version numbers to indicate current state of the program.

format: 1.2.3

1 is for major changes
2 is for significant changes
3 is for little changes and bugfixes

There are no upper limits for these 'digits', so, for example, you can see linux kernel version 2.6.17 etc. Imagine how big this number would have to be if they were forbidden to use dots. (or even just 1 dot). 


In contrast, closed source/commercial developers are often tempted to artificially increase version number to make their program appear more mature, and get more profit from sales (ads, or whatever). Look at Winamp:

There was never, ever winamp4. To my disgust, they oficially said that new version of their program was too great to call it 'winamp4'. Instead, they jumped from winamp3 to winamp5. Talk about narcism...
Free software maintainers aren't immune.  There was a major "version inflation" in slackware--it jumped from 7 to 10, I think, without any intervening steps.

With Winamp, they did a very "linux" think when they went from the 2.x tree to the 3.x tree--those two versions were very different from each other.

---

### Post by Henry Rayker on 2006-11-28
I didn't like the Winamp jump from 3 to 5 either, but it made sense...Winamp 5 was really like Winamp 2 + Winamp 3...

---

### Post by thomashauk on 2006-11-28
I also remeber slackware skipping a few numbers so it isn't just popritery software that does this.

Basically my advice is to look for a high point or point-point release because that generally means more bug fixes have been made. A major version number change means more features and hence more bugs.

A new major number also usually means a complete rewrite... Basically a whole new program...

---

### Post by ZuLuuuuuu on 2006-11-28
As not a real programmer but a forum script programmer, I will tell you why my forum script have not reached version 1.0 for about 2 years :)

The number 1.0 is very special looking. It sounds like the first real release and I want the forum script to be perfect on exactly that version. I know it can't be but at least as close to the perfect as possible. I have specified the features that I want in my forum script at the end and I haven't implemented all of them yet. I am not thinking of naming the version 1.0 until I have the script as I want it to be, with the features I specified. Also I want it to be perfectly stable on exactly that version :)

This is the excuse of mine for not releasing the version 1.0 yet :)

---

### Post by BWF89 on 2006-11-28
Linux software tends to not reach version 1.0 because open source developers are a lot more paranoid about their software being labled as stable when it hits 1.0 than proprietary developers.

I use tons of programs that haven't reached 1.0 but their just as stable as their proprietary counterparts that are labled AWESOME SOFTWARE 5.0!!!oneone111

---

### Post by engla on 2006-11-28
Well, not many people buy Software version 5.1 if you already have version 5.0. The large version are the buy-versions, the small ones are upgrades and fixes.. Now that's very general and I know thousands of exceptions, but you catch the drift; there is a bump everytime you re-roll the product and try to sell it again.

Free Software is often not marketed and sold in the same way, and the more technical user-base doesn't listen to major versions as they do specific functions and fixes. FOSS "sells itself" based on absolute merit.

---

