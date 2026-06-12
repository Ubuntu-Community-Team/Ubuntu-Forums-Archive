---
title: "[SOLVED] NX's excessive session log"
date: 2007-11-23
forum: Server Platforms
---

### Post by aboutblank on 2007-11-23
The "session" log file for the current NX session is flooded with a line saying

> nxagentDispatchEvents: Requested ConfigureNotify changes didn't take place.

That error is written to the log file hundreds of times every time a window is moved until the log reaches the maximum size and the session is terminated. I need to somehow stop this from being written to the log.

Under /usr/NX/etc/node.cfg and server.cfg, I have adjusted the SessionLogLevel variable to be 0 but with no success. 

The ConfigureNotify event seems to be activated when a windows size or placement changes. 

Any ideas on where the bug comes from or how to stop it from being logged would be awesome. Thanks!

============================================================================================
Edit: There is a fix...

[Trouble Report]("http://www.nomachine.com/tr/view.php?id=TR01F01982")

Workaround 2

As an alternative, set the SessionLogLimit key to 0 in the NX Node configuration file (i.e. /usr/NX/etc/node.cfg) to avoid the session closure.

---

### Post by exactopposite on 2007-11-25
i'm having the exact same problem, so i'll bring this back to the top since it's been a couple of days.

---

### Post by ombreduz on 2007-12-25
same thing here. Quite painful indeed. Did someone found a solution in the meanwhile?

---

### Post by mvyver on 2008-01-07
Hi,
I experience the same problem with 2 opensuse 10.2 machines - so it seems it is not limited to Ubuntu :)
I have two other opensuse 10.2 machines where I don't see this problem....

the main difference where I see this problem is that the client machine has compiz activated.

Do any of the above posters have or not have compiz/Beryl enabled?

HTH?

---

### Post by mvyver on 2008-01-10
Hi,
I pointed out to !M that there might be a problem, they were kind enough to suggest something:

> thank you for bringing this to our attention.

Our developers have queued this up for investigation and will evaluate
whether its necessary to open a Trouble Report.

In the meantime, you should do the following:

- in nxagent OSS avaiable from the NoMachine website, change  #ifdef WARNING
to  #ifdef DEBUG. This should stop the session files being flooded.

- recompile this modified nxagent. See here for more information on how
to do this:
[http://www.nomachine.com/documents/technology/building-components-3.1.0.php](http://www.nomachine.com/documents/technology/building-components-3.1.0.php).


We take this opportunity to thank you for your interest.


HTH?

---

### Post by aboutblank on 2008-01-12
> **mvyver said:**
> Hi,
I experience the same problem with 2 opensuse 10.2 machines - so it seems it is not limited to Ubuntu :)
I have two other opensuse 10.2 machines where I don't see this problem....

the main difference where I see this problem is that the client machine has compiz activated.

Do any of the above posters have or not have compiz/Beryl enabled?

HTH?

Good call! Yes, my client has compiz enabled.

Disabling compiz on the client machine does not cause the session log to grow. Can someone confirm this is the source of the problem? I'm going to try and figure out how to disable compiz for that window.

---

### Post by mvyver on 2008-01-12
That's enough confirmation for me :)

---

### Post by mvyver on 2008-01-12
> **aboutblank said:**
> Good call! Yes, my client has compiz enabled.

Disabling compiz on the client machine does not cause the session log to grow. Can someone confirm this is the source of the problem? I'm going to try and figure out how to disable compiz for that window.
It seems Compiz does not yet have application specific settings.
Nonethless, the posts in this thread may help you?

[http://ubuntuforums.org/archive/index.php/t-588497.html](http://ubuntuforums.org/archive/index.php/t-588497.html)

---

### Post by fordboy0 on 2008-01-16
Just as an FYI.  NoMachine has opened up a Trouble Report on this issue.  It can be accessed [HERE]("http://ubuntuforums.org/showthread.php?p=4094202#post4094202")

If you are not into re-building part of the NX software, I suggest making the SessionLogLimit=0 (workaround #2) change noted at the bottom of the TR.

-Jeff

---

### Post by aboutblank on 2008-01-24
[Trouble Report]("http://www.nomachine.com/tr/view.php?id=TR01F01982")

Workaround 2

As an alternative, set the SessionLogLimit  key to 0 in the NX Node configuration file (i.e. /usr/NX/etc/node.cfg) to avoid the session closure.

---

