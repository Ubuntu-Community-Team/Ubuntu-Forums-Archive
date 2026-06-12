---
title: "Decoding Kate format subtitles"
date: 2010-02-25
forum: Ubuntu Studio
---

### Post by afrodeity on 2010-02-25
I was struggling to find a way of including subtitles in an ogg file. Then I found the TheoraCookbook which shows how to embed srt streams as kate [http://en.flossmanuals.net/TheoraCookbook/EmbeddingSubtitles](http://en.flossmanuals.net/TheoraCookbook/EmbeddingSubtitles)

All good and fine, I now have an ogv file with kate subtitle stream. Only problem, nothing to play it with.


Movie Player
```

The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

```

It then searches for a codec but can't find any.


VLC
```

No suitable decoder module:
VLC does not support the audio or video format "kate". Unfortunately there is no way for you to fix this.
```

What's the problem?

---

### Post by lovinglinux on 2010-02-25
I don't know what the problem is, but why don't you use [mkvtoolnix-gui](apt:mkvtoolnix-gui) to mux the video and subtitles into a mkv container, instead of embedding it into the ogg file?

If you really need to embed the subtitles into the video, you could try mencoder - [http://ubuntuforums.org/showthread.php?t=1325336](http://ubuntuforums.org/showthread.php?t=1325336)

I never tried with ogg files and theora codecs tho.

---

### Post by afrodeity on 2010-02-26
I installed mkvtoolnix-gui. How do I run it. Tried entering in mkvtoolnix-gui in terminal, but command not found.

---

### Post by afrodeity on 2010-02-26
Okay got it: [http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge-gui.html#whatismkvmerge](http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge-gui.html#whatismkvmerge)

mmg

But it looks a wee bit complicated, for something which should be easy. :(

This is the d[ownload link for jubler.]("http://sourceforge.net/projects/jubler/files/Jubler Binary Releases/4.0/Jubler-4.0-linux_i386.sh/download") My proxy won't let me download. Have to wait for more bandwidth.

---

### Post by lovinglinux on 2010-02-26
> **afrodeity said:**
> But it looks a wee bit complicated, for something which should be easy. :(

Perhaps this will help [http://www.bssubs.net/mkv_tutorial/](http://www.bssubs.net/mkv_tutorial/)

---

### Post by andrew.46 on 2010-02-27
Hi afrodeity,

> **afrodeity said:**
> All good and fine, I now have an ogv file with kate subtitle stream. Only problem, nothing to play it with.

You may be interested to know that if vlc is compiled against libkate and optionally libtiger, it has no trouble reading such subtitle streams. I attach a screenshot of a suitably configured vlc playing [this sample file]("http://people.xiph.org/~oggk/elephants_dream/elephantsdream-with-subtitles.ogg"). I have compiled my own I am not sure if there is easy availability of a vlc package with this capability...

All the best,

Andrew

---

### Post by afrodeity on 2010-02-27
Thanks for letting us know. Would be great to install from a properly packaged kate vlc with its own ppa. I want to go the ogg theora kate route and not have to deal with matroska so soon. I know matroska is probably the better method for dealing with DVD authoring, but before you can author to DVD you have to cut and finish the project, bang it into a coherent whole and add effects and yes, subtitles are sometimes necessary in documentaries. It's the way I deal with bad sound quality. So any m :)ethod of making life easy for documentary videographers and artists I support!!!!

---

