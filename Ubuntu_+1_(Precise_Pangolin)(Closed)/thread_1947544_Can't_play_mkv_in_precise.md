---
title: "Can't play mkv in precise"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ubuntu27 on 2012-03-26
Hello guys. Are any of you able to play mvk files in Ubuntu Precise?

I get this error in Totem:

"An error ocurred.

Could not find GStreamer caps mapping for FFmpeg codec 'h264', and you are using an external libavcodec. This is most likely due to a packaging problem and/or libavcodec having been upgraded to a version that is not compatible with this version of gstreamer-ffmpeg. Make sure your gstreamer-ffmpeg and libavcodec packages come from the same source/repository."


It mentions libavcodec,
The libavcodec that I have installed is fromt the standard universe repository: **libavcodec-extra-53**, version 4:0.8.1ubuntu1

I see that there is another one called "**libavcodec53**". What is the difference between libavcodec53 and libavcodec-extra-53 ? Ubuntu-restricted-extras seems to install the latter. 

I tried to use both libavcodec53 and libavcodec-extra-53. None works.


** gstreamer-ffmpeg** dosn't seem to exist in the repository.


EDIT: I cannot play it with Totem, but I can play it with VLC.

---

### Post by teh603 on 2012-03-26
Might be in Medibuntu.

---

### Post by ubuntu27 on 2012-03-26
> **teh603 said:**
> Might be in Medibuntu.

I added medibuntu, but gstreamer-ffmpeg is not there [yet?].


Well, I will mark this thread as solved for now since I was able to play the file using VLC.
But, I am worried that Ubuntu's default media player cannot play this format.

Is this a bug or simply Totem's limitation?
Could there be a solution?

---

### Post by alphacrucis2 on 2012-03-26
Does vlc play them?

---

### Post by Gregory Lee on 2012-03-26
The one file that I can locate on my system with a ".mkv" suffix plays okay with totem, vlc, and banshee.

As I recall, mkv is not a codec, but a wrapper format that can contain encoded videos of various sorts, so whatever the error is, it doesn't necessarily have to do with a missing codec.

---

### Post by VMC on 2012-03-26
> **Gregory Lee said:**
> The one file that I can locate on my system with a ".mkv" suffix plays okay with totem, vlc, and banshee.

As I recall, mkv is not a codec, but a wrapper format that can contain encoded videos of various sorts, so whatever the error is, it doesn't necessarily have to do with a missing codec.

Your right. I use handbrake and the H.264 for the video encoding. I tried VP3 just to see what its all about, but it compresses too much. I prefer H.264.

VLC plays anything I through at it so far.

---

### Post by ubuntu27 on 2012-03-27
The file that I tried to play seems to be a H.264 inside mkv.

---

### Post by Starks on 2012-03-27
Try mplayer2 with smplayer in the repos.

---

