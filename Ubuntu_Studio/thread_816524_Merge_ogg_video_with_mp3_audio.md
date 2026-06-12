---
title: "Merge ogg video with mp3 audio"
date: 2008-06-02
forum: Ubuntu Studio
---

### Post by pytheas22 on 2008-06-02
I have an .ogg video file that currently contains no audio (it is a screencast made with recordmydesktop).  It uses the Theora codec.  I'd like to merge it with an mp3 file to add audio.  I've spent two days working on this now and still haven't found a good solution.

I tried using avidemux, but apparently that program doesn't support Theora video.  I also tried kino, but ran into the same problem.

I also tried using a command-line utility called ogmmerge, but I get the error, "Error: the reader for out.ogg did not produce a header page" when I try to run it.

I found that I can use vlc to reencode my .ogg video into an mpeg, which avidemux will open, and then add audio.  This is a solution of sorts, but I lose a lot of video quality in the conversion.

If anyone could tell me either how to make avidemux open .ogg files, or where I could find another program that would allow me to combine ogg video with mp3 audio, I would be grateful.  I'm surprised and a bit frustrated at how hard it is to find a program that can deal with Theora, a completely free format.

Alternatively, is there any screencast software that would encode video into a format that avidemux could open?  So far I've tried istanbul, recordmydesktop and xvidcap, but all of them seem to output to ogg Theora as the only option.

---

### Post by eye208 on 2008-06-03
To merge Theora video with MP3 audio without transcoding either, you need to choose a container format that can handle both, e.g. Matroska (.mkv). OGM works too but is considered obsolete.

There are Matroska muxing tools in the repository. Search for "mkvtoolnix".

If you need a video editor with Theora import, take a look at Blender.

---

### Post by pytheas22 on 2008-06-03
Thanks for the response.  I did find Cinelerra, which is able to open Theora video and append and mp3 into it without losing quality.  I was hoping that there would be a simpler solution--I don't need to edit my video and wait ten minutes for it to be rendered again; I just want to combine it with audio quickly and be done, like avidemux would allow--but Cinelerra is doing what I need for now.  I guess more people should start using .ogg so that the developers of applications like avidemux will have more motivation to add Theora and Vorbis support.

---

### Post by eye208 on 2008-06-04
> **pytheas22 said:**
> I was hoping that there would be a simpler solution--I don't need to edit my video and wait ten minutes for it to be rendered again; I just want to combine it with audio quickly and be done, like avidemux would allow
Well, I already mentioned the simple solution: mkvtoolnix.

---

