---
title: "Should Ubuntu devs concentrate more on fixing bugs?"
date: 2009-07-08
forum: The Cafe
---

### Post by change_mode on 2009-07-08
Lately I've seen more and more minor bugs in Ubuntu... not a problem, but then there are a lot of bugs that have been around for years already and have been on launchpad all the time.

Let's take a look at launchpad:

# 27499 New bugs
# 8883 Incomplete bugs
# 12060 Confirmed bugs
# 8790 Triaged bugs
# 827 In Progress bugs
> 812 Fix Committed bugs

Taking into account that probably not all new reported bugs are valid, that still leaves us with a good 40,000 bugs.

I am aware that there are custom fixes and workarounds for most of the bugs, but at some point these fixes should hit the repositories to provide a better user experience out-of-the-box.

My concern is, if the old bugs already take so long to fix and more new bugs are introduced, it will take even longer to fix those new bugs and it will consequently become harder to keep up.

I'm glad to see new features like the notification icon, but we got a pretty stable and complete system right now, so maybe it's time to get rid of these damn bugs or at least give it a higher priority. What do you think?

---

### Post by binbash on 2009-07-08
"I'm glad to see new features like the notification icon, but we got a pretty stable and complete system right now, so maybe it's time to get rid of these damn bugs or at least give it a higher priority. What do you think?"

Stable? Ubuntu is far from being stable, because of the bugs.Especially after crap intel performance, the trends of ubuntu is falling.


The devs should double focus on fixing bugs on Ubuntu

---

### Post by v8YKxgHe on 2009-07-08
And how many of these are actually bugs with Ubuntu its self? That number will shoot right down.

The reported bugs are going to include bugs that are issues with software upstream, and nothing Ubuntu developers can do about unless they want to start working on that software to fix them.

There is more to Ubuntu than just Ubuntu.

---

### Post by 3rdalbum on 2009-07-08
There are some bugs that it's simply not practical to go chasing after them.

I'm subscribed to a bug report where the kernel logs "Eeek! Pagemap count hit -1!" or something similar to that.

There has been an astonishing number of people posting their experiences and logs to this bug report, but there seems to be no link at all between the posters. And I'm sure a lot of posters, such as myself, have found that the problem went away during Ubuntus 8.04, 8.10 or 9.04.

Nobody knows what causes this problem. I don't think anyone knows how to reproduce it except to say "Install Ubuntu 8.04 on my computer and surf around on Firefox for a while and it will probably happen", or "Use my computer continuously and the problem will occur some time after 30 hours have passed". You can't fix bugs like that; it's impractical.

And a lot of the time, the bug is restricted to people who own a device that was only sold through Red Dot stores in southern Texas, made by a company that's out of business, and only through sheer conincidence can be used on Linux through a kernel driver for a similar device.

---

### Post by change_mode on 2009-07-08
> **AlexC_ said:**
> And how many of these are actually bugs with Ubuntu its self? That number will shoot right down.

The reported bugs are going to include bugs that are issues with software upstream, and nothing Ubuntu developers can do about unless they want to start working on that software to fix them.

There is more to Ubuntu than just Ubuntu.

It doesn't really matter how many of those are bugs with Ubuntu. The point is that the bugs that can be fixed should be fixed, unless it's really not worth it like the case 3rdalbum described.
Some of the bugs would take 5 minutes to fix, but they get a low priority and pile up while new features (with new bugs) are implemented.

They recently started a project that aims to fix 100 minor bugs before the Karmic release. It's a good start.

