---
title: "Devede size errors"
date: 2009-08-14
forum: Ubuntu Studio
---

### Post by seanlano on 2009-08-14
I have been using Devede for a while, and I love it. However, I've noticed that since I upgraded to Jaunty from Intrepid, I have lost control over the size of the resulting .iso image. No matter what quality setting (i.e. bitrate) I select, the .iso is always the same size (when using the same source). 

For example, I used Kaffeine to record a movie from my DVB card, and ProjectX to cut it to size. The .m2p file is 3.7GB. I go through Devede and I end up with an .iso that is 4.9GB, too big for a single-layer DVD. No matter what bitrate I specify, it is always 4.9GB. Devede says that it should only be about 3GB. 

I think it might be a problem with the back-end (Mencoder, I think), I have noticed that when I rip a CD to .mp3 using Rhythmbox the bitrate is "stuck" at 128kbps, no matter what I specify (but I normally use FLAC, so this doesn't bother me). 

I suspect that this problem is similar, the bitrate setting is "stuck" at a certain level, but I don't know how to fix it. 



Any ideas?

---

### Post by jtslau on 2009-08-15
Never had that problem like that with DeVeDe before, but then of course I could never get DeVeDe to work with Jaunty.  I am still with Intrepid because of that.

Obviously a "stupid" question to ask, but, is there any change you forgot to select "4.7 Single Layer DVD".  Just checking...

Note also, if I remembered correctly, you can go into the Properties of each video in DeVeDe and adjust the quality of the video accordingly, thereby reducing/increase the size of your encode to your specifications.

---

### Post by seanlano on 2009-08-15
Yeah, I had the 4.7GB DVD selected. And yes, the bitrate setting in the properties window is the setting that is stuck.

---

### Post by seanlano on 2009-08-20
I'm certain that it's a problem with Mencoder, I've tried it on another Ubuntu Jaunty machine, and got the same problem. I've used another program, tovid GUI, which uses mpg2enc, and it encodes with a proper size. The only problem is that tovid doesn't work properly, so I don't get a DVD at the end. 

What can I do to fix Mencoder?

---

### Post by Lord_ on 2010-01-03
was there every a fix for this?? I'm having a similar, but less significant problem whereby the resulting discs always finish at 3.7Gb. I'm concerned that i could either be fitting more onto a dvd or recording at a higher quality

---

### Post by seanlano on 2010-01-03
I don't think I ever solved this issue. I gave up (sad, I know) and I didn't make the DVD. Now I can't even remember what I was trying to put on DVD. I'll try again with Karmic and see if it is fixed for me. 

I've also experimented with using FFmpeg from the terminal, so I might just give up on the whole GUI thing entirely! But it is really hard to remember all those commands.

---

### Post by jtslau on 2010-03-12
Just to update, this error has been solved with the update to Karmic (and thus the bug is closed on launchpad).

And yes, it is not a problem with Devede itself, but either with the version of mencoder / ffmpeg / non-free-codecs that was packaged with Jaunty.

---

