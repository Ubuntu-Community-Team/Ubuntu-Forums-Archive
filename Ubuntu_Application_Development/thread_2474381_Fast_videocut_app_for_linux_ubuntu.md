---
title: "Fast videocut app for linux /ubuntu"
date: 2022-04-27
forum: Ubuntu Application Development
---

### Post by Kanehekili on 2022-04-27
I'd like to introduce an application for cutting videos. The cutting is lossless and more precise than the standard ffmpeg tools. [VideoCut]("https://github.com/kanehekili/VideoCut") is using its own muxer (based on the ffmpeg libavcodec libraries), the gui uses mpv to display the video frames. It has been developed for Ubuntu and can be downloaded from my [ppa]("https://launchpad.net/~jentiger-moratai/+archive/ubuntu/mediatools").

It the common codecs, is tested on old and new hardware, is mature and should be very fast.

---

### Post by TheFu on 2022-04-27
Nice.  I'll check it out.

Similar GUI tools are VidCutter and LosslessCut.  I know there are AppImages for both.  

**VidCutter** seems to be missing dependencies both in the AppImage and Snap package. It worked for about 6 months, but then stopped.  Some Qt dependencies were missing which sorta defeats the usefulness of the all-in-one packaging answers.

I've been using **LossLessCut** after a fix that made saving anything was fixed earlier this year.  I wish it had cut-point start-end settings with the left-hand (F3/F4 would be great!) and moving within the video using the right-hand only - arrows, shift-arrows, cntl-arrows to control the jump distances. cntl-arrows jump based on the total length of the video - which seems like a good idea - except that it isn't.  I'd let the author know on github, but since it became a MSFT owned property, I just can't use it for personal reasons.

For a video editor, snaps are generally useless. Videos that can only be access if they happen to be in a HOME directory breaks lots of workflows.

I would like to say that using ffmpeg for edits when no transcoding is involved/desired is extremely slow compared to using mkvmerge. If the output container will always be mkv, there's no need for ffmpeg - which seems to use a 2-step mode for cuts, then merging those cuts into the final output.  mkvmerge does it in 1 step - as fast as a file copy.  

Anyway, added your PPA and will check out the software soon.  Hey - what's the name of the videocut package?  I tried both videocut and VideoCut.  
**apt search videocut** returns nothing.

---

### Post by TheFu on 2022-04-27
FYI:
```
sudo add-apt-repository ppa:jentiger-moratai/mediatools
sudo apt update
$ sudo apt install --no-install-recommends videocut
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package videocut

```

BTW, the instructions on github have an extra 'install' in the command.
```
$ lsb_release -d
Description:    Ubuntu 18.04.6 LTS
```

---

### Post by Kanehekili on 2022-04-30
Due to some dependency problems of mpv I've refrained from building it for 18.04. Focal and jammy are supported. Thanks for trying though. 

Other than that you did everything right. 

You could download the the tar file from git, unpack it, open a terminal in the unpacked folder and execute
> sudo ./install.sh.
Make sure to install the dependencies like:
> sudo apt –no-install-recommends install python3-pyqt5 ffmpeg python3-pil libmpv1 

But the mpv Version I'm using is not available on bionic (library to old) . So running will fail with mpv. Using opencv (VideoCut -p cv) will work with the ffmpeg muxer, since remux is compiled against libav V4 and libav V5 - bionic provides libav V3 (a developers nightmare). 
 

And you are correct: Vidcutter and Videocut a similiar. But I was not satisfied with the quality of the ffmpeg cuts (which Vidcutter and other tools use) So most of the R&D went into the muxer, that replaces ffmpeg.

"no-install-recomends" is not supported by bionic ...

---

