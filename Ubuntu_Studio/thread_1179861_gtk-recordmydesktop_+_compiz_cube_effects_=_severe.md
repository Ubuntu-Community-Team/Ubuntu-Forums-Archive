---
title: "gtk-recordmydesktop + compiz cube effects = severe tearing"
date: 2009-06-06
forum: Ubuntu Studio
---

### Post by Nixie Pixel on 2009-06-06
Hi, I was wondering if there was a better way to record the compiz cube effects than with gtk-recordmydesktop. At the moment when I try to do so something is causing the desktop recorder to record visual tearing which does not exist, or at least is not visible to the naked eye. However when I play the video back it has a bad problem with tearing (i.e. what appear to be horizontal strips "torn" from the image).

Is there any way I can fix this, or is there a better program to use?

Thanks!

---

### Post by andrew.46 on 2009-06-06
Hi Nixie,

I know you are an FFmpeg fan so you may be interested to know that FFmpeg can capture your screen by using x11grab. Bad news is that I have never really got it working properly.

An example is:

```

ffmpeg -t 00:00:30 -r 30 -g 300 -s 1024x768 -f x11grab -i :0.0 \
       -vcodec qtrle screencast-1.mov
```

I have vague memories of ripping this syntax off from somebody on these forums and planning to use this string as a starting point but never got around to it :-). x11grab + FFmpeg is very poorly documented so if you could conquer the syntax and present it on your site this would be valuable!

All the best,

Andrew

---

### Post by igorzwx on 2009-06-06
On Ubuntu 9.04

ffmpeg -an -s 1200x900 -r 25 -f x11grab -i :0.0 -s 1200x900 -r 25 -vcodec libxvid -aspect 1.3333 -sameq video-nosound.avi

1200x900 is the size of the screen, take one which you need

Do not forget about aspect (4:3), but this parameter can be dropped


**gtk-recordmydesktop** is a great app :)

but it is not likely to be an optimal solution.

ffmpeg works well on Ubuntu 9.04

just works without problems :)

On Ubuntu 8.10, you can grab the screen to wmv2
On Ubuntu 8.04, ffmpeg does not grab the screen

But ffmpeg can be recompiled to enable all features on Ubuntu 8.4, 8.10, 9.04

I have created the script which does the work on Ubuntu 9.04:
[http://ubuntuforums.org/showthread.php?t=1176373](http://ubuntuforums.org/showthread.php?t=1176373)

It works well on old hardware.
It should work much better on power boxes.
But I have never tried to record any occult effects.

If anybody would try to record 3D, I would be very happy to have a feedback :)

---

### Post by andrew.46 on 2009-06-06
Hi Nixie,

Well, a little more work with the syntax I think has produced excellent results. I am not so keen on libxvid so I have again utilised FakeOutdoorsman's work and used single-pass Constant Rate Factor encoding with the x264 hq preset:

```
ffmpeg -vframes 100 -r 30 -g 300 -s 1024x768 -f x11grab -i :0.0 \
       -vcodec libx264 -vpre hq -crf 22 -threads 0 test.mp4
```

This produces quite acceptable results especially if you have kept the x264 libraries up to date. I have posted a quick sample here using this syntax:

```
wget http://andrews-corner.org/samples/nixie.mp4
```

Could definitely use a bit of work but this might be a good start?

Andrew

---

### Post by Nixie Pixel on 2009-06-06
Hi Andrew, would you do me the huge favor of explaining to me what the difference is between your syntax and the one that igor posted above?

Also, how do I keep the x264 libraries up to date?

Finally, how do I end the recording once I start it? 

Thanks!

---

### Post by andrew.46 on 2009-06-07
Hi Nixie,
 
I should preface all of the following comments by making it perfectly clear that I am not an expert in this field, only an enthusiastic amateur :-). I welcome comments and contradictions for those more experienced than myself (Lou where are you!!).

> **Nixie Pixel said:**
> Hi Andrew, would you do me the huge favor of explaining to me what the difference is between your syntax and the one that igor posted above?

igor's commandline was:

```
ffmpeg -an -s 1200x900 -r 25 -f x11grab -i :0.0 \
       -s 1200x900 -r 25 -vcodec libxvid -aspect 1.3333 -sameq video-nosound.avi
```

