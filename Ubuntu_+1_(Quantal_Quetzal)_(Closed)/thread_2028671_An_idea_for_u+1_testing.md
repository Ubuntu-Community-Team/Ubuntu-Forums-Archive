---
title: "An idea for u+1 testing"
date: 2012-07-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-07-18
WARNING: This is a wall of text, but please read and give your input!

I have been mulling over an idea to help solidfy and increase communication amongst the folks here and in the U+1 team with regards to the daily testing you do. Often your among the first to spot critical issues in new packages, etc. However, it's hard to communicate even amongst the group on the forums or in the u+1 team or qa team, etc about what's going on. Duplicate bugs get created, it's hard to confirm what's going on, etc. 

With that in mind, let me share my thoughts on an idea to help fix this using the tracker. The basic idea is to get a list of packages the u+1 team cares about and looks at -- things like graphics drivers, compiz, unity perhaps, browsers; and then put them in the tracker with a some testcases for them.

First, we'd have some basic smoke tests (things people are already doing, aka by running and using the software). If things are working, people can submit a good result. When the version increments in the archive, we'll push out a new build and people can report against that build as well. Sort of a nice heads-up display of the state of the dev version for the end-user.

Secondly, we'll include the testcases for the applications themselves where they exist and **we can then have testing event days** around running the tests and reporting results. We can target specific big version bumps and/or features as they land.

Discussions of course will continue to happen naturally here. The tracker just allows us all to see what we're collectively doing and working on, and helps facilitate discussions when breakage occurs. 

So, all that said, I thought today gave me the perfect oppurtunity to demo what I mean. Today the new software-properties package landed. And as usual you all found some bugs and reported them (way to go!). 

