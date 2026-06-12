---
title: "[SOLVED] What is your favourite Screen Recorder for Ubuntu?"
date: 2008-05-05
forum: The Cafe
---

### Post by Rytron on 2008-05-05
Hi,
What is your favourite Screen Recorder for Ubuntu?

I your choice is not on the above list, please then choose other and post a comment on what your choice is. Thank you.

I hope one day Ubuntu gets CamStudio.

---

### Post by erginemr on 2008-05-12
Hi,

**gtk-recordmydesktop** is the one that worked for me. In my antique system (Athlon 750 MHz, 512 MB RAM) gtk-recordmydesktop fulfills its premise. (I have tried Istanbul (maybe because it was my home city ;)) back in Gutsy, but had several problems in recording the video, and therefore had to leave using it.

---

### Post by blithen on 2008-05-13
GTK-RMD is the only one that actually WORKS for me. Though I wish it could save in a format that actually works with youtube..

---

### Post by Rytron on 2008-05-13
> **erginemr said:**
> Hi,

**gtk-recordmydesktop** is the one that worked for me. In my antique system (Athlon 750 MHz, 512 MB RAM) gtk-recordmydesktop fulfills its premise. (I have tried Istanbul (maybe because it was my home city ;)) back in Gutsy, but had several problems in recording the video, and therefore had to leave using it.

Although I did vote for XVidCap Screen Capture, I have since also found tk-recordMyDesktop to be the best one. Even though it records in ogg - there must be numerous ways to convert this to avi, mp4, etc. Not sure how to convert ogg to other video formats in Ubuntu yet though.

---

### Post by bigbrovar on 2008-05-13
> Not sure how to convert ogg to other video formats in Ubuntu yet though. u can use PSPVC although u have to compile it from source  .. but it just works ..

---

### Post by erginemr on 2008-05-13
I could just convert the ogg screencast I've recorded to avi via **ffmpeg**. To install:
```
sudo aptitude install ffmpeg
```
and to carry out the conversion:
```
ffmpeg -i <input_file> <output_file>
```
and then could edit the resulting file with **avidemux**:
[http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)

To install:
```
sudo aptitude install avidemux
```

You may also consider using **WinFF**, which will act as a frontend to ffmpeg:
[http://www.winff.org/](http://www.winff.org/)

There is also **mencoder**, which will convert video files into different formats.

---

### Post by Rytron on 2008-05-18
> **blithen said:**
> GTK-RMD is the only one that actually WORKS for me. Though I wish it could save in a format that actually works with youtube..

OGG can be uploaded to YouTube.
Check this out:
[http://www.youtube.com/watch?v=kdQFQU8SYik]("http://www.youtube.com/watch?v=kdQFQU8SYik")

---

### Post by bufsabre666 on 2008-05-18
istanbul is the one i use, it works for me, but honestly ive never even tried to others, is there any features that gtk record my desktop has that might be worth while to change to?

---

### Post by erginemr on 2008-05-18
> **bufsabre666 said:**
> istanbul is the one i use, it works for me, but honestly ive never even tried to others, is there any features that gtk record my desktop has that might be worth while to change to?

I guess they are more or less equivalent. As long as the one you are using works for you, I'd say, stick to it.

The following is a demo/screencast of gtk-recordmydesktop:
[http://showmedo.com/videos/video?name=1820000&fromSeriesID=182](http://showmedo.com/videos/video?name=1820000&fromSeriesID=182)
Or you may try it for yourself:
```
sudo aptitude install gtk-recordmydesktop
```

---

### Post by bufsabre666 on 2008-05-18
> **erginemr said:**
> I guess they are more or less equivalent. As long as the one you are using works for you, I'd say, stick to it.

The following is a demo/screencast of gtk-recordmydesktop:
[http://showmedo.com/videos/video?name=1820000&fromSeriesID=182](http://showmedo.com/videos/video?name=1820000&fromSeriesID=182)
Or you may try it for yourself:
```
sudo aptitude install gtk-recordmydesktop
```

yeah i figured as much, they both seemed the same when i reviewed them so i just thought i asked incase there was a worth while feature that i didnt know cause there seems to be quite a few gtk-record my desktop users

---

### Post by Rytron on 2008-05-18
> **erginemr said:**
> I guess they are more or less equivalent. As long as the one you are using works for you, I'd say, stick to it.

The following is a demo/screencast of gtk-recordmydesktop:
[http://showmedo.com/videos/video?name=1820000&fromSeriesID=182](http://showmedo.com/videos/video?name=1820000&fromSeriesID=182)
Or you may try it for yourself:
```
sudo aptitude install gtk-recordmydesktop
```

Thanks erginemr for that link.
Here are the commands from that video:

whole screen:
```
recordmydesktop
```

region:
```
recordmydesktop -x 1 -y 1 -width 800 -height 600
```

window:
```
recordmydesktop -windowid $( xwininfo -frame | awk '/Window id:/ {print $4}' )
```

note that if you want to record with no sound add ```
--no-sound
``` to end of a command line.

---

### Post by erginemr on 2008-05-19
You are welcome Rytron, or should I say C64 guy ;) I am glad that it works for you.

---

