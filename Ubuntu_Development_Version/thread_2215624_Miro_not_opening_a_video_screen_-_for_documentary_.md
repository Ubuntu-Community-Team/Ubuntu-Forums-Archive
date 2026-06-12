---
title: "Miro not opening a video screen - for documentary - just sound"
date: 2014-04-07
forum: Ubuntu Development Version
---

### Post by 23dornot23d on 2014-04-07
Just seems to have started recently as I often use Miro to watch the Ted Talks on Technology etc.

But this time when opening Miro - there was no video screen .... only the sound came back.

Yet I can go into the .miro/videos folder and find the videos to play and use VLC and they are fine

Has something changed that could affect that one application or are others also finding the same thing.

Not tried it yet in other desktops ......... but this is on the 64 bit 14.04 ....... with a Asus optimus computer

recent changes were to upgrade the drivers for Nvidia though ........ but as I say VLC works ok.


* ( just tried it in LXDE and UNITY ....... same thing happens ...... )

---

### Post by 23dornot23d on 2014-04-09
I still have this problem with Miro even after todays upgrade

to

# uname -a
Linux keith-K53SV 3.13.0-23-generic #45-Ubuntu SMP Fri Apr 4 06:58:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

If anyone else used it in this version - can they just acknowledge once that theirs is ok ......... so I can work out what 

if anything else attaches to this to give a display of the video ...... 

( just seems odd having to use it to download then to have to go get another application like VLC to watch things with )

Looked in preferences too and cannot see a way to redirect the video ....... but if anyone knows of a way could they
let me know. ty in advance .......

Could it be to do with the ffmpeg libav - changes ......

---

### Post by mc4man on 2014-04-09
It may be that miro needs the gstreamer0.10-ffmpeg for such files. If so it's not in trusty anymore, I  keep a trusty package build here - 
[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

---

### Post by 23dornot23d on 2014-04-09
Cheers mc4man ...... will have a look shortly and see if your ppa cures my problem ......

Have been running other video players and the files play ok ..... 

also saw an error after running mplayer on something to do with VDPAU but not sure what the main problem is yet.

Next to try this then and see if it restores my video display back ( ty ) -  gstreamer0.10-ffmpeg

That one file fixed it thank you very much  mc4man ........ 

Solved.

---

