---
title: "libvlc: How get current video resolution?"
date: 2024-09-20
forum: Ubuntu Application Development
---

### Post by Alex_K. on 2024-09-20
Hello,

How can I get current video resolution using libvlc? I wasn't been able to find any API for this.

I'm developing an application using libvlc in QT. Part of it, is playing video files using libvlc (that's what libvlc is for, in that project). Everything is basically working just fine, the only thing I wasn't been able to figure out by now, from libvlc documentation - is getting currently playing video track resolution (I'd like dynamically adjusting window/player size, for better end-user experience).

Any suggestion for figuring out resolution of LibVLC media or currently playing video in LibVLC media player, will be appreciated. Thank you!

---

### Post by TheFu on 2024-09-20
VLC has a website. I'd start there, since it isn't an Ubuntu project.  Always start with the real project team when seeking API answers.
Of course, you can also look through the header file(s) for libvlc and look for anything related to returning information about the current video in that API. I'd look myself, but none of my systems has VLC installed.    [https://www.videolan.org/vlc/libvlc.html](https://www.videolan.org/vlc/libvlc.html)  There's always the source code.

Found the header files, here: [https://code.videolan.org/videolan/vlc/-/tree/master/include?ref_type=heads](https://code.videolan.org/videolan/vlc/-/tree/master/include?ref_type=heads)

I know exactly how to get the resolution using other tools (mplayer, mpv, mediainfo) and a shell script, but I don't think that's your question.

---

### Post by ajgreeny on 2024-09-20
Go to the VLC menu item **Tools -> Media-Information -> Codecs** tab and there you will see the resolution figures.
See screenshot.

---

### Post by 1fallen on 2024-09-20
This may be more than you wanted so feel free to edit it:
```
mpv libvlc_video_get_width/libvlc_video_get_height and libvlc_video_get_size {Your File Here}
```
output:
```
(+) Video --vid=1 (*) (h264 1920x1080 24.000fps)
 (+) Audio --aid=1 --alang=en (*) (eac3 6ch 48000Hz)
     Subs  --sid=1 --slang=en 'English [SDH]' (subrip)
AO: [pipewire] 48000Hz 5.1(side) 6ch floatp
VO: [gpu] 1920x1080 yuv420p
AV: 00:03:58 / 00:39:49 (10%) A-V:  0.000
Exiting... (Quit)


```

---

