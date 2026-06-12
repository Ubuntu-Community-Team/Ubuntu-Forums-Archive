---
title: "AMD R9 290X test results on Vivid"
date: 2015-02-08
forum: Ubuntu Development Version
---

### Post by QIII on 2015-02-08
I got the AMD R9 290X courtesy of Canonical on Thursday.  Been puttering around from Precise through Vivid.

Um.  I'd really love to give a detailed report on all sorts of things wrong.  But I can't.  It works great with the driver available in the repo.  But I really can't comment on gaming performance, since I don't do that much.  TF2 looked pretty great until I got killed about 30 seconds in like always.  But the Phoronix Test Suite GLMark2 test, with all the settings in CCC maxed out and Tear Free enabled, held a steady 60 FPS.  Not bad for *all *the quality setting set to *full-on*.  So I imagine that will make the gamers happy if they tune it a bit for performance.

With the open source driver, not so much.  Performance was terrible.

The one thing I initially thought might be a problem -- a single line of white pixels at the bottom of one of the monitors when Tear Free was enabled -- turned out to be just a matter of "jiggling" the positions of the three monitors in Catalyst to get them aligned perfectly.

One thing to watch out for, as has been going on for me off and on for several releases, is that you don't want to shut down/reboot with Tear Free enabled if you are running multiple monitors.  When it starts up again, a couple of them may not be detected.  To solve that, you have to drop in to root at boot, mount rw, uninstall the driver and reboot with the open source driver.

More details in a nice write-up later for public consumption.  The gist of that will be:  For currently supported releases (except for < 12.04.2) the R9 290X runs great.  If you buy this thing, go ahead and upgrade if you have 12.04 or 12.04.1.

---