The only change before the input file (-i :0.0) would be the '-an' which is redundant in this case. Audio needs to be added in manually as an extra input via '-f oss -i <audio-device>' which quite frankly I have never managed to get working but if there is no audio FFmpeg will realise this without the '-an' option. After the input file '-s' does not need to be declared again unless resizing and I suspect the same for the framerate: '-r' although I am not so sure about this one. As igor mentioned the -aspect option could safely be dropped. Two things I would not do are the '-sameq' option for this as x11grab generates rawvideo and I am not so sure that the '-sameq' option would deal well with this and of course the avi container which is more than a little limiting.

My own syntax:

```
ffmpeg -vframes 100 -r 30 -g 300 -s 1024x768 -f x11grab -i :0.0 \
       -vcodec libx264 -vpre hq -crf 22 -threads 0 test.mp4
```

covers most of my nitpicks above hopefully, otherwise igor will turn the tables on me :-). Main change is the use of x264 encoding instead of libxvid. libxvid is an *external* library which I think FFmpeg now does better with its *native* implementation:

```
-vcodec mpeg4 -vtag XVID
```

but h264 encoding should always produce better results with lower file size and this is accomplished in FFmpeg by using the x264 encoder. If you have not done so already you would be best to have a look at the [FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095") on this area where he outlines as well the use of the preset I have used (-vcodec libx264 -vpre hq).

> Also, how do I keep the x264 libraries up to date?

The libraries are maintained in a git repository and you should see the details in the FakeOutdoorsman's guide. It is a simple matter to update these with the 'git pull' command from the source tree and then recompile.

> Finally, how do I end the recording once I start it? 

I guess you have 3 choices. You can limit the number of frames being recorded by use of the '-vframes <number>' option, you can limit the time of the recording by use of the '-t hh:mm:ss[.xxx]' option or you can press 'q' at any time to stop the encoding.

It is my hope that you put together a better encoding method than the one I have suggested as I have always been keen to see this working a little better than I have been able to get it to:-).

All the best,

Andrew

---

### Post by igorzwx on 2009-06-07
Try this too:

ffmpeg -f x11grab -s 1200x900 -r 25 -i :0.0 -s 1200x900 -r 25 -sameq video.avi

It works well.
It works on Ubuntu 9.04

---

### Post by Nixie Pixel on 2009-06-07
Thanks for the suggestions and the explanation - I will try them out!

I am not sure what help I might be in trying to make things better, I really am a n00b at all this.

---

### Post by andrew.46 on 2009-06-07
Hi Nixie,

> **Nixie Pixel said:**
> Thanks for the suggestions and the explanation - I will try them out!

I am not sure what help I might be in trying to make things better, I really am a n00b at all this.

Don't worry I am something of a n00b myself with FFmpeg, and certainly a complete n00b with x11grab :-).

Andrew

---

### Post by Nixie Pixel on 2009-06-07
I see -aspect 1.333 can be dropped, but what if I wanted to record in widescreen? Would -aspect 1.7778 work for 16:9?

Thanks!

---

### Post by Nixie Pixel on 2009-06-07
I followed the various links in the posts above, including FakeOutdoorsMan's guide, but I still had a problem when trying these commands - it tells me that x11grab is an unknown format.

Ok, my newbie search leads me to believe that I perhaps should have added the configuration option --enable-x11grab when I compiled ffmpeg, correct? Does this mean I have to recompile? 

(If so, is there an easy way to do that? I've never done it before...compiling stuff is new to me!)

---

### Post by Nixie Pixel on 2009-06-08
So I recompiled it with the --enable-x11grab option and it seems to work...sort of. I still have screen tearing. I'll attach a screenshot below.

[IMG]http://nixiepixel.com/misc/ffmpegtest.jpg[/IMG]

Any ideas as to what this is and why it is occuring?

Also, igor, your first command line failed with the output "video encoding failed" though that could be because I took out the -aspect option, changed the frame rate to 30, and changed the resolution to be 1920x1200.

---

### Post by andrew.46 on 2009-06-08
Hi Nixie,

> **Nixie Pixel said:**
> I followed the various links in the posts above, including FakeOutdoorsMan's guide, but I still had a problem when trying these commands - it tells me that x11grab is an unknown format.

Oops, my apologies :-). I somehow had the idea in my head that this guide enabled x11grab and obviously it does not.

