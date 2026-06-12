---
title: "Is there a codecs /  media formats for Dummies ?"
date: 2010-01-30
forum: Ubuntu Studio
---

### Post by LuridCinema on 2010-01-30
I have been playing w/ video for a few years now and recently made the switch from windoze to a real Os and I see that I'm in need of a good primer on video codecs. & formats. I see all sorts of terms thrown around h.264 aac lib mts m2t dvi avi dv mov mp4 mpeg4 mpeg2 etc etc etc and I havedone some searches on a few and get 10000 words on the paramaters, but I'm still not getting a good grasp of the whole picture enough to make educated decisions.

Im playing with animations and do some video which is in .mov format and I have played around w/ cinelerra some. I'm seeing that NLE's in Linux offer many many parameters in saving and encoding, but I feel in the dark on what a lot of this stuff means. I'm experimenting w/ ffmpeg and I do not feel that Im able to correctly use such a powerful tool. I look at a video and wonder do I go w/ .mov or mp4 and then do I go w/ ac3 on the audio or wma or.. or.. or..

My main point is .. Is there a place where I can go to get a primer on all the codecs and formats out there ??

---

### Post by wildhostile on 2010-01-31
> **LuridCinema said:**
>  . 

Hi,

You have first to make the difference between a container format and a codec.
According to wikipedia:
"[I]A container format is a computer file format that can contain various types of data, compressed by means of standardized audio/video codecs. The container file is used to identify and interleave the different data types. Simpler container formats can contain different types of audio codecs, while more advanced container formats can support multiple audio and video streams, subtitles, chapter-information, and meta-data (tags) - along with the synchronization information needed to play back the various streams together."
eg: .avi, .mov, .dv, .mpeg, .asf, .ogg, .mkv, etc.

[/I]*"Codecs (in the modern, software sense) encode a stream or signal for transmission, storage or encryption and decode it for viewing or editing.*" (wikipedia)
examples of video codecs: mpeg1, mpeg2, mjpeg, png, theora, h264 ... Video codecs can be lossy or lossless. Audio codecs can be non-compressed, lossless compressed or lossy.

---

### Post by LuridCinema on 2010-01-31
[SIZE=1]Thanxx...looks like I'm gonna have to do some research and try to keep it simple in a very complex area is my best bet. 

[/SIZE][FONT=verdana,arial][SIZE=1]I ultimately want to be able to deliver something for DVD ( 720x480 mpeg2 w/ ac3 5 channel audio ) , Blu-Ray ( 1920x1080p mpeg2 w/ ac3 5 channel audio ) and the Web ( differing resolutions h.264 mp4 w/ mebbe ac3 stereo ? or .flv) [/SIZE][/FONT]

---

### Post by wildhostile on 2010-01-31
> **LuridCinema said:**
> [SIZE=1] .[/SIZE][FONT=verdana,arial][SIZE=1] [/SIZE][/FONT]

Difference between container and codecs is a basic thing to know about multimedia formats and codecs. There are other things to figure out such as:
- interlaced or progressive
- size (PAL: 720x576, NTSC:720x480)
- aspect ratio (4:3 , 16:9 ...)
- bitrate
- framerate
- color model
... 
To find your perfect workflow, you may have to investigate on the formats/codecs used in your country or others countries as standards for broadcasting, distribution, archiving, internet diffusion... for SD or HD video.

---

### Post by FakeOutdoorsman on 2010-02-01
> **LuridCinema said:**
> [SIZE=1]Thanxx...looks like I'm gonna have to do some research and try to keep it simple in a very complex area is my best bet.

[/SIZE][FONT=verdana,arial][SIZE=1]I ultimately want to be able to deliver something for DVD ( 720x480 mpeg2 w/ ac3 5 channel audio ) , Blu-Ray ( 1920x1080p mpeg2 w/ ac3 5 channel audio ) and the Web ( differing resolutions h.264 mp4 w/ mebbe ac3 stereo ? or .flv) [/SIZE][/FONT]

As for encoding for the web, I recommend compiling FFmpeg and x264 if you are going to encode more than just a few videos.  FFmpeg and x264 development is very active and compiling will allow you to take advantage of the hundreds of bug fixes and several enhancements that the repository versions lack:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You may also want to subscribe to the [ffmpeg-user](http://ffmpeg.org/contact.html) mailing list.  See how things work in there and if you have a question that you can't seem to find an answer to, then try asking there.

Same goes with the #ffmpeg IRC channel.  That is another great resource for quick answers, but make sure you read the channel topic before asking any questions or you may be ignored.  Of course ubuntuforums.org is also a good place to ask questions.

Once you compile FFmpeg and x264 you can encode for the web.  Example:
```
ffmpeg -i input -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -crf 24 -threads 0 ffmpegoutput.mp4
```
You can read about these options with *ffmpeg -h*.  I also recommend the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) to learn more about what *crf* does.  The *-wpredp 0* option turns off the "weighted prediction analysis method" that older versions of Adobe Flash have trouble with.

