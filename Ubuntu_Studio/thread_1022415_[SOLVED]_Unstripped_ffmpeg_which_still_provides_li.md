---
title: "[SOLVED] Unstripped ffmpeg which still provides libavcodec-dev et. al.?"
date: 2008-12-26
forum: Ubuntu Studio
---

### Post by Ng Oon-Ee on 2008-12-26
Hi all,

I'm looking for a way to get ffmpeg installed with all supported video formats, including the proprietary formats not installed in the stripped version in the official Ubuntu repos.

My constraints are that I need to have libhighgui-dev (and the other OpenCV packages) installed for my work as a student, developing vision algorithms. These depend on libavcodec-dev, among others. Which depends on libavcodec, the stripped version. Which nerfs my ffmpeg to the point that it won't convert much of anything at all.

I'd previously compiled ffmpeg from source, following [this great guide]("http://ubuntuforums.org/showthread.php?t=786095") by FakeOutdoorsman. Unfortunately it then conflicts with the OpenCV packages, in terms of some packages, specifically:-
```
/usr/lib/pkgconfig/libavutil.pc
/usr/lib/pkgconfig/libavcodec.pc
/usr/lib/pkgconfig/libavformat.pc
```

So, I'm trying to see what I can do to get my unstripped ffmpeg and developmental opencv side-by-side. Here's my ideas so far:-

1. Compile ffmpeg in such a way as to provide libavcodec-dev et. al. Am not sure if this is possible, or how to do it, help welcome.
2. Extract a stand-alone ffmpeg executable, does it still depend on other packages to be installed in my system? That is, can I copy the binary out and use it without other packages? Or a folder, for example.
3. Download OpenCV's source and add it to my 'includes' when compiling, I haven't been able to get this to work though, not sure what else I have to do besides linking to the directory itself.

Anyone got any ideas on this topic? Help very much appreciated.

---

### Post by Ng Oon-Ee on 2008-12-26
As lame as it is to answer my own question, I've discovered that 2. is possible, that the executable itself will do what I need (convert videos and audio).

So, I followed FakeOutdoorsman's guide as linked to in my OP, up till installing ffmpeg. After that I remove it with ```
sudo apt-get purge ffmpeg
```. Checkinstall creates a .deb file, which I open in an archive manager and extract ffmpeg/ffplay/ffserver from, copying them to /usr/bin. I won't be able to compile using ffmpeg, this way, but I don't, anyway.

Alternatively, I could have just copied out the executables from /usr/bin before purging ffmpeg. But either way, I'm left with functional video/audio conversion and I'm still able to install dev files for OpenCV, so I can continue with my studies.

Good day, everyone.

---

