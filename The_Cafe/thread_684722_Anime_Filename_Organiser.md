---
title: "Anime Filename Organiser"
date: 2008-02-01
forum: The Cafe
---

### Post by Trail on 2008-02-01
Some old screenshots at [http://forums.animesuki.com/showthread.php?t=55871](http://forums.animesuki.com/showthread.php?t=55871). With KDE4 now it looks better :P

I've made a utility that can parse a filename, try to determine the fansub group, series title, episode number etc, and rename it to a user defined format. It also uses mplayer for audio/video information and cksfv for CRC32 support.

For example:
[Sub-Group]_Sample_Series_Name_-_01_[DVD_H264_AC3][1234ABCD].mkv
using my custom format will be renamed to:
[Sub-Group] Sample Series Name - 001 [640x480] [H264] [1234ABCD].mkv
just by drag-n-drop and hitting ok.

Since I have a rather large collection of anime, and I want it tidied up and uniform, I've been using it privately for a bunch of months and it's been working pretty well. I left development after a point though, so not everything i wanted is complete (Undo support for example, though it's 5-10minutes work, i'm lazy now).

Dependency: Qt 4.2+
You should also install a recent enough version of mplayer and cksfv, though not required.

The source code is quite a mess, I was in a hurry while writing it. Reading the code will eat your children :) And, even though I wanted to use some C++ techniques i've been learning, I was also learning the Qt library so I went the easy, fast and lame way.

You should be able to execute the file under bin/ directly if you have the necessary Qt libraries. Or you can compile it.

ADVANCED:
You can add "support" for more audio and video format than the default by:

edit ~/.config/kanon/kanon.conf
Add or replace these lines:

KAnOn\Audio%20Format%20Alias="8192,AC3", "vrbs,Vorbis", "85,MP3", "mp4a,AAC", "MP4A,AAC", "8193,DTS", "353,WMA"
KAnOn\Video%20Format%20Alias="XVID,XviD", "avc1,H264", "DX50,DivX", "WMV3,WM9", "DIVX,DivX", "DIV3,DivX"

Let me know if anyone finds it useful (or even if it works or not, heheh). I might continue it sometime.

---

### Post by gsmanners on 2008-02-03
I find anidb to be handy for stuff like that. I don't actually have an account there, but it's very useful.

Here's the only thing I use for checking files:

```
#!/usr/bin/env python
#
# check CRC against the file name

import sys
import os

def main():
    files = sys.argv[1:]
    for f in files:
        os.system("cksfv \"%s\" > /tmp/sfv.txt" % f)
        f2 = None
        try:
            f2 = open("/tmp/sfv.txt", 'rb')
        except:
            print "Failed to open sfv.txt"

        if f2:
            x = f2.readlines()
            f2.close()
            os.system("rm /tmp/sfv.txt")
            c = x[len(x) - 1][-9:-1]
            if f.find(c) >= 0:
                print "[OK] %s: %s" % (f, c)
            else:
                print "* Error * %s: %s" % (f, c)

if __name__ == "__main__":
    main()
```

---

### Post by Trail on 2008-02-04
I agree with anidb. Invaluable tool.

One of my ideas would be to be able to automatically connect to anidb and find/verify the info (maybe including more stuff, like year, total episode count, etc) automatically, No idea how would I be able to navigate directly to an episode in question, though, without searching for it...

---

