---
title: "ffmpeg quality worse with hardy?"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by finite9 on 2008-06-01
I use mencoder to encode home videos.  I made a custom script when feisty fawn was released to encode to xvid/mp3/avi (using ffmpeg ovc).

I was pleased with the quality at bitrate 1200.

Now when I upgrade to hardy and try to encode, the quality is much much worse using the same script.  If I change the ovc to xvid, the quality is very good.  Seems like something has changed in ffmpeg.  Is this a known issue?  I would stick with xvid if it wasnt for the fact that it does not save the aspect bit, which is why i chose ffmpeg.

I am using the version of mencoder/ffmpeg from medibuntu repository.  I will try with standard hardy versions this week to see if this makes any difference (probably not but you never know).

Otherwise maybe I should just download mencoder/ffmpeg and compile them myself.  I think that when I tested this with Feisty, I was using RAOFs repository for cvs versions of x264/ffmpeg/mencoder.  Maybe there were changes in his versions that made output better, but his repository does not seem to exist any more.

update:

quality does seem worse after extensive testing.  I swapped back to xvidencopts and the quality is good again (same birate etc). I heard that I can use autoaspect even with xvid ovc but unfortunately, xvid in Hardy Heron does not support threads=>1 so I cannot fully utilise my dual core cpu, but this is an acceptable trade-off for the good quality.

---

