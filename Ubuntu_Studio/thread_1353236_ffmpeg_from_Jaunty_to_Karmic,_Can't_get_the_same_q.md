---
title: "ffmpeg from Jaunty to Karmic, Can't get the same quality!"
date: 2009-12-12
forum: Ubuntu Studio
---

### Post by ndeubert on 2009-12-12
Hey Everyone, I'm hoping some of you video file experts can help me out here because I'm at a loss now. I had Jaunty installed and I came up with an ffmpeg command that converted my video files to a reasonable quality and size for use on my website, but then I did a reinstall with Karmic and found out I needed to install the svn version of ffmpeg and x264, so I did that and had to change my command around(to use presets). Ever since I have not been able to reproduce the same smoothness video files even though the bitrates are very close. On some slower systems when I play the new video file it is very choppy where as the video file I generated in jaunty is very smooth. The image quality is fine on both of them it's just all the new files I generate are jumpy and I don't know what the difference is. I have tried playing with doing 2 passes, using the hq and default presets, using the cfr option, using the bufsize option, tweaking the birate tolerance option, changing my audio options, and I don't know what it is that causes it play so much worse. Ffmpeg with it's pretty much default settings in jaunty worked perfect.

Here is a link to the video files I am talking about along with the commands I generated them with and the output from ffmpeg -i. FYI on newer very fast machines both files play fine and look the same but the files are definitely different and I don't know what it is. [http://members.cox.net/ndeubert/](http://members.cox.net/ndeubert/)

If you want play around with encoding the original file let me know and I will give you a link to it, it's just 23MB so I don't want to post it here.

Please help if you can, thanks!

---

### Post by FakeOutdoorsman on 2009-12-12
> **ndeubert said:**
> On some slower systems when I play the new video file it is very choppy where as the video file I generated in jaunty is very smooth. The image quality is fine on both of them it's just all the new files I generate are jumpy and I don't know what the difference is.

I don't see any video jerkyness on my Linux P4, and the two MP4 files look fairly similar.  The frame rate looks low and the quality is bad, but I am assuming that is from the source file.  Provide more information to narrow the problem down:

[list][*] What are the hardware specs of these slower systems?
[*] Are these Windows or Linux machines?
[*] How are you playing these videos on these slower systems?
[*] Have you ruled out the possibility that Flowplayer might be the culprit?
[*] Are the videos choppy when playing with another Flash player like JW Player?
[*] What about non-Flash players like MPlayer or VLC?[/list]

[s]The videos playing in Flowplayer on your site are not the same as the videos linked to in "Download good/bad video".  The ones playing in Flowplayer are VP6 video with MP3 audio.  What's with that?[/s]  Nevermind.  Dumb mistake on my part.

---

### Post by Madspyman on 2009-12-12
The newest version of FFmpeg only works with the latest version of x264, and only seems to convert to x264 using a preset. Getting an older version of FFmpeg is your best bet. I'm still using a version from back in august/september (FFmpeg version SVN-r19799). It build's great in Ubuntu Karmic, and works with the version of libx264-dev in the Karmic repositories.

---

### Post by ndeubert on 2009-12-13
Thanks for your reply...