Now use qt-faststart (part of FFmpeg) or MP4Box (part of the gpac package) to re-arrange the "moov atom" to the beginning of the file so it can start playing before the video file is completely downloaded:
```
qt-faststart ffmpegoutput.mp4 finaloutput.mp4
```
Your file is now ready for use on the web.  Good players are JW Player and Flowplayer.

---

### Post by LuridCinema on 2010-02-01
THANK You !! Lots of good info... It's time for me to study and get hooked up !

---

### Post by FakeOutdoorsman on 2010-02-01
I updated my example above.  It previously had an incorrect option name and is now correct with *-wpredp 0*.

---

### Post by LuridCinema on 2010-02-01
I recompiled my ffmpeg w/ the latest & greatest BUT after installing and checking ffmpeg....

I tried the command:
```
qt-faststart ffmpegoutput.mp4 finaloutput.mp4
```
and got the following error

```
p9@p9-desktop:~/Desktop$ qt-faststart ffmpegoutput.mp4 finaloutput.mp4
The program 'qt-faststart' is currently not installed.  You can install it by typing:
sudo apt-get install ffmpeg
qt-faststart: command not found
```crazy since I have ffmpeg installed

---

### Post by FakeOutdoorsman on 2010-02-01
Yes, you are correct that following the guide does not include **qt-faststart**.  Thanks for pointing that out.  It's easy to compile though:
```
cd ~/ffmpeg/tools
make qt-faststart
sudo mv qt-faststart /usr/local/bin
```
Kind of a messy way to install it, but I haven't figured out how to install it more cleanly, such as along with FFmpeg in the checkinstall step...if that is even possible.  Something to look into, but I don't have any answers for that yet.

---

### Post by paulrf on 2010-03-04
I realize the previous posts were some time ago, but I have a couple of questions...  I have been converting MP4 files to FLV believing that I need to do so for compatibility reasons (I put flash videos on my personal website).   I use JW Player, so I don't see a problem from my end, but would most browsers handle the MP4 format at this point?

Also, if someone could guide me to a good ffmpeg x264 reference...  one for dummies sounds like a good call. :-)  A number of forums refer me to: [http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) but that link is apparently not functional at this time.  Using the information above, I'm able to get quality mp4 videos (and I can convert to FLV if necessary), but the file size is a bit large.  Using the example above, my video was 87MB, and some of my family have slow internet connections.  I've found little to help me get the maximum resolution with the minimum file size.  Any guidance would be much appreciated.

---

### Post by FakeOutdoorsman on 2010-03-04
> **paulrf said:**
> I realize the previous posts were some time ago, but I have a couple of questions...  I have been converting MP4 files to FLV believing that I need to do so for compatibility reasons (I put flash videos on my personal website).
Adobe Flash Player with JW Player can play both FLV and MP4 (with *H.264* video, I'm not sure about *MPEG-4 Part 2* video), so you may not need to re-encode at all.

> **paulrf said:**
> I use JW Player, so I don't see a problem from my end, but would most browsers handle the MP4 format at this point?
Yes.  You should have no trouble using MP4 with H.264 video and AAC audio.

> **paulrf said:**
> Also, if someone could guide me to a good ffmpeg x264 reference...  one for dummies sounds like a good call. :-)  A number of forums refer me to: [http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) but that link is apparently not functional at this time.
That site has not been very stable lately, but a Google [cached version](http://74.125.95.132/search?q=cache:TK96XlO5grYJ:rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/+http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/&hl=en&client=firefox-a&hs=Eze&gl=us&strip=1) still works.

> **paulrf said:**
> Using the information above, I'm able to get quality mp4 videos (and I can convert to FLV if necessary), but the file size is a bit large. Using the example above, my video was 87MB, and some of my family have slow internet connections.
You can adjust the crf value to get a lower output file size.  A value of +6 higher than your current number will cut the bitrate approximately in half.  If you want your output file to be a specific output size, you can use a two-pass encode.  I recommend CRF unless you absolutely need a specific output file size.  There's a two-pass example here:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You can use a bitrate calculator to give you a proper bitrate for a certain file size, or: *bitrate * duration = output file size*.

> **paulrf said:**
> I've found little to help me get the maximum resolution with the minimum file size.  Any guidance would be much appreciated.

You can also adjust the preset with *-vpre*.  There are [several presets](http://ubuntuforums.org/showpost.php?p=8905745&postcount=895) available.  The slower the preset, the better the compression efficiency (usually), but the longer the encoding process.  The most important options for you to modify are *-crf* and *-vpre*.

---

### Post by paulrf on 2010-03-04
Thank you so much for you help! :-)

---

