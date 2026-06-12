---
title: "I Wish Ubuntu was more Polished with longer release cycle"
date: 2014-09-10
forum: Ubuntu, Linux and OS Chat
---

### Post by csiebester on 2014-09-10
I would really like to be able to use Ubuntu particularly on some older computers I still have that were made to run XP, and if it worked smoothly I would use it on my normal computers as well for security sake.  Every time I try it I have always picked the LTS distributions, and every time I install Ubuntu there always seems to be bugs that make the experience arduous and frustrating.  I always spend hours sifting through forums trying to figure out what to do to fix some problem and inevitably conclude it's not worth the trouble.  I think this may be true of many people and may limit the interest people have in using Linux.  Perhaps I just don't know enough about using it and if I had hundreds of hours to spend I could learn enough to be able to solve my problems quickly, but I just don't have that kind of time to commit to linux.  I really wish that instead of releasing new and buggy distributions every 6 months that the distributions would be more heavily polished, and the release cycle be lengthened.  I think that if this were done people like myself would have better experiences with linux which would lead to greater interest.

---

### Post by ian-weisser on 2014-09-10
> **csiebester said:**
> I would really like to be able to use Ubuntu particularly on some older computers I still have that were made to run XP,

Several flavors of Ubuntu run very well on older hardware. Have you tried them?
The Unity version of Ubuntu is not designed for older hardware, and that won't change.



> **csiebester said:**
> and every time I install Ubuntu there always seems to be bugs that make the experience arduous and frustrating.  I always spend hours sifting through forums trying to figure out what to do to fix some problem and inevitably conclude it's not worth the trouble.

We are happy to help new users with install problems, please provide examples.
References to existing threads would be most helpful.

---

### Post by csiebester on 2014-09-10
> **ian-weisser said:**
> Several flavors of Ubuntu run very well on older hardware. Have you tried them?
We are happy to help new users with install problems, please provide examples.
References to existing threads would be most helpful.

Ian, I most recently tried running Lubuntu on 2 separate computers.  I had trouble getting the wireless to work which was a major problem because I don't have acess to my apartment router, and I also had a problem with the screen resolution setting strangely with no option to change it.  The previous time I tried Ubuntu I had some kind of trouble with the password keyring, and the time before that I also had trouble with the wireless.  Yes it's true that I was able to get help from the very friendly and helpful community but it took lots of time in each case and that's the point.  I wish there was more emphasis on making a bug free usable out of the box without messing around OS and less of an emphasis on providing new features.

---

### Post by Tar_Ni on 2014-09-10
> **csiebester said:**
> Ian, I most recently tried running Lubuntu on 2 separate computers.  I had trouble getting the wireless to work which was a major problem because I don't have acess to my apartment router, and I also had a problem with the screen resolution setting strangely with no option to change it.  The previous time I tried Ubuntu I had some kind of trouble with the password keyring, and the time before that I also had trouble with the wireless.  Yes it's true that I was able to get help from the very friendly and helpful community but it took lots of time in each case and that's the point.  I wish there was more emphasis on making a bug free usable out of the box without messing around OS and less of an emphasis on providing new features.

There was an annoying bug on Lubuntu 14.04, the wifi icon wouldn't appear on the desktop. But now it has been fixed in Lubuntu 14.04.1. The screen resolution settings can easily be changed by clicking on the startup menu -> Preferences -> Screen settings et voilà!


As for Ubuntu, the reason why your wireless didn't work is most likely because your wifi card was not supported at the time. With each new release there come a kernel update, which ensure the support of newest hardware.

Hardware recognition used to be a serious problem for Linux in the past but the situation has vastly improved in recent years. A wide range of hardware and devices are now supported out-the-box. Canonical developpers are working hard on making Ubuntu a great and user-friendly OS. Ubuntu 14.04 is so far very stable for me. I have not encountered a single bug and crash. Maybe I am lucky but many people on these boards seem pretty happy with it, to the point that some cutting-edge enthousiasts are considered not to upgrade to the newest and latest 14.10!


BTW, Xubuntu runs well on older hardware too.

---

### Post by Bucky Ball on 2014-09-10
Lubuntu doesn't have an LTS release as far as I know. Try Xubuntu, it has three years for LTS. Runs well on older machines (and I use it on every machine, young or old!).

---

