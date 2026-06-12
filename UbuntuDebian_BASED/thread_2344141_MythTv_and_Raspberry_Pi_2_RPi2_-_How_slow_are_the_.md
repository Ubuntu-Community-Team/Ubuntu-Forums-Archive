---
title: "MythTv and Raspberry Pi 2 RPi2 - How slow are the menus?"
date: 2016-11-22
forum: Ubuntu/Debian BASED
---

### Post by krisbee2000 on 2016-11-22
I downloaded Raspbian Jessie and installed the MythTV Light packages - but it has been unusable due to the slowness - not the video... everything.  All menus take many seconds to page through.  So, just to get to the recordings page can take 20-30 seconds.  Press play and everything just grinds to a halt... 

I have installed the MPEG2 decode license key, bumped up the GPU to 256mb, Overclocked to High... Using OpenMax and ALSA... am I doing something wrong?  Is there something I just don't get? 

I assume most RPi users have a usable interface... The only thing I haven't tried is using a different SD card, but I copied one to another and will try tomorrow to see if that is the real bottleneck.

Bootup to the GUI is about 60 seconds, which I think is typical.  20 seconds or so to actually load the frontend program as well.

Thank you in advance for letting me know your experience... I'd much rather have a RPi as my frontend and leave on all the time (and have a second as a spare) than get another computer (though I do have an Nvidia Ion ready to go, it just isn't out of the box yet.)  I'm actively looking so I can replace my older frontend which I have revived from the dead one too many times (a dc 7100).

---

### Post by howefield on 2016-11-23
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by kellymartinv on 2016-12-27
> **krisbee2000 said:**
> it has been unusable due to the slowness - not the video... everything. 

I just set up a raspberry pi 3 with mythtv frontend as well, and it drags.  I can’t even navigate, it’s so slow. Did you find switching the SD card helped? Mine’s a class 6, but it performs great in my DSLR including for video so I figured it would perform okay for the RPi.

---

### Post by krisbee2000 on 2017-01-01
I found out that I had made a huge mistake - I was using a RPi1B, and not a 3.  Once I got a 3, the menus worked just fine.  However, using the mythtv-light packages I noticed a visual flaw that the developers of mythtv are aware of - there is a jerkiness on motion when watching mpeg2 - It isn't noticeable by everybody, but I did, especially since I have a 60 inch TV... Usually backgrounds during pans would hitch one out of 30 frames, but if there was something in the center of the frame, that wouldn't have an issue.  Kodi does not have this problem, but skipping forward or back is slow on Kodi with the mythtv plugin.  In the end I ended up buying a Jetway Nvidia Ion which has a flawless picture and is a small frontend computer that didn't cost too much.

---

