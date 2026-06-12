---
title: "dvdauthor error - won't properly create VIDEO_TS.IFO"
date: 2010-01-04
forum: Ubuntu Studio
---

### Post by qyot27 on 2010-01-04
I've been trying to put together a DVD lately, and wanted to do so using dvdauthor.  I have all my files ready, I have the XML file ready, dvdauthor runs through the process seemingly without a hitch, creating all the VTS files and so on, but when it comes time to scan the VTS files and create VIDEO_TS.IFO to pull it all together, it goes down in flames and creates an empty VIDEO_TS.IFO instead of one that has all the data it needs to.  It also spits out this error:
```
dvdauthor: dvdifo.c:537: TocGen: Assertion `i<=128' failed.
Aborted
```
Running the same version of dvdauthor under Windows XP netted this, if it helps:
```
assertion "i<=128" failed: file "dvdifo.c", line 537
    384 [sig] dvdauthor 1816 open_stackdumpfile: Dumping stack trace to dvdauthor.exe.stackdump
 229524 [sig] dvdauthor 1816 C:\Program Files\DVDAuthorGUI\bin\dvdauthor.exe: *** fatal error - called with threadlist_ix -1
```
In 0.6.17 and the 0.6.14 variant that comes with DVD Flick, the error is essentially the same, the wording is simply different (something about the application requesting the Runtime to terminate it in an unusual way).

I'm not sure where the cutoff is, either.  If I give it ten files, it completes without error.  If I give it 25, 50, or the full 70 I wanted in the first place, it exits with that error.  I don't get it.

Any ideas?

---

