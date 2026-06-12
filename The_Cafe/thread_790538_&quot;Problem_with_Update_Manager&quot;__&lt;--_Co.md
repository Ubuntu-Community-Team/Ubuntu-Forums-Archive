---
title: "&quot;Problem with Update Manager&quot;  &lt;-- Common problem.  Why?"
date: 2008-05-11
forum: The Cafe
---

### Post by diablo75 on 2008-05-11
I'm betting this has been something that's been a problem for many users for a while now:  A user will go to run their Update Manager, but it fails to download all the files it needs due to some server being unavailable or overloaded.  The best fix that I know, which I've repeated to newbies a few too many times lately, is to ask them to open their Software Sources and select a different server or to have it select one for them based upon ping time (which sometimes is not the best metric to measure by, especially for high latency connections like dial-up).  I've gotten great pings in the past from servers that had very poor upload capability before...

Can't this whole process be automated somehow so the user doesn't have to ever worry about this?  Can't update manager be made "smarter" so when it gets a 404 error, or FTP/HTTP server unavailable error or whatever when requesting a file, to try and download the same file from a mirror on the fly?  Can't there be a centralized status server setup simply to monitor the workload status of the rest of the repository servers and act as an auto-redirect for update manager?  I think it would make more sense if you expanded update manager so you can see the files as they're coming down, and watch one snag because a server isn't responsive, for it to perk up and say, "Download failed: Auto-attempting X mirror server.  Success!  Proceeding to next file."

If I were to rephrase this in one sentence, it would be, "Get rid of the Software Sources menu."

---

### Post by Joeb454 on 2008-05-11
I think a lot of this has to do with the CD being enabled as a software source. It's an easy fix, just go to System > Administration > Software Sources and disable the CD as a source

---

### Post by diablo75 on 2008-05-11
> **Joeb454 said:**
> I think a lot of this has to do with the CD being enabled as a software source. It's an easy fix, just go to System > Administration > Software Sources and disable the CD as a source

You've missed my point.  Nobody should be required to change their software sources manually.  Most new users don't even understand what "Software Sources" is for, nor wish to be troubled with having to do something that a simple daemon should be able to do for them automatically.  It is an unnecessary inconvenience to new and avid users alike.

---

### Post by Joeb454 on 2008-05-11
No I fully understand your point, however it was never enabled when I installed. So perhaps it's a bug?

---

### Post by diablo75 on 2008-05-11
> **Joeb454 said:**
>  however it was never enabled when I installed.

What are you referring to by "it"?  Use of the CD?  Again, it shouldn't matter.  If the computer tries a source of any type, and that source fails, it shouldn't come back with an error message  that confuses the user.  It should try any number of alternates automatically.

Edit:  I've gone ahead and posted this on Brainstorm.  Vote for it if you think it makes sense.  If it doesn't, I'd be glad to learn why it wouldn't work.

[http://brainstorm.ubuntu.com/idea/8376/](http://brainstorm.ubuntu.com/idea/8376/)

---

