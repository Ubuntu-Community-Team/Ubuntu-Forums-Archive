---
title: "Why is theora so big?"
date: 2008-05-24
forum: The Cafe
---

### Post by Polygon on 2008-05-24
I discovered a great little program called PyTube which downloads youtube videos and then converts them into a variety of formats

But i noticed that when it converts to OGM (theora) its almost twice as big as other formats. In fact, its bigger then the source file!

the source flv is 32 mb
the movie encoded in theora is 42 mb
the movie encoded in 'avi' (i think its mpeg) is 26 mb

Also i noticed that the theora version, when i try to seek around in the video, the video is corrupted for a few seconds before it normalizes.

So yeah, why is theora so big compared to other formats?

---

### Post by saulgoode on 2008-05-24
> **Polygon said:**
> But i noticed that when it converts to OGM (theora) its almost twice as big as other formats. In fact, its bigger then the source file!

This occurs because the quality of the OGG file you are creating is greater than necessary to maintain the original quality of the FLV file (sort of like recording a phone conversation at CD quality; there are a lot of wasted bits). 

The default quality setting for ffmpeg2theora is "5" (it can range from 1-10). YouTube FLV videos have a quality setting that is comparable to ffmpeg2theora's quality of "1" (about 200kb/s). 

My anecdotal experience is that* for a given level of video quality*, OGG files are under half the size of the original FLV files. 

> Also i noticed that the theora version, when i try to seek around in the video, the video is corrupted for a few seconds before it normalizes.

The default keyframe setting for ffmpeg2theora is "64". For 30 frames per second video, this means that a keyframe is created approximately every two seconds. The frames between keyframes are not recorded completely; they are generated as a deviation from the preceding keyframe (and subsequent non-keyframes). Fffmpeg2theora permits you to change the keyframe setting to as low "8", which would make seek responsiveness of about a quarter of a second for 30fps video. Lowering the keyframe rate will generally lower the compression ratio of the resulting video.

---

### Post by Polygon on 2008-05-24
Thanks dude, that helped a lot. I lowered the keyframes to 16 and it added only a megabyte and helped a lot with the corruption

i also noticed that yeah the program was setting the quality to 10, but if he didnt do that it looks even crappier (it would be compressing an already compressed video) so yeah =P

---

