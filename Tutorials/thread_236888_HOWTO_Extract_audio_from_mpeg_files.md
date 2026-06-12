---
title: "HOWTO: Extract audio from mpeg files"
date: 2006-08-15
forum: Tutorials
---

### Post by TeeAhr1 on 2006-08-15
"Dammit, it's a video!"  You thought you were downloading five songs.  Nope, five videos.  You don't want videos, you just want something to put on your mp3 player.  Here's how to do it:

1. Download **ffmpeg** from the repositories (and any dependencies requested).
2. In the terminal, type: **ffmpeg -i "/path/to/file.mpg" -f mp3 "/path/to/newfile.mp3"**
Note that if your filename or path has spaces, you need the quotes around it.
3. There is no 3.  You're done!

*Note: ffmpeg supports many different filetypes, and can do a lot more than just pull audio.  If you're interested, here's the [documentation]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html") page for ffmpeg.

---

### Post by RhysU on 2009-04-07
Try sticking '-ab 256k' or '-ab 128k' or whatever before '-f mp3', otherwise you may find your MP3 has a bitrate much lower than you'd usually want.

---

### Post by produnis on 2012-01-21
> **RhysU said:**
> Try sticking '-ab 256k' or '-ab 128k' or whatever before '-f mp3', otherwise you may find your MP3 has a bitrate much lower than you'd usually want.

thanks man,
thats exactly what I was looking for
:)

---

