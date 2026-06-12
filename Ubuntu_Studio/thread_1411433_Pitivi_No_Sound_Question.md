---
title: "Pitivi No Sound Question"
date: 2010-02-19
forum: Ubuntu Studio
---

### Post by hfw on 2010-02-19
I tried Pitivi for the first time today and had an issue.  I imported a long video with sound, and an mp3.  I split the sound out of the video track and deleted it.  Then I broke the video into pieces and the mp3 into pieces to get certain action to line up with certain sounds.  All told a little more than an hours worth of video.  Then I rendered the video using the default setting, other than changing the video size to match the source file.  When I play the file it generated I get sound for a minute or two, and then I don't have any sound.  About 10 minutes into the video I get another 30 seconds of sound, and then it goes quiet for the remainder of the video.  When I play the project file in Pitivi it plays fine.  Sound all the way through.

I am running Ubuntu 9.10 with the repo version of Pitivi.  I did try the developer PPA, but it would not work with the video file because it was too large, so I used ppa-purge to remove the developer ppa.

Thanks,

hal

---

### Post by kiddo on 2010-02-20
Have you tried the gstreamer dev PPA in combination with pitivi git? There's also a PPA for it: [http://rowinggolfer.blogspot.com/2010/02/pitivi.html](http://rowinggolfer.blogspot.com/2010/02/pitivi.html)

Did you use still images in that timeline?
Does the sound always cut off at the same points?

If you tried the gstreamer PPA + the pitivi git PPA and still have this problem, file a bug. See [http://www.pitivi.org/?go=bugs](http://www.pitivi.org/?go=bugs)

---

### Post by hfw on 2010-02-21
I had not tried the ppa for pitivi git.  Am upgrading now.  The pitivi.org site actually only shows the gstreamer ppa as a source for the newest pitivi.  

There are no still images, just the one video file and one audio file.  Probably should have a still image for the gaps in the video, but I was going to survive with just a black screen.

Sounds seems to go away at the same point every time I play it.  I did not render more than once.

-hal

---

