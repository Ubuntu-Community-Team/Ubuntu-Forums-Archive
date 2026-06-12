---
title: "h.264 cinelerra Imports only audio no video"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by ppeetteerr on 2008-05-05
I'm having some trouble with importing a h.264 file into cinelerra.  When I open the file all I get is the audio and no video.  I know that cinelerra is capable of importing it as I had it going under gentoo.  Has anyone else had this problem?

---

### Post by eagle416 on 2008-12-12
It happened to me as well. WMV's won't open, and sometimes it will compress the AVI sound into 3 seconds or garble it up.

---

### Post by eagle416 on 2008-12-20
I hadn't the patience, so I just used ffmpeg to convert it into an mpg.
Use the -sameq tag (keeps video quality good), and keep ahold of that audio only version as well, as the sound is disgusting in the mpg version.

That's just a jury rig I use until I eventually find a solution.

---

### Post by kayosiii on 2008-12-22
cinelerra is designed really to work with uncompressed video
- In fact it is easier to list the formats that it does work well with rather than the ones it doesn't. I know uncompressed files chew a lot of disk space but the results are far superior. Transcoding to mpeg before using in cinelerra is just throwing away quality. If you are going to use a lossy format try a mjpeg compressed avi or quicktime file on low compression settings... Damage is minimal and Cinelerra works well with this format. Other than that try an uncompressed YUV format if possible. I usually use mplayer to transcode stuff to yuv4mpeg format (think DVD stream without any compression) I am not sure that sound gets saved with this format.

Hope that helps

---

