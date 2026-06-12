---
title: "[SOLVED] ToDisc Green Menu"
date: 2008-07-13
forum: Ubuntu Studio
---

### Post by scott_g on 2008-07-13
Hi,

I've been using the todisc gui program to convert .avi files to DVD for a while, without issue.  However, all of a sudden, the video thumbnails on the menus turn out green.  This has happened with various input file types.  I've attached a screenshot of the problem.  Has anyone experienced this before?  Or know how to fix it?

Thanks,
Scott

---

### Post by grepster on 2008-07-17
> **scott_g said:**
> Hi,

I've been using the todisc gui program to convert .avi files to DVD for a while, without issue.  However, all of a sudden, the video thumbnails on the menus turn out green.  This has happened with various input file types.  I've attached a screenshot of the problem.  Has anyone experienced this before?  Or know how to fix it?

Thanks,
Scott
Hard to say.  Green frames are often caused by garbage at the beginning of the video, but the default -seek of 2 seconds should take care of that. Try posting to [http://groups.google.com/group/tovid-users](http://groups.google.com/group/tovid-users) and include the todisc.log.  Or better, go on irc to #tovid (irc.freenode.net) and plan to ask your question and hang around a while as we are not always there.  Evenings or weekends are probably best at the moment.

Does this happen both with the preview AND the final result ?  Does increasing the -seek help ?  What programs have you upgraded in the meanwhile since it stopped working:  ffmpeg ?  transcode ? imagemagick ?

grepster

---

### Post by scott_g on 2008-07-17
> **grepster said:**
> Hard to say.  Green frames are often caused by garbage at the beginning of the video, but the default -seek of 2 seconds should take care of that. Try posting to [http://groups.google.com/group/tovid-users](http://groups.google.com/group/tovid-users) and include the todisc.log.  Or better, go on irc to #tovid (irc.freenode.net) and plan to ask your question and hang around a while as we are not always there.  Evenings or weekends are probably best at the moment.
Log file has been attached to this post in a zip archive.  I have posted to Google Groups, referencing this thread, as I am unsure how to post the log file to that site.

> Does this happen both with the preview AND the final result ?
Preview turns out fine; its just the final results thats green.

> Does increasing the -seek help?
I've set the seek anywhere from 30 seconds to 3 minutes, without any changes.

> What programs have you upgraded in the meanwhile since it stopped working:  ffmpeg ?  transcode ? imagemagick ?
Not entirely sure on this one; whatever has been changed in the Ubuntu repositories.  Didn't notice any one in particular...

Thank you for the reply and advice; it is very much appreciated.
Scott

---

### Post by scott_g on 2008-07-18
Solved by re-installing libquicktime1 as per: [http://groups.google.com/group/tovid-users/browse_frm/thread/ea486680d5dc1165?hl=en](http://groups.google.com/group/tovid-users/browse_frm/thread/ea486680d5dc1165?hl=en)

---

