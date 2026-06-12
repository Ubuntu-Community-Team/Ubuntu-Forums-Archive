---
title: "Cinelerra questions."
date: 2009-04-04
forum: Ubuntu Studio
---

### Post by GARoss on 2009-04-04
My background is video editing with Sony Vegas (versions 2-8 ). But now I'm making a go with Ubuntu & cannot install Vegas with WINE because of netFramework & DirectX issues. I can dual boot but my goal is to eliminate Windows forever.
I've checked out several editors & Cinelerra (Lumiera, too) looks like it would be similar to Vegas but it lacks codecs & plugins for multi-format editing. I tried to load a .m2t file (Sony HDV mpeg audio-video file) without success.
Others use Cinelerra, so, were do you get codecs & plugins?

---

### Post by kelvin spratt on 2009-04-04
Before you do anything with Cinelerra I suggest you download the official manual 1st
it makes things a lot easier to understand.

---

### Post by Bucky Ball on 2009-04-04
You could try converting you footage to something Cinelerra will accept or recording in a different format (more generic) if your camera is capable.

Much quicker and easier, you could investigate these options and get it working if possible:

[http://au.altavista.com/web/results?itag=ody&pg=aq&aqmode=s&aqa=cinelerra+.m2t&aqp=&aqo=&aqn=&kgs=0&kls=1&dt=tmperiod&d2=0&dfr%5Bd%5D=1&dfr%5Bm%5D=1&dfr%5By%5D=1980&dto%5Bd%5D=4&dto%5Bm%5D=4&dto%5By%5D=2009&filetype=&rc=dmn&swd=&lh=&nbq=10]("http://au.altavista.com/web/results?itag=ody&pg=aq&aqmode=s&aqa=cinelerra+.m2t&aqp=&aqo=&aqn=&kgs=0&kls=1&dt=tmperiod&d2=0&dfr%5Bd%5D=1&dfr%5Bm%5D=1&dfr%5By%5D=1980&dto%5Bd%5D=4&dto%5Bm%5D=4&dto%5By%5D=2009&filetype=&rc=dmn&swd=&lh=&nbq=10")

As for Vegas and Wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15124)

---

### Post by GARoss on 2009-04-04
Thanks, Kelvin. 
I had done so prior to my post. Being my video format is .m2t only, I'm trying to find codecs & filters that would allow me to at least load the video to the timeline to test effects as I reading through the manual. Converting the file is an option but mov & avi can get extremely large!
Banshee will play .mov movie trailers (Apple h264 codec) but not .m2v.

Bucky,
This is what I was refering to in WINE -
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3467](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3467)

I'll do more reading but there must be something out there!;)

---

### Post by babarosa on 2009-04-04
Hello GARoss,

