---
title: "Which codec and file-format should i convert my DVDs to?"
date: 2009-09-26
forum: Ubuntu Studio
---

### Post by Neremor on 2009-09-26
Hello!

I know you find much stuff about that topic in the net. But I've searched the last two days for information and didn't find exactly what i was searching for.

I would like to copy some of my DVDs to my PC. Therefor I downloaded "dvd::rip", which is a nice program i think. But there are a few things confusing me. There was a nice codec getting famous over the last months, h.264... Off course i would like to use it for my video transcoding. So I selected "AVI" as container, "ffmpeg" as codec and "h264" as ffmpeg-codec. I copied one dvd to test the whole thing and it works. I get an AVI File that contains a video in h264. But I thought avi and h264 are not working together very well? Which container format should I use for the h264-codec? And how do I get 2- or 3-pass working for h264 (it's greyed out in dvd::rip)?

Thanks in advance for every help!
Greetings,
Jonathan

---

### Post by mtron on 2009-09-26
there is the native mp4 container and an inmho better [matroska .mkv]("http://www.bunkus.org/videotools/mkvtoolnix/") container for h.264 videos.

I mainly record videos from Satellite (DVB-S Mpeg2). Demux them with [projectX]("http://project-x.sourceforge.net/") (splits the audio and video stream and does error corrections on the broadcast stream) and finally use [mkvmerge]("http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge-gui.html") (part of the matroska tools) to add the audio & video stream to a matroska file.

For h.264 encoding purposes i use [Handbrake]("http://handbrake.fr/") (has a nice Linux gui now). It allows you to export to mkv and use h.264 2-pass encoding. Also it has inbuilt encoding presets that should make DVD encoding pretty easy. Give it a try ;)

One nice thing about mkv is the ability to attach other files to the container. Not only subtitles, but also pictures (if nautilus finds a pic embedded in a mkv it will use this as thumbnail)

---

### Post by Neremor on 2009-09-26
And which dvd-ripper could i use to convert the dvd-movie to h.264 (2-pass) and then save it in the mkv-container? The ProjectX seems to only support dvbt...

---

### Post by Neremor on 2009-09-26
Aaah sorry, i overread a part of your post. handbrake seems to work very nice for me and is doing exactly what i want :) thank you!

---

