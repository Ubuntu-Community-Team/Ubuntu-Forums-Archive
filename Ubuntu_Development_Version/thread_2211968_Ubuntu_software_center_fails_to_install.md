---
title: "Ubuntu software center fails to install"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by gifford on 2014-03-18
I am having trouble installing any deb external packages with the software center.
After downloading and clicking on the deb file, the software center opens up but gives the error of failed after starting to install.
The system log reports this error after installation fails.
AptDaemon.Worker: WARNING: An additional step to open the cache is required

This has happened for all external packages for several days.
I can however install with the command line.

What is the problem with the software center?

---

### Post by bapoumba on 2014-03-18
Which ubuntu version are you using. This sub-forum is for Ubuntu +1, 14.04.

---

### Post by gifford on 2014-03-18
I'm using 14.04 that has been updated daily.
Only noticed the problem a few days ago when trying to install downloaded packages. 
It is a persistent problem now.

---

### Post by bapoumba on 2014-03-18
OK thanks, your details say Ubuntu 12.04 Precise Pangolin :)

---

### Post by gifford on 2014-03-18
I use several different computers!
Details only provides for one listing of Ubuntu version.

---

### Post by bapoumba on 2014-03-18
No problem :)
I've been looking around with your error message that brings up old bugs not always related to the Ubuntu Software Center..

---

### Post by gifford on 2014-03-18
I have no idea at this point. Software selected from the software center installs without a problem..but any downloaded deb does not.
As I indicated earlier, I can install using the CL but the not with software center. Is this a bug?

---

### Post by cariboo on 2014-03-18
It could be a problem of missing dependencies, as I recall the Software Centre isn't very good at installing dependencies. I'd suggest giving gdebi a try, it's in the repositories.

---

### Post by su:bhatta on 2014-03-19
I am having this same problem, though I cannot say for how long, cause I generally Use GDebi or QApt Package Installer.

I noticed this on Monday 17th, when trying to install Syncwall from WebUpd8, which was opened in Software Center by default, and was reported as 'failed to install'.
GDebi, installed it right away.

---

### Post by gifford on 2014-03-19
I wonder how many others are having this problem?
While I can work around it, it would not be good for this issue to be a problem with the general release.
Should this be a bug report?

---

### Post by cariboo on 2014-03-19
This has been a problem since the Software Centre was set as the default app for installing debs that have been downloaded. It is really hit or miss when it comes to installing them. If there are no dependencies that need installing it works quite well, but it will fail every time if dependencies are needed to make a package work.

This is one of those corner cases where the average user that Ubuntu is aimed at, are only expected to use the repositories to install packages, but in light of some of the enhancements that have been added to Unity lately, I'd suggest a bug report is in order.

---

### Post by gifford on 2014-03-22
I'm really frustrated with trying to report this as a bug. The process is very cumbersome with no clear directions or answers on how to report it.
The issue still exists.

---

### Post by ikt on 2014-03-22
I reported the bug here:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228)

Feel free to +1 the bug report to get it some attention!

---

### Post by su:bhatta on 2014-03-22
> **ikt said:**
> I reported the bug here:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228)

Feel free to +1 the bug report to get it some attention!

Marked as ' affects me'..

---

### Post by cariboo on 2014-03-22
> **gifford said:**
> I'm really frustrated with trying to report this as a bug. The process is very cumbersome with no clear directions or answers on how to report it.
The issue still exists.

Reporting bugs is pretty simple if you follow the instructions on [this]("https://help.ubuntu.com/community/ReportingBugs") wiki page. Scroll down to How To Report Bugs.

---

### Post by chris_dummer on 2014-03-23
i have the same problem loading skype and steam, used gdebi installed ok

---

### Post by diascris on 2014-03-23
Also having this isseu with my fresh install of Ubuntu 14.04

---

### Post by gifford on 2014-03-23
This is an issue on both of our installations of 14.04.

---

### Post by gifford on 2014-04-07
Still not resolved.

---

### Post by cariboo on 2014-04-07
> **gifford said:**
> Still not resolved.

> **gifford said:**
> This is an issue on both of our installations of 14.04.

So gdebi didn't work for you? I doubt that the bug will be fixed before  release, so I'd suggest you mark the bug as affecting you, use gdebi, and get on with things, and hope the bug gets fixed before the next version is released.

---

### Post by gifford on 2014-04-08
No..I can install using other methods. Just was hoping this would be taken care of as we move close to the official launch.

---

### Post by Mateusz Stachowski on 2014-04-12
Looks like this is fixed with the newest aptdaemon (version 1.1.1-1ubuntu5). I installed today three external packages using Software Center without any problems.

It would be nice to confirm or deny this in the [bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228") report.

---

### Post by Mateusz Stachowski on 2014-04-14
One other user confirmed that the [bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228") is fixed and also Michael Vogt marked it as Fix Released so its SOLVED.

---

### Post by borischan on 2014-04-25
> **Mateusz Stachowski said:**
> One other user confirmed that the [bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228") is fixed and also Michael Vogt marked it as Fix Released so its SOLVED.

I can't open software center at all as of yesterday (April 24th), is this really solved or do I have a different issue? 
Upgraded to 14.04 recently, before that no issue.

---

### Post by cariboo on 2014-04-25
@borischan, I'd suggest you start a new thread in General Help, as you won't get any help for 14.04 problems in this sub-forum, we've all moved on to 14.10 Utopic Unicorn.

---

### Post by ventrical on 2014-04-25
Works beautiful here... new themes and icons too..

---

### Post by cariboo on 2014-04-25
Seeing as the work on Utopic has started, there is no need for this thread. Closed.

---

