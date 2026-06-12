---
title: "Trouble with Kdenlive and Studio 15.04?"
date: 2015-07-15
forum: Ubuntu Studio
---

### Post by dlaciv12 on 2015-07-15
Hello, I'm new to Ubuntu Studio but have played around with a few other Ubuntu flavors. I am a photographer and have been using darktable for almost all of my development. I wanted to make a time lapse and I tried it on Kdenlive but ran into a problem. I start a project and add a slide show to it. since it's a time lapse I set the frame duration to 0.25 seconds. When I hit OK the frame duration sets itself to 00:00:01:01, So my 37 frame time lapse is a 37 second project. No matter how I try to add a clip or change the frame duration under properties it returns to the 1:01 duration. 

I posted in the Kdenlive forums and all they could come up with is that it might be a problem with the low latency kernel in Studio. Is anyone else have problems? Am I missing something obvious? I've never use Kdenlive before so it might be user error.

---

### Post by jejeman on 2015-07-17
Had no musch issues with kdenlive.
Do you set time in frames? The 0.25 seconds is like 6 frames for 25FPS. I just set it and it works. 14 pictures duration 3s.
Ubuntu Studio 14.04 Kdenlive 0.9.10.
Is is silly to blame lowlatency kernel for this.

---

