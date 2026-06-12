---
title: "Ubuntu 22.10 VLC black screen"
date: 2022-10-03
forum: Ubuntu Development Version
---

### Post by bert.ram.aerts on 2022-10-03
I have upgraded Ubuntu 22.04 to Ubuntu 22.10 beta last Friday evening on my Lenovo laptop.
I have nVIDIA drivers 515.65.01 for GeForce GTX 2060 Mobile.
I still use Xorg X11 and not wayland and I use gnome.
When I start VLC there is no image, just black screen.
But when I stop VLC, there is a flash of an image from the video.
I removed .config/vlc and .config/share/vlc, didn't halp.
I switched Tools / Preferences / Video / Output == VDPAU output and get:

```
bert@legion5ubuntu:~/.local/share/vlc$ vlc
VLC media player 3.0.17.4 Vetinari (revision 3.0.13-8-g41878ff4f2)
[0000555c504ad550] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0000555c5054cf60] main playlist: playlist is empty
[00007fd0280011b0] mp4 demux: Fragment sequence discontinuity detected 1 != 0
[00007fd03001d220] main video output error: video output creation failed
[00007fd028c03d00] main decoder error: failed to create video output
[00007fd028c03d00] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  515.65.01  Wed Jul 20 13:42:26 UTC 2022 for hardware decoding
QObject::~QObject: Timers cannot be stopped from another thread
```

---

### Post by zebra2 on 2022-10-03
I have the same problem on my Intel system using Gnome 43/Wayland. Doesn't matter if it is Deb or Snap VLC.

This is just one of many (not ready for prime time) problems right now. I don't call it a bug since the problem most likely has nothing to do with the app.
Running 22.10 right now should only have being interested in the difficulties of running an unfinished project as being your objective. 

22.10 not ready for normal use.  Testing Only!! 22.10 has not been released for daily use!!  Don't install expecting your desires to be fulfilled!! 

Note: some of these problems may persist past the release date. FYI

---

### Post by guiverc on 2022-10-03
FYI: I've seen discussion in -devel channels on IRC related to this. Part of discussion was tracking down cause in hopes of finding fix, but I only noted the topic/discussion & not the detail thus cannot provide any advice  (*it was noted the 30th Sept first that I see on iRC*; *I've not had time to test & thus look at it*).

---

### Post by zebra2 on 2022-10-03
I just booted the 5.19.0-15 kernel just out of curiosity and no deal.  In fact with that kernel nautilus won't navigate the folders. Back on 5.19.0-18 now.

---

### Post by IanW on 2022-10-04
Having exactly this problem too.
I did notice "sudo apt autoremove" deleting some libavcodec files just before it happened, but thought it was because newer ones had been installed.
This was not in fact the case.
As a workaround, I installed smplayer. That plays videos fine.

---

### Post by zebra2 on 2022-10-04
reinstalled with latest 22.10 ISO (Oct 4).
smplayer works with Deb. Won't open with Snap, 
VLC Deb opens for .m4v  , black screen with .mpg, doesn't open at all for anything else.  VLC Snap won't open at all. 

and oddly enough Firefox snap installed by the system default won't open. 

Snap-store opens and works just fine but is seems that what it installs doesn't work so far.

5.19.0-19-generic kernel.
I will keep testing.

PS: However everything that works is flowing smoothly with the new kernel. No glitches with what is working.  Brave.deb, Office, smplayer deb  etc.

---

### Post by zebra2 on 2022-10-04
Just got a load of VLC plug-ins on an update.  VLC Deb now working properly.  Think I will purge it and try installing the Snap.

---

### Post by zebra2 on 2022-10-04
Removed VLC deb and Installed VLC Snap.  Snap doesn't work.
Reinstalled VLC Deb with plugins and it is working just fine.

---

### Post by helicase on 2022-10-04
Same problem here. My workaround for now is starting VLC without interface from the terminal with the command "cvlc"

---

