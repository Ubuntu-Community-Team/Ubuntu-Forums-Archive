---
title: "[SOLVED] really poor A/V sync encoding DVDs with OGMrip/mencoder."
date: 2008-05-21
forum: Ubuntu Studio
---

### Post by r3by on 2008-05-21
The system:
Ubuntu 8.04 64-bit
Celeron D 360 processor
2 GB DDR2 RAM
/, /home partitions on 160GB IDE drive and 
software raid 5 on three 400GB SATA drives
Video: MSI 8600GT video card 
Audio: onboard, Abit mobo

I'm using OGMrip to encode dvd rips on my hard drive and it seems that no matter what settings I encode with or which player I play the encoded videos with the audio is out of sync by at least a few hundred milliseconds, and up to several seconds.  It usually gets worse if I skip forward or ahead in the file.  Videos I have that were encoded elsewhere don't have the same problems, so I think it must have something to do with the encoding process.

Settings I've tried in OGMrip:
I've tried 15 different combinations with X264 and XviD video codecs (2 pass), AC3/copy, MP3 and OGG audio codecs, in avi or ogg containers, with and without the "Ensure A/V synchronisation" box checked, and I've tried playing them back with xine, vlc, and mplayer (including with -autosync, -framedrop, and different video drivers).

Other stuff that might be significant:
The audio is always ahead of the video.
I'm encoding from copies of the dvds (not iso images; the actual directory structure of the dvd is in my filesystem) and copying the files from my RAID array to the main hard drive so that data is being read from and written to the same drive and partition during the encoding process.  I've also tried using 1 and 2 threads during the encoding.

---

### Post by billl on 2008-05-22
Are you encoding a NTSC DVD ? Is it progressive ? Is it telecine ?

---

### Post by aeiah on 2008-05-22
it may be an FPS issue as was alluded to by bill

if your dvds are NTSC and you're converting to a PAL framerate, the audio may not be being converted / stretched.

if this isnt the case, you could always try another ripping tool, like acidrip, and see if the same problem occurs.

---

### Post by r3by on 2008-06-04
yes. Thanks.  There were two problems (both of which I managed to miss in my seemingly exhaustive list details.

1. DVDs made from film or TV wind up in different formats.  mplayer deals with this silently but ogmrip and mplayer have to be told what format it is or it won't work well.  See [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html)

2. The AVI container doesn't like variable bitrates (VBR mp3, or ogg) or variable framerates (Mixed progressive and telecine content, which is particularly common in DVDs of TV series).  I was trying to feed it both at the same time and rather than giving an error, it tried to adjust -- badly.  the MKV container handles that stuff well, and is pretty universally supported in the linux world.

And thanks, Bill, for OgmRip. It is the simplest, most effective encoding program of the 5 I tried.  A way to queue up jobs would make it perfect.

---

### Post by billl on 2008-06-04
I'm gonna release 0.12 by the end of the week and just after that I've planned to add the encoding queue.

Regards,

Olivier

EDIT: autodetection of telecine and/or progressive content is also planned.

---

### Post by pedrogent on 2008-07-30
I agree. OGMRip is an absolutely gold piece of software.

It makes really terrific x264/AAC Matroskas and is so simple to use.

I look forward to monitoring its progress.

Just trying 0.12.1 now...

---

### Post by pureblood on 2008-09-16
Check this thread to understand why the audio is very often ahead of the video for NTSC dvds:
[http://sourceforge.net/forum/forum.php?thread_id=2199019&forum_id=258033](http://sourceforge.net/forum/forum.php?thread_id=2199019&forum_id=258033)

---

