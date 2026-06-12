---
title: "Ubuntu, Netflix, Xfinity, Flash out of sync and players unmotivated to fix"
date: 2014-01-24
forum: Ubuntu, Linux and OS Chat
---

### Post by krainey2106 on 2014-01-24
With Ubuntu 13.10 I lost the brief capability I had to view Netflix.  I viewed various forums with suggestions on Wine, pipelight, flash, etc.  For a couple of hours every week or so, I tried them all and things got really messed up.  I was successful in getting back to zero, some things work some times, but discovered deeper problems as I tried using videos on YouTube, Xfinity, Amazon and other sources.  Flash is out of sync; 11.8.0 is required, but impossible to load, a wide range of error messages, etc.

Content providers still seem unmotivated to reach Linux users.  Any reader of this forum knows that, I am sure, but I am tired of dual booting and Wine is an imperfect answer, especially after distro changes.  Things get out of sync.

Is anything going on with content providers to motivate them to actively work on serving Linux users?  I would gladly pay for an app or buy a subscription to a Linux friendly content provider, anything short of giving up and buying an Apple machine or Windows software.

---

### Post by monkeybrain20122 on 2014-01-24
Youtube doesn't require anything other than flash 11.20, don't know about xfinity, Amazon requires drm so Linux flash won't work regardless of version (Chrome's pepper flash won't work either) Either install hal (from ppa) and it will work on Firefox (hal doesn't work for pepper flash) or install Windows' flash through pipelight, which works great in 13.10. 

I read your post on another thread, I think your problem is OS "upgrade", not any problem with 13.10 per se. upgrade only works when you have a pristine system. If you have ppas,--such as pipelight,--it will break. In general it is unreliable and takes a very long time. I would avoid "upgrade" at all cost, takes only 20-25 minutes to do a fresh install and maybe another 20 minutes to install all your software.

---

