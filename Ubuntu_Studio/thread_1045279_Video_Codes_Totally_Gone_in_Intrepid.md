---
title: "Video Codes Totally Gone in Intrepid?"
date: 2009-01-20
forum: Ubuntu Studio
---

### Post by HalNineThousand on 2009-01-20
I'm quite frustrated and have been trying to solve this problem for a while, using different resources.  My goal is simple: I have .mts files from an HD camcorder that I want to transcode to 2 different .mp4 files, one in 16:9 and one in 4:3 so I can put it on DVD for friends that don't have other ways to view the files.  I am a ballroom dancer at a small studio and have a background in video, so I tape all the showcase performances we do.  While I can usually get them on YouTube without a problem, many people need these in DVD format so they can review their performances and see what they've done wrong -- so it's important I can do this.

I used to be able to transcode with VLC with no problem -- under Hardy.  Then I upgraded to Intrepid and it went kaput.  I used a simple shell script with this line in it:

vlc -I dummy -vvv infile.mts --sout "#transcode{vcodec=mp4v,vb=4096,acodec=mp4a,ab=512,channels=2}:standard{mux=mp4,dst=outfile.mp4,access=file}" vlc:quit

(It's slightly changed to include file names instead of $1 for the input file since I used it as part of a small script.)

This doesn't work.  Now when I try to watch a .mts file on VLC, I get video but no sound.  If I try to transcode it to MP4, I get sound and no video.

I've installed WinFF, which worked a few times and suddenly has problems with the format for output to /dev/null (/dev/null needs a format?!?!), but it uses ffmpeg, just like VLC, so I can't see why VLC doesn't work.

Handbrake also works, but I can't use it to letterbox a 16:9 video to 4:3.  WinFF, as I said, doesn't work.  It worked fine several times until I tried specifying to output in 4:3 instead of 16:9 and since then it won't work no matter what.

I've brought this up on the VLC mailing list several times and I'm told that Ubuntu does not have the codecs I need, but I've installed what I supposedly need from medibuntu and, as I've pointed out, WinFF was able to convert mts to mp4.  I suspect that the VLC people answering me don't use Ubuntu so they find it easier to blame codecs than to figure out the actual problem, but I don't know.

I've tried, on VLC, to convert to Ogg, using Theora for video and Vorbis for audio, and I get the same problem: a file with audio and no video.


So I'm stuck.  I want to convert to good quality MP4 files, in both 16:9 and 4:3.  I can convert to 16:9, but can't make 4:3 so I can put it on a DVD.  I really need to resolve this since I have files from September and friends that really need those videos.

Should I use another tool?  While WinFF worked, the MP4 quality was pretty poor.  Like I've said, Handbrake did part of the job.  Maybe I could find a tool to convert the MP4 Handbrake produces to 4:3, but then that extra step (mts->mp4->4:3 mp4) could really mess up the quality.

Ideally I'd like to get VLC working so it transcodes audio and video.

I've posted about similar problems before and have received little that actually helps.

So what can I do to get this working?

Thank!

---

### Post by HalNineThousand on 2009-01-20
I just ran a test on this.  I was using WinFF and getting MP4, but when I looked at the command line, it was using an H264 codec, not mp4v, which was what I was using previously.  I tried specifying mp4v as an output video codec and get an error message -- "Unknown encoder 'mp4v'"

This is just absurd.  It seems these codecs just aren't there and those of us trying to do this are just S.O.L. with the new version.

Please, someone, tell me I'm wrong and these codecs are in some repository somewhere so I can install them without going through a lot of convolutions to get them!

---

### Post by FakeOutdoorsman on 2009-01-20
> **HalNineThousand said:**
> While I can usually get them on YouTube without a problem, many people need these in DVD format so they can review their performances and see what they've done wrong -- so it's important I can do this.
Are you trying to make a standard video DVD that will play in any DVD player, or do you want to just put the video files on the disc as a data DVD?
> I've installed WinFF, which worked a few times and suddenly has problems with the format for output to /dev/null (/dev/null needs a format?!?!), but it uses ffmpeg, just like VLC, so I can't see why VLC doesn't work.
FFmpeg can usually guess what format the video is supposed to be by the file extension, but it doesn't do very well with /dev/null.  You need to add the "-f mp4" option.
> I've brought this up on the VLC mailing list several times and I'm told that Ubuntu does not have the codecs I need, but I've installed what I supposedly need from medibuntu and, as I've pointed out, WinFF was able to convert mts to mp4.  I suspect that the VLC people answering me don't use Ubuntu so they find it easier to blame codecs than to figure out the actual problem, but I don't know.
I'm not sure what Medibuntu can offer you, but you should install the **libavcodec-unstripped-51*** package from the Ubuntu multiverse repository to enable several restricted encoders in ffmpeg including mpeg4, libmp3lame, and libx264.
> Should I use another tool?  While WinFF worked, the MP4 quality was pretty poor.
You can try ffmpeg itself.  If you use recent releases of ffmpeg and x264 you will have access to the libx264 presets which are useful and create excellent quality videos, but unfortunately you would have to compile them yourself.  More info:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

*You may have to remove libavcodec-unstripped-51 if you decide to compile ffmpeg yourself.  I'm not totally sure yet if it would conflict or not.

---

### Post by HalNineThousand on 2009-01-20
It appears that one issue with VLC is that it specifies "mp4v" instead of "mpeg4" or some other variation, which explains the VLC issues.  I do wonder if that is due to VLC or some changes in the newer packages in Intrepid.  I do know the VLC folks are basically blaming the whole thing on Ubuntu not including all the "proper" libraries.  I have installed the package you specified, but VLC still isn't playing nice with ffmpeg.

As to the DVD question, I want to be able to create a DVD friends can view in a DVD player.  Unless there are standards I don't know about, my understanding is that I need to produce video as MP4 in a 4:3 ratio for that.  Can I put 16:9 video on a DVD and have it play properly on a regular TV?

I've seen and made it through several pages on your thread on compiling ffmpeg from scratch -- I was hoping I could take care of the situation without going there, since my experience is that whenever I try to compile a large package, something always seems to go wrong or there are just too many variables to be sure it'll all work.  I have been told, though, that the regular ffmpeg package on Ubuntu is compiled to not include some non-free codecs.  I am currently using the unstripped codec package -- VLC still goes fubar when I try to transcode with it.  If, on the other hand, I could get the right command line for ffmpeg, that wouldn't be an issue, since I could stick it in a simple script and batch process all my files after an exhibition or show.

While I'm on that, in case it's a simple fix, I'm using this command line:

ffmpeg -threads 2 -i /data/Data/Video/Dance/RawMTS/SweptAway-DeepRun.mts -deinterlace -r 29.97 -vcodec mpeg4 -s 704x384 -aspect 16:9 -b 4096kb -acodec libfaac -ab 512kb -ar 48000 -ac 2 /data/Data/Video/Dance/Testing/SweptAway-DeepRunX.mp4

And it produces a file where the audio goes at normal speed, but the video is at 1/2 speed and the length of the file, in seconds, is twice what it should be.  If there's an easy fix for that, it may solve most of my problems.  (I know I probably should start another thread on that -- if I have time before I have to leave this evening, I may do that.)

---

### Post by FakeOutdoorsman on 2009-01-20
You need to create a mpeg-2 video for a standard dvd.  The resolution will be set to 720x480 for NTSC or 720x576 for PAL despite the aspect ratio.  People often recommend Devede to create video dvd, but I have no experience with it.  Or you could go command-line:
```
ffmpeg -i input1.mts -target dvd output1.mpg
ffmpeg -i input2.mts -target dvd output2.mpg
dvdauthor --title -o newdvd -f output1.mpg
dvdauthor --title -o newdvd -f output2.mpg
dvdauthor -o newdvd -T
mkisofs -dvd-video -o dvdimage.iso newdvd
```

---

### Post by HalNineThousand on 2009-01-20
I'm still experimenting with the command line.  I have found I have to add "-copyts" to keep it in sync.  Apparently there's an issue with .mts files from Canon camcorders -- they're always in a 60i envelope, no matter how many actual fps they use.

Thanks for the commands.  I'm going to work with them and see what I get.  I have noticed that even with "-target dvd" I still get a 16:9 image.  I'll find out at some point, after I burn the DVDs, how that looks on screen, but any chance anyone can let me know before that -- will it scrunch it into 4:3, will DVD players letterbox it, or is there a switch to specify letterboxing with ffmpeg?  I couldn't find letterbox referenced in the man page at all.

---

