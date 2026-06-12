---
title: "Decoding and converting AAC"
date: 2009-06-12
forum: Ubuntu Studio
---

### Post by Gannin on 2009-06-12
I'm using Intrepid.  Lately I've been getting some Flash videos with the intention of converting them to a different format.  The audio codec for the Flash videos is always one of two types.  It either says the codec is AAC, or MPEG-4 AAC Audio.

The videos that have the codec listed as MPEG-4 AAC Audio convert just fine.

However, I have issues with the videos that have the codec listed as just AAC.  If I try to load those in mplayer or use mencoder or ffmpeg to convert them, it says it can't recognize the file.  If I try to load it into Blender to do it that way, Blender crashes.  The only system that seems to be able to load them is gstreamer, which loads and plays them just fine.

When I try to then convert the videos to a different format, any format it doesn't matter what video or audio codec I choose, the resulting audio is always crackly.  I've tried multiple programs that work with gstreamer, like Pitivi and Ogg Convert, and as I mentioned I've tried a number of different codecs as a destination and it doesn't matter.  The audio is always crackly.  Any ideas why?  Or any other tools I could use that could get the job done?  Thank you.

---

### Post by andrew.46 on 2009-06-13
Hi Gannin,

> **Gannin said:**
> I'm using Intrepid.  Lately I've been getting some Flash videos with the intention of converting them to a different format.  The audio codec for the Flash videos is always one of two types.  It either says the codec is AAC, or MPEG-4 AAC Audio.

The videos that have the codec listed as MPEG-4 AAC Audio convert just fine.

However, I have issues with the videos that have the codec listed as just AAC. 

I wonder if you could post one of the troublesome aac files somewhere? I would be interested to see exactly what type of aac file it is...

Andrew

---

