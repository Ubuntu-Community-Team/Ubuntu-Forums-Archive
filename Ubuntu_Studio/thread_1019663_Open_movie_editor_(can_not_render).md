---
title: "Open movie editor (can not render)"
date: 2008-12-23
forum: Ubuntu Studio
---

### Post by snappy46 on 2008-12-23
I think that open movie editor is awesome for my 10 year old kid; it's easy to use and he was up and running within minutes.  The software runs ok but I can not render any video created. When trying to render the software crash calling an illegal instruction. I tried various video and audio coding.  It also tell me that audio codec Faac and Lame is missing which I know its not since I recompile libquicktime from source and lame and faac were available during the compile.  I also tried to compile open movie editor from source but I was not able to do so.  I am missing the Gmerlin library which I don't seem to be able to install from source (reasons unknown it just stop during the make command).

I know there are other program out there but they are much more complicated (Lives and cineralla) and I much prefer the simple open movie editor.

Does anyone has been able to gets open movie editor to work properly (with rendering) in Ubuntu.  I am using Ubuntu 8.10.

Any help will be appreciated.

Thanks.

---

### Post by fritsmartfu on 2008-12-23
Did myou try this link:
[URL="http://propirate.net/repos/openme-developers/doc/tutorial.html"] ?

I have installed the open movie editor but I'm (still) not experienced.
As the link shows, under the "project" tab there is realy a render possibility.

Succes!

---

### Post by snappy46 on 2008-12-23
Thanks for the link but I have no problem doing any of what is mentioned on that site except for the rendering part.

I know the program is capable of rendering it's just that when I try the program crashes with no other indication than illegal instruction was perform.

---

### Post by kayosiii on 2008-12-23
Things to try...
1) open openmovieeditor from a terminal window and see if any additional information about the crash is posted there.

2) hit the + symbol in the render window and see if a different combination of settings causes the same issues - especially try different containers mov,avi etc...

Hope that helps

---

### Post by snappy46 on 2008-12-27
Hi,

I ran open movie editor from the terminal; this is where I got the Illegal instruction error.  I tried quite a few different setting to render mov, avi etc... I did not try all the possible settings; but quite a few of them with the same result. Also there is a check box under the render menu where you should be able to select whether or not you want audio rendering and another box for video rendering.  I was going to disable one of them to try to see if the video or audio is causing the problem but unfortunately this option does not seem possible since the two check box (video and audio) are gray out and I do not have the option to disable either.

Thanks

---

### Post by daemon3 on 2009-01-01
Hello, I've had trouble with Open Movie Editor as well.  I'm able to render, but when I do, the rendered video turns out really jumpy, no matter what video format I use.  The raw video (AVI) runs smoothly, however.

There really seems to be no good video editor for Linux.  KDEnlives renders the video but any sound is out of sync.

I'm in the process of trying LiVES.  I can't drag and drop videos, so what's the point?

---

### Post by snappy46 on 2009-01-02
Hello daemon3; I tried quite a few linux software video editing software with various success.  I just don't seem to be able to find one that will work great and is easy enough for my 10 year old. I just wish that there were something like window movie maker around for linux.  Oh well! I can use window movie maker with virtual box and that way I don't need to reboot.

I hope that soon more and more software companies will see the benefit of offering software for the linux system.  I am sure that as more people use Linux the software companies will start to acknowledge it more as a developing platform.  They are better see the light soon though; because the open source software just keeps on getting better and better so why pay for software when a free version is available.

Anyhow let me know if you ever find a solution.  I have also tried KDEnlives, Lives and cinelerra but I find them quite complicated and sometimes do not even do a better job than open movie editor.

Thanks

---

