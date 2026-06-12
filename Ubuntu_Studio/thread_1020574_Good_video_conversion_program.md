---
title: "Good video conversion program"
date: 2008-12-24
forum: Ubuntu Studio
---

### Post by Sailorcancer on 2008-12-24
Hello, I'm looking for a program that can convert videos into other video formats.  Hopefully a program with the ease of use/feature set of Super!.

I'm running the latest Ubuntu 8.10.

Sorry if this is the wrong forum.  

Thanks.

---

### Post by paulmerchant on 2008-12-24
I generally use Avidemux or ffmpeg to convert video. Both are available in the repositories. Avidemux gives you a GUI and ffmpeg runs from the command line. To have access to all the latest video and audio formats, you might want to enable the medibuntu repositories (find out more at medibuntu.org).

---

### Post by Samhain13 on 2008-12-25
+1 on the Medibuntu package for FFMpeg. That's what I use too. :)

---

### Post by johnjoe on 2008-12-25
Hi 

Please see my reply in Multimedia & Video under "VRO"

John

---

### Post by namdung on 2008-12-25
+1 for Avidemux

---

### Post by Ng Oon-Ee on 2008-12-26
> **Samhain13 said:**
> +1 on the Medibuntu package for FFMpeg. That's what I use too. :)
+1 for ffmpeg. Unfortunately, if you're on Intrepid, its not in medibuntu anymore. You can still access all its capabilities using the unstripped libraries, but I'd recommend a source compile if you're up for it. [This guide]("http://ubuntuforums.org/showthread.php?p=6441650") should provide everything you need, and then some.

Edit: Just realized you're using SUPER on Windows, that's actually just a GUI front-end for ffmpeg, really. Unfortunately there's no corresponding Linux GUI, but I've gotten used to CLI ffmpeg, and its actually faster (conversion etc) compared to running it through a gui. Plus you can do nifty things like scripting the conversion of various folders full of mixed-filetype videos and music etc.

---

### Post by Samhain13 on 2008-12-27
"Unfortunately, if you're on Intrepid, its not in medibuntu anymore."

Oh! This, I didn't know. But I'm still on Hardy and I think I'm going to stick with it 'til the next LTS. Still, thanks for the guide. I will keep that link handy.

"Edit: Just realized you're using SUPER on Windows, that's actually just a GUI front-end for ffmpeg, really."

I don't think this is for me... :)

---

### Post by nowardev on 2008-12-27
mencoder is the best!

---

### Post by Ng Oon-Ee on 2008-12-27
> **Samhain13 said:**
> "Unfortunately, if you're on Intrepid, its not in medibuntu anymore."

Oh! This, I didn't know. But I'm still on Hardy and I think I'm going to stick with it 'til the next LTS. Still, thanks for the guide. I will keep that link handy.

"Edit: Just realized you're using SUPER on Windows, that's actually just a GUI front-end for ffmpeg, really."

I don't think this is for me... :)
You're right, it was for the OP. Never try to post when still groggy from too much holidaying =).

And yes, if Hardy works for you stick to it. I can't wait to try Jaunty. Nothing wrong with Intrepid, really, fixes some Pulse stuff which I had to manually adjust before. But this issue with ffmpeg/medibuntu and the lack of a RT kernel is iritating.

Oh, and I do suggest you keep the link handy. It appears ffmpeg won't ever make it back to medibuntu, being superceded by the 'unstripped' variants of libavcodec/libavutil/libavformat etc. Which allows ffmpeg to do the proper conversions, supposedly, but which I've never really gotten to work.

---

### Post by nowardev on 2008-12-27
super is NOT only a gui for ffmpeg

super is a gui for ffmpeg2theora ffmpeg mencoder. the same of nwc on linux (or maybe it should)

---

### Post by ipburbank on 2008-12-27
blender 3d.. I know it says 3d in the name, but it also is great for simple to extensive video editing, there are many output formats that blender supports, and it is also capable of using many inputs as well. let me know if you need a tutorial on how to do that.

---

### Post by redsoxreed on 2008-12-27
Handbrake.  It's superb.

[http://handbrake.fr/](http://handbrake.fr/)

---

