---
title: "HOWTO: AviSynth video processing with WINE"
date: 2009-11-21
forum: Tutorials
---

### Post by Bachstelze on 2009-11-21
[b]===============
HOWTO: AviSynth video processing with WINE
===============[/b]

[i]This guide has been tested with Ubuntu 9.10, 10.04 and 10.10, and AviSynth 2.5.8 and 2.6.0 Alpha 2 (090927), but should work in any modern Linux distribution, with any 2.5+ version of AviSynth (and probably older ones too).

Unless otherwise noted, all Windows-like paths (e.g. [font=monospace]c:\windows\system32[/font]) in this guide refer to the corresponding locations in your WINE virtual drive (by default, [font=monospace]~/.wine/drive_c[/font]).

This document is copyright 2009-2010 Firas Kraïem. It may be redistributed in any form, for any purpose, with or without modification, provided that this copyright notice appears in the distribution.[/i]

AviSynth is a very powerful video processing tool for Windows. Since it uses Windows-only interfaces like VfW (Video for Windows), AviSynth scripts cannot be used directly as input for Linux video encoding tools. However, a solution exists: [avs2yuv]("http://akuvian.org/src/avisynth/avs2yuv/") is an utility designed specifically for WINE, which takes an AviSynth script as input, and dumps its output as a yuv4mpeg stream to stdout or to a file, thus allowing further processing using any encoding tool that supports yuv4mpeg input.


**Usage**

In order to use it, the AviSynth DLLs ([font=monospace]avisynth.dll[/font] and [font=monospace]devil.dll[/font]) must be present in your WINE library path. Just running the AviSynth installer in WINE will do the trick. I also recommend copying [font=monospace]avs2yuv.exe[/font] to [font=monospace]c:\windows\system32[/font] so you can run it by typing just [font=monospace]wine avs2yuv[/font], instead of its full access path.

Finally, it is a good idea to have the latest x264 (see for example [this guide]("http://ubuntuforums.org/showthread.php?t=786095") about compiling it), since the build from the Karmic repositories is old and lacks some options that make our lives easier.

The avs2yuv homepage shows some usage examples. Another handy one, using x264 for encoding, would be:

```
wine avs2yuv input.avs - | x264 --stdin y4m --output output.264 -
```

The [font=monospace]--stdin y4m[/font] parameter is important: it tells x264 that what it gets on stdin is a yuv4mpeg stream. By default, x264 expects raw YUV data, which is not what we have.

If you kept the x264 version from the repos, you can use:

```
wine avs2yuv -raw input.avs - | x264 --fps 24000/1001 --output output.264 - 848x480
```

Since the x264 version from the repos does not support y4m on standard input, you have to pass raw YUV data instead, which means that you also have to specify the framerate and resolution of your video stream.

If you have a lot of similar encodings to do, you can use shell scripts to automate that, for example:

```
% cat encoding.sh
#!/bin/sh
#
# Usage:
#
# encoding.sh [input] [pass] [bitrate] [output]
#
# input:   input .avs script
# pass:    1 for first pass, 2 for second pass
# bitrate: bitrate :D
# output:  output file

if [ $2 = 1 ]; then
    output=/dev/null
else
    output=$4
fi

wine avs2yuv $1 - | x264 --preset slower --tune animation \
--pass $2 --bitrate $3 --stats "$4.pass" --bframes 4 --ref 8 \
--trellis 1 --colormatrix bt470bg --stdin y4m --output $output -

% ./encoding.sh input.avs 1 1500 output.264
[..]
% ./encoding.sh input.avs 2 1500 output.264
```


**Bugs and caveats**

