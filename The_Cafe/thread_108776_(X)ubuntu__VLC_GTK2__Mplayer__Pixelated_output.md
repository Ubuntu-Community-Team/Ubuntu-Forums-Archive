---
title: "(X)ubuntu / VLC GTK2 / Mplayer / Pixelated output"
date: 2005-12-27
forum: The Cafe
---

### Post by pelle.k on 2005-12-27
Hiya all.

I've been up all night long, trying to get some multimedia stuff working.

The default vlc works all right, and it seems i can have a smooth output by using the openGL module as video output. I thought XVideo would do the trick, but it didn't. Maybe because it's not activated? xvinfo says no adapters on screen 0...
Maybe i should add that the pixelated output seems to be a problem after installing the 8.16.20 fglrx driver from the respitories.
GTK2 is not working on vlc from universe respitories though! That sucks very much. But i did find a deb named "vlc-with-vc1.deb" with GTK2 working. Only to find it couldnt find a suitable access module to open ''. It doesn't seem to handle chosen files very well. So i gave up on VLC until a backport can be found (currently there are an updated powerpc and amd64 version made availiable though:( )

I'm a fan of ffmpeg/libavcodec (I use ffdshow as the ONLY codec in windows xp), so  i figured gstreamer with ffmpeg and some other stuff would make my life easier. But nooooo. Mplayer won't start. It complains about not getting a response from dbus fast enough, and telling me my video sink is busy. which it is not.
I'm sure this is a XFCE realted issue though. But it's too bad because i can't seem to find another good gstreamer based videplayer though!

xfmedia rocks though. Just the lightweight mp3-player i want!
I installed thunar yesterday, and I must say I like it A LOT...

---

### Post by poofyhairguy on 2005-12-27
My advice? Install Gxine. Then go in its preferences and select the "Master of the Known Universe' option. Then go to the video preferences and set post processing as high as you can.

I do the opposite to get videos to run well on my older machines.

---

### Post by elustran on 2008-03-20
I'm having basically the same problem here... tried installing gxine, but it won't even run.  Why the hell does nothing work?  VLC at least runs...

---

