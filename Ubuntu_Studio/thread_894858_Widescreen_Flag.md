---
title: "Widescreen Flag?"
date: 2008-08-19
forum: Ubuntu Studio
---

### Post by tyke on 2008-08-19
I wonder if anyone can help me with a small problem. Video I shoot on my JVC Everio camcorder in a 16:9 aspect ratio plays back at 4:3 on my PC. 

The Everio shoots MPEG-2 video, and I believe the problem is that it fails to set the "widescreen flag" on the files. They play back just fine if I manually change the aspect ratio in Mplayer.

So, is there a Linux app that will allow me to set the widescreen flag *without* having to re-encode the files?

Thanks in advance for any help.

---

### Post by mcduck on 2008-08-20
There is no such thing as "widescreen flag" for video files. The video is played back simply based on it's resolution. For example video file with 720x576 resolution would be 4:3, and file with 1080x720 resolution would be 16:9. There is no need for any "flag" to tell what aspect ratio the video is.

I'd suspect that you have imported the video from your camera into 4:3 size, resulting in anamorphic 16:9 (16:9 video squeezed into 4:3 aspect ratio) which would, just like you say, play correctly if the video player is forced to use 16:9 aspect ratio.

---

### Post by tyke on 2008-08-20
> **mcduck said:**
> There is no such thing as "widescreen flag" for video files. 

In which case, exactly what does SDCopy on windows do when I tick the "Set Widescreen Flag" option? Also, check out this link:

[http://www.elurauser.com/articles/JVC_Everio_mod_files.jsp]("http://www.elurauser.com/articles/JVC_Everio_mod_files.jsp")[http://www.elurauser.com/articles/JVC_Everio_mod_files.jsp](http://www.elurauser.com/articles/JVC_Everio_mod_files.jsp)
2 thirds of the way down. Widescreen bug.

> **mcduck said:**
> I'd suspect that you have imported the video from your camera into 4:3 size, resulting in anamorphic 16:9 

Except I imported the video by just dragging and dropping the files direct from the cameras hard disk. It just mounts as an external HDD. The format of the files should not be altered by copying from one drive to the next.

---

### Post by tyke on 2008-08-26
Hey all.

After much, much web searching, it turns out that this is a common issue with JVC camaras. I've resolved it now, but in case anyone else runs into the same problems, the quickest fix appears to be running DVDPatcher on the files. A good guide can be found here:

[http://www.ziova.com/forum/index.php?showtopic=728]("http://www.ziova.com/forum/index.php?showtopic=728")

Look about halfway down the page.

I'm afraid it does involve booting into windows. Not ideal, but no one seems to know how to resolve the problem under Linux.

---

### Post by jaanus on 2008-11-17
> **tyke said:**
> 
I'm afraid it does involve booting into windows. Not ideal, but no one seems to know how to resolve the problem under Linux.

There's a Python script on 
[http://m0sia.ru/files/sdcopy.py]("http://m0sia.ru/files/sdcopy.py")

which changes the widescreen flag in the file header amongst other things.

---

### Post by norv on 2009-01-02
From this thread:
[https://www.linuxquestions.org/questions/linux-software-2/video-editing-how-to-change-mpeg-header-334875/](https://www.linuxquestions.org/questions/linux-software-2/video-editing-how-to-change-mpeg-header-334875/)

"I learned that mpginfo is actual an alias for mpgtx and after searching the man pages I saw something interesting- several minutes of experimentation and I ended up with this:

mpgcat -A3 videofromcamera.vob > correctedfile.vob

Only works on mpeg and variants.

---