### Post by Tar_Ni on 2014-09-10
> **Bucky Ball said:**
> Lubuntu doesn't have an LTS release as far as I know. Try Xubuntu, it has three years for LTS. Runs well on older machines (and I use it on every machine, young or old!).

Lubuntu 14.04 is a 3 years LTS release. It's very first.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu)

---

### Post by QIII on 2014-09-10
> **csiebester said:**
> ... and the release cycle be lengthened...

LTS to LTS is 2 years.  Since they are supported for 5 years, if you are currently running 14.04 that means that you wouldn't have to reinstall until 18.04 and you would still have an LTS version.  You don't *have *to install anything in between.  You don't *have *to install the new releases every 6 months.

Distros like Fedora have significantly shortened their release cycles, too.  The world of Linux changes so quickly that keeping up means shorter release times.

Debian forgoes short release schedules for their Stable releases, but they move fairly quickly on Unstable.

There is no OS that ships initially without bugs.  None.  There is no software that ships initially without bugs.  None.  If you want to avoid the frustration of bugs, wait a month before installing a new release and keep an eye out on the Forums for what people are encountering.

If we in the industry wait to ship we get is "feature creep", which introduces bugs:  "Oh.  Well if we aren't going to ship until next month anyway, let's see if we can get feature X in as well."

This is and has always been the nature of things.

---

### Post by ian-weisser on 2014-09-10
> **csiebester said:**
> I had trouble getting the wireless to work which was a major problem because I don't have acess to my apartment router, and I also had a problem with the screen resolution setting strangely with no option to change it.

Seems like you purchased hardware incompatible with Ubuntu.
Linux relies on autodetection of hardware. Hardware is a kernel responsibility, not a user responsibility. But it only works if the manufacturers support it properly.

It's not Ubuntu's fault if the manufacturer refuses to release Linux-compatible kernel modules (drivers), nor if they refuse to release the interface specs so volunteers can create drivers, nor if a display lies about it's supported modes (manufacturing bug). If they release it, we will add it to Ubuntu.

In most of these cases, you unintentionally paid for that feature. You supported manufacturers that don't support Linux.
Next time, try not to do that.


  > **csiebester said:**
> The previous time I tried Ubuntu I had some kind of trouble with the password keyring.

Well, I empathize with your plight. It does stink when you run across a problem you don't expect, or know how to fix.
I cannot tell if it's really a bug from that description, or what the cause might be.
I can tell you that on a dozen systems with Ubuntu in the past nine years, I have never experienced that problem.


> **csiebester said:**
>  I wish there was more emphasis on making a bug free usable out of the box without messing around OS and less of an emphasis on providing new features.

Your wish seems granted. A high priority of Ubuntu developers in every release cycle is to fix bugs. They built an entire testing infrastructure to discover and fix whole classes of package and install/upgrade bugs. Other projects have been or are undergoing huge bug-fixing projects. Whole classes of Xorg and printing and pulse audio bugs have been eliminated in the past couple years.

There's also the Ubuntu Online Summit, where you can talk directly to project developers about the bugs you care about most. There's a whole volunteer Bug Squad, whose only task is to verify and improve bug reports so developers can focus on code and patches.

There's a huge amount of effort going on right now to fix bugs. And it's been going on for years.

---

### Post by grahammechanical on 2014-09-10
Every release of Ubuntu has a 26 week development period. Utopic Unicorn (14.10) had feature freeze on 18 August. It will have user interface freeze on 21 September and kernel freeze on 9 October with Final Freeze on 16 October. Developers are not allowed to keep adding stuff and making changes.

