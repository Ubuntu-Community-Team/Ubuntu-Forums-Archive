---
title: "Cannot Play This Disk"
date: 2009-07-26
forum: Ubuntu Studio
---

### Post by CompBio on 2009-07-26
From looking through the forums I decided that devede would be the best software for creating a DVD from a .AVI movie file.

I followed the instructions and burned the DVD.  It took quite awhile, almost as long as the movie itself, but finally it said it had completed successfully.  I put the DVD into my player and after it tried loading it for about 5 minutes, it gave me the message "Cannot Play This Disk".

Next I tried playing it on my computer and it sees the disk as blank??  Why did devede evidently not write ANYTHING to the DVD in ~1.5 hours of processing??

---

### Post by CompBio on 2009-07-26
Ok, I discovered that devede only seems to construct the .iso file but doesn't burn the DVD.  (??!)  So I used K3B to burn the .iso onto the DVD.

However, now when I try to play the DVD on my computer it says "GstPlayBin: A subtitle stream was detected, but no video stream."

Also, the video player won't play the DVD because it's from the wrong area.

So:

1. Why the heck can I play the .avi in Totem, but not the DVD?

2. How can I tell, before I waste a perfectly good DVD+R, that a .avi file is not from the correct region?

Thanks...!

---

### Post by Stochastic on 2009-07-27
It's not the avi that's from the wrong area, it's the settings on either your player or in Devede that are creating this error.

You could:
1) change the region code on your DVD player to match the disk (can only be changed 5 times EVER).

2) change the settings in Devede to burn to your correct region.

Here's a little more info: 
[http://en.wikipedia.org/wiki/DVD_region](http://en.wikipedia.org/wiki/DVD_region) 
[http://en.wikipedia.org/wiki/NTSC](http://en.wikipedia.org/wiki/NTSC)

Hope that helps.  I also hope you're not doing anything illegal.

---

### Post by CompBio on 2009-07-27
> **Stochastic said:**
> 2) change the settings in Devede to burn to your correct region.

Thanks -- that's the kind of thing I was concerned about.  American hubris, I guess, but I assumed these programs would use region 1 by default.

I don't think I'm doing anything illegal -- I downloaded a video from the internet.  We've already watched it on my computer but would prefer to watch it on the TV rather than huddling around a laptop.  Actually this particular video was little more than a test to make sure I could get the software to work.

My next task is learning how to do a montage of vacation photos with music, but I'll save those questions for another time.  :)

---

### Post by CompBio on 2009-07-27
Everything works fine now.  I found the devede tutorial under a different thread once I found the right thing to search for:

[http://ubuntuforums.org/showthread.php?t=1009684](http://ubuntuforums.org/showthread.php?t=1009684)

---

