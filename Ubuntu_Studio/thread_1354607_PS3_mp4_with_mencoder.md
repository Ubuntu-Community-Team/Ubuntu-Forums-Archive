---
title: "PS3 mp4 with mencoder"
date: 2009-12-14
forum: Ubuntu Studio
---

### Post by Emanuele_Z on 2009-12-14
Hi all,

I would like to use mencoder to create mp4 compatible files for PS3.
Regarding video everything is ok, if I both encode/copy a pre-existing h.264 stream PS3 will play it back.
Instead issues are with audio.
When you create an mp4 for PS3, you have to encode audio in AAC only.
With mencoder you can use *-oac faac* of the *-oac lavc -lavcopts acodec=libfaac* options.
Problem is file is 100% ok on my Pc (Ubuntu 9.10 x86-64), while on PS3 video is 100%, but audio, even if it is detected (PS3 'display' section correctly shows AAC 2 channels in audio codec) is like *muted*.

Has anyone else experiencing these issues?
Any suggestion to convert an MKV (h.264/DTS5.1) -> MP4 (h.264 copy/ AAC - conversion) ?
Or maybe in another PS3 supported format in one pass conversion?

I managed to first convert it as MKV (h.264/AC3) then with *tsMuxeR* exported as m2ts, but this is a very long process (plus I use a closed source tool)...

Any suggestions/recommendations?
Cheers,

---

### Post by Emanuele_Z on 2009-12-15
No one knows?

Cheers,

---

### Post by Emanuele_Z on 2009-12-20
I could use ffmpeg.
Do you know where can I find it pre compiled and packaged with aac support (and maybe h264/h264_vdapu as well)?

Cheers,

---

### Post by dream_coder on 2009-12-20
Just stream it to your ps3 using either ps3mediaserver or mediatomb thats all I do works fine.

---

### Post by VertexPusher on 2009-12-21
> **Emanuele_Z said:**
> Any suggestion to convert an MKV (h.264/DTS5.1) -> MP4 (h.264 copy/ AAC - conversion) ?
Load the MKV file into Avidemux, select video mode "Copy" and audio codec AAC. Click the audio filters button and select downmix to stereo. Select MP4 output format, then save the file. This will copy the H.264 stream while converting the audio stream to AAC. The resulting MP4 file should play on your PS3.

AAC support has been stripped from ffmpeg and libavcodec, but it is still available in Avidemux.

---

### Post by Emanuele_Z on 2009-12-21
I tried with an older version of avidemux, but it crashed, I will give it another try!
Btw any recommended version of avidemux to use?

Isn't there anyone which has pre-packaged ffmpeg with aac/h264/h264_vdapu ?

Cheers,

Ps. Why has aac been removed? for sw patents? Here in Europe don't exist...

---

