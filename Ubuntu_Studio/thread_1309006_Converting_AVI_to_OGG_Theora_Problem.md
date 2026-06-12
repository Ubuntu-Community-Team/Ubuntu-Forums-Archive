---
title: "Converting AVI to OGG Theora Problem"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by JakeStone on 2009-11-01
Hello!

I have several files stored in AVI and WMV, mostly recorded by [CamStudio]("http://camstudio.org/") (a great screen-recording software for Windows). I want to put them in a format that is supported by Firefox without any codec downloads/installs, which means putting it in OGG Theora, or .ogv format. Windows software for OGV is pretty slim pickings, so I've been running an Ubuntu VM in VirtualBox to get the job done.

Unfortunately, I can't find much for this on Linux either. So far I've been using [ffmpeg2theora]("http://v2v.cc/%7Ej/ffmpeg2theora/index.html"), but that handles AVIs very poorly - the converted file's video runs at a slightly faster speed than the audio, so video tutorials (my main intent) are much harder to use. Additionally, this solution has terrible stability/functionality - it crashes more often than not, never utilizes more than 12% CPU, and the quality settings are best described as schizophrenic.

Currently, I encode the large AVI to WMV using Windows Media Encoder first, then push the WMV through ffmpeg2theora to get OGV. This at least eliminates the crashes, but the audio/video speed problem remains, and I usually have to run the OGV encoding several times to get the file size and quality to behave. Clearly, a different approach is needed.

To make things fun, it's also hard to search for terms I want (AVI to OGV, etc) without getting tons of crapware. What other software out there has proper support for OGV and major formats?

---

### Post by JakeStone on 2009-11-02
Any ideas? :(

---

### Post by JakeStone on 2009-12-15
Bump again. No responses :(

---

### Post by howefield on 2009-12-15
Oggconvert ? It's in Synaptic.

"OggConvert is a small GNOME utility which uses GStreamer to convert
(almost) any media file to the patent-free Ogg Vorbis, Theora and
Dirac formats.

The main interesting points are:
 * It is very easy to use: drag a file onto the source bar (or use
   the file chooser) and hit Convert button. Of course, you can also change
   the video format, quality settings and the output filename if you like.
 * It uses GStreamer, so it can convert (almost) any file Totem can play.
 * It can deal with audio-only files, video-only files, and files with many
   audio tracks (such as DVD rips with a commentary track).
 * Thanks to the magic of GStreamer, metadata (for example, title and artist
   info on an MP3) is preserved.
 * Adheres to the GNOME HIG as much as possible.
 * Supports the Schroedinger encoder for encoding to the Dirac video format
   (note that this encoder is currently experimental).
 * Supports encoding to the Matroska container format."

---

### Post by peakpc on 2009-12-15
for a gui front end you could convert them with vlc, not installed by defualt but it is in the software center/add remove programs.

---

### Post by JakeStone on 2009-12-15
> Oggconvert ? It's in Synaptic.That looks cool! I ran a quick install, but when I select my AVI files, the video quality slider grays out, which I can only assume means it will only convert the audio. Sure enough, it produced an OGG (not OGV) and it was only audio.

The only other option was Matroska, which I understand is experimental, and not what I want anyway.

I also tried converting my AVI to a WMV first with Windows, but OggConvert complained that the file format "video/x-ms-asf" was not supported. Any tricks I'm missing?

**Edit: **I'm trying FFmpeg but getting another error, see this thread:[U]
_[http://ubuntuforums.org/showthread.php?t=1356440](http://ubuntuforums.org/showthread.php?t=1356440)_
[/U]

---

### Post by howefield on 2009-12-16
Sorry about that, it works fine with any avi I throw at it, can only assume that you are missing some codec or it is specific to your Camstudio files.

I use to have a copy of CamStudio, I'll give it a go and try converting from the avi it produces.

---

### Post by howefield on 2009-12-16
To confirm oggconvert works fine with Camstudio files, can only think you are missing a codec/package of some sort.

---

### Post by JakeStone on 2009-12-16
That's odd - as I mentioned in the thread I linked above, I've been using ffmpeg to convert those same CamStudio AVI files to OGV, so I have the libtheora and all that jazz. Any idea what I need to add?

Alternatively, if you know how to control file size in ffmpeg, that would be awesome too (see above thread), as I got OGV conversion working with ffmpeg, but the resultant file is about 62 MB for 5 min of video, which could be better.

---

