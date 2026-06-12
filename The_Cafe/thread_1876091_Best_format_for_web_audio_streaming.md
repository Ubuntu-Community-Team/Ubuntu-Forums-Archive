---
title: "Best format for web audio streaming"
date: 2011-11-05
forum: The Cafe
---

### Post by rmcellig on 2011-11-05
At the moment, all the audio files on my web site are MP3 192 format. I was wondering if I am able to cut down the file size while still maintaining credible audio sound. What format would be best for this? I don't mind having to convert the current files to another format.

My web site is [www.mcran.com](www.mcran.com)

---

### Post by juancarlospaco on 2011-11-05
HTML5 uses WebM / OGG

---

### Post by doorknob60 on 2011-11-05
Not really. You could use OGG which is open source and HTML5 supported (so an advantage over MP3), but that won't cut down on file size/bandwidth usage, unless you reduced the bitrate. You could reduce the bitrate if you wanted, but I wouldn't really recommend it. If you do, don't go below 128k. Also, keep in mind that converting between lossy audio formats (like from MP3 to OGG) will result in lost audio quality, so I don't recommend doing that either, unless you have an original copy in a lossless format like FLAC or an audio CD to convert from.

---

### Post by rmcellig on 2011-11-06
OGG format doesn't seem to work at all. I went to my web site and tried to play one of the OGG formatted shows. Nothing. Why is this? Does only mp3 an m4a work. Too bad because the file size went from around 162mb to around 74mb in OGG format and sounded fine. What are my options?


My web site is [www.mcran.com](www.mcran.com). Click on radio shows and try and play any of my shows from oct 2011. Check the path just to make sure it looks ok. Thanks!!

---

### Post by thenixedreport on 2011-11-06
If you're wanting better file sizes, OGG would be a good choice.  I have personally noticed that OGG files can be smaller than MP3 files.  In terms of HTML 5, the web browser in question will have to support it.  Most newer versions of Firefox will support it as well as Chrome/Chromium (even IE 9 has support for that sort of stuff nowadays.... at least as far as WebM is concerned).  FYI, clicked the first link you specified and it seems to work.

---

### Post by rmcellig on 2011-11-06
I also noticed that it worked on my iMac, but on my ipod doesn't seem to work. If you or anyone checking this thread has an iPod, tablet, Android or similar device I would appreciate you trying to see if you can play the ogg files I have on my site. Just go to [www.mcran.com](www.mcran.com) and slect radio shows. Then, select any of the files from October 2011. These are all ogg formatted files.

---

### Post by doorknob60 on 2011-11-06
It works for me in Firefox. It should work by default in any recent version of Firefox, Chrome, or Opera using HTML5, and probably also Android, but certainly not iOS. A format like MP3 or M4A would allow it to work on Apple devices, and also probably browsers like Safari or IE (with Quicktime or WMP plugins possibly needed), but would mean the open source browsers would not be able to play them without an external plugin. For me in Firefox, the MP3s opened in the mplayer plugin rather than the HTML5 player, which is not as ideal.

---

### Post by rmcellig on 2011-11-06
I think I will stay with mp3 format because it seems to be the most common across platforms and devices. I even think I will bring the bit rate down from 192 to 128 and on my jazz interviews, I think I will bring them down from mp3 192 to mp3 24. That should sound fine because it is only voice.

---

