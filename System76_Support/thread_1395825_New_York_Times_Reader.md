---
title: "New York Times Reader"
date: 2010-02-01
forum: System76 Support
---

### Post by bill516 on 2010-02-01
I learned recently that the New York Times Reader has a Linux variant, so I downloaded and installed it.  It appeared to do so properly.  If I click on the desktop icon, it appears to start (spinning disk symbol) but nothing happens.

In the larger forum there are posts from dndrich on Nov. 19 and wilee-nilee on Nov.4 reporting similar experiences.

Has anybody on the System 76 side of the house gotten the Reader to work with 64-bit Karmic?

---

### Post by thomasaaron on 2010-02-01
I get the same thing.

When I try to start the reader from a terminal, it throws this error...
Error loading the runtime (libadobecertstore.so: cannot open shared object file: No such file or directory)

I think the first paragraph here...
[http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04](http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04)
...says it all.

The Times Reader is powered by Adobe Air, and there's no 64-bit version of it available -- only 32-bit.

Looks like it *might* be possible to get it working right on 32-bit by following the instructions on that link.

I'm a little leery of trying the fix though, as it may interfere with 64-bit versions of the necessary libraries. I'll have to dig into it and do some research.

---

### Post by bill516 on 2010-02-01
Thanks Tom.  Appreciate the time you took to look at it.

I can report that it runs nicely on my wife's brand new HP laptop running Windows 7!  So I can sneak over there ....

No, Times Reader is *not* enough reason to run Windows7!

I did not realize the Reader was 32 bit only and I do not want to risk my very solid Ubuntu by trying to force the issue.

I do play with a 32 bit Mandriva, so it might e interesting to see if it works there.

Altogether better if the Times would open it up and let some smart Ubuntu folks fix it!

Bill

---

### Post by marshmallow1304 on 2010-02-02
I've gotten Air to install on 64-bit, but it was a major PITA and the app I wanted it for doesn't work properly anyway; I can't tell if it's a problem with Air or with the app itself.  Unless you really really want it, I'd stay away from Air on 64-bit for the time being.

---

### Post by bill516 on 2010-02-02
Well, marshmellow looks to be right.  The only 32 bit Linux I have running on this machine is a copy of Mandriva 2010-1, so I attempted an installation there.  Much the same result.  Of course the NYT is not in the Linux business, so we can only speculate whether the Linux package being installed is a deb (my guess) or an rpm.  Te Times Reader evidently is programmed to determine what type of operating system it is on and install the proper package, so there is no way to see what it is doing.

If I have a moment I might try it with a 32 bit Ubuntu just to see if that makes a difference.  If and when I do I'll report back.

---

### Post by Derath on 2010-02-02
It sounds a lot like the issue that people were having with Boxee (since there is/was no 64-bit client for it. People did get it to work using getlibs (I think, I'd have to find the original post)... Here we go, here's the link to the forum that steps through using getlibs in order to install a 32bit deb on a 64bit system (although now I notice that they have a 64 bit build).

[http://forum.boxee.tv/showthread.php?t=4980]("http://forum.boxee.tv/showthread.php?t=4980")

---

### Post by bill516 on 2010-02-05
Thanks Derath, that is an interesting link and worth a try when I get a moment.  I'll report back if it works.

---

### Post by Derath on 2010-02-06
Please note, that you'll do those steps for installing Air, I don't know about the Reader, but since Air is causing the issue, do that install for it first then try the Reader...

---