If you look on [http://packages.qa.ubuntu.com/](http://packages.qa.ubuntu.com/) you'll see there's a new section called 'u+1 testing'. Inside is the [software-properties package]("http://packages.qa.ubuntu.com/qatracker/milestones/225/builds/18905/testcases/1308/results"). There's a very basic smoketest in there, the changelog is noted at the top with a link to more info on the package. Installation instructions, and finally how to file a bug are included. And best of all, all the results from users like yourselves on whether it's working or not. You can even leave comments. Please go ahead and leave some results and play around with the system.

(If your curious to see what this might look like over a longer period of time, have a look at kernel testing.
Here's the history:
[http://packages.qa.ubuntu.com/qatracker/milestones/223/history](http://packages.qa.ubuntu.com/qatracker/milestones/223/history)
A result page:
[http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/testcases/1306/results](http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/testcases/1306/results)
The list of bugs opened and status for all of them:
[http://packages.qa.ubuntu.com/qatracker/reports/defects](http://packages.qa.ubuntu.com/qatracker/reports/defects)
)

This of course doesn't replace our wonderful discussions here, but augments them. Now we can refer to a singular place for the packages we care about and keep status on them and the versions that ship out all cycle. What do you think?

---

### Post by Stinger on 2012-07-18
I like it, I think it's a brilliant idea.

I'm afraid I'm limited to some kernel testing on Precise running [GNObuntu]("http://ubuntuforums.org/showthread.php?t=1999827") ;)
But that's another story.

---

### Post by ronacc on 2012-07-18
I would like just to be able to do some testing , since the start of the 3.5 kernel I have rarely even been able to get the installer to actually complete the install and if it does actually complete the install said install is so unstable that it usually won't make it to desktop without kernel panicking . and if by some miracle it gets all the way to desktop it kernel panics as soon as you try to do something like open a terminal to update or install something .

---

### Post by balloons on 2012-07-19
> **ronacc said:**
> I would like just to be able to do some testing , since the start of the 3.5 kernel I have rarely even been able to get the installer to actually complete the install and if it does actually complete the install said install is so unstable that it usually won't make it to desktop without kernel panicking . and if by some miracle it gets all the way to desktop it kernel panics as soon as you try to do something like open a terminal to update or install something .

Yikes! What kind of hardware is this? I too have found the 3.5 kernel to cause some issues on my box, but as of -rc7 I think they might be fixed. Anyway you could report a bug for this? Even if you can't get any logs from the kernel panics, it would be good to report. I'd be happy to help try and find someone with similar hardware to confirm what your seeing. Has every 3.5 kernel been this way? Does the 3.5 kernel on 12.04 userspace have the same issue? Does the mainline kernels have the same issue. Color me interested and willing to help if I can. I know having things fail open is quite frustrating.

---

### Post by dino99 on 2012-07-19
i'm having lot of kernel panic too (a bit less now than before, but still one at each cold boot :( and reboot never works (might be the same reason)

what is frustating:
- cant get these kernel panics logged, what a shame.
- seems like ureadahead is to blame for some part of the issue (bug #969926 )
- lot of logs are hidden into multiple subfolders

maybe its time to sum them inside a main dir, and maybe set apport to look deeper inside these. (see Brian Murray)

note: these kernel panics have started at the same time that upstart/udev have landed into ubuntu and hal dropped. (so not very new)
note2 : talking about upstart jobs, some scripts are still around (see them at shutdown time) and not switched to upstart yet)

---

### Post by ronacc on 2012-07-19
> **guitara said:**
> Yikes! What kind of hardware is this? I too have found the 3.5 kernel to cause some issues on my box, but as of -rc7 I think they might be fixed. Anyway you could report a bug for this? Even if you can't get any logs from the kernel panics, it would be good to report. I'd be happy to help try and find someone with similar hardware to confirm what your seeing. Has every 3.5 kernel been this way? Does the 3.5 kernel on 12.04 userspace have the same issue? Does the mainline kernels have the same issue. Color me interested and willing to help if I can. I know having things fail open is quite frustrating.

AMD64x2 4600+ , nvidia 7600gs , 4gb ddr2 , 6 drives 4 sata 2 ide  1 ide dvd drive , gigabyte ga m55plus s3g motherboard .

not an exotic rig by any standards and also note that it does not panic on quantal IF I choose the 3.4.0-5 kernel or earlier , only on the 3.5 series kernels . This is a kernel problem not a hardware problem .

at  the moment the only useable ubuntu install I have on that box is the precise install I upgraded at repo open , I haven't been able to get a useable install since A1 between installer crashes and kernel panics If I loose my upgraded precise I'm benched mabye for the rest of the game .If I could get a daily to install and be stable enough to play with I would , on top of everything else they took away from "recovery" mode any chance of doing much to recover . ( root console with networking )

---

### Post by ronacc on 2012-07-19
here is the message from one of the kernel panics , I copied it off of the screen since as dino99 notes when the kernel panics logging stops .

138.632664 BUG: unable to handle kernelNULL pointer at dereference 00000000000080  

there is another one too about not syncing I'll copy that one too net time it shows up ..some of the others are lost completely since the kernel don't always have the good graces to switch to a VT before dying and you are left with a frozen screen , no indication why and no way out but the power button ( no kbd and no mouse so no alt sysreq RSEIUB )

---

### Post by balloons on 2012-07-19
> **ronacc said:**
> here is the message from one of the kernel panics , I copied it off of the screen since as dino99 notes when the kernel panics logging stops .

138.632664 BUG: unable to handle kernelNULL pointer at dereference 00000000000080  

there is another one too about not syncing I'll copy that one too net time it shows up ..some of the others are lost completely since the kernel don't always have the good graces to switch to a VT before dying and you are left with a frozen screen , no indication why and no way out but the power button ( no kbd and no mouse so no alt sysreq RSEIUB )

Thanks, I'll take this along and open a bug report to start the process of looking into this. Hang in there. If you don't mind, I'm going to subscribe you as well, as input will likely be asked for ;-)

---

### Post by ronacc on 2012-07-19
since I finally got an install that would boot even if unstable and I had found out in my previous floundering around that if I got to the log in window and then ctrl>alt>f1 before loging in to the desktop the resultant terminal would be much less likely to cause a kernel panic and I atleast had a chance to update and install things  so I have been able to milk the current daily up to the 3.5.0-5 repo kernel and get G-S installed , G-S is much more stable than unity for me , not really stable just better than unity .

---

### Post by balloons on 2012-07-20
> **ronacc said:**
> since I finally got an install that would boot even if unstable and I had found out in my previous floundering around that if I got to the log in window and then ctrl>alt>f1 before loging in to the desktop the resultant terminal would be much less likely to cause a kernel panic and I atleast had a chance to update and install things  so I have been able to milk the current daily up to the 3.5.0-5 repo kernel and get G-S installed , G-S is much more stable than unity for me , not really stable just better than unity .

We've sidelined the thread a little, but this is important. dino99 and ronacc can you file kernel bugs

[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

to the best of your ability? ronacc since your able to boot and get to a terminal, you should be able to run 'ubuntu-bug linux' from the VT. Once opened, subscribe me to the bug and I'll make sure it gets looked at. Overall 3.5 feels a little uneasy.. if we can find the regressions causing issues before it releases that would be best.

---

### Post by ronacc on 2012-07-20
I am only able to get to a vt before a problem occurs , once the bug actually shows up the system is toast . the cause of the kernel panics is not being logged since the system dies instantly , and nothing is being caught by apport . I will file a bug on the sync failure as that occured again and I transcribed the last few lines onto another machine .

---

### Post by ronacc on 2012-07-20
filed bug # 1027322    , couldn't give much info , I didn't have much .

---

### Post by ventrical on 2012-07-21
> **guitara said:**
> WARNING: This is a wall of text, but please read and give your input!

I have been mulling over an idea to help solidfy and increase communication amongst the folks here and in the U+1 team with regards to the daily testing you do. Often your among the first to spot critical issues in new packages, etc. However, it's hard to communicate even amongst the group on the forums or in the u+1 team or qa team, etc about what's going on. Duplicate bugs get created, it's hard to confirm what's going on, etc. 

With that in mind, let me share my thoughts on an idea to help fix this using the tracker. The basic idea is to get a list of packages the u+1 team cares about and looks at -- things like graphics drivers, compiz, unity perhaps, browsers; and then put them in the tracker with a some testcases for them.

First, we'd have some basic smoke tests (things people are already doing, aka by running and using the software). If things are working, people can submit a good result. When the version increments in the archive, we'll push out a new build and people can report against that build as well. Sort of a nice heads-up display of the state of the dev version for the end-user.

Secondly, we'll include the testcases for the applications themselves where they exist and **we can then have testing event days** around running the tests and reporting results. We can target specific big version bumps and/or features as they land.

Discussions of course will continue to happen naturally here. The tracker just allows us all to see what we're collectively doing and working on, and helps facilitate discussions when breakage occurs. 

So, all that said, I thought today gave me the perfect oppurtunity to demo what I mean. Today the new software-properties package landed. And as usual you all found some bugs and reported them (way to go!). 

If you look on [http://packages.qa.ubuntu.com/](http://packages.qa.ubuntu.com/) you'll see there's a new section called 'u+1 testing'. Inside is the [software-properties package]("http://packages.qa.ubuntu.com/qatracker/milestones/225/builds/18905/testcases/1308/results"). There's a very basic smoketest in there, the changelog is noted at the top with a link to more info on the package. Installation instructions, and finally how to file a bug are included. And best of all, all the results from users like yourselves on whether it's working or not. You can even leave comments. Please go ahead and leave some results and play around with the system.

(If your curious to see what this might look like over a longer period of time, have a look at kernel testing.
Here's the history:
[http://packages.qa.ubuntu.com/qatracker/milestones/223/history](http://packages.qa.ubuntu.com/qatracker/milestones/223/history)
A result page:
[http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/testcases/1306/results](http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/testcases/1306/results)
The list of bugs opened and status for all of them:
[http://packages.qa.ubuntu.com/qatracker/reports/defects](http://packages.qa.ubuntu.com/qatracker/reports/defects)
)

This of course doesn't replace our wonderful discussions here, but augments them. Now we can refer to a singular place for the packages we care about and keep status on them and the versions that ship out all cycle. What do you think?

Hi guitara,

 You asked for input. I looked at some of the links and they seem most like  the same format  as when we were testing Precise.  The problem is that it takes so much time to set up a test in the format prescribed. Starting a post here in the forums is so much more up-time manageable.

Honestly, I try to spend at least 2 hours a day  testing various brands of Ubuntu and the daily .ISOs but I have work in the field that is a priority. There are other occasions when I can spend a whole day beta testing. My point is, I find using ubuntuforums and filing bugs in launchpad much more expedient. I understand that this does not necessarily help the developers but is seems like things get fixed a lot quicker when we all jump on a bug in the forums.

Thanks and regards :)

---

