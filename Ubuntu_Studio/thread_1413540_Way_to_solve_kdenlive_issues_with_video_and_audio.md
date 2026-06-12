---
title: "Way to solve kdenlive issues with video and audio"
date: 2010-02-22
forum: Ubuntu Studio
---

### Post by Slavutinsky Victor on 2010-02-22
Hi guys.

I've installed KDEnLive in 9.10 for some reason, and, like many others, faced sound and video glitches.  Here's way to solve it. It works for me, maybe it can help you too.

1) Install last version of KDEnLive from project site. Do not use version from Ubuntu repo.
2) Install rt kernel and use it instead of normal.
3) Convert all video files to same resolution and rate, same with project resolution.

If it hd720 25, use 

ffmpeg -i orig.avi -s hd720 -r 25 -vcodec mpeg4 -aspect 16:9 -b 200 -acodec mp2 -ab 64k -ar 44100 new.avi

for each file. Yep, do not even think to use mp3. It really slows anything.

4) Make complete uninstall of pulseaudio. Install audiohacks alsa from here 

[https://launchpad.net/~dtl131/+archive/ppa]("https://launchpad.net/%7Edtl131/+archive/ppa")

and set sound output to alsa in KDEnLive project.

5) Do not use large video files. It takes time to find part in it, so playback jumps on them. Chrop it by avidemux to really needed chunks instead.

It should do.

---