[list]
[*]FFT3DGPU does not work in WINE 1.2 but works in WINE 1.3 (remember to install Direct3D first, it's [font=monospace]d3dx9[/font] in winetricks).
[*]VSFilter does not work correctly in WINE 1.0 (though hopefully no one uses it anymore). It works in WINE 1.2/1.3, but some fonts look [very bad]("http://img138.imageshack.us/img138/5004/winefonts.png") with it.
[*]RemoveGrain's dynamically linked builds ([font=monospace]RemoveGrain.dll[/font], [font=monospace]RemoveGrainSSE2.dll[/font], [font=monospace]RemoveGrainSSE3.dll[/font], et al.) require the Microsoft Visual C++ 2005 runtime libraries ([font=monospace]vcrun2005[/font] in winetricks). The statically linked builds ([font=monospace]RemoveGrainS.dll[/font], et al.) do not.
[/list]

All other filters I've tested work out of the box. Of course, I can't test them all, so if you find one that doesn't, please report in this thread.

---

### Post by ymark on 2009-11-21
Hello,

Thank you for this post, this is very usefull.

I am curious about the impact on performance using avysinth in wine.

Thank you,
ymark

---

### Post by Bachstelze on 2009-11-21
I still have to benchmark that, but it's surefine to not have to reboot in Windows when you need to encode something. :p

My current experience is that it is at least not slower. Might be faster on 64 bit machines since it allows to use a 64 bit build of x264.

---

### Post by ymark on 2009-11-21
Hello


Thanks for the quick reply.


I've started to test this on a Ubuntu 9.04. 
I've installed wine, deployed avysinth 2.56 and avs2yuv.exe.


I am trying to run the following command :

```

wine avs2yuv input.avs - | x264 --stdin y4m --output output.264 -

```

and i get something like this :

> 
x264: unrecognized option '--stdin'
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 0
input.avs: 480x272, 500000/40833 fps, 1556 frames
Output error: wrote only 185710 of 195840 bytes




I guess the problem is from x264. It doesn't recognize the --stdin parameter.

I've compiled the latest x264 too, but with no success.


From the x264 help i see :


```

Infile can be raw YUV 4:2:0 (in which case resolution is required),
  or YUV4MPEG 4:2:0 (*.y4m),
  or AVI or Avisynth if compiled with AVIS support (no).
Outfile type is selected by filename:
 .264 -> Raw bytestream
 .mkv -> Matroska
 .mp4 -> MP4 if compiled with GPAC support (yes)

```

There is no --stdin parameter in the help menu


Somebody have some sugestion?


Thank you,
ymark

---

### Post by Bachstelze on 2009-11-22
You're probably using an old version of x264. The --stdin parameter does appear in the latest ones:

[http://mewiki.project357.com/wiki/X264_Settings#stdin](http://mewiki.project357.com/wiki/X264_Settings#stdin)

EDIT: You said you compiled the latest x264. Did you also uninstall the version from the repos if you had it installed? What does this command output?

```
which x264
```

---

### Post by ymark on 2009-11-22
Hello,

You were right. That was an older version. I've not uninstalled the version from repositories.

I removed the repo version and compiled again

Now all works fine,

Thank you

---

### Post by Bachstelze on 2009-11-23
Guide updated with instructions to use the x264 build from the repos. As you can see, it's a tad more complicated, so I highly recomment compiling the latest x264.

---

### Post by qyot27 on 2009-12-05
If you use Sherpya's mplayer/mencoder Windows builds ([regular](http://sourceforge.net/projects/mplayer-win32/files/MPlayer%20and%20MEncoder/revision%2029851), and [ffmpeg-mt](http://sourceforge.net/projects/mplayer-win32/files/mplayer-mt/revision%2029319-mt)), you should be able to retain the framerate and resolution info.

On a pure Ubuntu setup with Linux mplayer and Linux x264, this works:
> Now that that's done, we're all set.  What's going to happen is that we'll make a named pipe using mkfifo, then have mplayer open the video, and pipe it over to x264.
```
mkfifo /path/to/input.y4m
x264 /path/to/input.y4m <options> | mplayer -nosound -vo yuv4mpeg:file=/path/to/input.y4m /path/to/inputfile
```
Obviously, /path/to/inputfile and whatnot represent the actual paths on your setup, usually /home/username/video.avi or /home/username/Documents/video.avi or whatever it really is.  **The same goes for that named pipe.**  <options> is obviously where your x264 options go.
Taken from a tutorial I'd written for Intrepid, but should still be valid.  I have confirmed that Sherpya's build of mplayer r29851 can play AviSynth scripts, and the mencoder builds do as well (I use the mencoder builds a lot, so that was a given, but I don't use mplayer to test my scripts so I had to check).  So hopefully, it is possible to pipe from Windows mplayer to Linux x264 and keep the resolution and framerate intact so you don't have to specify it.  It seems to rest in whether Windows mplayer can correctly dump to mkfifo's output.

Special note: Using && to run the mkfifo and the x264 | mplayer commands in one incurs a performance hit that running mkfifo first, and then the other does not.

---

### Post by Bachstelze on 2009-12-05
I've found mplayer to be unreliable sometimes. For example when given a lossless x264 stream as input, the output was not frame-accurate (my subtitles were off-by-one).

---

### Post by qyot27 on 2009-12-05
> **Bachstelze said:**
> I've found mplayer to be unreliable sometimes. For example when given a lossless x264 stream as input, the output was not frame-accurate (my subtitles were off-by-one).
Couldn't that be a problem with libass, though?  If it is, then taking the decision out of its hands by using TextSub() would resolve it.  The problem with that encode could have been if the H.264 stream had certain frame types, though (does mplayer have a known problem with B-frames/B-pyramid/mixed refs?) - with AviSynth this would be null and void.

I can't seem to get ffmpeg to pipe correctly here, but if mplayer really is the culprit and not libass, maybe ffmpeg would be unaffected?  I have to rebuild ffmpeg with --enable-avisynth first, though.

---

### Post by Bachstelze on 2009-12-05
> **qyot27 said:**
> Couldn't that be a problem with libass, though?  If it is, then taking the decision out of its hands by using TextSub() would resolve it.  The problem with that encode could have been if the H.264 stream had certain frame types, though (does mplayer have a known problem with B-frames/B-pyramid/mixed refs?) - with AviSynth this would be null and void.


Yeah, you're right, I'll blame that on lack of sleep. :p

But anyway, the goal here is to make as little use of WINE as possible. However you look at it, WINE is in itself a hack, and as with all hacks, it is a bit dirty (just look at all the warning is spits out when you run pretty much anything), so the less we use it, the better. At least that's how I see it.

---

### Post by qyot27 on 2009-12-05
> **Bachstelze said:**
> Yeah, you're right, I'll blame that on lack of sleep. :p

But anyway, the goal here is to make as little use of WINE as possible. However you look at it, WINE is in itself a hack, and as with all hacks, it is a bit dirty (just look at all the warning is spits out when you run pretty much anything), so the less we use it, the better. At least that's how I see it.
The only thing being called with WINE would be mplayer, as it would take avs2yuv's place in the pipe.  The other solution would be to use *wine mencoder* to output to an ffvhuff or ffv1 AVI and then use the native mplayer+x264 method, which is currently what I do if I don't just output to raw YUV 4:2:0.

Agreed, though; if only there was a native framework that was compatible with VFW and DirectShow filters - albeit with necessary recompilation against the new framework - this would be solved (AviSynth 3.0 may have been well-intentioned, but I honestly think it was a little too much of trying to reinvent the wheel, and therefore was kind of doomed from the get-go).

---

### Post by verb3k on 2010-01-30
How can you trim audio if you're just piping a yuv stream?
For audio to stay in proper sync with video, it has to be trimmed with avisynth as well.

---

### Post by Bachstelze on 2010-01-30
> **verb3k said:**
> How can you trim audio if you're just piping a yuv stream?
For audio to stay in proper sync with video, it has to be trimmed with avisynth as well.

For audio you can use [WAVI]("http://sourceforge.net/projects/wavi-avi2wav/") which is basically the avs2yuv counterpart for audio (dumps the audio output of the AviSynth script in raw PCM or WAV format, to stdout or to a file).

---

### Post by verb3k on 2010-01-30
Thanks for the quick response, Bachstelze.

I've installed the ffdshow-tryout package with the latest avisynth, but when I try to open an avi with AVISource() it gives me the following message:

> 
Avisynth error:
No compatible ACM codec to decode 0x2000 audio stream to PCM.


I tried and made an avi with only video, and it works perfectly. So, I'd appreciate it if you could help.

Thanks in advance.

---

### Post by Bachstelze on 2010-01-30
> **verb3k said:**
> Thanks for the quick response, Bachstelze.

I've installed the ffdshow-tryout package with the latest avisynth, but when I try to open an avi with AVISource() it gives me the following message:

ffdshow is, as its name implies, a DirectShow filter, which means that it is only used to decode files with DirectShow. In AviSynth, you do that with DirectShowSource(). AviSource() uses a different decoding method, and requires a real VfW or ACM codec to decode files, not just a DirectShow filter. What is the audio format your video uses?

---

### Post by verb3k on 2010-01-30
For the file I used for the first test, it was using AC3. I also tried a file with MP3 and it gives the same message. DirectShowSource() would give me the following:

> 

Avisynth error:
DirectShowSource: Could not open as video or audio.

Video returned:  "DirectShowSource: RenderFile, the filter graph manager won't talk to me"

Audio returned:  "DirectShowSource: RenderFile, the filter graph manager won't talk to me"


---

### Post by Bachstelze on 2010-01-30
> **verb3k said:**
> For the file I used for the first test, it was using AC3. I also tried a file with mp3 and it gives the same message. DirectShowSource would give me the following:

I have actually never tried DSS() in WINE, that's something I would have to investigate. What I would do if I were you is extract the audio stream from the AVI file and decode it to WAV using ffmpeg:

```
ffmpeg -i input.avi -vn -acodec pcm_s16le audio.wav
```

And then use that as the audio stream in your AviSynth script with WAVSource():

```
video = AVISource("video.avi", audio=false)
audio = WAVSource("audio.wav")
AudioDubEx(video, audio)
```

That being said, for MP3, the WINE appDB says the [LameACM codec]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14681&iTestingId=34132") works, so you shouldn't need to do that.

---

### Post by verb3k on 2010-01-30
> **Bachstelze said:**
> I have actually never tried DSS() in WINE, that's something I would have to investigate. What I would do if I were you is extract the audio stream from the AVI file and decode it to WAV using ffmpeg:

```
ffmpeg -i input.avi -vn -acodec pcm_s16le audio.wav
```

And then use that as the audio stream in your AviSynth script with WAVSource():

```
video = AVISource("video.avi", audio=false)
audio = WAVSource("audio.wav")
AudioDubEx(video, audio)
```

That being said, for MP3, the WINE appDB says the [LameACM codec]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14681&iTestingId=34132") works, so you shouldn't need to do that.

Thank you very much Bachstelze, I didn't know about the audio=false argument and the WAVSource(). Now everything works great!
Thanks again :)

---

### Post by qyot27 on 2010-01-30
> **Bachstelze said:**
> ffdshow is, as its name implies, a DirectShow filter, which means that it is only used to decode files with DirectShow. In AviSynth, you do that with DirectShowSource(). AviSource() uses a different decoding method, and requires a real VfW or ACM codec to decode files, not just a DirectShow filter. What is the audio format your video uses?
ffdshow also has a VFW interface, and can do both encoding and decoding (I often used it through VirtualDub to produce ffvhuff and MJPEG files before I switched to using mencoder for the former, and it of course also provides the necessary support to *open* those formats in VirtualDub, et al).  I'm not entirely sure if the audio decoder is ACM-compatible, though.  I doubt it, however.

I don't think I've ever gotten DirectShowSource to work, even after attempting to get the Platform SDK 2003 (which is what has the DirectShow layer stuff in it) installed using winetricks.  Of course, that could just be a matter of me not configuring it right.  I can't remember what kinds of results I got with AVISource.  ffdshow is a terror to try to get setup correctly in Wine, though.  None of the drop-downs on the decoder configuration pages work - I had to grab the .reg file I generated under XP and import that into Wine's registry to make it select the formats I needed.

Generally, I would recommend sticking to MPEG2Source (DGMPGDec package), and FFmpegSource (both 1.21 and the 2.x branch/svn snapshots, since they don't conflict with each other) - those really cover most or all of what AVISource and DirectShowSource can do, and they're pretty much guaranteed to work under Wine because they're self-contained.  If they don't work then your files were probably already borked to start with.  FFmpegSource2 can use Haali's Media Splitter to work with MPEG2-TS files, and I don't know how well that would work under Wine.  The solution, of course, is just remux TS to MKV first.

For FFmpegSource, you can get it to index the audio by passing the atrack=-1 parameter.

1.21 (deprecated for quite a while now, but still works well):
```
FFmpegSource("video.mkv",atrack=-1)
```
or 2.x/svn:
```
FFmpegSource2("video.mkv",atrack=-1)
```
Technically, the function FFmpegSource2 is in the wrapper .avsi that comes with the plugin, and is provided for those more comfortable with 1.21's syntax, although because it can also load audio it has its own usefulness apart from that.

---

### Post by Arctures on 2010-04-13
Hi everyone. Avisynth is really great tool and I want to get it working on my Linux boxes but w/o any luck yet. I am trying to get simple avisynth script to work:

```
AVIFileSource("source.file")
complementparity
separatefields
```

Basically I have short HDV m2t footage captured via dvgrab. When I am encoding my m2t footage into Huffyuv avi file (or raw yv12 or mjpeg and etc) and then trying to feed avisynth with that I am getting:

```
Avisynth error:
AVISource: couldn't locate a decompressor for fourcc HFYU
(./sepfields.avs, line 1)
```

Same thing repeats for other formats with reflect of it's fourCC. I have ffdshow tryouts installed via wine (tried also klcodec and old ffdshow). Also I have tried to install Huffyuv for windows separately. Last guess was to change wine PATH variable. I had been put PATH info into wine registry and still getting the same errors. And yes I have tried issuing AVIFileSource("source.file"), DirectShowSource("source.file") and AVIFileSource w/o any luck. I cannot understand where the exact problem is and I wonder that nobody reports similar issue because I've got it over three different Linux boxes. Any clues would be greatly appreciated.

---

### Post by Bachstelze on 2010-04-13
> **Arctures said:**
> Hi everyone. Avisynth is really great tool and I want to get it working on my Linux boxes but w/o any luck yet. I am trying to get simple avisynth script to work:

```
AVIFileSource("source.file")
complementparity
separatefields
```

Basically I have short HDV m2t footage captured via dvgrab. When I am encoding my m2t footage into Huffyuv avi file (or raw yv12 or mjpeg and etc) and then trying to feed avisynth with that I am getting:

```
Avisynth error:
AVISource: couldn't locate a decompressor for fourcc HFYU
(./sepfields.avs, line 1)
```

Same thing repeats for other formats with reflect of it's fourCC. I have ffdshow tryouts installed via wine (tried also klcodec and old ffdshow). Also I have tried to install Huffyuv for windows separately. Last guess was to change wine PATH variable. I had been put PATH info into wine registry and still getting the same errors. And yes I have tried issuing AVIFileSource("source.file"), DirectShowSource("source.file") and AVIFileSource w/o any luck. I cannot understand where the exact problem is and I wonder that nobody reports similar issue because I've got it over three different Linux boxes. Any clues would be greatly appreciated.

Most probably the Huffyuv codec is not properly installed. Does it show up in the codecs list in e.g. VirtualDub?

---

### Post by Arctures on 2010-04-13
That is really strange. After ffdshow and Huffyuv installation I don't have it in VDub codecs. All I have is Cinepak, ffdshow Video codec, Wine MS, Wine Video1. As I understand ffdshow should show more than just 'ffdshow Video codec'?

---

### Post by Bachstelze on 2010-04-13
> **Arctures said:**
> That is really strange. After ffdshow and Huffyuv installation I don't have it in VDub codecs. All I have is Cinepak, ffdshow Video codec, Wine MS, Wine Video1. As I understand ffdshow should show more than just 'ffdshow Video codec'?

I don't know about ffdshow, but the Huffyuv codec definitely should.

---

### Post by qyot27 on 2010-04-13
I don't believe ffdshow's VFW interface is set by default to decode anything (or at least, not HuffYUV).  Supposing that you made sure to enable the VFW interface while installing, you can get to the proper dialog by choosing the VFW configuration option in the Wine menu, or going to the configuration for ffdshow through VDub (and no, if you're in VDub's codec configuration dialog, 'ffdshow Video Codec' is the only one that should show up there for ffdshow; the other configuration dialogs - Audio decoder, DXVA, and Video decoder, are separate from it and not relevant in this case).  You need to set the box for HuffYUV from 'disabled' to 'libavcodec'.

It's pretty hard to get the stuff selected, though - the drop-downs don't seem to work at all.  I worked around it by configuring it on Windows, making ffdshow export its configuration to a .reg file, and then importing that .reg file into Wine's registry.  Then it was fine.

DirectShowSource won't work at all - Wine can't use DirectShow yet, or only by going through a lot of really complicated hoops first.  I've never managed it, at any rate.

---

### Post by Arctures on 2010-04-14
Thank you for your answers. I was able to install Huffyuv with the following command:

```
wine /usr/lib32/wine/fakedlls/rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 ../avisynth/huffyuv.inf
```

 ../avisynth/ folder contains unzipped huffyuv package. But now I am stuck with

```
$ wine avs2yuv ./sepfields.avs -o - | mencoder - -o hfyu.avi -ovc lavc -lavcopts vcodec=ffvhuff:vstrict=-1:pred=2:context=1
MEncoder SVN-r29796-4.3.4 (C) 2000-2009 MPlayer Team
Reading from stdin...
success: format: 0  data: 0x0 - 0x0

Avisynth error:
Script error: there is no function named "Load_Stdcall_Plugin"
(ffavisynth.avsi, line 1)
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
```

All I want is to get my 50i footage delaced to 50p and then slowed down to 25p to achieve slow motion movement effect.

---

### Post by qyot27 on 2010-04-14
Why are you trying to execute the .avs like a shell script?  That's not necessary at all.  I don't know if that would be the sole issue, though - I've never been able to pipe properly to mencoder.

Worse comes to worst, you could always use a Windows build of mencoder, as [Sherpya's builds](http://oss.netfarm.it/mplayer-win32.php) include AviSynth support, so you wouldn't have to mess around with avs2yuv or piping.  Windows builds of ffmpeg also usually have support for AviSynth (you'd need to get r22717, though - ffmpeg compilation under MinGW is currently borked, and I think that r22717 - or r22718 - is the latest one that does compile cleanly*).

*technically, newer revisions can build fine, but I haven't pinpointed all the stuff that has to be disabled (I just know my ./configure line for an FFMS2-bound ffmpeg worked).  [The problem is in the RTSP code - it was fixed for POSIX systems, but broke MinGW.](http://ffmpeg.arrozcru.org/forum/viewtopic.php?f=1&t=1347)  Trying to disable just rtsp didn't seem to fix it.  Not sure what else I'd have to do.  The patch linked to in that thread didn't help, either, unfortunately.

EDIT Apr 16 2010: The RTSP timeout issue on MinGW is fixed now.

---

### Post by Arctures on 2010-04-15
Yes I have realized I should get windows-like editing curve as much as possible. Now I am using great tutorial from Eugenia - 
[http://eugenia.gnomefiles.org/2009/02/09/butter-smooth-slow-motion/](http://eugenia.gnomefiles.org/2009/02/09/butter-smooth-slow-motion/)
All main parts are working so far and I hope I could keep my box windows-free. I am using linux last 5 years and video editing is still a pain. Simple cut-encode works but when I need some creative steps it almost always a pain. Wish there would be sony vegas analog - I'll buy two.

---

### Post by Bachstelze on 2010-04-15
If you want to encode in Huffyuv, you can try doing it in VDub with the VfW codec instead of mencoder.

---

### Post by qyot27 on 2010-04-15
Well, it's not really a consolation right now, but I would keep an eye on VLMC - it looks like it has the potential to be a very good analog to NLEs like Premiere and Vegas.  I've played around with it some and it is still very much pre-alpha software by their own admittance, but the layout is nice and familiar (albeit the text is screwy if you use a dark theme), and so is the timeline.  I do hope they implement rubberbands and effect keyframing support - then I'd be pretty happy.

---

### Post by Arctures on 2010-04-16
Yes VLMC looks very promising. VLC guys know a lot about video and I hope it will be excellent tool. Also [http://www.editshare.com/index.php?option=com_content&task=view&id=164&Itemid=146](http://www.editshare.com/index.php?option=com_content&task=view&id=164&Itemid=146) Lightworks looks very promising. But they are going to go open source in Q3/2010 and as per specs it looks like there is no Linux version yet so it should be ported.

---

### Post by pokipoki08 on 2010-05-23
choose & input the following into system.ini

```
[drivers32]
vidc.X264=x264vfw.dll
vidc.FVFW=ff_vfw.dll
VIDC.HFYU=huffyuv.dll
msacm.ac3acm=AC3ACM.acm
msacm.lameacm=LameACM.acm
```

copy files .acm .dll into windows\system32 directory, test the codecs using virtualdub

get the codecs from [www.free-codecs.com](www.free-codecs.com)

I setup wine environment using winetricks, but install the video/audio codecs manually (don't use winetricks for this).

ffdshow-tryout also helps when configured properly. Everything wrt encoding works faster in wine!

---

### Post by Bachstelze on 2010-12-11
Updated because FFT3DGPU now works with WINE 1.3.

---

### Post by taipan67 on 2010-12-13
Before i get to the meat of the issue, can i first say a big thanks to the OP for this guide, which is also linked to from the Avisynth website for anyone asking after its use in Linux (if you didn't already know)!

I've just started playing around with this, as i'm not entirely happy with Avidemux or Handbrake for my MP4-encoding, and using Avisynth to filter sources into x264 compiled from source (so i can have at least *some* cpu-optimisation from my athlon-xp) seems like the optimum choice.

The reason i'm posting is that i'm trying to find the best way to see if Avisynth is doing what's expected through some sort of logging system. Unfortunately, the Windows utility **Debugview** doesn't work in Wine, but based on the fact that the Avisynth filters that support debug-output do so through a function with *"debugstring"* in its name, i've come up with this solution:-```
mkfifo piped.y4m &&
WINEDEBUG=warn+debugstr wine avs2yuv input.avs -o piped.y4m 2>&1 | cut -d" " -f2- >avs.log & 
   x264 <options> --muxer mp4 -o output.m4v piped.y4m
```
This appears to me to work okay - i can see that the functions in the avs-script with debugging enabled are doing their thing. However, i don't have a Windows system to compare the output to, and i'd like to hear from anyone who can do such a comparison, and also from anyone who actually understands what the multitude of $WINEDEBUG alternatives do, and if there are better options than the one above.

In the meantime, if anyone wants to make use of my technique, i'd recommend adding the *'trim()'* function to your input-script initially, and possibly piping to mplayer rather than an encoder - just to save time while checking the logging capability... ;)

---

### Post by superdupont on 2011-05-12
Hi.
I'm using avisynth with wine for years on Ubuntu (using either avs2yuv or vdubmod)...but since natty upgrade few days ago avisynth plain stopped working :confused:

if I chain avs2yuv->x264, I got "failed to load avisynth.dll", and if I load .avs script with vdubmod(even one single line to load any d2v file) , I get "import AVi error unknown (80040154)"

I tried to purge/reinstall avisynth, tried different versions (2.5.7 / 2.5.8 & alpha...), no luck, nothing still no avisynth...

Could someone tell me where to look to try to solve this nonsense ? :)

---

### Post by Bachstelze on 2011-05-12
I just tried in a Natty VM, and I had to install the Visual C++ 6.0 libraries (vcrun6 in winetricks). Try that and see if it works for you as well, then I'll add it to the tutorial.

---

### Post by superdupont on 2011-05-13
> **Bachstelze said:**
> I just tried in a Natty VM, and I had to install the Visual C++ 6.0 libraries (vcrun6 in winetricks). Try that and see if it works for you as well, then I'll add it to the tutorial.

just launched winetricks to check, alas vcrun6 was already installed.
So I added vcrun2005-2008 just in case, and  I got some error near the end of install...

> 
Executing w_do_call vcrun2008
Executing load_vcrun2008
Executing mkdir -p /home/jc/.cache/winetricks/vcrun2008
Downloading [http://download.microsoft.com/download/9/7/7/977B481A-7BA6-4E30-AC40-ED51EB2028F2/vcredist_x86.exe](http://download.microsoft.com/download/9/7/7/977B481A-7BA6-4E30-AC40-ED51EB2028F2/vcredist_x86.exe) to /home/jc/.cache/winetricks/vcrun2008
Using native,builtin override for following DLLs: msvcr90
Executing winetricks_early_wine regedit C:\windows\Temp\_vcrun2008\override-dll.reg
Executing wine vcredist_x86.exe
err:module:attach_process_dlls "msvcrt.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Y:\\vcrun2008\\vcredist_x86.exe" failed, status c0000142
------------------------------------------------------
Note: command 'wine vcredist_x86.exe' returned status 66.  Aborting.


no clue if it's related...

edit : ok, something is very wrong here, I can't even launch regedit anymore , same "msvcrt.dll" initializing error than above, seems my problem is larger than just avisynth, argh...

---

### Post by Bachstelze on 2011-05-13
Are you using WINE 1.2 or 1.3 ?

---

### Post by superdupont on 2011-05-13
> **Bachstelze said:**
> Are you using WINE 1.2 or 1.3 ?

1.2.2. although it always worked with it, will try with 1.3.x

edit : upgraded to 1.3.19 ... and still same problems, no regedit ,no avisynth, failed to load/initialise dlls...
I smell it could have something to do with paths although I don't know how to fix things...

re-edit : found msvcrt.dll listed in winecfg->libraries in 'remplacements existants", trashed it, now regedit works at least. but still no avisynth...

---

### Post by superdupont on 2011-05-13
WORKS  :popcorn:
[[IMG]http://img832.imageshack.us/img832/6074/capture1efr.th.png[/IMG]](http://img832.imageshack.us/i/capture1efr.png/)

dunno how exactly, I just purged/reinstalled avisynth one more time, after wine upgrade AND this msvcrt.dll "doppelganger" trashed via winecfg->libraries.

---

### Post by Kenjitamura on 2011-06-06
I'm on Ubuntu 10.10 and have wine 1.3.20, I deleted my wine directory and when I reinstalled avisynth I received error  "Avisynth.dll failed to load".  Installing vcrun2006 fixed the problem.

---

### Post by brothermechanic on 2011-12-29
hello
I often use in my work avisynth.
The fact that I'm on Linux and avisynth works for me with wine, you've guessed it themselves)))
The question is ....
In the script, avisynth to load the plugin I'm writing something like this
............
LoadPlugin ("C:\Program Files\AviSynth 2.5\plugins\MYPLUGIN.dll")
..........
Is it possible to simplify the writing to
.........
LoadPlugin ("MYPLUGIN.dll")
..................
(I hate backslashes))))
I guess that if you copy plug-in system32 will work, isn't it ?????
but then there will be not pretty cool
How to make the path 
C:\Program Files\AviSynth 2.5\plugins\system
more easier???
thank you

---

### Post by Bachstelze on 2011-12-29
All relative paths in an AviSynth script are interpreted relative to the directory where the script is locateds, so if you want to just use the filename, the plugin must be in the same directory as the script.

---

### Post by chickenPie4breakfast on 2012-02-06
> **Arctures said:**
> Yes I have realized I should get windows-like editing curve as much as possible. Now I am using great tutorial from Eugenia - 
[http://eugenia.gnomefiles.org/2009/02/09/butter-smooth-slow-motion/](http://eugenia.gnomefiles.org/2009/02/09/butter-smooth-slow-motion/)
All main parts are working so far and I hope I could keep my box windows-free. I am using linux last 5 years and video editing is still a pain. Simple cut-encode works but when I need some creative steps it almost always a pain. Wish there would be sony vegas analog - I'll buy two.

I use Sony Vegas 8.0c under WINE

---

### Post by chickenPie4breakfast on 2012-03-24
what do you think of this port for linux anyone tried it?
[http://code.google.com/p/avxsynth/]("http://code.google.com/p/avxsynth/")

---

### Post by qyot27 on 2012-03-24
> **chickenPie4breakfast said:**
> what do you think of this port for linux anyone tried it?
[http://code.google.com/p/avxsynth/]("http://code.google.com/p/avxsynth/")
I've been wrangling with it since last night.  There's a couple of issues, so I'd wait for it to mature a bit, but once those are resolved the core functionality will be there.  Then it'll just be a waiting game to get the third-party plugins to work with it.

Currently I can't get the modified FFMS2 to work with it (as in, it doesn't want to load it at all), which means not really being able to test anything because that's the only source filter available at this point.

It is rather disappointing that it's based on 2.5.8 instead of the 2.6 CVS trunk, but according to the devs that might be doable with a couple months' work.

---

### Post by qyot27 on 2012-03-25
Updated build instructions (2012-05-1[color="black"]8[/color]) are a few posts down from here:
[http://ubuntuforums.org/showpost.php?p=11948686&postcount=50](http://ubuntuforums.org/showpost.php?p=11948686&postcount=50)


Yeah, so the FFMS2 loading issue is because of funky shared library conventions.  Once I got over that hurdle, I was able to troubleshoot it a bit more and finally got it to load video.

[old instructions snipped]

Whether this is still necessary for Precise or when dealing with newer builds of AvxSynth I don't know; I'm leaving it here just in case.

This is a fix for the debugger hanging on dlopen.  In your home directory:
```
touch .gdbinit
```

Now, open .gdbinit in your text editor of choice and copy and paste the following into it.  It does differ based on which version you run.
(for 32-bit Ubuntu)
```
set env LD_PRELOAD /lib/i386-linux-gnu/libpthread.so.0
```
(for 64-bit Ubuntu)
```
set env LD_PRELOAD /lib/x86_64-linux-gnu/libpthread.so.0
```

[old instructions snipped]

I was able to open a normal H.264 MKV file and resize it without any big issue, and mplayer displayed it correctly as well.  I didn't do a whole lot of testing, but it does look good for how early it is in the porting process.

---

### Post by chickenPie4breakfast on 2012-04-05
@qyot27  Wow, thanks for taking the time for the mini guide !

It's better than the one on the official website which put me off even trying it - that's why I asked here if anyone had tried it to see if it was worth it, I may be brave and give it a go now.

by the way DirectShowSource has been working for me under wine, I think it was after I installed the Klite-codec pack (full)  I use it to open Mpg files in virtual dub via an avisynth script but may start using mpeg2source instead.

---

### Post by qyot27 on 2012-04-05
> **chickenPie4breakfast said:**
> @qyot27  Wow, thanks for taking the time for the mini guide !

It's better than the one on the official website which put me off even trying it - that's why I asked here if anyone had tried it to see if it was worth it, I may be brave and give it a go now.
It's actually based in part on the guide from the official site.

And the patch for ffms2avs stopped wanting to work with wget shortly after I made the post.  You should still be able to navigate to the page in your browser and download it that way, provided the Gist hasn't been removed.  Of course, this might become moot with there being an avxsynth branch on FFMS2's SVN repo now.  I haven't gotten around to messing with that yet, though.

> by the way DirectShowSource has been working for me under wine, I think it was after I installed the Klite-codec pack (full)  I use it to open Mpg files in virtual dub via an avisynth script but may start using mpeg2source instead.
Well, if DirectShowSource is working then it's not because of K-lite, it would be because Wine finally got the framework support itself hashed out, which would then allow K-lite or other DirectShow filters to work.  And wow, I didn't even realize they were up to 1.5.x as the development branch.  I think I'm still on 1.3.something.

That said, there's little use for DirectShowSource anymore.  There's only two reasons to still use it: very quick previewing of files (as DSS doesn't have to index anything like MPEG2Source or FFmpegSource/FFMS2), or being able to convert softsubbed files to hardsubbed files without demuxing the subs and/or attachments first and using a separate subtitling filter.  The indexing-based filters have always taken priority* due to being both more accurate and not being tied to platform-specific frameworks like DirectShow, which means that they usually can be used in Wine with zero problems.

*with an exception for most types of AVI files; AVISource is fine to use or even preferred for those.

Regarding MPEG2Source, there's an SSE-optimized build of DGDecode 1.5.8 that is hosted on HCenc's homepage.  That's the version to use.  Just replace the DGDecode.dll that came with DGIndex with the SSE one, and voila.


Actually, I usually cross-compile FFMS2 on Ubuntu for use under Windows, which also means Wine installations can use it (and it works perfectly well under Wine on OSX, as tested on the iMacs I have access to that run Snow Leopard and Lion).

---

### Post by qyot27 on 2012-05-18
Due to a rash of buildsystem-related commits to AvxSynth over the last few days, things are much easier to coalesce together now.  FFmpeg and FFMS2 can now be built statically and linked in, and they no longer have to be installed to the system (so that existing versions won't conflict with the ones AvxSynth gets).  In light of that, an updated set of instructions for building it:


Grab the dependencies:
```
sudo apt-get install build-essential checkinstall subversion git yasm liblog4cpp5-dev liblog4cpp5 libcairo2-dev libpango1.0-dev libjpeg-dev libqt4-dev libqt4-designer libqt4-gui kdevelop
```
I left checkinstall in there so that maybe we can get a proper command for that for the AvxSynth step, even though I don't use it right now.

MPlayer is also a dependency, but I have it in a separate step because there's a chance that the user might compile their own copy.
```
sudo apt-get install mplayer
```


FFmpeg and FFMS2 will be installed to a directory named ffavxbuild in the user's $HOME.  AvxSynth will detect them there and then it - and only it - will get installed to the system.
Build FFmpeg
```
git clone git://git.videolan.org/ffmpeg.git
cd ffmpeg
./configure --prefix=$HOME/ffavxbuild --enable-gpl --enable-version3 --extra-cflags="-march=native -mtune=native"
make
make install
```

Build FFMS2
```
svn checkout http://ffmpegsource.googlecode.com/svn/trunk ffms2
cd ffms2
PKG_CONFIG_PATH=$HOME/ffavxbuild/lib/pkgconfig ./configure --prefix=$HOME/ffavxbuild --enable-static --disable-shared
make
make install
```

Build AvxSynth
```
git clone git://github.com/avxsynth/avxsynth.git
cd avxsynth
sed -i 's/\/usr\/bin\/mplayer/mplayer/g' apps/avxframeserver/frameserverlib/src/avxSynthAppInterface.cpp
PKG_CONFIG_PATH=$HOME/ffavxbuild/lib/pkgconfig ./configure --prefix=/usr
make
sudo make install
```
Normally, AvxSynth looks for mplayer in /usr/bin.  This won't be true for users that compile mplayer themselves and keep the install path at the default /usr/local[/bin].  If mplayer is there, AvxSynth won't be able to find it.  The sed line removes the /usr/bin from the mplayer search path and allows it to find mplayer anywhere, so long as it's on the PATH.

I also forced it to install AvxSynth into /usr because installing it into /usr/local resulted in it not being able to find the libs correctly.  Maybe that was related to stuff (--disable-debug --enable-strip) I tried in a previous build test but dropped later, or something.  But forcing it to /usr resolved it.

---

### Post by avxsynthTesting on 2012-05-31
> **qyot27 said:**
> Due to a rash of buildsystem-related commits to AvxSynth over the last few days, things are much easier to coalesce together now.  FFmpeg and FFMS2 can now be built statically and linked in, and they no longer have to be installed to the system (so that existing versions won't conflict with the ones AvxSynth gets).  In light of that, an updated set of instructions for building it:

snipped


First off, thank you for your interest in AvxSynth. I am a member of the AvxSynth team and am responsible for improving the build system. As such, I am very interested in your feedback. Please note that AvxSynth has an [official forum thread]("http://forum.doom9.org/showthread.php?t=164386") at Doom9's forum. Additionally, we invite you to provide feedback at the official [GitHub project page]("https://github.com/avxsynth/avxsynth").

I have come here because your post shows as one of the top results on a Google search for AvxSynth, and would like to address some points before any confusion is caused:

1. AvxSynth libraries can be installed and run from /usr/local/lib without problem. You must run the command "sudo ldconfig" after installing any shared libraries. As of earlier today, the build system now does this automatically.

2. Attempting to link static libraries into shared libraries is non-portable. Specifically, attempting to do this on x86-64 will cause a linking error. Therefore, I would advise those intending to build their own copy of ffmpeg/libav to enable the shared libraries.

Thank you!

---

### Post by qyot27 on 2012-05-31
> **avxsynthTesting said:**
> First off, thank you for your interest in AvxSynth. I am a member of the AvxSynth team and am responsible for improving the build system. As such, I am very interested in your feedback. Please note that AvxSynth has an [official forum thread]("http://forum.doom9.org/showthread.php?t=164386") at Doom9's forum. Additionally, we invite you to provide feedback at the official [GitHub project page]("https://github.com/avxsynth/avxsynth").
I've been responding on the Doom9 thread too.  I reported the recently-resolved [mplayer path issue](http://forum.doom9.org/showpost.php?p=1566881&postcount=64) there back in March, along with some other things that have also been resolved.  I'm watching the Github repo and it's on my RSS feeds.

> 1. AvxSynth libraries can be installed and run from /usr/local/lib without problem. You must run the command "sudo ldconfig" after installing any shared libraries. As of earlier today, the build system now does this automatically.
That certainly explains it.  The need to run ldconfig escapes me at times.

> 2. Attempting to link static libraries into shared libraries is non-portable. Specifically, attempting to do this on x86-64 will cause a linking error. Therefore, I would advise those intending to build their own copy of ffmpeg/libav to enable the shared libraries.
Wouldn't the linking error be solved by using position-independent code flags on all the dependencies?  That's what a cursory Googling seemed to hint at.  For x86-64 it's generally recommended to use that option anyway; the only reason I omitted it from my typical instructions is that I primarily work on x86 and it doesn't require it to be explicitly declared there.

---

### Post by avxsynthTesting on 2012-05-31
> **qyot27 said:**
> I've been responding on the Doom9 thread too.  I reported the recently-resolved [mplayer path issue]("http://forum.doom9.org/showpost.php?p=1566881&postcount=64") there back in March, along with some other things that have also been resolved.  I'm watching the Github repo and it's on my RSS feeds.


That certainly explains it.  The need to run ldconfig escapes me at times.


Wouldn't the linking error be solved by using position-independent code flags on all the dependencies?  That's what a cursory Googling seemed to hint at.  For x86-64 it's generally recommended to use that option anyway; the only reason I omitted it from my typical instructions is that I primarily work on x86 and it doesn't require it to be explicitly declared there.

Unfortunately, due to some issues in ffmpeg/libav codebase, merely compiling with PIC options enabled is not sufficient. For more information, please see [http://roundup.libav.org/issue1563](http://roundup.libav.org/issue1563) . In general, this is not a recommended operation, and I especially recommend new users to stick with shared libraries.

---

### Post by qyot27 on 2012-06-02
> **avxsynthTesting said:**
> Unfortunately, due to some issues in ffmpeg/libav codebase, merely compiling with PIC options enabled is not sufficient. For more information, please see [http://roundup.libav.org/issue1563](http://roundup.libav.org/issue1563) . In general, this is not a recommended operation, and I especially recommend new users to stick with shared libraries.
Yeah, I ran into the problem last night when I finally tried it on a 64-bit install of 11.10.  I only had enough energy last night to figure out, like in the bug report there, that it works if --disable-asm (and probably more specifically, --disable-mmx) is used.

I wondered about that, looked at the actual piece of FFmpeg source code that had the issue, gave up on that, then looked at how the C-plugin version of FFMS2 does it for normal AviSynth (which gave me an idea), and then tried a little bit more just now.  Turns out that the only thing needed after the PIC flagging is to pass -Wl,-Bsymbolic to AvxSynth with --extra-ldflags.  No need to disable assembly, everything linked and seemed to work just like it does on my 32-bit system.



Since I'm wondering about the comments about portability, is this pertaining to something internal to the code development process?  Because the only use of 'portability' I'm used to is in reference to being able to use a piece of software built on computer A on similar computer B without problems, but I have a feeling that's not what was meant in those discussions and comments.

---

### Post by avxsynthTesting on 2012-06-06
Portability there is referring to running on multiple operating systems  and machine architectures. Generally speaking, mixing static and shared  libraries is not a well-defined operation on all systems. That said,  AvxSynth is unlikely to ever run on anything but x86 and Linux so it is a  bit of a moot point. It is interesting that you managed to compile the  plugin with -Bsymbolic, but I'm reluctant to just add that into the  build system.

---

### Post by qyot27 on 2012-06-06
> **avxsynthTesting said:**
> Portability there is referring to running on multiple operating systems  and machine architectures. Generally speaking, mixing static and shared  libraries is not a well-defined operation on all systems. That said,  AvxSynth is unlikely to ever run on anything but x86 and Linux so it is a  bit of a moot point. It is interesting that you managed to compile the  plugin with -Bsymbolic, but I'm reluctant to just add that into the  build system.
Although it would seem to be a little weird and kind of unelegant, it could be passed as a parameter.  Something like --static-dep that has a warning that it's only relevant for x64.  Alternatively that there could be some conditional detection of the dependencies that would be able to tell whether -Bsymbolic is needed and add it only as necessary.  The latter option is what the FFMS2 trunk seems to do, as there's a check toward the end concerning whether -Wl,-Bsymbolic is needed.

While I had actually gotten the idea from looking at FFMS2's AviSynth C-plugin (since FFMS2 normally has the decoders/demuxers/parsers statically linked in when used on Windows, and I knew that in addition to that, that the plugin can be built as 64-bit for the 64-bit fork(s) of AviSynth), the -Bsymbolic fix was actually noted in that bug report from FFmpeg as the way to resolve it, toward the end.

---

### Post by qyot27 on 2012-10-23
Since it's notable to the thread, [VapourSynth](http://www.vapoursynth.com/) has been getting attention lately.  Obviously the advanced usage is beyond the scope of the thread and the INSTALL file that comes with the source tells you pretty much everything you need to do to build it, but having a post describing the methodology on Ubuntu specifically might be in order.  I actually had this worked out a while ago, but wanted to wait for Quantal to be released so I could verify that the steps still worked.

VapourSynth scripts are written in Python, since VS itself is implemented as a Python module.  So they're going to look different than AviSynth scripts.

First, follow the guide on getting FFmpeg compiled here:
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
(in the checkinstall step, use 7: in the pkgversion instead of 5: - otherwise, the system will try to replace it whenever libav-tools has an update)

You can probably use libav, but since I don't I'm not going to comment on it.

Installing the dependencies and building an up-to-date version of Cython:
```
sudo apt-get install libqtcore4 python3 python3-dev wget subversion
wget "http://pypi.python.org/packages/source/C/Cython/Cython-0.17.1.tar.gz#md5=f0bd2494dbe080a1185b61fa358135f2" -O - | tar -xzvf -
cd Cython-0.17.1
sudo python3 setup.py install
```

Building and installing VapourSynth itself:
```
svn checkout http://vapoursynth.googlecode.com/svn/trunk vapoursynth
cd vapoursynth
./bootstrap.py
./waf configure
./waf build
sudo ./waf install
sudo ./setup.py install
sudo ldconfig
```

Building and installing FFMS2:
```
svn checkout http://ffmpegsource.googlecode.com/svn/trunk ffms2
cd ffms2
./autogen.sh
./configure --enable-shared
make
sudo checkinstall --pkgname=ffms2 --pkgversion="1:$(./version.sh)-svn" --backup=no --deldoc=yes --fstrans=no --default
sudo ldconfig
```
The ./autogen.sh step is only necessary until the next time the build system for FFMS2 is regenerated officially.  If you don't perform the autogen step, the VapourSynth interface won't get built.



Now, for the script.  You could just look at the documentation, since it's explained there, but for the sake of making a complete post:
```
#!/usr/bin/python3
import vapoursynth as vs
import sys
core = vs.Core()
core.std.LoadPlugin("/usr/local/lib/libffms2.so")
ret = core.ffms2.Source("inputvideo.avi")
ret.output(sys.stdout, y4m=True)
```
As you can see, it's Python.  The #!/usr/bin/python3 line forces the script to be interpreted by the correct version of Python (since 12.10 still ships with Python 2.7.3, you're going to have two different versions of Python installed, and this ensures you're using 3.2).

The syntax is explained at greater length in the official documentation.


To use it with something, first make the script (we'll call it vstestscript.vpy) executable:
```
chmod +x vstestscript.vpy
```

Now feed it to mplayer:
```
./vstestscript.vpy | mplayer -
```
Or this *would* work, if mplayer accepted ffmpeg's extended Y4M format that VS uses.  To get around this, pipe it through ffmpeg first (part of the reason I advise to use bona-fide ffmpeg, and not libav):
```
./vstestscript.vpy | ffmpeg -i - -f yuv4mpegpipe - | mplayer -
```
In x264's case, support for the extended Y4M format is in the x264-devel branch, so hopefully there'll be an update soon that pushes it into the main branch.  For those wondering, the reason for the extended format is because VS supports high bit depths, and so does the extended Y4M format.  I have my doubts about the 'running it through ffmpeg first' thing actually preserving these higher bit depths (and possibly colorspaces), so hopefully we can get direct support of the extended Y4M or .vpy scripts into all of this stuff soon.

Seeing as the scripts are just normal Python, you could do more exotic things with them.  Not that I know how to accomplish that, but the option is there.

---

### Post by FakeOutdoorsman on 2012-10-23
> **qyot27 said:**
> 
First, follow the guide on getting FFmpeg compiled here:
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
(in the checkinstall step, use 7: in the pkgversion instead of 5: - otherwise, the system will try to replace it whenever libav-tools has an update)

Thanks, I forgot about that one. The guide has been updated.

---

### Post by qyot27 on 2013-03-27
Because this is relevant, both x264 and FFmpeg (and by extension, anything that uses libavformat, like mpv) now support opening AviSynth scripts on Linux and OSX directly by using AvxSynth.  x264 enables it automatically, FFmpeg requires the --enable-avisynth option.

---

