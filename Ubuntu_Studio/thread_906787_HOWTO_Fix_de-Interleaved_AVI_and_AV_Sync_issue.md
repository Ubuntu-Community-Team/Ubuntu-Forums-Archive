---
title: "HOWTO: Fix de-Interleaved AVI and A/V Sync issue"
date: 2008-08-31
forum: Ubuntu Studio
---

### Post by ish4269 on 2008-08-31
This is an anecdotal HOW TO:, i.e. it worked for me but it may not work for you.

In my travels I have come across many AVI files of full length feature films ;). Some have been of reasonable some have not, for example there was one which when played with mplayer worked with no A/V problems, but when played with a stand alone DivX/DVD player didn't (no sound). Further investigation, using mplayer in the command line, found the AVI wasn't interleaved so the sound channel wasn't recognised when played on a stand alone DVD player.

Initial Solution:
```
mencoder -idx AVI_BROKEN.avi -ovc copy -oac copy -o AVI_fix.avi
```

However, in my case this made the A/V go out of sync 

and using
```
avisync -i AVI_fix.avi -o AVI_fix_sync.avi -n <+/-audio_shift>
``` 
always seem to make A/V syncing worse or destroy the indexing and/or interleaving of the file.

I then tried just avisync-ing the original AVI_BROKEN.avi deinterleaved file which did not have syncing issues with zero audio shifting:

```
avisync -i AVI_BROKEN.avi -o AVI_fix_sync.avi -n 0
```

This worked, avisync rebuilt the avi file as a proper interleaved AVI with no A/V sync issues.

If this thread works for you, don't forget to click on the thanks button :)

---