### Post by helicase on 2022-10-04
> **zebra2 said:**
> Just got a load of VLC plug-ins on an update.  VLC Deb now working properly.  Think I will purge it and try installing the Snap.
Now partly works for me with these updates. Strangely, some videos work while others with the same codec don't.

---

### Post by zebra2 on 2022-10-04
Right now I'm using the deb VLC which is up to date on my 22.10. When I reinstalled this morning I used the "Pending" ISO.   I am just trying to run the snap applications where available since they are default in 22.10. 
It is just messed up right now and I am tolerant of that.

---

### Post by guiverc on 2022-10-04
Please note:  This should be read as *hearsay* ... only time will tell what will happen.

An upstream (Debian) maintainer has advised Ubuntu *dev(s) *to *drop* VLC from future releases.

-*** ffmpeg4*** has been dropped from Debian (*thus Ubuntu*),
- ***ffmpeg4*** & ***ffmpeg5*** cannot co-exist
- there are *VAAPI* problems with ***ffmpeg5 *******thus VLC issues on *kinetic *with some files

A solution maybe using MPV (*or other alternative(s)*)instead, as general discussion on iRC (dev rooms, esp. *flavors*) seem to indicate there maybe **no easy solution**, esp. given how late (*beta & thus already frozen*) in the cycle we are, and no solution(s) seem to be available upstream (*except time to look for replacement*). 

Note:  I have no crystal ball** **and all of this could change with time.  We'll probably only see what happens next *cycle* (ie.* ll or whatever codename will become 23.04*). Please do note I'm also no expert here!

---

### Post by bert.ram.aerts on 2022-10-05
After the updated VLC packages of this morning, VLC works again. 

I've put back [COLOR=#000000]*VLC preferences video output to Automatic and hardware acceleration to Automatic. *[/COLOR]

---

### Post by MyMurry on 2022-10-05
I have still no video (intel).

---

### Post by mIk3_08 on 2022-10-06
> **MyMurry said:**
> I have still no video (intel).
In my case I just deleted the "vlc-qt-interface.conf" and "vlcrc" under home /home/username/.config/vlc/vlcrc and if you haven't seen it because by default the folders are hidden just press ctrl+h then it will appear all the hidden folders/file under home window then after you successfully deleted the files do a restart. The vlc restarted just like fresh install then it plays the video again. Regards and cheers.

---

### Post by zebra2 on 2022-10-06
> **mIk3_08 said:**
> In my case I just deleted the "vlc-qt-interface.conf" and "vlcrc" under home /home/username/.config/vlc/vlcrc and if you haven't seen it because by default the folders are hidden just press ctrl+h then it will appear all the hidden folders/file under home window then after you successfully deleted the files do a restart. The vlc restarted just like fresh install then it plays the video again. Regards and cheers.

+1 Thanks!!  Works for me. May be a hold over due to reinstalling but leaving /Home intact. Also, I have become enamoured by SMPlayer since the discussion in this thread.  I find it to be my # 1 goto right now. Don't know how it compares to VLC since I'm not a advanced user of video but it has a drag and drop utube video player that I like.

---

### Post by MyMurry on 2022-10-06
Works for me too.

Thanks

---

### Post by IanW on 2022-10-10
Thanks for this. VLC is back in operation here too!

---

### Post by IanW on 2022-10-17
CORRECTION - recent updates have resurrected this problem. I have to delete the config files _every time_ I start VLC.

TL;DR - I've now moved to smplayer

---

### Post by VValdo on 2023-04-05
YMMV, but in the new beta for ubuntu 23.04, the black screen went away in VLC.  Instead, I saw this error:

[FONT=Courier New]libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_1_0
zsh: segmentation fault  vlc[/FONT]

This lead me to try [FONT=Courier New]vainfo[/FONT] which also crashed similarly.

However, setting this...
[FONT=Courier New]
export LIBVA_DRIVER_NAME=vdpau[/FONT]

Seemed to fix the issue and vlc (from the command line after this is set) is finally working when it didn't work reliably in 22.10.

(posting in case anyone in the future sees this error and wants to try it...)

---

