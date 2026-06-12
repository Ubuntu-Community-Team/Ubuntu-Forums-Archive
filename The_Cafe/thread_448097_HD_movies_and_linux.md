---
title: "HD movies and linux"
date: 2007-05-18
forum: The Cafe
---

### Post by juxtaposed on 2007-05-18
Well, I have some H.264 720p HD movies, and on windows they ran fine (even if it did take a bit to seek through the movie). In ubuntu however they were choppy in VLC, and totem showed a big part of the movie as green (maybe incomplete h.264 support, I don't know). However, on Debian, they work fairly great in VLC (even with swiftfox taking up 130MB RAM). Even better then windows (it takes 1-3 seconds to seek, compared to just under 10s in windows)

I find that very odd. This is good since I don't have to go into windows to watch HD movies :D

What has everyone elses experiences been with HD movies in linux? Did it run better or worse then windows? Did any particular linux distro beat any other that you've tried?

I think very intensive HD movie playing could be a good way to compare the bloat or speed of different distros. I'd particularly like to test Fedora, FreeBSD (or another BSD), SUSE, and Gentoo. It might be hard to get it turned into hard stats to put on the internet, but it would show me the difference with the feel of everything when playing HD movies.

---

### Post by Polygon on 2007-05-18
what exactly do you mean by hd movies?

Like a .mpeg or .xvid that is just the resolution of a HD movie with 720 progressive?

---

### Post by WalmartSniperLX on 2007-05-18
Tweak some xorg settings or change to a different decoder or codec?

---

### Post by juxtaposed on 2007-05-18
> Like a .mpeg or .xvid that is just the resolution of a HD movie with 720 progressive?

H.264 matroska files with a resolution of 1280x720.

> Tweak some xorg settings or change to a different decoder or codec?

What do you mean?

I wasn't asking how to play them, I was asking others what they're experience with them was in linux, as HD movies are very demanding on your computer.

I noticed a difference between performance on different OSes and I thought it might be a good thing to do to test how fast/efficient different OSes (and distros) are.

Though perhaps I was wrong, debian doesn't run them aswell as windows. It does for awhile, then the picture stops for a few seconds, then it is fine again. Still better then ubuntu. Maybe VLC is more optimized for windows.

---

### Post by reacocard on 2007-05-18
> **juxtaposed said:**
> H.264 matroska files with a resolution of 1280x720.

I wasn't asking how to play them, I was asking others what they're experience with them was in linux, as HD movies are very demanding on your computer.

I noticed a difference between performance on different OSes and I thought it might be a good thing to do to test how fast/efficient different OSes (and distros) are.

Though perhaps I was wrong, debian doesn't run them aswell as windows. It does for awhile, then the picture stops for a few seconds, then it is fine again. Still better then ubuntu. Maybe VLC is more optimized for windows.

Is there anywhere I can download a short video at this resolution? I'd like to test it myself.

EDIT: Google to the rescue: [http://www.highdefforum.com/showthread.php?t=6537](http://www.highdefforum.com/showthread.php?t=6537)
Mostly WMV, but there's some DivX too. I'll post back after I've tested.

---

### Post by BarfBag on 2007-05-18
What kind of graphics card do you have?  Which graphics driver are you using?

---

### Post by juxtaposed on 2007-05-18
> Mostly WMV, but there's some DivX too. I'll post back after I've tested.

DivX would probably be easier on resources, though not as good quality as H.264.

> What kind of graphics card do you have? Which graphics driver are you using?

ATI X200 (or 300, or something) Integrated. On debian I don't have the ATI driver installed (I think it is using Mesa or something) as it seems hard, I will probably try in the next few days. I had fglrx on ubuntu working fine with 2d accleration (though it supports Directx better then opengl).

> Is there anywhere I can download a short video at this resolution? I'd like to test it myself.

There are probably some trailers or something on apples website, though I havn't looked or anything. I don't know if they would use less resources then a full length movie would though.

---

### Post by reacocard on 2007-05-18
> **juxtaposed said:**
> There are probably some trailers or something on apples website, though I havn't looked or anything. I don't know if they would use less resources then a full length movie would though.

It's the same resources either way, if its the same resolution and format. I just want a short one because my internet connection is slow, only 256kbps. I'm downloading one right now ([http://trailers.divx.com/Dreamworks/Madagascar_HD.zip](http://trailers.divx.com/Dreamworks/Madagascar_HD.zip)), and I'll post back after testing. Currently it's about 70% downloaded, so it'll be another 10 minutes or so.

---

### Post by WalmartSniperLX on 2007-05-18
> **juxtaposed said:**
> H.264 matroska files with a resolution of 1280x720.



What do you mean?

I wasn't asking how to play them, I was asking others what they're experience with them was in linux, as HD movies are very demanding on your computer.

I noticed a difference between performance on different OSes and I thought it might be a good thing to do to test how fast/efficient different OSes (and distros) are.

Though perhaps I was wrong, debian doesn't run them aswell as windows. It does for awhile, then the picture stops for a few seconds, then it is fine again. Still better then ubuntu. Maybe VLC is more optimized for windows.

I haven't had any problems except once when I was using Fedora and an old Ati gpu with open drivers. Movie was extremely slow (the HD Elephants Dream movie). Other than that I havent had any probs (even with Ubuntu). My guess is that its the GPU/drivers in contrast with the xserver. Sorry if I was off topic. I was suggesting a way to help fix your problem.

---

### Post by ricrac on 2007-05-18
mplayer- 1.0-rc1-0ubuntu9   with -cache 1000000,   that's 1,000,000  needs to be > 256000
H.264
amd64, 3700 w/4gb ram
dual nvidia 6600gt using nvidia current drivers
alsa 
ubuntu studio base system

Coming to america trailer 1080p
The Magic of flight 1080p

No problems, with idle mysql, apache, and numerous other things "running".


I set my mplayer cache high because I have 3 monitors and tv out and like to surf while watching background fluff.  Some web pages cause firefox to incur heavy loads and can cause sync issues, skips or framedrops if cache is not used.

---

### Post by juxtaposed on 2007-05-18
> Sorry if I was off topic. I was suggesting a way to help fix your problem.

Oh, no, i'd certainly like help with that, I thought you thought I was asking how to play them or something.

Now I feel stupid for not realising that :P

> I haven't had any problems except once when I was using Fedora and an old Ati gpu with open drivers. 

That sounds like this situation. So i'll see if I can get the normal driver installed tommorow.

---

### Post by reacocard on 2007-05-18
Here's my results with an MPEG4 (DivX) movie at 1280x720.

Initially, the player (Totem or Xine, using Xvideo) just crashes when I try to open the file. Running the player from a terminal shows that the Xserver doesn't have enough memory to play the file. After adding
```
 Option "LinearAlloc" "6144"
```
To the "Device" section of my xorg.conf as suggested on the [i810 driver page]("http://intellinuxgraphics.org/man.html") (I have i915GM graphics) and restarting X, the video plays back perfectly. On my Pentium M at 1.7 Ghz, it takes about 30% CPU, and at 600 Mhz, about 80%. Video is perfectly smooth, no choppiness, skipped frames, artifacts or anything else at either speed. Seeking is almost instantaneous.

EDIT: Just retried with an H.264 video at the same resolution, it gives the exact same results.

I would test with VLC, but VLC has never worked well for me. The video driver never works properly unless I use Xshm, in which case it eats CPU.

---

### Post by jiminycricket on 2007-05-18
Since it works in Debian, you may have to see what changes there are in the VLC from Ubuntu repositories.  Or compare xorg versions and configurations.

---

### Post by pmj on 2007-05-19
Windows users have CoreAVC, which is by far the fastest (if not the most accurate) h.264 decoder. Linux is generally pretty far behind Windows in this area, which is a damn shame.

Why it worked better for you on Debian than Ubuntu, though, I don't know.

---

### Post by dodgePT on 2007-05-19
Well, i always thought that linux was light years away from windows when it comes to multimedia. Well, maybe not light years away, but some miles for sure.

I tried everything to get good XviD/DivX quality playback, and although i can watch movies ("normal" ones, not HD), quality's never that good as in windows. It seems to me that windows codecs do a better job when decoding then those from linux.

Overall image quality just seems a bit blurry and has some flickering on some spots.

As an example i have attached a snapshot taken with xine, which is the player that gives me better results. This same image in windows looks more sharp and with no blur at all.

BTW, post processing is maxed, but that blur i talked about happens with all post processing settings. I have an ATI 9600 pro, maybe that's the problem... :(

---

### Post by juxtaposed on 2007-05-19
> Windows users have CoreAVC

I could never get that installed for some reason in windows. I have no idea why.

> It seems to me that windows codecs do a better job when decoding then those from linux.

For me, in ubuntu, video had the odd effect that I think came with interlacing or something. And it was more pixel-y (not pixelated like in a low video bitrate, but the pixels were more visible and harsher).

It looks perfectly fine in debian:

[[IMG]http://img252.imageshack.us/img252/9379/vlcsnap1617054fr2.th.png[/IMG]](http://img252.imageshack.us/my.php?image=vlcsnap1617054fr2.png)

[[IMG]http://img259.imageshack.us/img259/4559/vlcsnap1617326vn7.th.png[/IMG]](http://img259.imageshack.us/my.php?image=vlcsnap1617326vn7.png)

---

### Post by screaminj3sus on 2007-05-19
Downloaded the HD madagascar one posted earlier and it worked fine, even when moving windows around the cube in beryl, system was perfectly responsive.

---

### Post by pmj on 2007-05-20
> **screaminj3sus said:**
> Downloaded the HD madagascar one posted earlier and it worked fine, even when moving windows around the cube in beryl, system was perfectly responsive.

That's not so strange, since DivX of such low resolution can be played on computers that are several years old.

I just got a neat surprise. I still run Edgy, and I have had trouble with 1080p h.264; they were simply not playable on my Core 2 Duo E6600. I recently upgraded both mplayer and ffmpeg and I installed SMPlayer, and one or more of these made h.264 decoding quicker and made it possible for me to finally watch Ghost in the Shell 2 in 1080p, which, for the most part, looked absolutely amazing. Hopefully the speed improvements are in the versions you get with Feisty.

I think that the versions of the players and decoders is a much bigger factor than the rest of the distro. If you tried Ubuntu a couple of months ago, it was probably quite a bit slower than a very up-to-date Debian because of this.

---

### Post by juxtaposed on 2007-05-20
> I recently upgraded both mplayer and ffmpeg and I installed SMPlayer

I should try that, if I have old versions. Lenny isn't that up to date anyway, Ubuntu Feisty is probably much more up to date. Lenny doesn't have the newest Gnome or XFCE.

> 
I think that the versions of the players and decoders is a much bigger factor than the rest of the distro. If you tried Ubuntu a couple of months ago, it was probably quite a bit slower than a very up-to-date Debian because of this.

I think I installed Debian about a week ago, and did HD in ubuntu a bit before that.

---

### Post by Amorphous_Snake on 2007-05-21
I have a similar problem. I download lots of HD trailers from gametrailers.com and also through Steam. Resolution is mostly 1280x720 and file type is WMV. The thing is that they run fine in Windows using the codecs that I installed and any player (except VLC) and in Linux (Ubuntu) they ran fine in Totem with Xine, but not with GStreamer (but they ran later on, but not as good under Xine, after installing win32codecs).

The problem is that VLC runs them very, very slow and the quality is choppy. I tried it in Ubuntu, Windows XP and Windows Vista and I still get the same results.

What's wrong?

---

### Post by pmj on 2007-05-21
> **Amorphous_Snake said:**
> I have a similar problem. I download lots of HD trailers from gametrailers.com and also through Steam. Resolution is mostly 1280x720 and file type is WMV. The thing is that they run fine in Windows using the codecs that I installed and any player (except VLC) and in Linux (Ubuntu) they ran fine in Totem with Xine, but not with GStreamer (but they ran later on, but not as good under Xine, after installing win32codecs).

The problem is that VLC runs them very, very slow and the quality is choppy. I tried it in Ubuntu, Windows XP and Windows Vista and I still get the same results.

What's wrong?

Gstreamer has (or had) some kind of bug that made many wmvs not playing smoothly. VLC and mplayer both use ffmpeg, but for some reason they don't decode video at the same speed. Perhaps it's the level of post processing or something, but I don't notice any difference in quality. When I tried a 1280x720 wmv file from gametrailers.com just now, mplayer (via SMPlayer) used about 11% and VLC 40% of my CPU.

So try SMPlayer. There's no reason you shouldn't use it anyway.

---

### Post by Amorphous_Snake on 2007-05-21
> **pmj said:**
> Gstreamer has (or had) some kind of bug that made many wmvs not playing smoothly. VLC and mplayer both use ffmpeg, but for some reason they don't decode video at the same speed. Perhaps it's the level of post processing or something, but I don't notice any difference in quality. When I tried a 1280x720 wmv file from gametrailers.com just now, mplayer (via SMPlayer) used about 11% and VLC 40% of my CPU.

So try SMPlayer. There's no reason you shouldn't use it anyway.

I use MPlayer when I am in Linux. But I want to use VLC in Windows! I know that MPlayer can run in Windows, but is there anyway to make VLC run these movies.

My PC is not that ancient. It's a 2.4 GHz P4 with 1 GB RAM.

---

### Post by Sunflower1970 on 2007-05-21
I was having a bit of trouble, myself with an HD movie..it was showing up a bit green, pixely,and choppy in all the other players etc..Installed SMPlayer after reading this thread, and the movie now plays fine. No green-ness, not pixely, it's (almost) perfect...Sound will get off-track a bit, but that may be due to the computer being a P4 2.2 Ghz...

---

### Post by prizrak on 2007-05-21
Never had a problem with totem, streaming was slow but downloads ran just fine.

---

### Post by juxtaposed on 2007-05-21
I just installed smplayer (wow, I compiled something for the first time :)) and it seems to run HD movies fine... At least it seeks almost instantly.

---

### Post by wmcbrine on 2007-05-22
The problem I have with HD clips is that my Xv windows will only go up to 1024x1024, so the right is cut off. (This is with a Matrox G400.) So, I do a rescale from the command line to play them, and also drop frames when needed:

mplayer -vf scale=1024:1024 -framedrop clip.mpg

(Scale factor varies... often I use 720:480, i.e. DVD resolution.)

---

### Post by reacocard on 2007-05-23
> **wmcbrine said:**
> The problem I have with HD clips is that my Xv windows will only go up to 1024x1024, so the right is cut off. (This is with a Matrox G400.) So, I do a rescale from the command line to play them, and also drop frames when needed:

mplayer -vf scale=1024:1024 -framedrop clip.mpg

(Scale factor varies... often I use 720:480, i.e. DVD resolution.)

You probably just need to tweak something in your xorg.conf, as I did (see above).

---

### Post by fatboysmith on 2007-06-16
I also have trouble playing back h.264 1080p movies.  My rig is very fast, (2GB DDR, Opteron 180 oc to 2.8, 7800GTX X 2 SLI, etc.) I am running 1680x1050, 16:10 A.R.   Playback is choppy and audio/video gets out of sync quickly, with lots of frame dropping. I prefer to use VLC for most everything, but Mplayer is the only player that I've found that works. The only solution I've found is to edit .mplayer/config and add the following line;

> lavdopts=fast=1:skiploopfilter=nonkey:threads=2

This will reduce the quality to about the quality of a standard DVD/MPEG2 video.  

Mplayer website describes in detail the lavdopts options.

(obviously if you don't have a dual core cpu, remove the threads option, although some claim that this option is ignored.  My personal observation, using the System>Administration>System Monitor is that both cores are run anywhere from 15 to 70 percent, during playback)

I wonder if a x.264 hardware enabled video card such as 8800 would improve playback.

Dennis

[www.georgianerd.com](www.georgianerd.com)

---

### Post by jjacobs2 on 2007-06-18
Does ffdshow have SMP support yet?  I thought they didn't so when you used a dual core processor it would only use one core.

---

### Post by fatboysmith on 2007-06-19
I read that same fact on mplayer website.  My personal observation has been though that during playback of h.264 encoded video (usually in a mkv wrapper), that both cores would fluctuate up and down from 15 to 70%, kind of like a DNA chain.  I don't know, this may be a function of the SMP kernel and not ffdshow.

Dennis

[www.georgianerd.com](www.georgianerd.com)

---