[https://wiki.ubuntu.com/UtopicUnicorn/ReleaseSchedule](https://wiki.ubuntu.com/UtopicUnicorn/ReleaseSchedule)

[https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)

[https://wiki.ubuntu.com/UserInterfaceFreeze](https://wiki.ubuntu.com/UserInterfaceFreeze)

[https://wiki.ubuntu.com/KernelFreeze](https://wiki.ubuntu.com/KernelFreeze)

[https://wiki.ubuntu.com/FinalFreeze](https://wiki.ubuntu.com/FinalFreeze)

Now, to fix bugs prior to release the developers need to know that there are bugs. It is no use waiting until after a version has been released and then say, "Look, I found a bug." From the second week of the development cycle there will be daily ISO images of the development version. We can test the installer. We can install the development version and update daily. We can help to identify bugs before the version is released.

Do not just wish. Wishing never changes anything. Join in.

[https://qa.ubuntu.com/2014/04/14/trusty-release-week-get-your-test-results-in/](https://qa.ubuntu.com/2014/04/14/trusty-release-week-get-your-test-results-in/)

Regards.

---

### Post by QIII on 2014-09-10
> **grahammechanical said:**
> Every release of Ubuntu has a 26 week development period. Utopic Unicorn (14.10) had feature freeze on 18 August. It will have user interface freeze on 21 September and kernel freeze on 9 October with Final Freeze on 16 October. Developers are not allowed to keep adding stuff and making changes.

Exactly my point.  The releases come on schedule, there is no delivery slip, there is no feature creep.

---

### Post by csiebester on 2014-09-11
Perhaps I have just gotten unlucky, or perhaps I do have hardware issues.  In lubuntu 14.04 I struggled with all of the bugs that were described above as now being fixed, so perhaps I just should have waited longer for more bugs to be found.  I also realize that a lot of work goes into what is a very complicated program with a great deal of that work being debugging.  It's just been my experience that every time I have tried linux I have had trouble of some sort.  I'm sure other novice linux users have had similar experiences and been turned off.  I guess my thought, which could very well be wrong, is that if all the time spent making making new linux distributions every 6 months were put toward really polishing the LTS releases or something on longer time scale than 6 months, then maybe everything would be smoother.

---

### Post by vasa1 on 2014-09-11
> **csiebester said:**
> Perhaps I have just gotten unlucky, or perhaps I do have hardware issues.  In lubuntu 14.04 I found all of the bugs that were described, so perhaps I just should have waited longer for more bugs to be found.  I also realize that a lot of work goes into what is a very complicated program with a great deal of that being debugging.  I'm just frustrated because every time I have tried linux I have had trouble of some sort and I would like to be able to run it on at least my old computers without hassle.  I'm sure other novice linux users have had similar experiences and been turned off though.
Have you asked for help here? As a novice user, I asked for help and most certainly didn't get "turned off". I guess I really wanted to use Linux rather than lecture others about their failings or those of Linux.

---

### Post by PondPuppy on 2014-09-11
"[COLOR=#000000]I'm sure other novice linux users have had similar experiences and been turned off." 

You bet. Just read the "Absolute beginners" forum. 

For myself, I haven't had problems. I did with Windows 7 -- a missing internet card driver. As GrahamMechanical said, all OSes have bugs. You can read Windows help forums and find many complaints about that OS too.

The "keyring did not get unlocked" issue is one I had a long time ago on a Linux machine... there are some posts about that. [http://askubuntu.com/questions/184266/what-is-unlock-keyring-and-how-do-i-get-rid-of-it](http://askubuntu.com/questions/184266/what-is-unlock-keyring-and-how-do-i-get-rid-of-it)



[/COLOR]

---

### Post by ian-weisser on 2014-09-11
> **csiebester said:**
> Perhaps I have just gotten unlucky, or perhaps I do have hardware issues.  In lubuntu 14.04 I struggled with all of the bugs that were described above as now being fixed, so perhaps I just should have waited longer for more bugs to be found.  I also realize that a lot of work goes into what is a very complicated program with a great deal of that work being debugging.  It's just been my experience that every time I have tried linux I have had trouble of some sort.  I'm sure other novice linux users have had similar experiences and been turned off.  I guess my thought, which could very well be wrong, is that if all the time spent making making new linux distributions every 6 months were put toward really polishing the LTS releases or something on longer time scale than 6 months, then maybe everything would be smoother.

This idea of slow-down-development-so-we-can-spend-more-time-fixing-bugs pops up regularly.
It seems based on a misunderstanding of how open source development works, and upon how Ubuntu and other distros work with upstream projects.

Most development work takes place at upstream projects who (quite correctly) don't care one whit about Ubuntu's six-month release cycle. They release when they release. They fix the bugs in their software that they learn about.

All those upstream packages get integrated by the distro, tested somewhat to ensure they work as intended, and released as a snapshot. Ubuntu does this every six months. Ubuntu has an enormous testing program, focused on stability - making sure all those disparate puzzle pieces work together without crashing.

Changing the release cycle won't affect most upstream development and bugfixing - but it will lengthen the the time before those fixes are propagated through the distro in the next release.

The best thing users can do is to report confirmable bugs, learn to triage bugs, and participate in upstream projects to influence the design and bugfixing processes of that upstream work. None of which is easy or obvious for new users. Learning the best way to get stuff done in *any* complex organization takes time and experience.

---

### Post by vasa1 on 2014-09-11
[http://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](http://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar)
[http://en.wikipedia.org/wiki/Release_early,_release_often](http://en.wikipedia.org/wiki/Release_early,_release_often)

---

### Post by help_me2 on 2014-09-12
Buy a PC that has Ubuntu preinstalled, and then you won't have any problems. System 76 has some real nice computers.

---

### Post by craig10x on 2014-09-12
I can tell you that toshiba laptops that are all intel are extremely linux and ubuntu friendly....runs like a dream on them...

---

### Post by sam-c on 2014-10-03
I play around a lot with mainly Ubuntu based Systems and Have found that elementary OS is lovely and very efficient

---

### Post by Michael_McKenney on 2014-10-03
Microsoft Windows releases a upgrade every 18-24 months.  It goes through alpha and beta testing.  Manufacturers can have problems if changes are made after beta testing is completed to the Release versions and final version.  Most of the time it is a smooth transition.   You have people getting paid to get it right or working.   With Linux, you have a community volunteering time and energy into it.  I was told when Linux came out in 20+ years ago, if it works, don't fix it.  It is sort of like every other version of Windows.  

XP Pro worked
XP Millenium sucked for most
NT 3.51 was ahh 
NT 4.0 was slightly better
Vista sucked for most, for me Vista worked good with drivers but memory management sucked.
Windows 7, fixed memory management but requires 16GB of RAM to really work well.
Windows 8, I would not install it on Obama's computer.
Windows 10, I don't want to be like Apple so I am playing with Ubuntu till Microsoft kills my Windows 7.  

I found Nvidia hardware does not work well with Ubuntu for me other than video cards.  Intel NICs work great.

---

### Post by JeQhdMD on 2014-10-06
A couple of posters in this thread made an excellent point:   _IF you really want to have an "apples to apples" comparison with MS-Windows or Apple MacOS's_ . . . . . then you "must" buy a PC with Linux pre-installed.   

Any other type of comparison is invalid, unless ALL windows and apple OS user would also be required to install those OS's from scratch.    In other words, the Win and Apple PC's have been "pre-engineered" for those OS's, not retrofitted like Linux and BSD PC's.     

*Given that scenario, Linux OS's (distros) like Ubuntu, Fedora, OpenSuse and a host of others work remarkably well*.   Because of the UEFI mess and because I'm getting older and hopefully wiser, my next machine (laptop or desktop) will likely be from either System 76 or Zareason - - with the latest install of Ubuntu.   **Simple enough that even a cave-man could do it**.

---

### Post by help_me2 on 2014-10-06
You always buy pc's with windows preinstalled, right? Try one with linux preinstalled. system76.com or zareason.com can help there. You can't expect ubuntu to work on every hardware configuration in the world. OSX doesn't, and neither does windows. I've been using ubuntu since 2007 with almost no problems because I was smart enough to know what it works on, and what doesn't. Don't have time to learn? Use windows or Mac. I'm sure they would love to have you.

But once you actually have a linux compatible computer, the experience is awesome. My laptop is 3 yrs old and has run every version of ubuntu since then perfectly. Do you buy a mac computer and try to put windows on it? Buy a linux compatible computer, and you'll have a much different experience. But noobs and windows users don't understand that concept. To them, linux MUST be able to run on their existing proprietary windows pc. 

Fair enough if you still don't understand what I'm saying, stay with windows or mac. Good luck to you.

---

### Post by help_me2 on 2014-10-06
> **csiebester said:**
> if all the time spent making making new linux distributions every 6 months were put toward really polishing the LTS releases or something on longer time scale than 6 months, then maybe everything would be smoother.
Maybe if manufacturers could come out with drivers for all the new stuff (microsoft relies on these), then it would be better. I just buy compatible hardware. Problem solved. Btw, any "noob" isn't going to be able to install windows or mac osx either. So, your point? Any computer literate person can install ubuntu without any major problems and can navigate through any issues. It's not much different than installing anything else. Just do some research.

---