maybe your issues with netFramework and directx can be solved using wine ([http://www.winehq.org/](http://www.winehq.org/)) in combination with wine-tricks ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)).

Video editing on gnu/linux systems to my mind largely lacks behind the other os' apps, you won't find something equal to vegas, pinnacle, vision, ... in linux.

Cinelerra and lives are very buggy, avidemux is simple and has sync problems, blender is reported to be the most advanced but never could satisfy my needs. I still do video editing on windows.

But the community is very agile developing new applications.

Regards, Michael

---

### Post by GARoss on 2009-04-04
> **babarosa said:**
> Hello GARoss,

maybe your issues with netFramework and directx can be solved using wine ([http://www.winehq.org/](http://www.winehq.org/)) in combination with wine-tricks ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)).

Video editing on gnu/linux systems to my mind largely lacks behind the other os' apps, you won't find something equal to vegas, pinnacle, vision, ... in linux.

Cinelerra and lives are very buggy, avidemux is simple and has sync problems, blender is reported to be the most advanced but never could satisfy my needs. I still do video editing on windows.

But the community is very agile developing new applications.

Regards, Michael

And hello to you, Michael!
I love Vegas, but, the reports from WineHQ;
[http://appdb.winehq.org/objectManage...ation&iId=3467](http://appdb.winehq.org/objectManage...ation&iId=3467)
indicate the preview doesn't work on v5 & nothing much works with v6-8. It would seem that wine tricks would have been tried in their testing, but, maybe not. v5 is good for DV but lacks newer support for AVCHD. HDV was good, though. 
Maybe dual boot is the only solution.:sad:

---

### Post by Bucky Ball on 2009-04-05
> **GARoss said:**
> 
Maybe dual boot is the only solution.:sad:

Advisable. As much as I might love Linux, until the powers that be port their wares to it, I will still have Windoze for Pro Tools, Cubase, Premiere Pro, Reason, blah blah ... a bit of a drag really. Trying to get tricksy with Wine to do this stuff just isn't worth it. I use Linux for Linux and Windows for Windows, personally, have never seen the point or bothered with Wine (although I see the point for needs other than my own, naturally).

At this point, my windows installs exist for one reason ... Sibelius (a music notation editor). How boring. (and no, nothing comes close in Linux ... yet!). Not like it's the community's fault; we can't force software creators to create Linux versions.

---

### Post by GARoss on 2009-04-05
> **Bucky Ball said:**
> Advisable. As much as I might love Linux, until the powers that be port their wares to it, I will still have Windoze for Pro Tools, Cubase, Premiere Pro, Reason, blah blah ... a bit of a drag really. Trying to get tricksy with Wine to do this stuff just isn't worth it. I use Linux for Linux and Windows for Windows, personally, have never seen the point or bothered with Wine (although I see the point for needs other than my own, naturally).

At this point, my windows installs exist for one reason ... Sibelius (a music notation editor). How boring. (and no, nothing comes close in Linux ... yet!). Not like it's the community's fault; we can't force software creators to create Linux versions.

I hear ya. Overall, the Linux community is great. But the things we're talking about don't exist there...yet! I'd love to avoid dual booting but what choice does one have? It's a huge mountain to climb when all one needs to do is boot XP or whatever & get to work! If I were smart enough to make it myself, I would. And, I respect those who can & do. But, these things take years & every year there's a new codec to chase down or whatever. It's easy to see why few have tried!
The silver lining is Linux is getting more popular & that popularity will drive the development.

---

### Post by Bucky Ball on 2009-04-05
> **GARoss said:**
> If I were smart enough to make it myself, I would. 

You have the right idea. If I had the time, I would certainly be putting it into developing and learning more. I would love to record and put together open-source sample libraries to use in Ubuntu Studio (among other things). But hey, I don't have a spare year right now  ... one thing I don't think I'd be developing any time though is a Linux only audio file format !

> every year there's a new codec to chase down or whatever. It's easy to see why few have tried!Partly advancing technology but also because of the divisiveness of the industry. You must have this so this will run with this and all that will cost you plenty of this $$$. Do you want to be in my gang? Of course, it would be easier if we all used a few of the most flexible and best file formats for audio and video so we were all compatible, no hassles, but that would lose too much money. 

> The silver lining is Linux is getting more popular & that popularity will drive the development.Absolutely. A combination of friendlier user experience, ease of installation, growing popularity (meaning more people get more interested and understand more then get involved in developing and ...). The list goes on. 500 heads are better than 50 and that is what it's all about. A big thing is the community spirit and support of community and developers that money can't buy. :)

---

### Post by cotcot on 2009-04-05
My workflow for using .m2t  (in my case .MTS from a Canon HF100) is to transform them in mpeg using :
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 00126.MTS -ofps 25 -fps 50 -o 00126.mpg
```
The -fps 50 is important. Use this command with mplayer compiled from svn. See [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=558538") to know how to compile the latest mplayer. 
Alternatively you can transform them to mpg with Handbrake. The latest version (I compiled it from source) has .m2t support.
Then you can go on with cinelerra or blender or so.

---

### Post by Bucky Ball on 2009-04-05
Good tip.

---

### Post by GARoss on 2009-04-06
I downloaded HandBrake & have rendered a few files that do work in Cinelerra-kinda. There's no audio & the 16x9 composer screen is weird. If you divide the 16x9 screen side to side into 4 parts- A-B-C-D you'd see B-C-D-then A on the far right side which should be on the far left! Weird. I'm sure it has something to do with preferences which I haven't figured out yet. And, the fact that HDV is 1440x1080 with 1.333 wide pixels probably has something to do with it. I'm sure it can be fixed.
I'm not sure about the audio. Perhaps a missing codec?

---

### Post by cotcot on 2009-04-07
For the audio use AC3 instead of the default AAC (you can change it in the audio/subtitles tab).
What settings do you use ? I saw some problems with mp4. I have not tried all possibilities yet. It works well with the Matroska container (MKV). 
I also see that VLC cannot play back some of the results while movie player can. So try another player as well.

---

### Post by GARoss on 2009-04-07
"For the audio use AC3 instead of the default AAC (you can change it in the audio/subtitles tab)."

In HandBrake under audio/subtitles the only option is AAC; the others are not selectable. Must need some additional plugins.
The video will play normal in Banshee. Video quality isn't the greatest but it does play. Loading the same video into Cinelerra I get no audio & well, take a look at the attached photo. I've tried several combinations of settings in HandBrake but get the same results in Cinelerra; no audio & split video.

---

### Post by GARoss on 2009-04-07
OK. Fixed the picture problem. It seems Cinelerra doesn't like the "Anamorphic" flag rendered in HandBrake. This is need for playback in mplayer or Banshee but in Cinelerra all that is needed is a 16x9 setting.
Now on to the audio issue.

---

### Post by cotcot on 2009-04-08
Missing some codecs. Try ```
sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg
```

---

### Post by GARoss on 2009-04-10
> **cotcot said:**
> Missing some codecs. Try ```
sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg
```

Didn't help.:cry:

---

### Post by cotcot on 2009-04-11
It looks like your ffmpeg is missing support for ac3. (I read a couple of days ago in this forum that ffmpeg does not use external codecs. It wants to have them compile in ffmpeg)
You could try to compile x264 and ffmpeg. [[COLOR="Red"]Here[/COLOR]]("https://wiki.ubuntu.com/ffmpeg") is a tut explaining how.

This is what I get as info on my ffmpeg ```
:~$ ffmpeg
FFmpeg version SVN-r18281, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 2. 0 / 50. 2. 0
  libavcodec    52.22. 3 / 52.22. 3
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2009 21:08:16, gcc: 4.3.3
```

Hope this brings you closer to a solution.

---

### Post by Cresho on 2009-09-02
I'm also doing video editing in ubuntu.  Cinelerra is very powerful and very easy to use.  I currently run both vegas video 8 and cinelerra under ubuntu hardy heron with no problems.  For proffesional use, I use both.  I preffer cinelerra though.

From my expirience, vegas is more buggier than cinelerra and also, I render around 100x faster videos and can also preview videos much better in cinelerra.  I also can manage effects easier.

my current workflow is..

xacti hd1000->winff->cinelerra->devede.
I recently did a sweet 15 party and took me a week to convert in vegas and dvd architect.  Using cinelerra and devede took me about 4 hours total time including video editing with transitions and effects and color correction.
Here is what I have installed
medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
akira version of cinelerra
[http://www.youtube.com/watch?v=bcBxE6m7x8w&feature=related](http://www.youtube.com/watch?v=bcBxE6m7x8w&feature=related)
here are my winff paramater
winff used from repository.

```

-vcodec mpeg1video -r 59.94 -s 1280x720 -b 20000K -acodec mp2 -ab 320k -ar 48000 -ac 2

```

all i do is throw the videos avchd into winff and it converts the files as fast as you can transfer data through the drive.  very fast.

then i load them in cinelerra and render the files using these paramaters
1.video for quicktime
2. video is mpeg4 (hit the wrench button
3. audio is mpeg4

it renders video as fast as you watch it.  It is converted to mov compliant quicktime video 6 standart i guess.

I recently updated my executable in a bash script.  I found out cinelerra in x11-opengl or x11-xv color callibration is Null and x-video settings in the nvidia drivers are none existant for this application.  It uses the x server xvideo (which is the desktop colors) that is totally uncalibrated.  I calibrated the colors and have now corrected the color brightness contrast issue that was my main problem for about a week.  I now launch cinelerra with this bash script and when i exit, it returns your desktop to normal color.

```
#!/bin/bash

xgamma -gamma .7;
Cinelerra;
xgamma -gamma 1.0
```

i also created 2 buttons with these xgamma to correct the desktop when i have cinelerra rendering my videos incase i want to read news while i wait my few minutes instead of days from what vegas video 8 or 9 takes.  I think that vegas is rediculous.

hope this helps a few of you.

Once you understand the real power behind cinelerra, you will wonder WHY!  why does vegas cost so much!

---

