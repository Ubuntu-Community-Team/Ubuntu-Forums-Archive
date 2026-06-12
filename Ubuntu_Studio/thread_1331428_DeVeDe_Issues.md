---
title: "DeVeDe Issues"
date: 2009-11-19
forum: Ubuntu Studio
---

### Post by jplunday on 2009-11-19
I've been using DeVeDe for about 2 years now and it works great. I've used it in Ubuntu 8.10 and 9.04 but when I upgraded to Ubuntu 9.10 I can't get DeVeDe to accept any of my video files.

I keep getting the error: Some files weren't video files. - None added.


I've installed every codec and video editing library I can find but none of that seemed to help.

Is there some kind of error log that I can research to see what the actual error is coming from DeVeDe?

Is anyone else having issues with DeVeDe?

I appreciate any help on finding out my issue, thanks.

---

### Post by jplunday on 2010-03-10
I finally found the issue. 

Apparently, Karmic version of MPlayer has a new configuration setting called SRATE (Streaming Rate) which defaults to 480000. 

I don't know if my hardware doesn't like that setting or what but I commented it out in the mplayer.conf file and Devede now works as it did before I upgraded to Karmic.

---