> Ok, my newbie search leads me to believe that I perhaps should have added the configuration option --enable-x11grab when I compiled ffmpeg, correct? Does this mean I have to recompile? 

As you have worked out by now the answer to that one is yes. To see all the available options you can change to the svn source and run:

```
./configure --help
```

and this will show options + correct syntax.

> (If so, is there an easy way to do that? I've never done it before...compiling stuff is new to me!)

Only easy way is a faster computer or perhaps scripting some of the work. But it can be quite relaxing watching a big program compile don't you think? As for the tearing I am afraid I have gone as far as I know with screen capture, remember I am looking to you to sort it all out now :-).

All the best,

Andrew

---

### Post by Nixie Pixel on 2009-06-08
Thank you yet again! 

Unfortunately I don't have a clue where to start in looking for a solution to the tearing problem. Is there an official ffmpeg forum out there where I can ask about this?

---

### Post by andrew.46 on 2009-06-08
Hi Nixie,

> **Nixie Pixel said:**
> Unfortunately I don't have a clue where to start in looking for a solution to the tearing problem. Is there an official ffmpeg forum out there where I can ask about this?

Well there is but they can be a bit of a tough crowd who will punish the smallest infraction of the unwritten rules quite savagely. The details of FFmpeg-users can be found here:

ffmpeg-user -- FFmpeg user questions and RTFMs
[https://lists.mplayerhq.hu/mailman/listinfo/ffmpeg-user/](https://lists.mplayerhq.hu/mailman/listinfo/ffmpeg-user/)

and I would really strongly suggest a period of lurking before posting there :-). #ffmpeg can be quite useful if you are into irc? Full details of these 2 and a couple of others can be seen [here]("http://ffmpeg.org/contact.html").

Andrew

---

### Post by igorzwx on 2009-06-08
This kind of chaos management can only produce more disorder in brains.
Somebody tried something, and nobody knows what is really going on.

On Ubuntu 9.04, you do not need to recompile ffmpeg to grab the screen.

So what?

---

### Post by Nixie Pixel on 2009-06-08
Sorry Igor, I am not really sure of what you are trying to say.

---

### Post by igorzwx on 2009-06-08
Nothing special.

On Ubuntu 9.04, you do not need to recompile ffmpeg.

This works for recording 2D:

ffmpeg -f x11grab -s 1200x900 -r 25 -i :0.0 -s 1200x900 -r 25 -sameq video.avi

ffmpeg -an -s 1200x900 -r 25 -f x11grab -i :0.0 -s 1200x900 -r 25 -vcodec libxvid -aspect 1.3333 -sameq video-nosound.avi

It has not been tested for recording 3D.

This might be a starting point for experiments.

1. Apply to 2D
2. Apply to 3D

If you provide exact info about what was done,
it might be possible for others to understand what you are doing.

---

### Post by andrew.46 on 2009-06-09
Hi igorzwx,

> **igorzwx said:**
> On Ubuntu 9.04, you do not need to recompile ffmpeg to grab the screen

Actually I was not sure if the repository FFmpeg was compiled with x11grab, thanks for clearing this up. But to achieve quality screen capture while encoding with the x264 encoder I believe it is very necessary to compile the current svn FFmpeg and latest git x264. In my own tests this has produced better results with x11grab that libxvid or mpeg4. I am ready to be contradicted on this point though :-).

All the best,

Andrew

---

### Post by igorzwx on 2009-06-09
Hi Andrew!

I tried your command:

ffmpeg -vframes 100 -r 30 -g 300 -s 1400x1050 -f x11grab -i :0.0 -vcodec libx264 -vpre hq -crf 22 -threads 0 test2full.mp4

I tried it on Ubuntu 9.04 without recompilation of ffmpeg.
The result is very nice. I am impressed.

I would be very happy if you would continue your experiments and publish the results.

Perhaps, you may start a new thread.
We may try different settings and discuss the results.

I am actually busy with another thing.
The point is to provide ordinary users with a simple
and effective tool for making screencasts.

To summarize, we have 3 very interesting themes:

1. Recording 3D effects with ffmpeg

2. Your experiments with the x264 encoder

