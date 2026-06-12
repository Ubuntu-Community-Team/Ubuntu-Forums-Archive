---
title: "Lemur webcam recording video is terrible"
date: 2011-04-02
forum: System76 Support
---

### Post by thejambi on 2011-04-02
This is a little frustrating so far. I've had my Lemur for a couple months and this has always been a problem, I believe.

The webcam "works" - But when trying to record a video in Cheese, it doesn't work properly. Here is what happens for a video recorded with Cheese:
- The audio is recorded through the built in mic fine and sounds okay when playing the video file. So this isn't an issue.
- When I begin recording, the webcam feed in Cheese looks choppy - It starts off black and then it shows the image, and in a 30 second video, the image may only change 3 or 4 times. It simply jumps between images. It's no flowing video.
- While viewing the video, the video ends much much sooner than when I had ended the recording.

It seemed to work better when I changed the resolution to the lowest/worst setting. The second highest setting was just as terrible as the highest resolution setting.

How can we fix this? Is this an issue on all Lemur machines? 

This is a big issue that would prevent people from buying this machine.

---

### Post by Ebonwumon on 2011-04-02
I have this same problem, however, I defintely believe that it's software/drivers.

If you use guvcview, the video recording is fine (it's a little laggy at 1024, but 640/480 is fine). However with guvcview the audio is out of sync and that's annoying.

---

### Post by thejambi on 2011-04-03
Thanks for the reply - I'll have to check that out and see how it works for me. It seems like this is an issue for linux in general but hopefully it will be an area that's improved on soon!

---

### Post by HotShotDJ on 2011-04-03
This is a long-standing issue with Cheese -- If I recall correctly, the problem lies in the gstreamer drivers.  Give GUVCView a try (it is in the repositories).  The downside of GUVCView is that it is not as intuitive to use as Cheese.  But the BIG up-side is that it works perfectly (once you get used to it.  Be sure you go to the Audio tab of the program and set sound to "pulse" or your sound and video may be out of sync.  Good luck!

---

### Post by thejambi on 2011-04-03
Fantastic! Changing the sound settings to pulse seems to have fixed the audio/video sync in recording. I don't really use it for recording video a lot but I've known people who got really frustrated with not being able to record video in Ubuntu and it seemed like it was a big turn off for them. I knew there had to be a fix out there. 

Thanks guys.

---

### Post by robbielink on 2011-12-01
This fix worked for me with a Logitech C910 cam. Changing audio setting in GUCView to Pulse and also making sure you're using MPEG2 for the format. It still lagged using MP3 for me.
Thanks for the fix!

---

