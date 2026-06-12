---
title: "trying  to convert dv to mpeg2/4 in vlc without success"
date: 2008-12-26
forum: Ubuntu Studio
---

### Post by marttali on 2008-12-26
i get this error:
Streaming / Transcoding failed:
VLC could not find encoder "MPEG AAC Audio".
Streaming / Transcoding failed:
VLC could not find encoder "MPEG-4 Video".

i really don't know what to install. I have installed all kinds of libs and stuff.DV was captured with Kino to raw 1394.
Any better tools for the job ?

system:Kubuntu 8.10 64 bit

---

### Post by 67GTA on 2008-12-26
Something happened with 8.10, because the "full" ffmpeg is no longer in the Medibuntu repo. Now, ffmpeg is in the main repos, but is kind of crippled. Make sure you have installed ```
kubuntu-restricted-extras
``` Then open your package manager of choice and search for "unstripped". Install anything with unstripped in it's name. This will replace the crippled libs with the full ones that used to come with ffmpeg, and try it again.

---

### Post by marttali on 2008-12-26
thank you, that did the trick.

---

### Post by waydes on 2008-12-27
Thanks, I have been hunting for this fix for several days.

---