3. A simple tool for recording screencasts


This is what I have on Ubuntu 9.04 without recompilation of ffmpeg:

$ ffmpeg
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Best regards,
Igor

---

### Post by Nixie Pixel on 2009-06-11
Ok, after much chatting in the #ffmpeg IRC channel, it seems my problem may have to do with graphics card overlay / writeback. The problem only exists while I am recording 3D effects, not 2D effects. 

Here is the latest command I used, after input from folks in the channel:
```
ffmpeg -r 30 -s 1920x1200 -f x11grab -i :0.0 -g 300 -threads 0 -vcodec libx264 -vpre fastfirstpass -vpre baseline -sc_threshold -1 -cqp 22 -flags -loop ffmpegtest.mp4
```

The results were the same, I still had screen tearing. I tried setting my desktop resolution down to 1440x900 and then changing the ffmpeg string accordingly, but the problem became worse - much, much worse, actually.

So at this point I'm lost. They suggested I try another capture tool, or get a video capture card so that the encoding isn't done on my PC while I'm trying to record.

If you have any more suggestions, I am all ears.

Thanks again!

---

### Post by Nixie Pixel on 2009-06-11
Wait, after talking in #compiz I chose Force synchronization between X and GLX in the Compiz settings and it has all but wiped out the problems! I'm working it out with the guys there, but I think I can call this resolved now. 

Thanks again!

---

### Post by andrew.46 on 2009-06-11
Hi Nixie,

Glad to hear you have just about got on top of this one :-). Hopefully you will post a link here to your finished product?

Andrew

---

### Post by Nixie Pixel on 2009-06-11
Sure! The problem isn't completely gone, but it is good enough that with one minute of twisting my sphere around I should be able to get a good amount of video to pull from.

Either that or I get a video capture card (which I wanted to do and build a HTPC anyway :).

I have real problems when I try to show that I can play video in a 3D window which is displayed around a 3D sphere - gee, I wonder why :p

---

### Post by andrew.46 on 2009-06-11
Hi Nixie,

> **Nixie Pixel said:**
> Sure! The problem isn't completely gone, but it is good enough that with one minute of twisting my sphere around I should be able to get a good amount of video to pull from.

And I guess this means you are convinced that libx264 and the FFmpeg presets are the way to go? Mind you I see that your discussions with #ffmpeg have yielded a commandline much more advanced than the one I casually suggested :-).

Andrew

---

### Post by Nixie Pixel on 2009-06-12
Well, I will probably end up going with xvid only because the non-linear video editor I am using won't handle h264 at the moment.

Still, the best solution is probably a video capture card - which would allow me to do lots of other things as well.. but that isn't in my budget at the moment (digital capture cards are $250 or more).

Thanks again!

---

### Post by igorzwx on 2009-06-12
libx264 seems to be a really cool thing!

Andrew is absolutely right!
This is the way to go!

I hope that Andrew may continue his revolutionary experiments with libx264

You can encode with this command:

ffmpeg -f x11grab -s 1392x1040 -r 25 -i :0.0 -vcodec libx264 -sameq test2full-sameq.mp4

(it works on Ubuntu 9.04 without recompilation of ffmpeg)

Then try to open mp4 with your video editor.

-sameq  means "same video quality"

-s 1392x1040  - width and height should be divisible by 16, otherwise compression may suffer.

But you can grab the screen as you want (to a lossless format), and then crop the video with ffmpeg. Something like this:

       -croptop size
           Set top crop band size (in pixels).

       -cropbottom size
           Set bottom crop band size (in pixels).

       -cropleft size
           Set left crop band size (in pixels).

       -cropright size
           Set right crop band size (in pixels).

Generally speaking, if you are going to edit your screencasts,
you may better record to a lossless format.

FFV1 - FFmpeg codec #1 - might be a solution

