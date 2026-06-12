---
title: "Suggested application"
date: 2008-08-01
forum: Ubuntu Brainstorm
---

### Post by nosto on 2008-08-01
This could already exist and could already be out there but not implemented.

With all of the forums for users requesting help (ubuntu specific) it would be nice if there was software that would take a snapshot of some crucial information for helping users diagnose the problem.  Ie hardware configuration, drivers in use, ubuntu version and type 32.64 kde or gnome.  Etc etc.  Something that could be generally copied and pasted into posts to help users get the ball rolling either in irc or on the forums.  Any input?

---

### Post by smartboyathome on 2008-08-01
You wanna make that program? Cause it doesn't do much to request someone else make it unless you are willing to pay. If you want it done, start it, and others will come. :)

---

### Post by cszikszoy on 2008-08-02
> **smartboyathome said:**
> You wanna make that program? Cause it doesn't do much to request someone else make it unless you are willing to pay. If you want it done, start it, and others will come. :)

I think if he wanted to do it himself he wouldn't have posted in the Idea Pool forum...

But anyways, KDE sort-of, kind-of has this sort of functionality, with their crash handler.  When an application crashes it pops up with a stack trace and other information relating to the crash of the program.

As for Gnome though - not sure if anything like this exists.  KDE apps are generally much more tightly integrated into the core of the system, so it is easy to determine when an application has crashed.  I'm not sure if Gnome has any way of knowing when an application crashes.

---

### Post by BackwardsDown on 2008-08-03
Yes, it's called apport. It creates a trace of the bug and some memory dumps and asks the user if he wants to create a launcpad bug for it. Uploading the dump and information gets done automatically.

---

### Post by cszikszoy on 2008-08-03
Thats right, but it doesn't seem as though apport is widely used.  The only place I've ever seen it is while using gparted.  I've experienced tons of crashes with nautilus without ever seeing apport.

Perhaps it would be best to further integrate apport into more gnome apps.

---

### Post by BackwardsDown on 2008-08-04
You need to manually enable it by hand in /etc/default/apport (set enabled=0 to enabled=1).

It's not enabled by default because we could not handle all the crash-reports of millions of users, it would make the bug-triaging a living hell.

---

### Post by nosto on 2008-08-04
First of all thanks for noting that I wouldn't have made the suggestion unless I couldn't do it myself.  And the functionality appears to exist however I'm not speaking in reference to memory dumps or log files.  That could be a starting point but it'd be moreso something that can state hardware/operating system details that may help in the more specific forums.

Another thing too is that this forum I thought was for ideas of future releases in the form of a default etc etc.  If this tool could be out there and have a name that makes a little more sense such as "System Snapshot" This could possibley make more sense to a newbie or even a convert from Windows.

Also something graphically friendly and then have a "copy information" so that they can directly post it into the forums here.

That was my overall goal and it might sound like I just rephrased what I said - because thats what I did.  It would be great if someone could just say "What is your System Snapshot output?" and then the user paste that information over to you.

Just my 2 cents.

---