[https://edge.launchpad.net/hundredpapercuts/karmic](https://edge.launchpad.net/hundredpapercuts/karmic)

---

### Post by 23meg on 2009-07-08
> **change_mode said:**
> It doesn't really matter how many of those are bugs with Ubuntu. The point is that the bugs that can be fixed should be fixed, unless it's really not worth it like the case 3rdalbum described.
Some of the bugs would take 5 minutes to fix, but they get a low priority and pile up while new features (with new bugs) are implemented.


What does matter though is that Ubuntu, compared to upstream, has a very small workforce, which has its hands full maintaining Ubuntu and fixing Ubuntu-specific bugs. 

What will help fix bugs at a greater rate is more developers and bug triagers (as opposed to more concentration on bug fixing by the existing set of contributors), and better bug triage procedures and practice.

---

### Post by unutbu on 2009-07-08
Please correct me if I'm wrong:

Let A represent the Linux kernel and application developers.
Let B represent the Debian packagers.
Let C represent the Ubuntu packagers.

A is the group of people who fix most of the bugs.
B takes A's code and makes Debian packages.
C takes B's Debian packages, modifies and repacks them as Ubuntu packages.

Each group provides a very useful component for the ultimate product, our Ubuntu systems.
C relies on A and B, but C is focused on integrating the packages into an overall easy to use system. C is not focused on fixing bugs, and I doubt it ever will be. 

C provides launchpad, which collects bug reports. 
Since there are a lot of C users, launchpad collects a lot of bug reports.
C fixes some bugs, but I think most are simply reported upstream to B or A.

C is where a lot of the users are, but A is where the bugs get fixed, and the people in A do not necessarily work through or even read launchpad. To get a bug fixed, it seems the best way is to either read code and create the patch yourself, or talk to the developers in A (post in their mailing list for example).

---

### Post by 23meg on 2009-07-08
Except the following details, you're spot on:

[QUOTE=unutbu]C provides launchpad, which collects bug reports. [/QUOTE]

Launchpad is an independent product developed by Canonical, not the Ubuntu community. But yes, the Ubuntu community does use it for bug and feature tracking, translations and support, just like many other projects do.

[QUOTE=unutbu]To get a bug fixed, it seems the best way is to either read code and create the patch yourself, or talk to the developers in A (post in their mailing list for example).[/QUOTE]

That's usually not going to be a good idea, since with most suspected bugs, you won't be able to tell from the start whether the bug (if there actually is one) is in the upstream code or the Ubuntu integration, and you wouldn't want to flood upstream developers with what could be Ubuntu or Debian-specific issues. 

The best way to get a bug fixed, short of fixing it yourself, is:

[list][*] [Get]("https://wiki.ubuntu.com/Bugs/BestPractices") [really]("http://www.fabianrodriguez.com/blog/2008/01/18/the-bug-reporting-culture-10-things-to-avoid-10-things-you-must-do/") [really]("http://www2.bryceharrington.org:8080/drupal/node/35") [good]("https://wiki.ubuntu.com/MeetingLogs/openweekintrepid/BugReporting") at [reporting bugs]("http://help.ubuntu.com/community/ReportingBugs"), *and following up with them* to provide the required information (I can't stress the latter part enough). Don't forget that like every skill, it's acquired, and improves with practice. 
[*] Do [whatever it takes]("https://wiki.ubuntu.com/DebuggingProcedures") to get your bug to the "Triaged" status in Ubuntu, past which point it will be forwarded upstream if it's an upstream issue. 
[*] If the processes that will lead to the bug getting fixed seem to have got stuck, engage in the subtle diplomacy that may be needed to unclog the pipes. [/list]

---

### Post by unutbu on 2009-07-08
Thanks for the info and advice, 23meg. :)

---

### Post by FuturePilot on 2009-07-08
You also have to take into account the number of New bugs and Incomplete bugs that really aren't even bugs.

---

### Post by zekopeko on 2009-07-08
many bugs could be twarted if applications developer would have comprehensive test suites. regression would be easier to spot since all of this would be automated. but alas this is up to developers.

---

### Post by 23meg on 2009-07-10
> **unutbu said:**
> Thanks for the info and advice, 23meg. :)

You're welcome.

> **FuturePilot said:**
> You also have to take into account the number of New bugs and Incomplete bugs that really aren't even bugs.

"Bug report" is a better term for those. Bug report != bug.

---

