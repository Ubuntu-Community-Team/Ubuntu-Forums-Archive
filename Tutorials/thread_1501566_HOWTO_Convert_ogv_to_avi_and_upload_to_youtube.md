---
title: "HOWTO: Convert ogv to avi and upload to youtube"
date: 2010-06-04
forum: Tutorials
---

### Post by irv on 2010-06-04
After having trouble uploading ogv files to youtube and getting help on the forum I thought I would put a quick video howto together showing how to convert the file and upload it to youtube. First, the command I used to convert the ogv file to a avi was this:

```
mencoder foo.ogv -o foo.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

OK, here is the link to the video on the howto: 

[http://www.youtube.com/watch?v=VuhYV0voL3M]("http://www.youtube.com/watch?v=VuhYV0voL3M")

---

### Post by stmiller on 2010-06-10
An easier way is to just use Handbrake. 

[http://handbrake.fr/](http://handbrake.fr/)

Encode your .ogv source file as .mkv normal profile. Upload that to youtube, done. :)

---

### Post by irv on 2010-06-10
> **stmiller said:**
> An easier way is to just use Handbrake. 

[http://handbrake.fr/](http://handbrake.fr/)

Encode your .ogv source file as .mkv normal profile. Upload that to youtube, done. :)

What could be easier then a CLI, enter the command and you are done. Just to check it out, I set "ppa:stebbins/handbrake-snapshots" in the repositories and installed handbreak and gave it a spin. I converted a ogv file and when I went to play it, it was missing a lot of the graphics. You could see background and mouse movement but no desktop or wallpaper. Very bad converted file. So I un-installed it and removed from repository. Back to my easy way.

---

### Post by ron999 on 2010-06-10
OK irv, I'm glad you got it sorted.
I've tested your command with Ubuntu 9.10 Karmic and the YouTube upload is fine.:p

Just a suggestion, in your HOW-TO, why not use generic names for the ogv and avi files.
eg **foo.ogv** and **foo.avi**

---

### Post by irv on 2010-06-10
> **ron999 said:**
> OK irv, I'm glad you got it sorted.
I've tested your command with Ubuntu 9.10 Karmic and the YouTube upload is fine.:p

Just a suggestion, in your HOW-TO, why not use generic names for the ogv and avi files.
eg **foo.ogv** and **foo.avi**

I will take you suggestion next time. Thanks.

---

### Post by MichaelCooper on 2010-06-20
I'm really frustrated here. Instead of posting information as if you already know it, could you explain how to do this step by step. I watched your info video and it explained nothing. A lot of people search these forums for clear concise info and have no idea where to begin.

I posted your "code" in the terminal and nothing happened accept:

MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
File not found: 'foo.ogv'
Failed to open foo.ogv.
Cannot open file/device.

I then replaced "foo.ogv" with the file name of my short video clip and got this:

MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
File not found: 'beastclips.ogv'
Failed to open beastclips.ogv.
Cannot open file/device.

Exiting...

I'm sure you can now tell that there are visitors to Ububntu forums that have no idea what they are doing - Like me - Help please

---

### Post by HotshotGG on 2010-06-21
> **irv said:**
> After having trouble uploading ogv files to youtube and getting help on the forum I thought I would put a quick video howto together showing how to convert the file and upload it to youtube. First, the command I used to convert the ogv file to a avi was this:

```
mencoder foo.ogv -o foo.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```OK, here is the link to the video on the howto: 

[http://www.youtube.com/watch?v=VuhYV0voL3M](http://www.youtube.com/watch?v=VuhYV0voL3M)

Extremely poor how-to for two reasons. You have it backwards. AVI is a busted old media container that used in Flash. The web is moving away from flash video players in favor of HTML 5 audio and video tags. Theora in the future as well as WebM will be natively supported in YouTube with HTML 5 . I don't want you to take this the wrong way, but it seems like you are completely misinformed! If anything it would be wiser for the time being to show people how to use H.264 in an MP4 container, which is even more acceptable rather then a crappy old container that's older then I am. I am not trying to start a flame war, but I don't understand why people have a difficult time understanding this.

---

### Post by irv on 2010-06-21
> **HotshotGG said:**
> Extremely poor how-to for two reasons. You have it backwards. AVI is a busted old media container that used in Flash. The web is moving away from flash video players in favor of HTML 5 audio and video tags. Theora in the future as well as WebM will be natively supported in YouTube with HTML 5 . I don't want you to take this the wrong way, but it seems like you are completely misinformed! If anything it would be wiser for the time being to show people how to use H.264 in an MP4 container, which is even more acceptable rather then a crappy old container that's older then I am. I am not trying to start a flame war, but I don't understand why people have a difficult time understanding this.

I am not a video guy, all I was interest in doing was to get a video uploaded to youtube that worked. After reading your reply I understand what you are saying. OK, let me ask if you can do a howto on converting ogv to MP4 using H.264. And I will see if this howto could be removed.
And don't worry about starting a flame war, I am not taking offense on this subject.

Edit: I am adding this edit because I found this howto dealing with the newer technology.
[http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/]("http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/")

---

### Post by HotshotGG on 2010-06-22
> **irv said:**
> I am not a video guy, all I was interest in doing was to get a video uploaded to youtube that worked. After reading your reply I understand what you are saying. OK, let me ask if you can do a howto on converting ogv to MP4 using H.264. And I will see if this howto could be removed.
And don't worry about starting a flame war, I am not taking offense on this subject.

If you want to it would be wiser to simply start a new one showing people how to encode to Theora or WebM, which are more widely supported within Linux and will be supported in HTML 5 in the future. I am am not knocking your tutorial I am simply making a suggestion. If you want any assistance with that I can help you out.  Ogg Theora is already supported within Firefox, Opera, and Chrome btw built-in. There is no need to convert to flash for any particular reason whatsoever. I don't blame you just the the people on YouTube who make everything complicated. Google is well aware of the problem.

---

### Post by irv on 2010-06-22
The best document on "videos on the web" I ran into can be found at:
[http://diveintohtml5.org/video.html]("http://diveintohtml5.org/video.html")

I have also used a program call devede to convert files from ogv to avi.
In the above mention document, it states:
> You may think of video files as “AVI files” or “MP4 files.” In reality, “AVI” and “MP4&#8243; are just container formats. Just like a ZIP file can contain any sort of file within it, video container formats only define how  to store things within them, not what kinds of data are stored. (It’s a little more complicated than that, because not all video streams are compatible with all container formats, but never mind that for now.)
I found this very interesting because I never looked at AVI or MP4 files in this way. It was very helpful in understanding these formats.

Also I have been doing some searches on Theora and WebM's. I have been trying to educate myself on video over the web. With HTML5 I really am seeing things are changing.

---

### Post by irv on 2010-06-22
Seeing WebM was mention I thought I would add this from the above mention document:
> WebM is a new container format. It is technically very similar to another format, called Matroska. WebM was announced at Google I/O 2010. It is designed to be used exclusively with the VP8 video codec and Vorbis audio codec. (More on these in a minute.) It will be supported natively, without platform-specific plugins, in the next versions of Chromium, Google Chrome, Mozilla Firefox, and Opera. Adobe has also announced that the next version of Flash will support WebM video.

---

### Post by HotshotGG on 2010-06-23
> **irv said:**
> Seeing WebM was mention I thought I would add this from the above mention document:

WebM is VP8 / Vorbis wrapped into a new container called "WebM" for streaming transport. That web page you found is extremely accurate except they aren't building Vorbis correctly in WebM. There is a developers bug that will need to addressed in the next version of ffmpeg, which uses suboptimal build of Vorbis tor encoding audio. The developer who write the blog entry for compiling WebM is not savy enough to understand that there is a bug there that needs to be corrected. Everyone seems to be compiling based upon his instructions, which need to modified slightly to fix this issues especially for early versions of the encoder. I am encoding with Theora personally right now, which still requires a lot of work before it get's up to snuff with H.264, but in particular does a very good job! I have the "Thusnelda" build on my Ubuntu box here. I have yet to cross-compile WebM though. Embedding them within HTML 5 is a piece of cake and will be in the future. No more need for Flash.:guitar:

---

### Post by irv on 2010-06-23
I followed a link from the document to this howto, but I had some issues with setting it up. Here is the link I am talking about.

[http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/comment-page-1/#comment-14681]("http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/comment-page-1/#comment-14681")

These were the issues I had:
> I ran into two problems
A).libvpx: the third part
Line 1. sudo cp vp8/*.h /usr/include/ (cp: cannot stat `vp8/*.h’: No such file or directory)
Line 2. sudo cp vpx_codec/*.h /usr/include/ (cp: cannot stat `vpx_codec/*.h’: No such file or directory)
B). ffmpeg: line 21 the make will not work:
This is the error I get,
Makefile:342: /tests/fate.mak: No such file or directory
make: *** No rule to make target `/tests/fate.mak’. Stop.

I am glad to see you are devoted your time encoding with Theora personally right now, and when you get the bugs out of it I would like to be made aware of it. I plan on stopping what I am doing because it is going nowhere and I am in over my head. 

On last thing, I have HandBrake installed on my Ubuntu laptop and have converted some ogv's into m4v. I did find this document I found very well written and very informational.  I am talking about the one at [http://diveintohtml5.org/video.html.]("http://diveintohtml5.org/video.html.")

---

### Post by HotshotGG on 2010-06-23
> **irv said:**
> I followed a link from the document to this howto, but I had some issues with setting it up. Here is the link I am talking about.

[http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/comment-page-1/#comment-14681](http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/comment-page-1/#comment-14681)

These were the issues I had:


I am glad to see you are devoted your time encoding with Theora personally right now, and when you get the bugs out of it I would like to be made aware of it. I plan on stopping what I am doing because it is going nowhere and I am in over my head. 

On last thing, I have HandBrake installed on my Ubuntu laptop and have converted some ogv's into m4v. I did find this document I found very well written and very informational.  I am talking about the one at [http://diveintohtml5.org/video.html.](http://diveintohtml5.org/video.html.)

Lardbucket is the blog I was referring to above for building WebM. His instructions are OK... You need to drop the -acodec vorbis line from the compile and use libvorbis instead he doesn't mention that in the blog post. That will be corrected in the next version of FFMPEG. Theora is much easier to encode with right now. 

> I ran into two problems
A).libvpx: the third part
Line 1. sudo cp vp8/*.h /usr/include/ (cp: cannot stat `vp8/*.h&#8217;: No  such file or directory)
Line 2. sudo cp vpx_codec/*.h /usr/include/ (cp: cannot stat  `vpx_codec/*.h&#8217;: No such file or directory)
B). ffmpeg: line 21 the make will not work:
This is the error I get,
Makefile:342: /tests/fate.mak: No such file or directory
make: *** No rule to make target `/tests/fate.mak&#8217;. Stop.                       
libvpx is VP8 codec for FFMPEG. It needs to be patched against FFMPEG as it's not included in original source. The code above is trying to copy VP8 source code into proper directories. Those are C header files that's what the codec is written in. Line 21 is make file for cross-compiling a piece of code called "Fate" in the source. I have the FFMPEG source-code on my machine I will take a look again. 

> On last thing, I have HandBrake installed on my Ubuntu laptop and have  converted some ogv's into m4v. I did find this document I found very  well written and very informational.  I am talking about the one at [http://diveintohtml5.org/video.html.](http://diveintohtml5.org/video.html.) Yeah that article is well constructed by a Linux user. Very informative. Handbrake can encode to Theora and H.264. Outside of H.264 though it's Theora functionality is very limited!. H.264 can very COMPLICATED to encode with. That's why a lot of people are pushing for VP8 or Theora as settings are more streamlined. In H.264 you need to worry about complicated switches like BSAC, loop quantization, etc. and PATENTS Fancy stuff that the average user could care less about and unless you are developer wouldn't understand.  Unless you are doing an AC3 passthrough the AAC encoder in Handbrake is inferior in Linux to some other ones that exist out there with H.264 (With the exception of Mac OS/X build). It's OK for now to transcode to H.264 if you need to. I would encode two versions of my video one encoded with Theora for HTML 5 and the other H.264 for YouTube and then one for WebM once they fix that bug!

---

### Post by FakeOutdoorsman on 2010-06-23
> **HotshotGG said:**
> AVI is a busted old media container that used in Flash.
I've never seen AVI being used with a Flash player.

> **HotshotGG said:**
> H.264 can very COMPLICATED to encode with.
I disagree. Example:
```
ffmpeg -i input.foo -vcodec libx264 -vpre fast -crf 22 -threads 0 output.mp4
```
See the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more details.

The Lardbucket instructions are outdated.  You don't need to copy any headers or use those patches anymore.  The following is more up to date and includes *libvpx* instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

FFmpeg from the repository may have trouble converting OGV from recordMyDesktop, but a recent self-compiled FFmpeg handles these files with no issues.  FFmpeg 0.6, which Ubuntu will eventually use, will handle them fine too.

---

### Post by irv on 2010-06-23
First I want to say HotShotGG, I have been enjoying your posts in this thread.

I ran across an article in “The Register” entitled “Jobs drops hint on Google open video codec.” Right at the beginning of the article it stated that Steve Jobs has indicated that Apple is unlikely to embrace Google's newly-open sources VP8 video codes. The reason is because of the fact that it “appears to be significantly weaker” in terms of compression and slower to decode than H.264, the patented codec that Apple uses for HTML5 video in its Safari browser.

In the “Diary Of An x264 Developer” it stated that:

> “Overall, VP8 appears to be significantly weaker than H.264 compression-wise.” 

He goes on to give all the reasons why he finds it weaker, and then later on in this same writing it said that: 

> it seems that Google is not open to changing the spec: it is apparently “final”, complete with all its flaws.

If this is the case then I can understand why Steve Job is unlikely to embrace it.

But the bottom line in the summary was this:

> VP8, as a spec, should be a bit better than H.264 Baseline Profile and VC-1.* It’s not even close to competitive with H.264 Main or High Profile.* If Google is willing to revise the spec, this can probably be improved.
VP8, as an encoder, is somewhere between Xvid and Microsoft’s VC-1 in terms of visual quality.* This can definitely be improved a lot.
VP8, as a decoder, decodes even slower than ffmpeg’s H.264.* This probably can’t be improved that much; VP8 as a whole is similar in complexity to H.264.
With regard to patents, VP8 copies too much from H.264 for comfort, no matter whose word is behind the claim of being patent-free.* This doesn’t mean that it’s sure to be covered by patents, but until Google can give us evidence as to why it isn’t, I would be cautious.
VP8 is definitely better compression-wise than Theora and Dirac, so if its claim to being patent-free does stand up, it’s a big upgrade with regard to patent-free video formats.
VP8 is not ready for prime-time; the spec is a pile of copy-pasted C code and the encoder’s interface is lacking in features and buggy.* They aren’t even ready to finalize the bitstream format, let alone switch the world over to VP8.
With the lack of a real spec, the VP8 software basically is the spec–and with the spec being “final”, any bugs are now set in stone.* Such bugs have already been found and Google has rejected fixes.
Google made the right decision to pick Matroska and Vorbis for its HTML5 video proposal.

---

### Post by irv on 2010-06-23
Thanks FakeOutdoorsman, I was looking for your howto: [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095") I did a clean sweep and re-installed everything from your howto. I had done it before so it was a breeze. Thanks for the post.

---

### Post by HotshotGG on 2010-06-23
> FFmpeg from the repository may have trouble converting OGV from  recordMyDesktop, but a recent self-compiled FFmpeg handles these files  with no issues.  FFmpeg 0.6, which Ubuntu will eventually use, will  handle them fine too.     I understand, but keep in mind the FFMPEG encoder has no Psychoacoustics model. It's subpar when compared to the Vorbis 1.4.0 libraries and the AoTuV community builds which many audio guys including myself strongly believe in. 



> **irv said:**
> First I want to say HotShotGG, I have been enjoying your posts in this thread.

I ran across an article in &#8220;The Register&#8221; entitled &#8220;Jobs drops hint on Google open video codec.&#8221; Right at the beginning of the article it stated that Steve Jobs has indicated that Apple is unlikely to embrace Google's newly-open sources VP8 video codes. The reason is because of the fact that it &#8220;appears to be significantly weaker&#8221; in terms of compression and slower to decode than H.264, the patented codec that Apple uses for HTML5 video in its Safari browser.

In the &#8220;Diary Of An x264 Developer&#8221; it stated that:



He goes on to give all the reasons why he finds it weaker, and then later on in this same writing it said that: 



If this is the case then I can understand why Steve Job is unlikely to embrace it.

But the bottom line in the summary was this:

The forums rules state not to get into a political discussion, but I feel for the sake of convincing you it's important.  No offense, but Jobs is an "*******" who only wants everyone to play by his rules and is just spreading F.U.D and making up excuses. The reason they want people to use H.264 is, because he knows WebM is in direction competition with it. Wait until they start charging royalties for people who stream content On Demand from their independent audio and video sites. Last time I checked too the Internet especially W3C was built on "open standards". The same standards people like Mozilla believe in. The diary of an H.264 developer is by an developer who has probably has never had the audacity to work on anything else besides H.264 no offense. Lastly WebM is BSD licensed. I know people have a difficult time differentiating between "free" and "open source", but the code is their so that it can be improved upon and lastly if were covered by patents the open source community would be the first people to know about it and would make the changes necessary so that it was not. Our friends over Xiph have been through this hell with Vorbis before so they understand what that is like. Bottom line is it's F.U.D from both parties in that regard. Everyone has the time to "rip" open source projects, but the same people who have the power to change that never do anything about it's ridiculous.

---

### Post by ron999 on 2010-08-08
@ irv
I can confirm FakeOutdoorsman's comment in post # 15:-
> FFmpeg from the repository may have trouble converting OGV from recordMyDesktop, but a recent self-compiled FFmpeg handles these files with no issues.:)

I have now converted the your ogv file using ffmpeg compiled from the instructions here:-
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")
> FFmpeg version SVN-r24643, Copyright (c) 2000-2010 the FFmpeg developers built on Aug  1 2010 10:38:14 with gcc 4.4.1

When uploaded to YouTube the result seems to be OK.

This is the command that I used:-
```
ffmpeg -i foo.ogv -vcodec libx264 -vprefast -crf 22 -threads 0 -acodec libfaac -ab 96k -ac 1 foo.mp4
```

Using x264 greatly reduces the file size too. The original ogv is 26.3MB. The new mp4 is only 8.4MB. :cool:


**[COLOR="Red"]EDIT[/COLOR]**
I've been back to check the uploaded video.
There's something wrong with it.
It looks like the audio is delayed by a few seconds.
That file plays OK on my hard drive so it's YouTube who have screwed up.
Maybe stay with using mencoder for now.

---

### Post by FakeOutdoorsman on 2010-08-09
The video quality looks good.  I haven't uploaded to YouTube recently, so I'm not sure how picky it is.  I can think of some things that you can try next time:

Copy the audio instead of re-encoding it and put it into a MKV file:
```
ffmpeg -i input.ogv -vcodec libx264 -vpre fast -crf 22 -threads 0 -acodec copy foo.mkv
```

Output the audio as VBR (and don't force to mono with *-ac 1*). *-aq 100* should be similar to *faac -q 100*, which is faac's default according to *faac --long-help*:
```
ffmpeg -i input.ogv -vcodec libx264 -vpre fast -crf 22 -threads 0 -acodec libfaac -aq 100 foo.mp4
```

Or use a different audio encoder (and a different output container):
```
ffmpeg -i input.ogv -vcodec libx264 -vpre fast -crf 22 -threads 0 -acodec libmp3lame -aq 4 foo.mkv
```

Maybe YouTube likes the *Main Profile*?  I can't imagine this being much help, but I had to use it for one video or YouTube halved the frame rate:
```
ffmpeg -i foo.ogv -vcodec libx264 -vpre fast -vpre main -crf 22 -threads 0 -acodec libfaac -ab 96k foo.mp4
```

Who knows why it's delayed.  I'm just guessing things to try here.  The best way for me is to just test until I find something that actually works with the 'tube.  (There are also the *-async* and *-vsync* options, but they are so poorly documented that I tend to ignore those.)

Lancanshire?  I expected a British accent.

---

### Post by verb3k on 2010-08-09
> **HotshotGG said:**
> The diary of an H.264 developer is by an developer who has probably has never had the audacity to work on anything else besides H.264 no offense. 

That's arguably true, his work mostly deals with H.264, but he also helped write FFmpeg's native VP8 decoder, after which his views started to change slightly (at least that's my impression :wink:)

---

### Post by ron999 on 2010-08-09
I converted it again keeping the original vorbis soundtrack and the result is good.

> FFmpeg version SVN-r24754, Copyright (c) 2000-2010 the FFmpeg developers built on Aug 10 2010 16:01:47 with gcc 4.4.1

Command used:-
```
ffmpeg -i foo.ogv -vcodec libx264 -vpre default -acodec copy foo.mkv
```

Size of ogv file = 27.9MB
Size of mkv file = 7.6MB
:guitar:

Here it is:-[http://www.youtube.com/watch?v=dO2FtzLt0Nk]("http://www.youtube.com/watch?v=dO2FtzLt0Nk")

---

### Post by lelandnielsen on 2011-01-31
Hey FakeOutdoorsMan,
I followed your instructions for [**Install FFmpeg and x264 on Ubuntu Lucid Lynx 10.04**]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289") and received the following errors, highlighted in orange:

[ogg @ 0x1689510] Page at 200 is missing granule
[vorbis @ 0x168e0c0] Extradata missing.

Here's what I get in Terminal:

```

jarednielsen@typewriter:~/Documents/dvdrip-data/obsession/avi/002$ ffmpeg -i 2.pg4obsession.ogv -vcodec libx264 -vpre fast -crf 22 -threads 0 output.mp4
FFmpeg version SVN-r26402, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan 30 2011 17:01:56 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.74. 0 /  1.74. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[ogg @ 0x1689510] Page at 200 is missing granule
[vorbis @ 0x168e0c0] Extradata missing.
    Last message repeated 345 times
[ogg @ 0x1689510] max_analyze_duration reached
Input #0, ogg, from '2.pg4obsession.ogv':
  Duration: 00:06:25.01, start: 0.000000, bitrate: 3218 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x464, 29.97 fps, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: vorbis, 48000 Hz, 2 channels, 499 kb/s
File 'output.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0x168d160] w:624 h:464 pixfmt:yuv420p
[libx264 @ 0x168b9c0] using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x168b9c0] profile High, level 3.0
[libx264 @ 0x168b9c0] 264 - core 113 r1884 7313bb5 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=22.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
[vorbis @ 0x168e0c0] Extradata missing.
Output #0, mp4, to 'output.mp4':
    Stream #0.0: Video: libx264, yuv420p, 624x464, q=10-51, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening decoder for input stream #0.1


```

I'm new to this and at a loss.  What next?  
Many thanks in advance.

---

### Post by irv on 2011-01-31
> **lelandnielsen said:**
> Hey FakeOutdoorsMan,
I followed your instructions for [**Install FFmpeg and x264 on Ubuntu Lucid Lynx 10.04**]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289") and received the following errors, highlighted in orange:

[ogg @ 0x1689510] Page at 200 is missing granule
[vorbis @ 0x168e0c0] Extradata missing.

Here's what I get in Terminal:

```

jarednielsen@typewriter:~/Documents/dvdrip-data/obsession/avi/002$ ffmpeg -i 2.pg4obsession.ogv -vcodec libx264 -vpre fast -crf 22 -threads 0 output.mp4
FFmpeg version SVN-r26402, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan 30 2011 17:01:56 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.74. 0 /  1.74. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[ogg @ 0x1689510] Page at 200 is missing granule
[vorbis @ 0x168e0c0] Extradata missing.
    Last message repeated 345 times
[ogg @ 0x1689510] max_analyze_duration reached
Input #0, ogg, from '2.pg4obsession.ogv':
  Duration: 00:06:25.01, start: 0.000000, bitrate: 3218 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x464, 29.97 fps, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: vorbis, 48000 Hz, 2 channels, 499 kb/s
File 'output.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0x168d160] w:624 h:464 pixfmt:yuv420p
[libx264 @ 0x168b9c0] using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x168b9c0] profile High, level 3.0
[libx264 @ 0x168b9c0] 264 - core 113 r1884 7313bb5 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=22.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
[vorbis @ 0x168e0c0] Extradata missing.
Output #0, mp4, to 'output.mp4':
    Stream #0.0: Video: libx264, yuv420p, 624x464, q=10-51, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening decoder for input stream #0.1


```

I'm new to this and at a loss.  What next?  
Many thanks in advance.

This is a very old post. Maybe you should start a new thread for this problem.

---

### Post by FakeOutdoorsman on 2011-01-31
> **lelandnielsen said:**
> ...
I'm new to this and at a loss.  What next?  
Many thanks in advance.

It appears that you have encountered a bug (a regression to be more specific) in FFmpeg:
[Issue 2428: vorbis in ogg can't be decoded](https://roundup.ffmpeg.org/issue2428)

You have several options:
1. Use another tool to decode the audio and then encode with FFmpeg:
```
oggdec 2.pg4obsession.ogv
ffmpeg -i 2.pg4obsession.ogv -i 2.pg4obsession.wav -map 0:0 -map 1:0 -vcodec libx264 \
    -vpre fast -crf 22 -threads 0 -acodec libfaac -aq 100 output.mp4
```

2. Use an older FFmpeg. You can remove the version you compiled and try FFmpeg from the repository. Or you could compile an older revision (r25845 or earlier).

3. Wait for a fix and then update your FFmpeg. This would be an indefinite wait.

---

### Post by weedeater64 on 2011-01-31
Wanted to try this, but hit a snag..
Linux version 2.6.26-2-686 (Debian 2.6.26-26lenny1)


```

jeff@optiplex:~/Desktop$ !11612
mencoder executable.ogv -o executable.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
bash: mencoder: command not found
jeff@optiplex:~/Desktop$ dpkg --get-selections |grep mplayer
mozilla-mplayer                                 install
mplayer                                         install
mplayer-doc                                     install
mplayer-skin-blue                               install
smplayer                                        install
smplayer-themes                                 install
smplayer-translations                           install
jeff@optiplex:~/Desktop$ apropos mencoder
mencoder (1) [mplayer] - movie player
jeff@optiplex:~/Desktop$ mencoder
bash: mencoder: command not found


```

What gives???

---

### Post by irv on 2011-01-31
If you are interested I made a little video awhile ago on howto convert ogv to avi and upload to youtube. here is the link:
[http://www.youtube.com/watch?v=VuhYV0voL3M]("http://www.youtube.com/watch?v=VuhYV0voL3M")
I also have the code in the remarks section on the youtube page.

---

### Post by weedeater64 on 2011-01-31
> **irv said:**
> If you are interested I made a little video awhile ago on howto convert ogv to avi and upload to youtube. here is the link:
[http://www.youtube.com/watch?v=VuhYV0voL3M](http://www.youtube.com/watch?v=VuhYV0voL3M)
I also have the code in the remarks section on the youtube page.


Yeah, I watched your video, and I have mplayer, which means I should have mencoder..

I briefly looked at the man page for mplayer, and it says right away that mencoder is mplayers encoder, yet I get 

:~$ mencoder
bash: mencoder: command not found
 

I probably need to go ask in the Debian forums about this..

---

### Post by weedeater64 on 2011-01-31
Turns out it's a debian-multimedia thing. On the recommends of the guys at #debian I'll pass.

I haven't had any problem uploading .ogv to youtube,
[http://www.youtube.com/watch?v=MuSpCC7cidU](http://www.youtube.com/watch?v=MuSpCC7cidU)
 and I've converted to .ogg with kino.
[http://www.youtube.com/watch?v=6D5JYP2dLB0](http://www.youtube.com/watch?v=6D5JYP2dLB0)

I was just curious, and thought I'd try something new. But I don't want to break my system.

---

### Post by irv on 2011-01-31
> **weedeater64 said:**
> Turns out it's a debian-multimedia thing. On the recommends of the guys at #debian I'll pass.

I haven't had any problem uploading .ogv to youtube,
[http://www.youtube.com/watch?v=MuSpCC7cidU](http://www.youtube.com/watch?v=MuSpCC7cidU)
 and I've converted to .ogg with kino.
[http://www.youtube.com/watch?v=6D5JYP2dLB0](http://www.youtube.com/watch?v=6D5JYP2dLB0)

I was just curious, and thought I'd try something new. But I don't want to break my system.
I just tried to upload a ogv file to youtube and here is what I get.
[http://www.youtube.com/watch?v=Rqb2D4h6PeQ]("http://www.youtube.com/watch?v=Rqb2D4h6PeQ")
This is the same problem I always have uploading ogv file. That is why I convert them to avi files.

Edit: the video I have in my signature is an ogv file I have on my own server because youtube has problems with ogv files.

---

### Post by tg3793 on 2011-09-20
> **HotshotGG said:**
> Extremely poor how-to for two reasons. You have it backwards. AVI is a busted old media container that used in Flash. The web is moving away from flash video players in favor of HTML 5 audio and video tags.

Wow, who pee'd in your Cheerios.

Let me try to add a little truthful positive on this by expressing how grateful I am for IRV putting this CLI string where I could find it. 

It was particular useful for me because I have a video that I needed to send to a fledgling television studio that can't import OGV or FLV files. Would you believe that Adobe Premier can't import OGV or FLV files? [sheesh] and [ha ha].

---

### Post by irv on 2011-09-22
> **tg3793 said:**
> 

Let me try to add a little truthful positive on this by expressing how grateful I am for IRV putting this CLI string where I could find it. 

It was particular useful for me because I have a video that I needed to send to a fledgling television studio that can't import OGV or FLV files. Would you believe that Adobe Premier can't import OGV or FLV files? [sheesh] and [ha ha].
Glad this was of use to you. When it come to video formats I wish everyone would go in the same direction. There are too many driving the wrong way on a one way street and they keep crashing into one another. [COLOR="Red"]Standardisation[/COLOR]  that's the answer.

---

### Post by perspectoff on 2011-09-22
> **stmiller said:**
> An easier way is to just use Handbrake. 

[http://handbrake.fr/](http://handbrake.fr/)

Encode your .ogv source file as .mkv normal profile. Upload that to youtube, done. :)


While I absolutely love Handbrake, it doesn't do .AVI or .FLV (anymore). Not everyone can play Mastroska (my older DVD players don't, for example). While I agree that .AVI is a bit outdated and a bit of a pain to use, it is still fairly universal. Note everyone can be (or wants to be) the very cutting edge. MKV (Mastroska) over OGV any day, of course.

I don't think Handbrake does XVID/DivX anymore, either. (X264/H.264 is way better than XVID/DivX, I agree, but, again, some older DVD players don't yet accommodate H.264/X264).

I don't use FLV anymore at all. Adobe has become too aggressive with updates and options and it makes one's head spin. The problem with backwards/forwards compatibility with their own formats made me drop them like a hot potato. When Silverlight was being rolled out by Microsoft, I stuck with Flash, but no longer.

Now there's no excuse to stay with Flash, with the benefits (in quality and size) of H.264/X264 for pure video content.

To be honest, the OP's mencoder method works pretty well and yields some relatively universally viewable videos. Mencoder uses FFMPEG libraries, so FFMPEG could be used as well (as long as one avoids older versions of FFMPEg. FFMPEG had some growing pains the past few years. Oh wait, they changed all their commands recently, too. As soon as a person gets used to FFMPEG they change it.).

YouTube/Google converts a huge a number of formats automatically, though, so largely it doesn't matter what you upload to them (these days).

---

