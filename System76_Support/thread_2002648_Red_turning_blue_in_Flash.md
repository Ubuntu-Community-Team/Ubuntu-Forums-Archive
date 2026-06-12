---
title: "Red turning blue in Flash"
date: 2012-06-13
forum: System76 Support
---

### Post by mapman88 on 2012-06-13
OK, people in videos on the web are blue, pretty sure they weren't always so, but they definitely are now.

Any thoughts?

---

### Post by BeenLikeFlynn on 2012-06-13
try modding your video input, like java settings or other video settings... i'm new so idk...

---

### Post by howefield on 2012-06-13
Right click on the video, select settings and uncheck the "enable hardware acceleration" option. You'll most likely need to go full screen to do this.

---

### Post by Ubun2to on 2012-06-13
I think I heard something about bad Nvidia drivers somewhere.

---

### Post by isantop on 2012-06-14
> **mapman88 said:**
> OK, people in videos on the web are blue, pretty sure they weren't always so, but they definitely are now.

Any thoughts?

Any specific sites? Can you post a screenshot? Also, what type of graphics hardware do you have? AMD/ATI, Nvidia, or Intel. (alternatively, I can look it up based on your model number).

---

### Post by ahowe42 on 2012-07-24
I've got the same thing on youtube - red & blue seem to be transposed, but not for all videos.  A good example is [http://www.youtube.com/watch?v=BSLPH9d-jsI](http://www.youtube.com/watch?v=BSLPH9d-jsI).  My order # is 21306, and I'm completely updated.

Andrew

---

### Post by Grenage on 2012-07-24
There ised to be a queer glitch where Totem's video setting defaulted to increased Cyan, after an update.  Does that still occur?  Does Totem have plugins for web use?

Worth a check, as it takes 5 seconds.

---

### Post by rbuck01 on 2012-08-06
> **mapman88 said:**
> OK, people in videos on the web are blue, pretty sure they weren't always so, but they definitely are now.

Any thoughts?
If you're talking about YouTube specifically, I read that it's an Adobe Flash problem.

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

---

### Post by SeijiSensei on 2012-08-06
> **Ubun2to said:**
> I think I heard something about bad Nvidia drivers somewhere.

No, it's Adobe's fault.  Somewhere along the way they reversed the red/blue channels when Flash tries to play "Stage Video" streams that use the NVIDIA adapter's H.264 hardware acceleration code.  YouTube uses Stage Video and thus you get "smurfed" people.

As others have said, the fix is to go fullscreen, right-click on the video and choose Settings.  Uncheck the hardware acceleration box.  Then close the browser and open it again.  The problem should be resolved.

This bug was created by Adobe but will never be fixed, since they have discontinued support for Flash on the Linux platform.  Nice of them to leave us with this bug just as they shut down development.

---

### Post by markbl on 2012-08-06
> **SeijiSensei said:**
> 
This bug was created by Adobe but will never be fixed, since they have discontinued support for Flash on the Linux platform.  Nice of them to leave us with this bug just as they shut down development.
It's obscene really. Such an easy issue to fix. I just don't understand the contempt demonstrated by some companies towards linux. We may be small in relative size but there still is a heck of a lot of us linux users. The xorg nvidia driver crash introduced by nvidia 6 months ago (for some older cards) is a similar infuriating issue which nvidia just seem to ignore.

---

### Post by ahowe42 on 2012-08-07
There has to be a better solution for fixing *only youtube videos* than disabling hardware acceleration, which will potentially affect everything that uses the screen...

---

### Post by Scott Harrison on 2012-08-07
I had the same (comical) issue a while back. Here is the fix:

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

---

### Post by isantop on 2012-08-07
> **SeijiSensei said:**
> No, it's Adobe's fault.  Somewhere along the way they reversed the red/blue channels when Flash tries to play "Stage Video" streams that use the NVIDIA adapter's H.264 hardware acceleration code.  YouTube uses Stage Video and thus you get "smurfed" people.

As others have said, the fix is to go fullscreen, right-click on the video and choose Settings.  Uncheck the hardware acceleration box.  Then close the browser and open it again.  The problem should be resolved.

This bug was created by Adobe but will never be fixed, since they have discontinued support for Flash on the Linux platform.  Nice of them to leave us with this bug just as they shut down development.

FYI: Development of flash on Linux has been turned over to Google, so all hope is not lost.

---

### Post by ahowe42 on 2012-08-07
The solution Scott linked to seems to have worked for me.  Thanks!

---

### Post by Ubun2to on 2012-08-08
> **isantop said:**
> FYI: Development of flash on Linux has been turned over to Google, so all hope is not lost.

Hopefully Google will maintain Flash development for browsers besides Chrome. I prefer Chromium to Chrome, as it is open source.

---

### Post by finny388 on 2012-09-25
> **ahowe42 said:**
> There has to be a better solution for fixing *only youtube videos* than disabling hardware acceleration, which will potentially affect everything that uses the screen...

Agreed
The only thing that upsets me more on this issue than Adobe leaving us hanging is people proclaiming Solved! by turning off HW acceleration.

You can have low grade video, choppy high res, or crystal clear high res smurfs.

i can't wait for Flash to die but it's gonna be a long time

I encourage people to sign up for YouTube's html5 trial, though in my experience most everything is still in Flash.

---

### Post by finny388 on 2012-09-25
> **ahowe42 said:**
> The solution Scott linked to seems to have worked for me.  Thanks!

There are a few solution options on that page. Which one worked for you?
:)

---

### Post by Ubun2to on 2012-09-26
> **finny388 said:**
> Agreed
The only thing that upsets me more on this issue than Adobe leaving us hanging is people proclaiming Solved! by turning off HW acceleration.

You can have low grade video, choppy high res, or crystal clear high res smurfs.

i can't wait for Flash to die but it's gonna be a long time

I encourage people to sign up for YouTube's html5 trial, though in my experience most everything is still in Flash.

In my experience, hardware acceleration was extremely buggy. Sometimes, it would play way faster than it should, then slow down a lot.

---

