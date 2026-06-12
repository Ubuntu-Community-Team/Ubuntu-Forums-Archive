---
title: "Devede deinterlace options help"
date: 2009-01-06
forum: Ubuntu Studio
---

### Post by japtar10101 on 2009-01-06
I can't find that much information on deinterlacing with Devede, even with Google's help.  What do each of these options mean, and for the USA (NTSC), which option is the best?

[LIST=1]
[*]Linear Blend
[*]Median filter
[*]FFmpeg filter
[*]LowPass5 filter
[*]Yadif filter
[/LIST]

---

### Post by chronos00 on 2009-02-01
I have been reading some technical information about different de-interlacing algorithms, but couldn't arrive to any conclusion for DeVeDe.
By trial and error, I found out that YADIF de-interlacing algorithm is very superior to the rest; and if it means anything, I read that YADIF algorithm was the last to be added to DeVeDe.
I tested de-interlacing with a film that looked HORRIBLE without de-interlacing and worked out pretty well.

I see your post is 3 weeks old. Did you arrive to any conclussion?

---

### Post by ubunlilluz on 2009-07-15
it'd be interesting for me too this information.
Nobody know?
thanks

---

### Post by vinan on 2010-07-11
Heads up for  chronos00
[COLOR=SeaGreen]
[/COLOR]  [COLOR=SeaGreen]YADIF de-interlacing algorithm [/COLOR]did the smoothest picture, i ever could deam of. 


Thanks  for sharing u r knowledge 
M8 :p

---

### Post by ricardisimo on 2011-03-08
Thanks. I was wondering this as well. I've been using FFMpeg, for no particular reason other than familiarity with the term ffmpeg... how dumb is that. I'll try YADIF and report back as well.

---

### Post by ricardisimo on 2011-03-10
_*Very*_ nice. I'm sold. Thanks again.

---

### Post by ricardisimo on 2011-03-15
Hmmm... There's one problem that simply will not go away, and I'm starting to think it's devede that's the problem. Whenever there is a fade-to-black (as with commercials in television programs) the audio breaks up and goes dramatically out of synch with the image. This corrects itself within a minute or less, but it is, as I'm sure you can imagine, thoroughly annoying.

I'm noticing the problem mostly when attempting to render disc images for dual-layer DVDs. When I create an image for a 4.7G disc, it seems to be fine most of the time if not always. Has no one else experienced these problems?

---

