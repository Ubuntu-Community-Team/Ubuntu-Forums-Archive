---
title: "Meerkat Ion NetTop 1080p H.264?"
date: 2012-06-14
forum: System76 Support
---

### Post by Tristan Schmelcher on 2012-06-14
Can the Meerkat Ion NetTop play 1080p H.264 content in VLC and Flash with Ubuntu 12.04? Clearly the Atom CPU cannot handle it, but I wonder if the acceleration from the NVIDIA graphics can. I found an old thread ([http://ubuntuforums.org/showthread.php?t=1316849](http://ubuntuforums.org/showthread.php?t=1316849)) where the consensus was that it can't be done, but that was 2.5+ years ago when VDPAU was in its infancy.

System76 guys: In your latest tests, does 1080p content play smoothly on the Meerkat?

---

### Post by isantop on 2012-06-14
> **Tristan Schmelcher said:**
> Can the Meerkat Ion NetTop play 1080p H.264 content in VLC and Flash with Ubuntu 12.04? Clearly the Atom CPU cannot handle it, but I wonder if the acceleration from the NVIDIA graphics can. I found an old thread ([http://ubuntuforums.org/showthread.php?t=1316849](http://ubuntuforums.org/showthread.php?t=1316849)) where the consensus was that it can't be done, but that was 2.5+ years ago when VDPAU was in its infancy.

System76 guys: In your latest tests, does 1080p content play smoothly on the Meerkat?

We know it'll handle it really well if the player is a local application (or really anything not-flash based). If it is flash, then you have to suffer through its built-in "Hardware Acceleration" feature, which I've never had good results with personally. 

Local video, though, looks great.

---

### Post by krismatth3 on 2012-06-17
> **Tristan Schmelcher said:**
> 
System76 guys: In your latest tests, does 1080p content play smoothly on the Meerkat?

The real question is: can your sound system overcome the rocket engine fan that the meerkat contains?

---

### Post by Tristan Schmelcher on 2012-06-19
Thanks isantop. I did some more research and it turns out that Flash's VDPAU integration is only used for Flash apps that use its Stage Video API, and only a handful of apps do. Notably, Hulu does *not*, and that's one of the things I wanted to use a Meerkat for. So I will go with a more powerful machine instead.

---

### Post by isantop on 2012-06-19
> **Tristan Schmelcher said:**
> Thanks isantop. I did some more research and it turns out that Flash's VDPAU integration is only used for Flash apps that use its Stage Video API, and only a handful of apps do. Notably, Hulu does *not*, and that's one of the things I wanted to use a Meerkat for. So I will go with a more powerful machine instead.

The Ratel is an excellent machine, and it's HD 4000 graphics (in the base configuration) are easily powerful enough for video and light 3D.

---

### Post by jacobroecker on 2012-08-06
I'm loving my new Meerkat Ion NetTop, but have been having frames skip when watching 720p video.  What am I missing?

I'm using VLC the video is:
Codec: H264 - MPEG-4 AVC (part 10) (avc1)

I've tried both of the "Additional Drivers" and am currently using the NVIDIA accelerated graphics driver (post-release updates)(version current-updates) as this one has the least amount of frames being dropped.

I did have to reinstall ubuntu 12.04 from scratch and my internet is only 15K, so I have no idea if the system76 "driver" app is even working to get whatever other drivers I might be missing (there's no download status--or any measurable way to see what/if it's doing anything).

I'm connected to my 1920x1080 monitor via a VGA cable if that helps to resolve the issue.  Any ideas why I'm dropping frames?

---

### Post by Ubun2to on 2012-08-06
> **jacobroecker said:**
> I'm connected to my 1920x1080 monitor via a VGA cable if that helps to resolve the issue.  Any ideas why I'm dropping frames?
1920*1080 and you are using VGA? VGA begins to degrade in quality once you go over 1280x1024. You need either DVI, HDMI, or DisplayPort.

---

### Post by jacobroecker on 2012-08-06
> **Ubun2to said:**
> 1920*1080 and you are using VGA? VGA begins to degrade in quality once you go over 1280x1024. You need either DVI, HDMI, or DisplayPort.

Downgrade it may, but does that mean I should have skipped frames?

---

### Post by isantop on 2012-08-06
> **jacobroecker said:**
> Downgrade it may, but does that mean I should have skipped frames?

No, It will become fuzzier and less clear the higher you go. Since it's analog, you won't skip frames, but the display response will degrade and EM interference will affect clarity.

---

### Post by jacobroecker on 2012-08-06
> **isantop said:**
> No, It will become fuzzier and less clear the higher you go. Since it's analog, you won't skip frames, but the display response will degrade and EM interference will affect clarity.

OK, I've upgraded to DVI and yes it looks clearer.  Thank you for that advice.  

Still wondering what I should be doing to get it so it doesn't skip frames though.  Quite frustrating.

---

### Post by isantop on 2012-08-06
> **jacobroecker said:**
> OK, I've upgraded to DVI and yes it looks clearer.  Thank you for that advice.  

Still wondering what I should be doing to get it so it doesn't skip frames though.  Quite frustrating.

Are you playing a local video file, or something from YouTube, Hulu, etc.?

---

### Post by Tristan Schmelcher on 2012-08-06
You may not have hardware accelerated decoding enabled. It is somewhere in the VLC options.

---

### Post by jacobroecker on 2012-08-06
Yes to local file. (.mp4 on USB 3.0 HDD)

Yes to hardware acceleration.  I had figured the problem wasn't VLC as I had experienced the same thing with Movie Player.

---

### Post by isantop on 2012-08-07
Does it change if you disable hardware acceleration? Also, what graphics driver do you have installed?

---

### Post by jacobroecker on 2012-08-07
I've done some more digging on the problem.  First, there was a driver update when I used the update manager this morning and the new driver seems to work fine.

Second I've gone back through other files in my library and they're all playing considerably better than what they did at first.  Now if it is skipping frames I can't tell.

No more frustration with the Meerkat on this end.  Happy to recommend it for what it's got, it's size, and general awesomeness.

Thank you all for helping me work through this.  Glad to have the community support!

---

