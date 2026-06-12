---
title: "Panasonic Camcorder video format doesn't like Kdenlive"
date: 2008-05-28
forum: Ubuntu Studio
---

### Post by Morichalion on 2008-05-28
I bought a Panasonic SDR-H40P/PC a week ago. I figured the HDD camera style would simplify video capture a bit. To be honest, it does that part quite nicely.

I can play the video clips just fine using Ubuntu's default video player, but when I try to preview the clip in Kdenlive, I can't get any audio from it. 

Looking at the manual showed me that the camera uses an "independent standard" for it's video format. When I asked their customer support about an app that would transcode the clips to a more common format, they told me that the included disk is all that would work. Except that it's for windows. ><

So, I guess my question is, does anyone have an idea of what I can do in this situation? I'm planning on returning this camera sometime today or tomorrow, if I can't get this solved.

---

### Post by eye208 on 2008-05-29
> **Morichalion said:**
> I can play the video clips just fine using Ubuntu's default video player, but when I try to preview the clip in Kdenlive, I can't get any audio from it.
If the clip works with the default player, there is no reason to return the camera. You can use Avidemux or FFMPEG or MEncoder to transcode the audio track into a format that Kdenlive can handle.

---