QOUTE:
FFV1, which stands for "FF video codec 1", is a lossless intra-frame video format. It can use either variable length coding or arithmetic coding for entropy coding. The encoder and decoder are part of the free, open-source library libavcodec in the project FFmpeg. FFV1 is included in ffdshow.
[http://en.wikipedia.org/wiki/FFV1](http://en.wikipedia.org/wiki/FFV1)

This seems to be a magic solution to all problems:

ffmpeg -f x11grab -r 25 -s 1392x1040 -i :0.0 -vcodec ffv1 -sameq output-lossless-8.avi

It works on Ubuntu 9.04
It should also work on Ubuntu 8.10
No recompilation of ffmpeg is required.

The ffv1-avi can be played with MPlayer,
and it can be re-encoded to any format.

Best,
Igor

---

### Post by FakeOutdoorsman on 2009-06-12
Interesting thread.  I added *--enable-x11grab* to the FFmpeg compilation guide.  Reminds me that I once told Andrew that the x11grab guide was next on my guide list, but I obviously have been slacking.  Now I have less of an excuse now that Nixie did the hard work.

---

### Post by andrew.46 on 2009-06-12
Hi Fakeoutdoorsman,

> **FakeOutdoorsman said:**
> Interesting thread.  I added *--enable-x11grab* to the FFmpeg compilation guide.  Reminds me that I once told Andrew that the x11grab guide was next on my guide list, but I obviously have been slacking.  Now I have less of an excuse now that Nixie did the hard work.

I was hoping that you were reading this :-). And igorzwx has reminded me that you once also suggested exporting as lossless video which I never actually got around to trying.

Andrew

---

