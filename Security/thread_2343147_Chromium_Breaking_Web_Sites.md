---
title: "Chromium Breaking Web Sites"
date: 2016-11-13
forum: Security
---

### Post by MarkMatis on 2016-11-13
Ubuntu 14.04.4

Chromium has started announcing "Your connection is not private" for web sites like [www.wunderground.com]("http://www.wunderground.com") and [www.lowes.com]("http://www.lowes.com")  Even when I click "Proceed to [www.lowes.com]("http://www.lowes.com") (unsafe)", the browser refuses to load the page as designed.  Is there any alternative to make Chromium work on these sites?  Or do I need to drop Chromium and find another browser that actually works?

---

### Post by kpatz on 2016-11-13
I don't have a solution, but I'm having the same issue with Yahoo! Mail on Chromium in 16.04.  Chrome on Windows is working fine, as well as Firefox in 16.04.

---

### Post by untrustytahr on 2016-11-14
It's a bug in version 53.

[https://knowledge.symantec.com/support/ssl-certificates-support/index?page=content&id=ALERT2160](https://knowledge.symantec.com/support/ssl-certificates-support/index?page=content&id=ALERT2160)[URL="https://knowledge.symantec.com/support/ssl-certificates-support/index?page=content&id=ALERT2160"]

[/URL][URL="https://bugs.chromium.org/p/chromium/issues/detail?id=664177"]https://bugs.chromium.org/p/chromium/issues/detail?id=664177
[/URL]
Easiest thing to do is use a different browser temporarily.  Alternatively, you could downgrade chromium, but you'll probably cause more dependency headaches than it's worth.

---

### Post by MarkMatis on 2016-11-14
Thanks for the info!  I have installed QupZilla and will use that until Chromium fixes their issues, at which time I'll note that this issue is "solved".

---

### Post by MarkMatis on 2016-11-15
Ubuntu software just updated, and included Chromium update.  Now seems to work with those web sites that had previously been problems.  Current build is [COLOR=#303942][FONT=Ubuntu]53.0.2785.143.  I concur that this issue is "Solved".  Is there a way for me to mark it as such?[/FONT][/COLOR]

---

### Post by asomad on 2016-11-15
> **MarkMatis said:**
> Ubuntu software just updated, and included Chromium update.  Now seems to work with those web sites that had previously been problems.  Current build is [COLOR=#303942][FONT=Ubuntu]53.0.2785.143.  I concur that this issue is "Solved".  Is there a way for me to mark it as such?[/FONT][/COLOR]

Hello. Are you *sure* it's fixed? 53.0.2785.143 is the affected version, and while a fix has been committed as far as I can tell it has not been pushed down into the main repository yet..

---

### Post by vasa1 on 2016-11-15
> **MarkMatis said:**
> ... Is there a way for me to mark it as such?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by MarkMatis on 2016-11-15
Before I left home today, Ubuntu offered an update that included a new package of Chromium with that version number.  I tried it and was able to successfully access sites that had previously been a problem.  I am now down here at a friends' home, updated their software, but Chromium does NOT access sites properly, so the fix is NOT in.  Not sure why it works on my computer at home with that version, but not on this computer with the same version and the same Ubuntu release (14.04.4, since 16.4 does not yet have updated AMD drivers).  I did note that the software update down here did NOT push a new Chromium package...

NOT SOLVED.

---

### Post by Bryan55 on 2016-11-16
I'm on [COLOR=#303942][FONT=Ubuntu]Version 53.0.2785.143 Built on Ubuntu , running on Ubuntu 14.04 (64-bit) and still have problems.

SO NOT SOLVED.[/FONT][/COLOR]

---

### Post by PaulW2U on 2016-11-16
Here's the Launchpad bug report - [https://bugs.launchpad.net/ubuntu/+bug/1641380](https://bugs.launchpad.net/ubuntu/+bug/1641380) - for anyone wanting to keep track of Ubuntu's progress on this.

As at the time of posting a fix has **not** yet been released although the issue **is** being worked on.

---

### Post by Bryan55 on 2016-11-16
Update just came through and it works.

---

### Post by kpatz on 2016-11-16
Just ran updates and I can check my Yahoo mail in Ubuntu again.  Fixed!

---

### Post by firefox_user2 on 2016-11-16
Mine is fixed too as of the latest Chromium update a few minutes ago. I've been trying to figure out what went wrong for days now but all seems good. Thanks to whomever.

---

### Post by MarkMatis on 2016-11-17
This computer at my friends' home is now fixed as well, although the Chromium version still shows as "[COLOR=#303942][FONT=Ubuntu]Version 53.0.2785.143 Built on Ubuntu , running on Ubuntu 14.04 (64-bit)[/FONT][/COLOR]".  I'll wait until I get back home to verify it hasn't broken again, and if it's still working on Friday afternoon, I'll mark this as "Solved" per the info provided earlier.  Thanks to all for your help!

---

### Post by LifeEnemy on 2016-11-17
I've had the same problem on 14.04 with Amazon.com and nytimes.com (this one loaded, it just showed a bunch of plain text and broken links).

The most recent update to chromium seems to have solved the issue though, after restarting the browser. :)

---

### Post by MarkMatis on 2016-11-18
Chromium still seems to work properly on my home computer as well, so I consider this issue solved.  Thanks to all who fixed it so quickly!

---

### Post by dwpbike on 2017-08-12
problem still exists - option to "try later" still comes up in yahoo mail, but no longer works.  ubuntu 16.04 lts, all updates installed.

---

