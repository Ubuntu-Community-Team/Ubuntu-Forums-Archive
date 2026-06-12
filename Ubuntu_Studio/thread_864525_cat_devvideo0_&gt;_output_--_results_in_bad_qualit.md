---
title: "cat /dev/video0 &gt; output -- results in bad quality"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by arsenic23 on 2008-07-19
I have a PVR capture card that works with the ivtv drivers and I noticed something odd today.  If I just play the video stream off of it the quality of high motion scenes is pretty good.  
I normally use the following:
```
mplayer -vf pp=lb /dev/video0 -ni
```

Now if I just **cat /dev/video0 > output.mpg**, I get poor quality on high motion scenes.  It looks like every other line of pixels is out of sync.

Is there any way to take care of this or run the stream through mplayer first ?

---

### Post by Dee2 on 2008-07-20
Sounds like it's interlaced, try and activate deinterlace filter for playback, (in xine you press 'i').

Probably someone can give you a oneliner that runs it through mencoder with a deintercae filter activated. 

I'd like to see that too :-)

Cheers

---