### Post by igorzwx on 2009-06-15
[comparison of different lossless video codecs]("http://compression.ru/video/codec_comparison/lossless_codecs_2007_en.html")
[http://compression.ru/video/codec_comparison/lossless_codecs_2007_en.html](http://compression.ru/video/codec_comparison/lossless_codecs_2007_en.html)

QUOTE:
**Main conclusions:**
                       In Video Capture and Video Editing Area the overall clear winner is Lagarith.             
 In Maximum Compression area the overall winner is YULS.             
 The most balanced and flexible codec is FFV1: relatively good speed and high compression for various presets.         
  The comparison paper is 130 pages long and contains a lot of graphs to facilitate analysis

Andrew!
If you can read in Russian, you may find something here:
[http://compression.ru/](http://compression.ru/)

[http://compression.ru/video/codec_comparison/x264_options_analysis_08.html](http://compression.ru/video/codec_comparison/x264_options_analysis_08.html)
**&#1040;&#1085;&#1072;&#1083;&#1080;&#1079; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1086;&#1074; &#1074;&#1080;&#1076;&#1077;&#1086;&#1082;&#1086;&#1076;&#1077;&#1082;&#1072; x264 &#1089;&#1090;&#1072;&#1085;&#1076;&#1072;&#1088;&#1090;&#1072; MPEG-4 AVC/H.264**

---

### Post by igorzwx on 2009-06-15
in English:
[SIZE=-1]         [Fifth MPEG-4 AVC/H.264 Comparison (May 2009)]("http://compression.ru/video/codec_comparison/mpeg-4_avc_h264_2009_en.html")         [SIZE=-1][COLOR=red]**(New!)**[/COLOR][/SIZE]      
[/SIZE]http://compression.ru/video/codec_comparison/mpeg-4_avc_h264_2009_en.html
[COLOR=#727272]**Codecs that Were Tested**[/COLOR]                     
Dicas H.264           
 Elecard H.264           
 Intel IPP H.264           
 MainConcept H.264           
 x264           
 XviD (MPEG-4 ASP codec)         
                            
[COLOR=#727272]**Comparison Rules**[/COLOR]
                [IMG]http://compression.ru/images/spacer.gif[/IMG]**All codec options and presets were provided by codec authors.**              
 An important restriction on a preset is encoding time for it.                   A few iterations of compliance testing and preset optimization                   were made to meet the requirements.              
 Provided decoders or JM 9.8 reference decoder were used to decode all encoded streams.              
 All objective metrics measurements were performed with 
                    [                  MSU Video Quality Measurement Tool (Pro Version)]("http://www.compression.ru/video/quality_measure/video_measurement_tool_en.html").              For each preset both speed and quality were measured.

---

### Post by igorzwx on 2009-06-16
HuffYUV Lossless video codec. Fantastic performance! This is the magic tool for capturing screen.

HuffYUV video codec is very fast. Incredibly fast!
Video files are big, but you can compress them afterwards how you want.

HuffYUV - Lossless codec from BenRG 
Bit-for-bit identical with the original input!

HuffYUV is a lossless video codec created by Ben Rudiak-Gould... 
"Lossless" means that the output from the decompressor is bit-for-bit identical with the original input to the compressor, given that no color space conversion takes place. Huffyuv's algorithm is similar to that of lossless JPEG-LS, in that it predicts each sample and then Huffman-encodes the error.
VLC media player and MPlayer
[http://en.wikipedia.org/wiki/Huffyuv](http://en.wikipedia.org/wiki/Huffyuv)

Step 1: Record the screen

ffmpeg -f x11grab -r 25 -s 1392x1040 -i :0.0 -vcodec huffyuv -sameq Lossless-HuffYUV.avi

Result: Lossless-HuffYUV.avi - it can be played with VLC and MPlayer
This works on Ubuntu 9.04
It should also work on Ubuntu 8.10.
No recompilation of ffmpeg is required.

2 minutes Full Screen => 250MB Lossless-HuffYUV.avi


Step 2: Convert HuffYUV AVI to Mpeg2 video

ffmpeg -i Lossless-HuffYUV.avi -f mpeg2video -sameq Mpeg2.mpg

Result: Mpeg2.mpg - it can be played with VLC and MPlayer
This works on Ubuntu 9.04
It should work on Ubuntu 8.10 too.
No recompilation of ffmpeg is required.

2 minutes Full Screen => 100MB Mpeg2.mpg


Step 3: Convert Mpeg2 to Microsoft MPEG-4 4.2 video

mencoder -forceidx -mc 0 -noskip -skiplimit 0 -ovc lavc -lavcopts vcodec=msmpeg4v2:vhq -o Windoze-MPEG4.avi Mpeg2.mpg

Result: Windoze-MPEG4.avi - it can be played by any player, including Windows Media Player.
This works on Ubuntu 9.04
It should work on Ubuntu 8.10 too.
No recompilation of ffmpeg or mencoder is required.

2 minutes Full Screen => 12MB Windoze-MPEG4.avi


On Ubuntu 9.04 you can also encode to mpeg4 and XviD and mp4 (libx264):


Step I: Convert HuffYUV AVI to mpeg4 video

ffmpeg -i Lossless-HuffYUV.avi -sameq mpeg4.avi

Result: mpeg4.avi - it can be played with VLC and MPlayer

2 minutes Full Screen => 6MB mpeg4.avi


Step II: Convert HuffYUV AVI to XviD video

ffmpeg -i Lossless-HuffYUV.avi -vcodec libxvid -aspect 1.3333 -sameq XviD.avi

Result: XviD.avi - it can be played with Totem, VLC and MPlayer

2 minutes Full Screen => 5MB XviD.avi


Step III: Convert HuffYUV AVI to mp4 (libx264) video

ffmpeg -i Lossless-HuffYUV.avi -vcodec libx264 -sameq libx264.mp4

Result: libx264.mp4 - it can be played with Totem, VLC and MPlayer

2 minutes Full Screen => 2MB libx264.mp4


You can add an audio file to avi with ffmpeg or mencoder.
VLC allows to play a video file with "an external audio file".

You can edit your videos with ffmpeg, mencoder, or Avidemix (GUI), or else.

---

### Post by igorzwx on 2009-06-17
**Lagarith** is an [open source]("http://en.wikipedia.org/wiki/Open_source") [lossless]("http://en.wikipedia.org/wiki/Lossless") [video codec]("http://en.wikipedia.org/wiki/Video_codec") written by Ben Greenwood.
[http://en.wikipedia.org/wiki/Lagarith](http://en.wikipedia.org/wiki/Lagarith)

It is available for Windows and Mac, but not for Ubuntu.
Why?

---

### Post by Nixie Pixel on 2009-06-17
Thanks for reviving the thread!

Update: I was directed to [this launchpad entry]("http://gitweb.compiz-fusion.org/?p=fusion/plugins/workarounds;a=commit;h=46960f12a9d213e5f0e841557e2ed2f7ea18cc79") by Nate who posted over at linuxhaxor.net in response to my latest video (I would give more accurate credit to him but he didn't leave contact info :(). It has helped me record even 1920x1200 while playing youtube videos in a 3D window while rotating the cube with just minor flickering (which I can edit out). I wish I could record exactly what I'm seeing, a smooth, flawless rotation, but this is as good as it is going to get without a hardware solution I think.

I added compiz-plugins-unsupported and tried running Snow while rotating the cube. Even just viewing it with 3D windows (the effect is that the snow actually falls -off- of the cube/sphere in 3D space, really cool!) had my computer at its knees, and the recording was even worse. So I won't be trying to show that off, as cool as it is!

Anyway, I just wanted to let you know how it was going, and what the workaround was for this problem.

Thanks!

---

### Post by igorzwx on 2009-06-19
[B]How to estimate the quality of lossless recording
and the quality of lossy encoding (XviD, mpeg4, etc.)

An Easy Way[/B]

Run Audacity, or other GUI application.

Record a part of screen with this command:

ffmpeg -f x11grab -r 25 -s 800x608 -i :0.0 -vcodec huffyuv -sameq Audacity-Lossless-HuffYUV-nosound1.avi

or this command:

ffmpeg -f x11grab -r 35 -s 928x704 -i :0.0 -vcodec huffyuv -sameq Audacity-Lossless-HuffYUV-nosound2.avi

Then, encode the recordings to various lossy formats (XviD, mpeg4, etc.)

Now you can zoom into your videos and see the quality:

Step 1: Open video file with VLC

Step 2: Change to full screen

---

### Post by igorzwx on 2009-06-22
Hi all!

This might be very interesting link:
[http://www.kdenlive.org/mantis/view.php?id=248#bugnotes](http://www.kdenlive.org/mantis/view.php?id=248#bugnotes)

QUOTE:

"Ever tried using "-pix_fmt yuv422p -vcodec huffyuv capture.avi" or "-vcodec flashsv capture.flv?""

"This seems like the** ultimate tool** to make quality screen captures."

I do not like the idea to pipe sound into ffmpeg,
but they claim that it works:

sox -t alsa "default" -q -c1 -r48000 -t raw - | \
ffmpeg -f s16le -i - -acodec copy \
-f x11grab -r 10 -s 1280x768 -i :0.0 \
-pix_fmt yuv422p -vcodec huffyuv \
-t 10 \
capture.avi

I believe that it is much better to run 2 ffmpegs. One records sound from ALSA, or OSS.
Another captures the screen.

Examples:
     
ffmpeg -f oss -ar 44100 -ac 1 -i /dev/dsp1 -acodec pcm_s16le mumuv-dsp1.wav 

ffmpeg -f alsa -ar 44100 -ac 1 -i plughw:1,0 -acodec pcm_s16le alsa-exp-1.wav

arecord -D plughw:1,0 -d 10 -r 44100 -c 1 -f S16_LE -t wav alsa-exp-2.wav

---

### Post by Nixie Pixel on 2009-06-22
igor, thank you very much! Your tutorial on lossless formats has helped me quite a bit. I am unable to use huffyuv at the moment due to prohibitive file sizes and limited space, but I plan to soon. However your suggestions gave me an idea - I reduced the compression and it helped me clear up most of the remaining problems I have been having.

Here is what I am currently using (mpeg4/avi so I can send it to Windows if I need to):  

```
ffmpeg -r 30 -s 1920x1200 -f x11grab -i :0.0 -vcodec msmpeg4v2 -qscale 2 output.avi
```

This has done really well for me and is not TOO large (your huffyuv suggestion was over 1GB in under a minute, you need a lot of working space for those videos).

So expect a demonstration of the Compiz cube soon, thanks to all of the help here and over at #ffmpeg (Dark_Shikari rocks)!

---

### Post by igorzwx on 2009-06-22
Interesting solution! You are very creative.
It seems that it works well.
I tried it with -s 912x688, then zoomed into the video with VLC.
Quality seems to be perfect.
You can compress it with 7zip and send to Windows users.
But those users are very special, the most of them do not know 
what 7zip is.

In a word, one may believe that "-r 30" is something real.
But it might be as real as a label on a container, not more.

Try this command:

ffmpeg -r 3000 -s 928x704 -f x11grab -i :0.0 -vcodec msmpeg4v2 -qscale 2 output-3000.avi

The Label will be 3000 fps.
But the real rate of the stream will be something like this: 10 fps (or 3 fps, or else).

You see, you have listing on the terminal.
At the end of the listing, you may find a line:

frame= 58 fps= 10 q=2.0 ...

This 10 fps would be a universal constant of your box.
It would not depend on Ubuntu, or Xubuntu, on mpeg4, or huffyuv. 
It would be always about the same on the same box.

This universal constant is much more important than GBs.
If you have at least 10 fps, you can make screencasts.
Otherwise, you may better make screenshots.

If GBs are the problem, you may try ffv1.
The quality is about the same as that of huffyuv, but the size is smaller.

ffmpeg -f x11grab -r 50 -s 912x688 -i :0.0 -pix_fmt yuv422p -vcodec ffv1 -sameq ffv1-yuv422p.avi

(perhaps, -sameq might be dropped when you record to lossless formats).

ffv1-avi can be played with Mplayer, and it can be converted to anything else.

Good luck!

---

### Post by igorzwx on 2009-06-26
This works on Ubuntu 9.04 and Ubuntu 8.10:

ffmpeg -r 30 -s 928x704 -f x11grab -i :0.0 -vcodec qtrle -sameq screencast.mov 

ffmpeg -r 30 -s 928x704 -f x11grab -i :0.0 -vcodec qtrle -qscale 2 screencast.mov

No recompilation of ffmpeg is required.

Thus, the users of Ubuntu 8.10 can record screen to mov, or to lossless formats with
huffyuv or ffv1. And they can encode any video to mov:

fmpeg -i input-video -vcodec qtrle -sameq output.mov

Moreover, the users of Ubuntu 8.10 can encode videos to any format with mencoder.
**[11.3. Encoding with the libavcodec codec family]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html")**

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html)

---

### Post by bgiannes on 2009-07-10
i've been trying to capture the desktop as well, this is my best syntax to date



> ffmpeg -s 1280x1080 -r 29.97 -f x11grab -i :0.0 -b 1536k -vcodec mpeg4 -f oss -i /dev/dsp -ac 2 -acodec libmp3lame -ab 256k -vol 254 -ar 48000 -f mpeg out.avi


note:
doing the "-f mpeg" at the end makes ffmpeg run at the ~correct framerate, without it i get 29 on the lable and 3 to 1 fps real rate, the sound still needs work.

---

### Post by igorzwx on 2009-07-10
!!! Do not record both sound and screen with the same ffmpeg !!!

Run two ffmpegs, one records screen, another sound.

Take my script and modify it how you want
[http://n2.nabble.com/New-script-for-recording-screencasts-on-Ubuntu-9.04-td3081264.html#a3081264](http://n2.nabble.com/New-script-for-recording-screencasts-on-Ubuntu-9.04-td3081264.html#a3081264)

your oss device might be not the real one, if you have not OSS4 installed.

FFmpeg can record from oss, alsa and jack

What is the reason for using alsa emulation of oss? 
It is buggy.

You may find the correct command in this thread.

Good luck!

---

### Post by bgiannes on 2009-07-10
mmmm....

i get a lot of static when i try and record both audio and video.

but when i record just sound with the same syntax (ie audio part) it's clear. doh!


igorzwx, how does your script/ffmpeg re-sync V and A back together, is there an internal clock id that is matched?  does -isync just do that?

---

### Post by igorzwx on 2009-07-10
does -isync just do that?

I do not know exactly, but the result seems to be perfect.

whithout -isync it may work too :p

You see, I tried everything, and pipes too.

It is not much written in the "man ffmpeg",
but you can ask on ffmpeg forums.

There was a lot of noise too.
The reason was PulseAudio.

Eventually, I decided to remove Pulse from all boxes for security reasons.

Try this or that and tell what works better for you.

---

### Post by hariks0 on 2009-09-10
Just use VLC media player for recording your desktop [version 1.x >]. VLC--> Media menu--> Open Capture Device [Ctrl+c] Select Desktop in capture mode.minimize VLC and whatever you do in the desktop, it will be recorded in a video file [*.mpg] format in your home folder.

---

### Post by Feelin_froggy8877 on 2009-11-07
Back at desktop recording...New comp, new hardware. Most of the above commands work very well, no droped frames chopping etc. What would be the option to record sound? If possible. I can always use kino to add audio.

---