> **FakeOutdoorsman said:**
> The frame rate looks low and the quality is bad, but I am assuming that is from the source file.
The source file is a 1280x720 video from my canon sd940is point and shoot camera:
Seems stream 0 codec frame rate differs from container frame rate: 6000.00 (6000/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '../MVI_0010.MOV':
  Duration: 00:00:07.86, start: 0.000000, bitrate: 23663 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, 22954 kb/s, 30 tbr, 3k tbn, 6k tbc
    Stream #0.1(eng): Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
  Metadata
    major_brand     : qt  
    minor_version   : 537331968
    compatible_brands: qt  CAEP


> **FakeOutdoorsman said:**
>  What are the hardware specs of these slower systems? Are these Windows or Linux machines?
Well the main machine I see the problem on is my Xubuntu P4 2.8 GHz with 1GB of ram which should be plenty fast enough, but I do not see any problems on my wife's 2.4GHz iMac. I want the bitrate low so they stream well because I don't have that high of an upload bandwidth.

> **FakeOutdoorsman said:**
> How are you playing these videos on these slower systems? Have you ruled out the possibility that Flowplayer might be the culprit?
I've been testing them through flowplayer mostly, but the bottom line I was coming to is the video I made before played fine in flowplayer and I would think I should just be able to reproduce that. In most cases playing them through mplayer plays them both fine but I did have some cases where mplayer says my system is too slow.

> **FakeOutdoorsman said:**
> Are the videos choppy when playing with another Flash player like JW Player? What about non-Flash players like MPlayer or VLC?[/list]
I haven't tried jw player before, I will give it a shot tomorrow.

> **FakeOutdoorsman said:**
> The videos playing in Flowplayer on your site are not the same as the videos linked to in "Download good/bad video".  The ones playing in Flowplayer are VP6 video with MP3 audio.  What's with that?
How do you figure that? It must be flowplayer doing something to them because those are the only 2 files on the server.

---

### Post by ndeubert on 2009-12-13
> **Madspyman said:**
> The newest version of FFmpeg only works with the latest version of x264, and only seems to convert to x264 using a preset. Getting an older version of FFmpeg is your best bet. I'm still using a version from back in august/september (FFmpeg version SVN-r19799). It build's great in Ubuntu Karmic, and works with the version of libx264-dev in the Karmic repositories.

I considered installing the jaunty packages, I just wasn't sure if they would be totally compatible. Maybe I'll try that if JWPlayer doesn't work.
Thanks.

---

### Post by FakeOutdoorsman on 2009-12-13
> **ndeubert said:**
> In most cases playing them through mplayer plays them both fine but I did have some cases where mplayer says my system is too slow.

Starting at the first process and working up might be the best way to figure out what step may be at fault.  Involving Flash players can introduce problems from Flash itself (are you using the same version of Flash on both machines?), the Flash player, and the browser (same browser?) at the very least.  If MPlayer said your system is too slow to play these videos then it is probably telling the truth.

> **ndeubert said:**
> How do you figure that? It must be flowplayer doing something to them because those are the only 2 files on the server.

Oops, my mistake.  I copied the wrong files from the */tmp* directory and inspected them with FFmpeg, but didn't actually play them.  I should have known to actually play them since they were a different format.  Duh.

> **ndeubert said:**
> I considered installing the jaunty packages, I just wasn't sure if they would be totally compatible. Maybe I'll try that if JWPlayer doesn't work.
Thanks.

It's usually not a good idea to mix packages between Ubuntu releases.  There are usually more effective solutions than this.

---

### Post by Madspyman on 2009-12-13
> **ndeubert said:**
> I considered installing the jaunty packages, I just wasn't sure if they would be totally compatible. Maybe I'll try that if JWPlayer doesn't work.
Thanks.

I wouldn't recommend using an older repo version either, the version of FFmpeg I used was an older version of the source from SVN. It had originally been compiled in Jaunty, but I recompiled it in Karmic.

I tried the latest version, but it wouldn't work with libx264-dev from the repos, and when I did upgrade to the latest version of libx264-dev, FFmpeg would only convert to x264 using a preset command, and the quality was always choppy and horrible.

So I went back to the x264 version from the repos, and compiled an older version of FFmpeg. It works just like it did in Jaunty.

If you can get an older version of the source you might want to try that.

If you'd like I could tar the version I'm using up so you can try compiling it. Although, you might need to chown it first, so I'm not sure.

---

### Post by ndeubert on 2009-12-13
> **FakeOutdoorsman said:**
> Starting at the first process and working up might be the best way to figure out what step may be at fault.  Involving Flash players can introduce problems from Flash itself (are you using the same version of Flash on both machines?), the Flash player, and the browser (same browser?) at the very least.

Well the problem isn't so much that a file works on one computer and not another... it's more with finding out why 2 files of nearly the same bitrate play totally different.

Also I tried JW player and both files play pretty choppy with it. Seems like Flowplayer performs a little better for the type of files I'm using.
[http://members.cox.net/ndeubert/jw_test.html](http://members.cox.net/ndeubert/jw_test.html)

> **FakeOutdoorsman said:**
> If MPlayer said your system is too slow to play these videos then it is probably telling the truth.

Well I was just putting that out there but in this case I am using video files that play just fine in mplayer. If it didn't play well in mplayer I wouldn't expect it to in flash.

I would like to know more about the difference between these 2 files and the way I compressed them, like if the default buffering settings changed from one version of ffmpeg to another, etc. The bitrate and framerate of the 2 files are the same, so what other ffmpeg options contribute to smoothness?

---

### Post by ndeubert on 2009-12-13
> **Madspyman said:**
> I tried the latest version, but it wouldn't work with libx264-dev from the repos, and when I did upgrade to the latest version of libx264-dev, FFmpeg would only convert to x264 using a preset command, and the quality was always choppy and horrible.

Sounds like you ran into the same issue I am.

> **Madspyman said:**
> So I went back to the x264 version from the repos, and compiled an older version of FFmpeg. It works just like it did in Jaunty.

If you can get an older version of the source you might want to try that.

Yeah unfortunately I might have to do this as well. I don't particularly like using an older version of a program just because it regressed in quality or whatever the difference may be.

> **Madspyman said:**
> If you'd like I could tar the version I'm using up so you can try compiling it. Although, you might need to chown it first, so I'm not sure.
I might take you up on that offer if I can't find a good revision to go with.

Thanks for everyone's input so far.

---

### Post by FakeOutdoorsman on 2009-12-16
> **ndeubert said:**
> Well the problem isn't so much that a file works on one computer and not another... it's more with finding out why 2 files of nearly the same bitrate play totally different.

Can you make the 7 second source video available?  I just tested the videos linked from your original post and the second video does play choppy in Flowplayer on my MSI Wind netbook.

Although your two files may be of similar bitrates, the newer one may (I didn't reference your FFmpeg revision to see if this is true) utilize some new encoding features, such as weighted P-frame prediction.  These features probably abide by the H.264 specification, but the [decoder may be broken](http://x264dev.multimedia.cx/?p=212).

I can try some different encoding settings with the source file if you make it available.  I doubt there is any reason to revert to older revisions, and that may actually require more work.

**Update:** The files play smoothly in MPlayer on my netbook.

---

### Post by ndeubert on 2009-12-16
That's interesting, although it says adobe was fixed it in 10.1 and I
have 10.1 installed now so that wasn't particularly the problem.

Here's the link to the original:
[http://nickdeubert.com/media/pictures/pictures09/09-18-golf/MVI_0010.MOV](http://nickdeubert.com/media/pictures/pictures09/09-18-golf/MVI_0010.MOV)

Also interestingly I was browsing the x264 source and saw this commit
so I was going to retry it tonight and see if that made a difference
for me: [URL="http://git.videolan.org/?p=x264.git;a=commit;h=c9cafc75352f036bdcb90f2a26e7233920567b13"]Fix
two bugs in 2-pass ratecontrol[/URL]

Thanks for your help!

---

### Post by qyot27 on 2009-12-16
I think I've found the cause.  It was tricky, since mediainfo wouldn't give the full option readout for the original, non-problematic file, but it has to do with the feature set used.

The new default preset uses higher accuracy options, while the old default didn't.  Most notably, the difference is CABAC (see: [Wikipedia for more info](http://en.wikipedia.org/wiki/Context-adaptive_binary_arithmetic_coding)) - the new -vpre default is High Profile and uses CABAC, the old version output Baseline Profile, which **cannot** use CABAC (it uses CAVLC instead).  This is important, because CABAC is one of the biggest resource using features of H.264, although it does produce significant gains from the efficiency.

As a test, run the new version of ffmpeg with the *-vpre default* option set, but add *-cabac 0 -trellis 0* (or it might be *-coder 0* instead of *-cabac 0*) after it and see if you still have problems with it being choppy.


If it's anything other than that it'll be hard to diagnose because the 'good' file doesn't have its option readings stored in it like it's supposed to.

---

### Post by FakeOutdoorsman on 2009-12-16
> **qyot27 said:**
> I think I've found the cause.  It was tricky, since mediainfo wouldn't give the full option readout for the original, non-problematic file, but it has to do with the feature set used.

The new default preset uses higher accuracy options, while the old default didn't.  Most notably, the difference is CABAC (see: [Wikipedia for more info](http://en.wikipedia.org/wiki/Context-adaptive_binary_arithmetic_coding)) - the new -vpre default is High Profile and uses CABAC, the old version output Baseline Profile, which **cannot** use CABAC (it uses CAVLC instead).  This is important, because CABAC is one of the biggest resource using features of H.264, although it does produce significant gains from the efficiency.

As a test, run the new version of ffmpeg with the *-vpre default* option set, but add *-cabac 0 -trellis 0* (or it might be *-coder 0* instead of *-cabac 0*) after it and see if you still have problems with it being choppy.


If it's anything other than that it'll be hard to diagnose because the 'good' file doesn't have its option readings stored in it like it's supposed to.

Excellent investigative work.  I did a test with *-vpre hq -coder 0* and it was still choppy, but the addition of *-flags -loop* seemed to do allow it to decode smoothly.  Either of these commands should work:
```
ffmpeg -i MVI_0010.MOV -acodec libfaac -vcodec libx264 -vpre hq -coder 0 -flags -loop -crf 28 -s 1024x576 output-hq.mp4
```
or:
```
ffmpeg -i MVI_0010.MOV -acodec libfaac -vcodec libx264 -vpre hq -vpre baseline -crf 28 -s 1024x576 output-baseline.mp4
```
The first option should create a smaller file size, but I'm unsure if it requires more processing power to decode.

---

### Post by ndeubert on 2009-12-17
Wow that seems to have fixed it! Thanks so much for your help guys!

---

