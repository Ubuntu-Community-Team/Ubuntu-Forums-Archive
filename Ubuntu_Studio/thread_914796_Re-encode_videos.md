---
title: "Re-encode videos"
date: 2008-09-09
forum: Ubuntu Studio
---

### Post by darkhammer8108 on 2008-09-09
hello. i just set up a mythtv box and found that the recordings take about 5.4gigs a piece for a movie. when i transcode these videos into the mpeg4 format they still seem to take up a lot of space (even without commercials). is there a program for linux that can re-encode videos into a better format such as divx or something else that will get the size below 1GB of space while still keeping some of the quality?

---

### Post by tamoneya on 2008-09-09
yeah but it is more a question of the codec and parameters used not just the program.  I use mencoder and I like the guide on the gentoo wiki.

[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

I typically use the xvid two pass encoding with mp3lame VBR.

---

### Post by aeiah on 2008-09-09
xvid two pass is probably good enough, but the best size vs quality is x264. its more complicated and takes longer to encode, but if you have HD content its the way to go. if not, then xvid will probably be more convenient.

---

### Post by darkhammer8108 on 2008-09-09
> **aeiah said:**
> xvid two pass is probably good enough, but the best size vs quality is x264. its more complicated and takes longer to encode, but if you have HD content its the way to go. if not, then xvid will probably be more convenient.

im going to try xvid 2-pass since its just standard television. ill report back with how that goes.

---

### Post by darkhammer8108 on 2008-09-09
i tried it with xvid and i had MAJOR audio and video syncing issues. half way through the movie there was approximatly a 30 minute difference in in the place for the audio video track.
EDIT: i didnt use VBR so im trying that over night. ill get back about it in the morning.

---

### Post by darkhammer8108 on 2008-09-10
just tried with vbr and its about 1/2 a second delay throughout the hole movie. a lot better than when i didnt use vbr but still looks lousy.

---

