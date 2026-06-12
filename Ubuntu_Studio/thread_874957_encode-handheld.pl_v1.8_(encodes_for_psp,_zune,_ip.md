---
title: "encode-handheld.pl v1.8 (encodes for psp, zune, ipod) using ffmpeg."
date: 2008-07-30
forum: Ubuntu Studio
---

### Post by HolyRoses on 2008-07-30
My newest released version of encode-handheld.pl ( v5.3 )

Includes binaries for ffmpeg and AtomicParsley for MacOS and Linux.

(copy bins to /usr/local/bin)

[Download via RS old Version 4.8.  Some extra Tools included.]("http://rapidshare.com/files/254028257/encode-handheld-4.8.tar.gz")

[Download via RS Version 5.2. Includes new ffmpeg, super new AtomicParsley and script.]("http://rapidshare.com/files/320550146/encode-handheld-5.2-with-ffmpeg-and-atomicparsley.tar.gz")

updated script only for 5.3.  fixes bugs and adds features.  next rev will probably feature better dvd support for audio channel remapping and extracting/encoding for apple tv, like it does support MKV currently.

[Download script version 5.3.]("http://rapidshare.com/files/359099898/encode-handheld-5.3.pl")

-HR

----------------------------------------------------------------------
```

./encode-handheld-5.0.pl -h

    PSP & iPod h264 video and AAC audio encoder.
    PSP Motion JPG encoder.  (22min = 916mb vs 84mb using h264)
    PSP 720x480 16:9 & 4:3 encoder.
    PSP 640x480 encoder.
    PSP 640x480 wide encoder.
    iPod 720x576 16:9 "PAL DVD" encoder
    iPod 720x480 16:9 "NTSC DVD" encoder
    iPod 640x480 16:9 "near DVD" encoder
    iPod 480x320 16:9 "half DVD" encoder
    iPod 320x240 19:9 wide encoder
    AppleTV encoder (use -b for better results)
    Zune 30GB Windows Media 8 A/V encoder.
    Cell phone 176x144 encoder.

    usage: ./encode-handheld-5.0.pl [-hl] [-t psp|psp640|psp640wide|psp720|pspavi|ipod|ipodwide|ipod480|ipod640|ipoddvd|ipodntscdvd|ipodpaldvd|appletv|zune|zune30|3g2] [-s XXXXX] [-n title] [-f file]

     -h        : this (help) message
     -v        : displays version
     -a        : hard box the video
                 (pillarbox and letterbox the video, AR set to AR of screen size)
     -A        : Auto 16:9 the video.  Your video will be cropped horizontally or vertically until
                 it is at a 16:9 AR.  Works with regular cropping commands as well.  You can crop
                 a DVD matte off and still use -A to force 16:9.
     -g        : letterbox video to next macro block height (ex 480x202 -> 480x208)
     -r        : frame rate (24000/1001 or 30000/1001 are suggested override values) (default 24000/1001)
     -l        : legacy psp file naming
     -s XXXXX  : 5 digit legacy numbering sequence
     -f file   : file to encode
     -n title  : psp title displayed when using legacy naming
                 or file is renamed to this value (if AtomicParsley then also atom)
     -t type   : psp, ipod, zune, zune30, psp640, 3g2 encoding
     -o num    : volume(gain) 1x=256, 2x=512, 3x=768, 4x=1024 (default: No Change)
                 when encoding audio from MKV this controls gain in decibels
                 I don't advise going over +20, as that is extremly loud.  +10 is fine.
     -c num    : thumbnail capture time in seconds (default: 120)
     -z num    : encode time in seconds (default: whole thing)
     -j num    : start encode time in seconds (default: beginning)
     -b        : encode using b frames (psp only) (default: no)
     -p        : 2 pass encoding
     -i        : iPhone & iPod touch PSP compatible profile (switches coder to 0)
     -m num    : ffmpeg threads (example, dual core: -m2, quad core: -m4, default 2)
     -M        : Extract audio from Matroska video files (requires signifcant disk space)
                 only use this for MP4 files destination files.
     -x        : when using type psp640 it will put contents in 720x480 container
                 WARNING: as of PSP firmware v5.0 it does not respect the 8:9 PAR.
                 It will play the video with a 1.5 AR (720/480).
                 The effect is your video will play 80 pixels wider than it should be.
     -X        : force widescreen DVD detection
                     --  Crop options --
     -T num    : crop top (must be even number)
     -B num    : crop bottom (must be even number)
     -L num    : crop left (must be even number)
     -R num    : crop right (must be even number)
                     --  AtomicParsley options --
     -N str    : name (if not specified then -n is used)
               : this option is used for TV shows (-n "Family Guy s07e01" -N "Love Blactually")
               : example with quotes in title (-N "There's No \"We\" Anymore")
     -k str    : artist (req AtomicParsley and type ipod, psp, 3g2)
     -K num/tot : sets tracknum (auto determined, only pass if you want to do a num/tot with example (-K 01/13)
     -u str    : album (req AtomicParsley and type ipod, psp, 3g2)
     -d str    : description (req AtomicParsley and type ipod, psp, 3g2)
     -D str    : long description (req AtomicParsley and type ipod, psp, 3g2)
               : example with quotes in description (-d "Escape \"quotes\" on command line.")
     -e str    : genre (req AtomicParsley and type ipod, psp, 3g2)
     -y value  : year (req AtomicParsley and type ipod, psp, 3g2)
               : pass 4 digits or pass a year string value to encode a Release Date also.
               : see examples below.  (If no value is passed then current year is used.)
     -q str    : US TV & Movie rating (req AtomicParsley and type ipod, psp)
                 us-tv: "TV-MA, TV-14, TV-PG, TV-G, TV-Y, TV-Y7"
                 mpaa: "UNRATED, NC-17, R, PG-13, PG, G"

    note:
    If you end your titles for TV Shows with sXXeXX then it will be parsed correctly as a TV Show.
    If you end your titles for Music Videos with mvid then it will be parsed correctly as a Music Video.

    crop note:
    crop is done to the original video prior to encoding.  AR is recalculated on new crop size.

    year notes:
    If you pass -y XXXX you will get a year timestamp on your MP4 file only.
    If you pass -y "string value" you will get a year timetamp and Release Date information on your MP4 file.
    All string values are converted to UTC.

    Some example valid year strings:
    "July 24, 2007 10pm EST"
    "Mon Jan 26 12:26:13 EST 2009"
    "2009-01-23 21:00:00 EST"
    "2009-01-23 9pm EST"
    "2009-01-23"
    "2009-01-23 EST"
    "19 Dec 1994 EST"
    "oct 2 1994"
    "october 2 1994"
    "october 2 1994 EST"
    "october 19 EST"
    "`date`"

    general usage examples:
    example: ./encode-handheld-5.0.pl -t psp -l -s 10101 -n "My Video" -f file.avi -o 768 -c 120
    example: ./encode-handheld-5.0.pl -t psp -f file.avi
    example: ./encode-handheld-5.0.pl -t psp -f file.avi -n "hookah"
    example: ./encode-handheld-5.0.pl -t zune30 -f file.avi
    example: ./encode-handheld-5.0.pl -t zune30 -f file.avi -n "hookah"
    example: ./encode-handheld-5.0.pl -t ipod -f file.avi
    example: ./encode-handheld-5.0.pl -t ipod -f file.avi -n "hookah"
    example: ./encode-handheld-5.0.pl -t 3g2 -f tvshow.avi -n "TV Show s04e16" -r 24000/1001
    example: ./encode-handheld-5.0.pl -t psp -pi -f tvshow.avi -n "tvshow s01e13" -o 512 -r 24000/1001 -d "Jedi Crash" -q "TV-PG"
    example: ./encode-handheld-5.0.pl -t psp -pi -f rounders.avi -n "Rounders" -o 512 -r 30000/1001 -T 106 -B 102 -L 2 -y 1998 -q R -e Drama -d "Damon plays poker."
    example: ./encode-handheld-5.0.pl -t psp720 -pb -f rounders.avi -n "Rounders" -o 512 -r 30000/1001 -T 106 -B 102 -L 2 -y 1998 -q R -e Drama -d "Damon plays poker."

```

---

### Post by Creative2 on 2008-07-30
zune? well linux handle only wmav2 ..and wmv2 so quality is very poor...
on windows is wmv9 version 2.... it would be better leave zune convertion , this my point of view

---

### Post by HolyRoses on 2008-07-30
yea, it is crappy in comparison to the h264.  I bumped up the bit rate to 512kb and it looks good enough to watch though in my opinion.  Kids seem to think its passable.

The newer zunes though can play h264 video however and the ipod settings should be OK.  I dont have a newer zune though to play with.

The wmv2 & wmav2 that come with the apt-get version of ubuntu won't work very well at all.  I tried.  You need a newer rev of ffmpeg if you want to do that kind of encoding.

-HR

---

### Post by talz13 on 2008-09-05
Does this take advantage of multiple cores?  I built my ffmpeg with --enable-pthreads but it doesn't look like it's using multiple cores.  Maybe there should be an option to use ffmpeg's

`-threads count'
    Thread count. 

option.

---

### Post by Creative2 on 2008-09-06
it's a codecs problem only xvid and 264 codec can handle dual or more core , if you use others ffmpeg or mencoder will not use multicore

---

### Post by doggyworld on 2008-09-10
Thanks this actually seems to encode videos which can be played directly on my Zune, but the problem I see is that it sometimes lags and skips in audio and video.  Anyone else experience this?

---

### Post by HolyRoses on 2008-09-11
If you are using the the ffmpeg that comes with ubuntu then yes you will experience freakyness with WMV encoding.  I suggest you update to the latest svn for both ffmpeg and x264.

I have a much improved version of this script I should get around to posting, I need to clean up something though and the newest svn ffmpeg has some changes that make it not work properly again.

---

### Post by FakeOutdoorsman on 2008-09-11
You could probably use ffmpeg from the Medibuntu repository instead of compiling your own.

*Own horn tootage* - if you want to compile ffmpeg and x264:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by HolyRoses on 2008-09-11
I was going to suggest your guide.  heck I even followed it ;-)

Anyhow, if you encode PSP, this about the best darn thing there is.  Well my newer script has 2 pass encoding options and iphone and ipod touch support as well.

-HR

---

### Post by HolyRoses on 2008-09-11
Updated script and attachment.  It has more features now.

-HR

---

### Post by jdmpike on 2008-09-27
I used this script to encode some videos for my 3.90 PSP and everything worked great.

After an update to 4.01, my PSP can no longer play files that I used this script to encode (media type not supported).

Any idea what types of modification to the script (or the flags I pass to it during creation) must be made to continue using this awesome script with 4.01 firmware?

Thanks,

jdmpike

---

### Post by morgan10 on 2008-09-28
**Ashley Olsen steps out with new man**Ashley Olsen has started dating National Treasure actor Justin Bartha, according to reports.The pair have set tongues wagging after being spotted attending a performance of musical Jersey Boys in Las Vegas on Tuesday night. They were later seen enjoying a meal together in the city.A source told FoxNews.com: "[They] couldn't keep their hands off each other. They were rubbing each other, hand-touching and there was barely a break in their conversation. It's pretty serious. Ashley is really comfortable with Justin. It's a good fit [Everyday Slaves](http://www.everydayslavesblog.com/)."As well as starring as Riley Poole in the [Big Boob Pass](http://www.paysitespy.com/big-boob-pass/) Treasure films, Bartha, 30, has also appeared in 2006 movies Trust The Man and Failure To Launch.Olsen, 22, and her twin sister Mary-Kate were recently branded "disruptive, intrusive and totally disrespectful" by their neighbours [Orgy Sex Parties](http://www.orgysexparty.info/).Jade Goody has left hospital following two weeks of treatment for cervical cancer.The Big Brother star was snapped outside London's Royal Marsden Hospital carrying cuddly toys given to her by well-wishers as she underwent a hysterectomy [Heel Grabbers](http://www.heelgrabbers.biz/).Goody will spend the weekend at home with her family before starting a course of chemotherapy.Her spokeswoman said: "She is going to be at home with her boys. She can't wait to see them [Double Plugged](http://www.doubleplugged.biz/)."It was recently reported that the reality star faces a year of chemotherapy and radiotherapy after learning that her cancer has spread.

---

### Post by HolyRoses on 2008-09-29
Updated script to 2.7.

-----------

I don't know what the problem could be jdmpike.  I have encoded everything with 4.01 M33-2, a Dark Alex custom firmware release.

I suggest resetting PSP to defaults, making a backup of your memory stick and then formatting it using the PSP.

Everything created with this script should be 100% compatible with 4.01 M33-2.  I have never been able to create something that wasn't compatible.

As of this posting I am using ffmpeg SVN-r15418 and x264 0.64.979 6d4af8d.

It's nothing wrong with the script that is causing you issues.  Its either your ffmpeg or your x264 or your PSP firmware and memory stick, etc.  Upgrade to the PSP firmware I am using and reset your PSP to defaults and wipe your memory stick and try again.

-HR

---

### Post by HolyRoses on 2008-10-02
toying with the idea of adding a new blocking option.  This option will let you block to the next height that is dividable by 16.

Here is what I have worked up so far:

macroblocks of 16 and AR by 480
16*17 = 272 1.76
16*16 = 256 1.875
16*15 = 240 2
16*14 = 224 2.142857
16*13 = 208 2.3076
16*12 = 192 2.5
16*11 = 176 2.7272~
16*10 = 160 3
16*9  = 144 3.3333~
16*8  = 128 3.75

Here are some sizes I have used before:

psp sizes i have used
480x196 = 2.4489
480x200 = 2.4
480x202 = 2.3762
480x204 = 2.3529
480x208 = 2.3076
480x252 = 1.9047
480x258 = 1.8604
480x260 = 1.8461
480x262 = 1.8320
480x264 = 1.8181~
480x266 = 1.8045
480x268 = 1.7910
480x270 = 1.7777~ (1.78:1)

So basically what we would do would be to pad or block to the next macroblock size.  The original video will be the same, we are just letterboxing it to the next 16 dividable size and adjusting the AR to the new letterboxed size.

Can read more about macro blocks here:
[http://en.wikipedia.org/wiki/Macroblock](http://en.wikipedia.org/wiki/Macroblock)

This will stop h264 from complaining about not correct size, compression will suffer, it will also make it so the green bar disappears while playing video in VLC.

-HR

---

### Post by jdmpike on 2008-10-04
I think this is a great idea.

Keep up the great work HR!

---

### Post by HolyRoses on 2008-10-07
added new blocking option as previously discussed.

add -g to block to next macro block height.

I didn't put in any logic to handle non widescreen sources, so it may mess up the AR if you attempt to use -g with a non widescreen image.  I didn't do any testing with it.

Also of note if you are using the latest ffmpeg and x264 then the B frames option isn't going to work properly since the developers have made changes to -subq and the removal of -flags2 +brdo and -bidir_refine 1.  I haven't made code to determine if you have those options in your ffmpeg or not to make a decision on which flags to use.

Your new 2 pass PSP encode with iPhone, iPod touch, Nano 3G compatiblity will be something like this:

./encode-handheld.pl -t psp -pig -n "Good Movie" -f Desktop/Movies/Good Movie/good\ movie.avi -r 24000/1001 -o 512


-HR

---

### Post by jdmpike on 2008-10-08
Can we get this script in the the repos? I would love to have apt or Synaptic update this thing for me.

If you can't tell I am a big fan of this. I use it on several machines, so updating it everywhere is more tedious than I would like.

Just a thought.

Keep up the great work!

---

### Post by HolyRoses on 2008-10-15
I haven't tested this using ffmpegX under MacOS in a long time and noticed there is a bug with me method detection.

To fix latest script to work under MacOS X using ffmpegX find this area in the code:

# determine me method
open(ME_METHOD, "$ffmpeg 2>&1 |");
while(<ME_METHOD>){
        if (/-me_method/) {
                $me_method = "-me_method";
                last;
        } else {
                $me_method = "-me";
        }
}
close(ME_METHOD);

then add the following right under it:

# override for ffmpegX
if ( $kernel_name eq "Darwin" ) {
        $me_method = "-me";
}

Not the prettiest work around but it works.  I supposed I could change the detection and see if you have -me first and then use that, if you don't have -me then use -me_method.  Until then though, use that.

-HR

---

### Post by talz13 on 2008-12-06
Can this support passing along subtitles to the output mp4 file?  I have been playing with your 1.9 version since september, and today after building new svn ffmpeg and x264, and changing the -me option to -me_method, I was able to produce a working psp video with threads 4 option.  However, subtitles didn't seem to be getting added to the output file.  I could extract the subs from the original file and mux them, but I don't want to have to manually do it each time...

---

### Post by HolyRoses on 2008-12-07
version 1.9 is old.  Go to the first page and download 2.8.  read the options and example encode string as I changed many things since 1.9.

I don't think you can burn subs into the video using ffmpeg.  I have done it successfully however using mencoder.

-HR

---

### Post by talz13 on 2008-12-08
> **HolyRoses said:**
> version 1.9 is old.  Go to the first page and download 2.8.  read the options and example encode string as I changed many things since 1.9.

I don't think you can burn subs into the video using ffmpeg.  I have done it successfully however using mencoder.

-HR

I know 1.9 is old, but it's working for me, and you know, if it's not broke, don't fix it :)

I was able to add the -scodec copy command to the script, but PSP video doesn' support subtitle streams, so that idea went out the window...

Did you make PSP videos with mencoder?  If so, do you have command line settings for it?  If you could provide that for me I'd be glad to see if I could work it into my script.

---

### Post by jdmpike on 2008-12-11
Does 2.8 still work with the latest svn/git version of ffmpeg and x264?

I think I compiled working copies of these binaries and there were errors trying to use encode-handheld, not sure if some of the flags changed or what. Can you point me to some log files so I can try and help figure out what is going on?

I am going to recompile/reinstall ffmpeg and x264, then I will give it another shot.

Thanks!

---

### Post by jdmpike on 2008-12-11
Here is the output when I try to encode a file with the latest versions of ffmpeg and x264.

```

jordan@luckyseven:~/scripts$ ./encode-handheld.pl -t psp -pig -f /home/jordan/theMovie.avi -o 768
Selected file: /home/jordan/theMovie.avi
Selected type: psp
Selected Volume: -vol 768
Selected thumbnail time: 120
Selected naming: simple
Selected thumbnail type: theMovie.jpg
video width = 608
video height = 256
video aspect ratio = 2.375
The psp_encode_height: 202 is even. No adjustment necessary.
video frame size is 480x202
psp video aspect ratio = 2.37623762376238
psp video height difference = 68 pixels
the padtop height 34 is even. No adjustment necessary.
Letterboxing video to next macro block
pad top = 4
pad bottom = 2
new video frame is 480x208
new frame aspect ratio is 2.30769230769231
encoding file: /home/jordan/theMovie.avi
output file = theMovie.m4v
FFmpeg version SVN-r16054, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 11 2008 07:59:38, gcc: 4.3.2
[NULL @ 0x1e74870]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/home/jordan/theMovie.avi':
  Duration: 01:32:15.70, start: 0.000000, bitrate: 1060 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 608x256 [PAR 1:1 DAR 19:8], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
/usr/local/bin/ffmpeg: unrecognized option '-me'
FFmpeg version SVN-r16054, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 11 2008 07:59:38, gcc: 4.3.2
[NULL @ 0x248d870]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/home/jordan/theMovie.avi':
  Duration: 01:32:15.70, start: 0.000000, bitrate: 1060 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 608x256 [PAR 1:1 DAR 19:8], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
/usr/local/bin/ffmpeg: unrecognized option '-me'
generating thumbnails
Thumbnail height of 67 is odd, decreasing value.
thumb_height is 66
thumb_height_difference = 54
The thumb padtop: 27 is odd. Adjusting.
thumb pad top = 28
thumb pad bottom = 26
FFmpeg version SVN-r16054, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 11 2008 07:59:38, gcc: 4.3.2
[NULL @ 0x22d0870]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/home/jordan/theMovie.avi':
  Duration: 01:32:15.70, start: 0.000000, bitrate: 1060 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 608x256 [PAR 1:1 DAR 19:8], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
[imgconvert @ 0x22f4aa0]PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, image2, to '/home/jordan/Desktop/Handheld-Video/theMovie.jpg':
    Stream #0.0: Video: mjpeg, yuvj420p, 160x120 [PAR 57:32 DAR 19:8], q=2-31, 200 kb/s, 23.98 tb(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[mpeg4 @ 0x22d0870]Invalid and inefficient vfw-avi packed B frames detected
frame=    1 fps=  0 q=3.0 Lsize=      -0kB time=0.04 bitrate=  -4.2kbits/s    its/s
video:3kB audio:0kB global headers:0kB muxing overhead -100.626424%

```

---

### Post by talz13 on 2008-12-12
You can update the script to use "-me_method umh" instead of just "-me umh" or whatever it had before.  Mine didn't recognize "-me" either, though I don't know if that's the only issue for you right now.

Also, when you built your ffmpeg and x264, did you install them as those particular names (i.e. as "ffmpeg" and as "x264"), or did you change the names of them to not conflict with existing packages?

I had been having issues with everything I encoded with the script until I removed the original ffmpeg and x264 packages, rebuilt my new ones, and installed them with the original library name.  I don't know if it was the rebuild of fresh svn/git that did it, or if it was the actual replacement of the ubuntu libraries with what I had built that did it.  After that, it started using my built libraries instead of the ubuntu ones and it started producing good files.

---

### Post by HolyRoses on 2008-12-13
/usr/local/bin/ffmpeg: unrecognized option '-me'


yes 2.8 was adjusted to use me_method, old -me was removed from svn.

-HR

---

### Post by jdmpike on 2008-12-16
Maybe I should check which version of the script my symbolic link points to?

Thanks again!

---

### Post by HolyRoses on 2009-01-08
Will be posting a new version soon that supports iTunes tagging and allows my 480 width videos to play on ipod 5g and 5.5g.  New version fully supports tv shows with season & episodes, movies, music vids tagging automatically.

Also will support cell phone output and sony cyber shot camera conversions.

Would post it today but i destroyed it in the process of packaging it with a oppsie tar command....  had to recode about a weeks worth of crap.

-HR

---

### Post by HolyRoses on 2009-01-08
OK.  I have updated main page with v3.1 client.

It has a lot of new features.  The biggest feature is now my 480 width encodes will play on an ipod 5g and 5.5g.

Other new features are a 640x480 CABAC encode and cell phone 174x144 encode.

It also does a lot of iTunes tagging.

-HR

---

### Post by FakeOutdoorsman on 2009-01-08
Many features.  I'll have to try it out, although I am handheld playerless.  Perhaps you should add it to: [Encoding Video for the iPod Video](https://help.ubuntu.com/community/iPodVideoEncoding) [Ubuntu Wiki]

---

### Post by HolyRoses on 2009-01-08
Hmm, probably a good idea.  My program makes flawless video for what its intended for.  I been using variations of it for a while now.  I have never edited a wiki though.  I would have to again revisit the ffmpeg though from svn to make sure its 100% compatible.  I haven't updated my ffmpeg since they changed the way subq and b frames work.  So might be a slight incompatibility there.  Hard to keep on top of ffmpeg... changes so often.

-HR

---

### Post by HolyRoses on 2009-01-19
I have released v3.2 of this script.  Just google it please for download.

This version adds support for US TV & Movie ratings.

Otherwise basically same pack as 3.1

-HR

---

### Post by FakeOutdoorsman on 2009-01-19
You should release a version of the script that does not include any binaries for those of us who already have svn ffmpeg and AtomicParsley.  In other news, ffmpeg now has libx264 iPod presets.  See [HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095) for usage examples.

---

### Post by HolyRoses on 2009-01-23
Latest version: v3.4

This version adds cropping support, genre, removes restriction on some atoms.  Cleaned up code a little bit.

Download from this link: 
[http://R](http://R) A P ID  SH a Re . com/files/187855243/encode-handheld-3.4.tar.gz



-HR

---

### Post by HolyRoses on 2009-01-26
My latest version of encode-handheld.pl.

New stuff:

* Using jhead to remove comment from PSP thumbnail, thereby creating a proper JPEG header.

* Added support for adding unique title atom to videos other than just the file name.
so now you can do -n "Family Guy s07e01" -N "Love Blactually".
That will set the file name to "Family Guy s07e01.m4v" and the title to "Love Blactually".

* Added track support for TV Shows. This will be auto populated if you use naming structure
of "TV Show s01e01". If you want a num/tot then pass 01/13 for example.

* Added support for Release Date using year. Can now pass a year string and now Release
Date will be filled. Look at examples in encode-handheld.pl -h

* If creating TV show, now Album and Artist will be filled out automatically.
Album will be "TV Show, Season #". Artist is a copy of TV Show.


Change:

* The default year value is now current year and not 2009.


Download from:

[http://rapidshare.com/files/189811550/encode-handheld-3.5.tar.gz](http://rapidshare.com/files/189811550/encode-handheld-3.5.tar.gz)


Good luck!

-HR

---

### Post by HolyRoses on 2009-01-29
My latest version of encode-handheld.pl v3.6


New stuff:

* Added support iPod 640 width encodes (default video bit rate 1024kb ABR)

* Added support for PSP Motion JPG encodes (default video bit rate 4480kb)

* Added support for quotes (" ") in description, was in title only before.


Changed stuff:

* Disabled some needless print messages.

* Removed trellis from the iPod encode line, wasn't hurting anything, but not doing anything either.

Notes:

You may want to mess with the video bit rate for iPod 640w.  I found 640kb to be fine, but there was slight pixelization around opening credits when I was working with my test clip.
  
[Download via RS.]("http://rapidshare.com/files/190900315/encode-handheld-3.6.tar.gz")


Good luck!

-HR

---

### Post by HolyRoses on 2009-01-29
My latest version of encode-handheld.pl v3.6a


New stuff:

* Check to make sure description isn't over 255 characters.  If it is then the description is truncated to 255 and displayed to user.  If it is over 255 iTunes will not display the description.

Changed stuff:

* iPod encodes now default to format psp if psp is a valid format in your ffmpeg.  Encoding with format mp4 or format ipod produces mpeg4 files that cannot be re-tagged using AtomicParsley.  AP gives an error.  Error doesn't occur if you use format psp.

[Download via RS.]("http://rapidshare.com/files/191183176/encode-handheld-3.6a.tar.gz")


Good luck!

-HR

---

### Post by HolyRoses on 2009-02-06
My latest version of encode-handheld.pl v3.8


New stuff:

* Added support PSP 720x480 anamorphic widescreen encodes (default video bit rate 768kb ABR).
  This is the highest quality encode that the script will create.   Should use this
  if you are encoding for PSP, xbox 360, PS3 and want the highest quality.  Should use
  HD sources for material.  Use settings "-t psp720 -pb" for highest quality (this will be SLOW).

* Added support for new ffmpeg and x264 bframes and subq settings.


Changed stuff:

* Moved some objects around for psp720 support


Note:

* For proper playback of 720x480 material on the PSP your screen setting should be "Full Screen"

* Script is good for making custom ringtone videos for a Samsung Rant too ;-)  May need to adjust
  bitrate for audio and video to create small size file for video ringtone for Rant, must be 512kb or less.
  use options "-t 3g2 -j xx -z xx" Create ringtone videos of around 15-30 sec in length.

  
[Download via RS.]("http://rapidshare.com/files/196435861/encode-handheld-3.8a.tar.gz")


Good luck!

-HR

---

### Post by HolyRoses on 2009-03-19
bumped rev on main page to v4.5

Lots of changes since last update.

Now support DVD's, matroska ac3 and dts audio, ipod 16:9 widescreen anamorphic style encodes, iPod long description, probably some other minor things too.

If you want to use DVD source, then you need to dump the DVD with vobcopy or mplayer.  If the dvd has audio/video delayed you need to use -j 1-3 to get it to be in sync.  use mediainfo to determine if the audio is delayed.

Use supplied AtomicParsley binary if you want "ldes" or compile your own and used supplied diff.

-HR

---

### Post by HolyRoses on 2009-03-19
this document:

[https://help.ubuntu.com/community/iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding")

is entirely usless.  It should be totally scrapped and someone build a new document that uses this script as its base.  This script is the definative iPod encoder.

That document is full of bunk and misinformation.  The internet is full of false information regarding iPod and PSP encoding.  Don't believe half of what you read out there.  This script pushes the iPod and PSP to its limits.  It will build correct files everytime without guesswork.

-HR

---

### Post by Stochastic on 2009-03-19
> **HolyRoses said:**
> this document:

[https://help.ubuntu.com/community/iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding")

is entirely usless.  It should be totally scrapped and someone build a new document that uses this script as its base.  This script is the definative iPod encoder.

That document is full of bunk and misinformation.  The internet is full of false information regarding iPod and PSP encoding.  Don't believe half of what you read out there.  This script pushes the iPod and PSP to its limits.  It will build correct files everytime without guesswork.

-HR


That's a **community** editied site, you have just as much ability to change what you're complaining about than anyone else.  So go ahead and edit!!

---

### Post by HolyRoses on 2009-03-19
guess I am going to have to.

---

### Post by HolyRoses on 2009-04-19
updated rev on main page to 4.6.  Added 2 new profiles to support true NTSC DVD and PAL DVD resolutions for iPod.  These only work on current selling units.

Tested on latest compiled ffmpeg and x264.  Works correctly with new metadata api.

-HR

---

### Post by miltonsj on 2009-05-27
Thanks for the 4.6 version of encode-handheld.pl!  The previous version 3.5 kept quitting early during conversion, but this one works perfectly. 

I downloaded your precompiled binary of ffmpeg, and it works perfectly with it as well.  Nothing like hours on Ubuntu trying to convert your videos for PSP :(

Again, THANKS! THANKS! THANKS!

---

### Post by tjack360 on 2009-05-30
Encode-handheld.pl is the best PSP encoding application I have ever used. It's so good, I switched from Windows to Ubuntu to use it and I haven't regretted it yet. Nice work.

---

### Post by maka on 2009-06-01
hmm.. has anyone gotten this to work with a Zune 30?  I tried the following:

encode-handheld.pl -t zune30 -f 01.rmvb -n "01"

It converted it and looked good on my computer.  I then transferred it to my WinXP machine and tried to sync.  The software seemed to reject it due to "invalid media type"

TIA

---

### Post by HolyRoses on 2009-06-16
> **maka said:**
> hmm.. has anyone gotten this to work with a Zune 30?  I tried the following:

encode-handheld.pl -t zune30 -f 01.rmvb -n "01"

It converted it and looked good on my computer.  I then transferred it to my WinXP machine and tried to sync.  The software seemed to reject it due to "invalid media type"

TIA

I honestly haven't touched the zune30 profile in eons.  It should work though.  It did when I created it ;-)  Basically this just creates a movie in WMV for the zune 30gb unit since that is all that that unit can play.  It could be that the Zune has updated their firmware on that unit so that the movies created with the older WMV codecs aren't allowed to play anymore.  The zune I tested with is now broken and doesn't power on.  So I don't know I can even validate it anymore.

These two options should work fine for your zune30 also, however the zune software will transcode the movie at sync time (leading to a far longer sync time).

-t ipod
-t psp -i

The ipod profile will encode faster than the other due to less pixels to compute.

You may also need to set a frame rate, sometimes not setting a frame rate makes the movie encode bad or not compatible.  If its PAL use -r 25, NTSC DVD -r 24000/1001, Some TV 30000/1001.

-HR

---

### Post by KamalGurung on 2009-07-09
I am getting the following error messages, please tell me what's causing this ?

> [mpeg4 @ 0xa438700]Error at MB: 553
Marker bit missing before vop_coding_type in video packed header
[mpeg4 @ 0xa438700]concealing 283 DC, 283 AC, 283 MV errors
[mpeg4 @ 0xa438700]slice end not reached but screenspace end (20 left FFFF70, score= -303)
[mpeg4 @ 0xa438700]concealing 774 DC, 774 AC, 774 MV errors
[mpeg4 @ 0xa438700]ac-tex damaged at 16 1B time=19.93 bitrate= 433.6kbits/s    
[mpeg4 @ 0xa438700]Error at MB: 60
[mpeg4 @ 0xa438700]marker does not match f_code
[mpeg4 @ 0xa438700]concealing 764 DC, 764 AC, 764 MV errors
[mpeg4 @ 0xa438700]slice end not reached but screenspace end (9 left FB8000, score= -482)
[mpeg4 @ 0xa438700]concealing 774 DC, 774 AC, 774 MV errors
[mpeg4 @ 0xa438700]ac-tex damaged at 19 6B time=23.44 bitrate= 576.2kbits/s    
[mpeg4 @ 0xa438700]Error at MB: 283
[mpeg4 @ 0xa438700]marker does not match f_code
[mpeg4 @ 0xa438700]concealing 546 DC, 546 AC, 546 MV errors

Also my system is encoding as the following :-
frame= 1773 fps= 12 q=18.0 size=    5118kB time=73.43 bitrate= 571.0kbit

My system specifications are Intel Pentium IV 3.0 Hyper Threading 4 GB Ram. 512 MB Nvidia Graphics Card. How long does it take for a full video to get encoded ?

---

### Post by HolyRoses on 2009-07-09
Looks like a corrupt mp4 file you are using as a source?

Can you post the encode-handheld.pl string you are using, you can omit the actual file name.

also run ffmpeg -i filename.you.are.trying.to.encode

so we can see what ffmpeg thinks the file is.

oh and as far as speeds, well that depends on your source file, destination profile and speed of computer.

---

### Post by KamalGurung on 2009-07-09
Ok I used ./encode-handheld.pl -t psp -f myfile.avi -n "title" only.

When I run ffmpeg -i filename I get the following :-
> FFmpeg version SVN-r19392, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 10 2009 02:14:09, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (10000000/417083)
Input #0, avi, from 'filename.avi':
  Duration: 01:44:54.40, start: 0.000000, bitrate: 934 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 688x288 [PAR 1:1 DAR 43:18], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 112 kb/s
At least one output file must be specified


It took me more than 4 hours for the Video to get encoded ? Is it very slow ? It's for the first time I am doing this.

So please guide me with all the details.

Ok Another Update after the encode completed I can play it on Totem Movie Player 2.26.1 but when I transferred it to my PSP it shows corrupted data. I am on Official Firmware 5.03.

---

### Post by HolyRoses on 2009-07-09
set the frame rate with -r 24000/1001

use that frame rate whenever you see 23.98 fps or if its 24/1 (a ffmpeg read error)

rerun it again with that -r option and -z 300 to encode for 5 min to see how it turned out.

It could be slow ya ;-) use option -i also if you are using -t psp it might encode faster, but you will need to be running psp firmware 4.01 or higher to play the vid.  encode while you are sleeping then it will seem really fast to you!  Hey there is a video here!

Also updated main page with RS link to 4.8.  Not that it will fix your problem or anything.


-HR

---

### Post by HolyRoses on 2009-07-09
I am also not familiar with that cpu, it might be a dual core or quad core cpu?

mess around with option -m

like try -m2

or up to -m4 or something and see if the FPS goes up.

---

### Post by HolyRoses on 2009-07-09
it showed corrupted because it encoded the video at 10000000/417083 FPS which is very crazy like.  refer to other posts i just made.


Well I just read about Hyper-threading and it is like an intel core duo.  So use -m2 to speed things up.

---

### Post by KamalGurung on 2009-07-09
ok Thank you for your replies, I will try as you said in the other posts. It's only 3.0 Hyperthreading Pentium 4 Processor it's not core 2 duo processor. So can I still use -m2. I will give you the results shortly after I try.

Also I installed Vobcopy and I am trying to make iso of a DVD. I tried to Install mkisofs but it says the following :-
> sudo apt-get install mkisofs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting genisoimage instead of mkisofs
genisoimage is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So can I also encode .iso files directly like -f mydvd.iso ?

---

### Post by HolyRoses on 2009-07-09
according to [http://en.wikipedia.org/wiki/Hyperthreading](http://en.wikipedia.org/wiki/Hyperthreading)

It is treated to the OS as a dual cpu's so yes -m2 is fine.

you can't encode from .iso/.img  (you must first mount the img then rip like a normal dvd disc)

use vobcopy to rip a dvd

vobcopy -l

the readme.txt has examples.

then encode the resulting .vob (ripped title from movie).

---

### Post by KamalGurung on 2009-07-09
Thank you again,

I used ./encode-handheld.pl -t psp -f myfilename.vob -n "title" -r 24000/1001 -m2 and now its encoding as following without any errors:-

frame=  894 fps= 13 q=19.0 size=    2399kB time=36.99 bitrate= 531.2kbits/s 

so is it good ?

---

### Post by HolyRoses on 2009-07-10
> **KamalGurung said:**
> Thank you again,

I used ./encode-handheld.pl -t psp -f myfilename.vob -n "title" -r 24000/1001 -m2 and now its encoding as following without any errors:-

frame=  894 fps= 13 q=19.0 size=    2399kB time=36.99 bitrate= 531.2kbits/s 

so is it good ?

I would just encode for 5 min, to see that its working properly.

use -z 300 or 240 (for 4 min, etc)

copy to psp, check sync, see if its working like you expect.  If it is then do a full encode.

---

### Post by KamalGurung on 2009-07-10
I did the following and it's working. Thank you once again HolyRoses.

> ./encode-handheld.pl -t psp -f file.vob -n "File" -r 24000/1001 -m2 -z 240

Also what switches do I need to use to encode full screen size videos for PSP.

---

### Post by HolyRoses on 2009-07-10
There isn't any logic to manipulate every source to a 16:9 AR (480x272) to fill the psp screen.  That would require cropping the source to a 16:9 AR.  Best thing I can say is use the zoom display mode on your psp.  Press Triangle while playing, select screen mode, then press that until its at zoom.  That would be the correct way to do it.

---

### Post by KamalGurung on 2009-07-12
I finished Encoding few movies but the sound volume is very low in these encoded movies ? What might the problem be ? Also am I missing something for the audio ?

---

### Post by HolyRoses on 2009-07-12
you realize there is a help option?

./encode-handheld.pl -h

the -o option is for adjusting audio gain.

---

### Post by KamalGurung on 2009-07-21
Thank you again, yes I used the -o 2560 and the audio is good now. Also if I have a Tripple Core Processor do I use -m3 ? Also will this encode-handheld work on Fedora or does it have to be Ubuntu only ?

---

### Post by HolyRoses on 2009-07-21
wow, that should be crazy loud and probably has a good amount of distortion too.

You can use any linux.

I'm not aware of a triple core processor but ya -m3 would be applicable.  You can adjust the value to see if your fps goes up.

---

### Post by KamalGurung on 2009-07-24
Yes it was very loud hehehe, I used I used ./encode-handheld.pl -t psp -f myfilename.vob -n "title" -r 24000/1001 -m3 -0 1024 and it took me 2.51 hours for the video encoding to complete and the output file size was 555.72 MB. So is this good ?

I recently upgraded to AMD Phenom Tripple-Core Processor 2.10 Ghz with 2 GB Ram 800 Mhz FSB and the Graphics is inbuilt it has 400 MB Dedicated but Ubuntu 9.04 doesn't support it and I am not getting the drivers. If I have a good Video Card then will this encoding process be fast ?

The Final results were the following :-
frame=226270 fps= 33 q=-13859676.7 Lsize=  569061kB time=9049.54 bitrate= 515.1kbits/s

The Video works great and the audio is also good I don't notice any distortion or I don't know what the audio distortion is :D while playing a video.

Thank you very much for all the support and kind replies.

---

### Post by HolyRoses on 2009-07-24
33 fps is alright, its processing faster than real time at least.  24fps is realtime.  You can try using -m4 or -m6 see if fps goes up.  Or just clock it and see how long it takes to encode 5 minutes with -m3 vs -m6

---

### Post by HolyRoses on 2009-11-17
Bumped rev to 5.0 on main page.


**Changes in 5.0**
Changed some of the logic regarding b frames and flags2.  It is possible now to create videos that will not play on ipod.  So dont use -b unless you dont want it to play.

Added beta AppleTV profile (1280x720 HD).  Use -pb for best results.  Has yet to be verified these play on AppleTV.  Plays fine on PS3 and Xbox 360.

Added iPod 480x320 anamorphic profile.  No real point to this, but someone may want it.  In between profile from -t psp -i and -t ipoddvd.  Creates 569x320 viewing dimensions.

Added auto 16:9 mode.  Will auto crop any source to 16:9.  Use option -A (not -a, that is auto pad).  If you are using Auto Crop to appletv profile you should use a 1080p source.  You don't want to manufacture pixels.  If your input is 1920x800 it will be cropped to 1422x800 and then encoded using that source size to 1280x720.  So no pixels will have to be created, only reducing. If using -t ipoddvd it would be encoded to 640x480 with a 16:9 ar resulting in 853x480 viewing.  In this case you could of used the 1280x534 (949x534 reduced) version and not created pixels.

note: the only profiles that are iPod and PSP compatible are -t psp -i and -t ipod


**Changes in 4.9**
Retooled script, no longer uses or requires faac (binary) or MP4Box.

set a default fps to 24000/1001
set a default threads to 2

new option to force widescreen dvd selection.

recognizes "flip video stream" for audio processing.

fix minor bugs that may or may not of been there in 4.8 ;-)  more bugs may appear.

Limited testing, give feedback.

May provide more accurate syncing when syncing audio processed externally via a52dec or dtsdec (100-200ms).  Compare encode with 4.8 using DTS processed audio and 4.9  DTS processed audio using -M.  In 4.8 audio adjust with VLC and use -100 to -200 delay and see if it matches 4.9 audio.

NOTE: you will have to have an ffmpeg that accepts piped input.  For a while there it was broken in SVN, but it appears fixed again.

---

### Post by area51manah on 2009-11-23
How do i install it??
im a newbie to karmic & linux and i very much like your rip?
pls help

---

### Post by HolyRoses on 2009-11-23
As much as I would like everyone to use encode-handheld.pl it is not meant for everyone.  You need to have a basic understanding of Linux and more specifically Linux command line.

If you are talented in linux command line then the program is a real no brainer.  Its like any other linux command line program.

In sum, all you need to do is (unpack 5.0d first) move encode-handheld*, ffmpeg*, and AtomicParsley to /usr/local/bin/.  Then run encode-handheld.pl -h to see all the available options.

If you are successful in this then I suppose I could answer general questions regarding usage, but it is pretty self explanatory (read the help options).  Everything is explained in the help options.  You have to read it however, which most people fail in...

-HR

---

### Post by area51manah on 2009-11-24
> **HolyRoses said:**
> 
In sum, all you need to do is (unpack 5.0d first) move encode-handheld*, ffmpeg*, and AtomicParsley to /usr/local/bin/.
[IMG]http://www.mediafire.com/imageview.php?quickkey=joztnmhqh2n[/IMG]
[IMG]http://www.mediafire.com/imageview.php?quickkey=joztnmhqh2n[/IMG]
[B]i cant access /usr/local/bin/?
when i open the said folder nothing is there i cant paste/move anything there?
pls help


[/B]

---

### Post by sanket_s on 2009-11-24
@HolyRoses do i move the ffmpeg provided in ur v5.0d to the folder /usr/bin or /usr/local/bin and then run config script given in the ffmpeg folder?

and one more thing, do i have to put avi files as input to this code or can i put mpg or flv files as well??

Thanx in advance :p

---

### Post by lie07 on 2009-11-24
since i have been dloading holyroses rips for my zune hd [they all work great] so now i have decided to try it on my own for some Bwood movies...
wish me luck :P

---

### Post by area51manah on 2009-11-24
> **lie07 said:**
> since i have been dloading holyroses rips for my zune hd [they all work great] so now i have decided to try it on my own for some Bwood movies...
wish me luck :P
If you ever succeed share with us too !! well be damn greatfull 
:plove holyroses rip:p

---

### Post by HolyRoses on 2009-11-24
please do not discuss "rip" or anything remotely regarding such a thing.  This is totally not the correct forum for such discussion.

I will provide the exact key sequence to install.

open a terminal window

change directory to where encode-handheld-5.0d-with-ffmpeg-and-atomicparsley.tar.gz is located.

for instance if its on your desktop

cd Desktop

gzip -dc encode-handheld-5.0d-with-ffmpeg-and-atomicparsley.tar.gz | tar xvf -

cd encode-handheld-5.0d-with-ffmpeg-and-atomicparsley/

sudo mv encode-handheld* /usr/local/bin

cd ffmpeg-SVN-r20562/

sudo mv ffmpeg* /usr/local/bin

cd ..

cd AtomicParsley/

sudo mv AtomicParsley /usr/local/bin

installation  is completed.

now run

encode-handheld.pl -h

When prompted for password from sudo enter your current password.

-HR

---

### Post by lie07 on 2009-11-24
> **HolyRoses said:**
> please do not discuss "rip" or anything remotely regarding such a thing.  This is totally not the correct forum for such discussion.


I know, but i had to put it out there...

i have everything working great, questions...
1) do i really need jhead? 
hmmm let me see if i have anymore....
i guess not right now...

---

### Post by HolyRoses on 2009-11-24
sudo apt-get install jhead

no, you dont *need* it.  Just makes things correct.

you will also need the following if you want to process dts and ac3 audio inside mkv file.

sudo apt-get install libdca0
sudo apt-get install liba52-0.7.4
sudo apt-get install mkvtoolnix mkvtoolnix-gui

---

### Post by lie07 on 2009-11-24
> **area51manah said:**
> If you ever succeed share with us too !! well be damn greatfull 
:plove holyroses rip:p

here is someething that i came across [my 1st try]
i dont know if i could post links here or not but here is [linky]("http://googlygu.com/encoded/1sttry.m4v")

this is what i used "encode-handheld-5.0d.pl -t ipod480 -i -f /home/me/Desktop/1sttry.mkv -n "1sttry" -o 768 -c 170"

i dont know if im missing anything [HolyRoses fill me up] 

thanks so much HolyRoses, HolyRoses for president! :P

---

### Post by HolyRoses on 2009-11-24
-i is only useful with -t psp, otherwise it does nothing.
-c only does something on psp profiles.

you could of skipped that weird license thing with option -j 6 and cleaned up the video more with -p

there are a lot of different profiles, play around with them.  there are a lot of options, no one force you to use them all, use em, or dont use em.

---

### Post by lie07 on 2009-11-24
> **HolyRoses said:**
> -i is only useful with -t psp, otherwise it does nothing.
-c only does something on psp profiles.

there are a lot of different profiles, play around with them.  there are a lot of options, no one force you to use them all, use em, or dont use em.

yes i know there a lot of options but i wanted to hear it from president

---

### Post by sanket_s on 2009-11-25
Thanks a lot HolyRoses for this script... was able to put up videos in my ipod conveniently for the first time in linux... :D

---

### Post by HolyRoses on 2009-11-25
update for Apple TV owners/users.

Apple TV can play:
-t psp720 -b
-t appletv -b

and of course all the other ipod profiles.  I'm sure -t psp640 & psp640wide will work as well, but untested.  -x will probably work too, but also untested.

So appears it will play CABAC Main Profile encoded movies with B frames (up to 16) as long as they are within NTSC DVD (720x480 anamorphic) or PAL DVD (720x576 anamorphic) resolutions.  appletv profile is CAVLC High Profile (dct8x8), 3 bframes, probably supports more bframes, but quicktime doesn't like up to 16 bframes in 1280x720 cavlc.  Confirmed it does play 16 b frames using appletv profile on Apple TV without corruption found in QuickTime.  CABAC 1280x720 doesn't show up on the Apple TV listing, at least not with the test file I had.  Will try to gen my own and try.

These are not documented specs according to:

[http://www.apple.com/appletv/specs.html](http://www.apple.com/appletv/specs.html)

but published specs are often very wrong I have found out.  So basically all H264 profiles that encode-handheld.pl creates are Apple TV OK.

Next revision of encode-handheld.pl will include Poster Art support since without it, it looks very goofy on Apple TV.  Possibly include 5.1 AAC audio for Apple TV.


UPDATE:

updated main page with link for 5.1, which adds support for artwork.
updated main page with link for 5.1a, fixes logic for mp4 type output defaulting to mp4 only.

update, ok so apparently apple is just chuck full of lies regarding appletv.  It plays cabac with trellis2 just fine in 720p.  wth...  This does increase your encoding time by like double though.

updated main page with link for 5.1b, adds support for CABAC Apple TV.
updated main page with link for 5.1c.

New in 5.1c
Changes to support wez AtomicParsley --longdesc

Includes new AtomicParsley.  You must install this if you are using appletv and the output file is over 2gb.  You will get a fatal AtomicParsley error otherwise when it tries to tag the file.

Just a note, if you use the -I option with -t appletv you may experience framerate slow down in certain scenes (with Apple TV playback).


-HR

---

### Post by bhigh24 on 2009-12-13
Just wanted to give thanks to HolyRoses.  Love being able to put my shows on my Ipod.  Keep it up....you are appreciated.

---

### Post by HolyRoses on 2009-12-13
Hey thanks,

Updated main RS link on first page to 5.2

New in 5.2

tweaks to help output
was searching for AtomicParsley with all lowercase, changed.
Included iTunMOVI-1.1.pl to add new advanced tagging to files.  (Not yet incorporated into encode-handheld.pl as it requires switching to Getopt::Long;)
renamed psp720 to psp480p in support for psp576p
corrected psp640 (was missing refs)
added: PSP 720x576 16:9 & 4:3 encoder. (use psp768 for 4:3 and psp576p for 16:9)
(believe you need psp firmware 5.50 and above to use the new PAL 720x576 sizing)
Search for dcadec instead of dtsdec
dcadec and a52dec were being called by name instead of variable, corrected
Disable wpredp if present in ffmpeg
added support for mbtree if present in ffmpeg
Removed reliance on unix date command for formatting the iTunes year. (fixed Mac OS X year problem)


-------------------------------------

Now includes binaries for Mac OS X.  Binaries were compiled on Mac OS X Snow Leopard on Intel i386 platform.  ffmpeg, mkvmerge, mkvextract are not compiled statically like they are for Linux.  I have included them in tarball fashion so when you unpack the tarball you will get the needed dynamic libraries.

Mac binary versions:

ffmpeg SVN-r20797
x264 0.80.1373 4322f63
mkvmerge v2.9.9 ('Tutu') built on Dec  7 2009 01:07:42
AtomicParsley wez commit 31.



-HR


Have made significant progress on adding soft subtitles and extra audio tracks, hopefully something added soon to tool base to make it easy.  I have a huge write up on the current status of it on a torrent for 5.2, but I dont want to repaste it here or link it.

In the mean time if you have a Mac use subler, it works great.

---

### Post by alberto2172 on 2010-03-04
hey HolyRoses i just want to say that i like the movie release that you give us. i am new at this and i was wondering if you can teach me how to encode video files useing encode handheld. I am new at Ubuntu and i dont know how to install and use encode handheld. i was wondering if you could really appreciated it. Or if you could make a video showing me how to install and use encode handheld. 
Thanx Alot!!!

---

### Post by HolyRoses on 2010-03-04
read this entire thread.

read the how to compile ffmpeg thread as well.

its not for new people, this script really designed for people who know command line already.

it is not gui program or simple click and point thing.  you need to know the underlying components and how to install them, should also have some general knowledge about the underlying programs as well.

If you have all the necessary programs and knowledge then the program is very powerful and good for you.  Maybe someone be nice and wrap it in a tcl/tk gui program some day.  I dont care if someone wants to do that, go for it.

-HR

---

### Post by HolyRoses on 2010-03-04
updated main page with link to 5.3 script.   fixes bugs with audio channel mapping in mkv with certain files and other fixes/improvements, mainly to apple tv or surrounding it.

-HR

---

### Post by alberto2172 on 2010-04-28
hey holyroses thanks alot for the script!! well i installed ubuntu on my pc just so i can work with your encode handheld!! its sweet man.. well i still havent installed it but im looking at this forum and i see you showed how to install will take a look at that and try to install it by myself!! hopefully i dont fail!!! Thanx Alot HolyRose!!! <33 O:)

---

### Post by alberto2172 on 2010-04-29
hey holyroses!!! yeah i got it installed an im testing it out right now..! i just want to know hwo to adjust the proper width and height for the video output. i want to make to output to be capatible with the psp and the ipod touch. Thanx Alot!!! You Rule

---

### Post by HolyRoses on 2010-05-02
It automatically sets the width and height based on profile selected and of course input media.

use flags

-t psp -i

if you want a psp and ipod compatible encode.  It will be limited to 480x272 dimensions (max allowed dimensions for this profile type).

Just look at the help options  -h for the various profiles and options.  Not all options are needed for an encode, only a few.  You will likely only use a couple until you are familiar with it more.

There isn't any mode to just copy the source HxW, all profiles standardize the HxW to published specifications.


-HR

---

### Post by HolyRoses on 2010-05-02
Use this AtomicParsley

[http://bitbucket.org/wez/atomicparsley/overview](http://bitbucket.org/wez/atomicparsley/overview)

It has my changes to support the advanced features and tagging of encode-handheld.pl

-HR

---

### Post by alberto2172 on 2010-05-03
oh okay! thanks alot i got it working.. i just want to know one more things... srry im asking to many question.. :( well i want to know how i can change the ripper name..like poppedtart in TBP he has (c) copy right. Poppedtart. all rights reserved. is there a way i can change that?? thanx ALOT!!! your great. :D

---

### Post by alberto2172 on 2010-05-03
i tried to update encode-handheld-5.2.pl to verison 5.3 i did  " sudo mv encode-handheld-5.3.pl /usr/local/bin/"  it copied it to usr/local/bin/ but there are 2 encode-handheld.pl version 5.2 and 5.3 did i update it the right way or what are the commands to update.. THanx in advance

---

### Post by alberto2172 on 2010-05-07
okay.. thanks. i deleted the old version and changed the name of  ripper.. i also did the symoblic link. I updated my computer to version  10.04 ubuntu and i cant get encode-handheld to work it say file is  missing. this is the code i am useing " encode-handheld.pl -t psp -f  Over.avi" but it tell me this " jhead not found.  Comment in the PSP  thumbnail will remain.
This basically means the thumbail doesn't have a proper JPEG header.
Selected file: Over.avi
Defaulting frame rate to 23.976.
Defaulting threads to 0 (auto).
Selected Volume: No Change
Selected thumbnail time: 120
video dimensions = 600x320
video aspect ratio = 1.875
Selected type: psp
Selected naming: simple
Selected thumbnail type: Over.jpg
psp video dimensions = 480x256
psp video aspect ratio = 1.875
psp video height difference = 16 pixels
encoding file: Over.avi
output file = Over.m4v
FFmpeg version SVN-r23056, Copyright (c) 2000-2010 the FFmpeg developers
  built on May  7 2010 17:56:08 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree  --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad  --enable-libmp3lame --enable-libopencore-amrnb  --enable-libopencore-amrwb --enable-libtheora --enable-libx264  --enable-libxvid --enable-x11grab
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.67. 0 / 52.67. 0
  libavformat   52.62. 0 / 52.62. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'Over.avi':
  Metadata:
    ISFT            : VirtualDubMod 1.5.10.1 (build 2366/release)
  Duration: 01:23:16.74, start: 0.000000, bitrate: 1174 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 600x320 [PAR 1:1 DAR 15:8],  23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Please use vfilters=pad
Generating thumbnail for PSP.
Thumbnail height of 85 is odd, decreasing value.
thumb height is 84
thumb padding amount = 36
thumb pad top = 18
thumb pad bottom = 18
FFmpeg version SVN-r23056, Copyright (c) 2000-2010 the FFmpeg developers
  built on May  7 2010 17:56:08 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree  --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad  --enable-libmp3lame --enable-libopencore-amrnb  --enable-libopencore-amrwb --enable-libtheora --enable-libx264  --enable-libxvid --enable-x11grab
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.67. 0 / 52.67. 0
  libavformat   52.62. 0 / 52.62. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'Over.avi':
  Metadata:
    ISFT            : VirtualDubMod 1.5.10.1 (build 2366/release)
  Duration: 01:23:16.74, start: 0.000000, bitrate: 1174 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 600x320 [PAR 1:1 DAR 15:8],  23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Please use vfilters=pad
Setting iTunes atoms
AtomicParsley error: can't open  /home/alberto/Desktop/Handheld-Video/Over.m4v for reading: No such file  or directory
Displaying AtomicParsley text data
AtomicParsley error: can't open  /home/alberto/Desktop/Handheld-Video/Over.m4v for reading: No such file  or directory
AP error trying to fopen: No such file or directory "
  i triend everything i new but i cant get it to work.. i dont know whats going on?

---

### Post by HolyRoses on 2010-05-08
looks like the pad command was removed from ffmpeg

Please use vfilters=pad

and they want to use a new vfilters option.  Also means crop is likely broken.

No code is written to support those changes in ffmpeg.  You could downgrade your ffmpeg to a version that doesn't have that new code.  Something around this level SVN-r20562.  ffmpeg is in constant development and I don't follow it usually.

Ill have to compile a newer build of ffmpeg and see what they have changed.  I don't have a fix for you, shouldn't of upgraded...



this new option doesn't look nearly as powerful as the old options either.

you using like todays build of ffmpeg.

FFmpeg version SVN-r23056, Copyright (c) 2000-2010 the FFmpeg developers

use your old build files if you have them.

its going to be a major re-write to accommodate these changes.

---

### Post by FakeOutdoorsman on 2010-05-08
Looks like r23050 removed pad:
```
$ svn log -l 24 svn://svn.mplayerhq.hu/ffmpeg/trunk
------------------------------------------------------------------------
r23050 | michael | 2010-05-07 04:16:23 -0800 (Fri, 07 May 2010) | 3 lines

Remove messy pading hack in ffmpeg.c.
Use avfilters if you want padding!

------------------------------------------------------------------------
```

---

### Post by HolyRoses on 2010-05-08
Thanks FakeOutdoorsman.

Check out a revision of ffmpeg older than that then if you want to restore functionality until I recode the script or you could just remove all PAD references in the actual encode lines as a hack.

Use this command to checkout an older version and let me know if it works for you

svn co -r 23049 svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg

compile this one against your x264.

You should get in a habit of saving your old ffmpeg/x264 source code.  I just rename mine in case something goes bad and I can just reinstall the old.

Well I tried it, now you get these new errors

swScaler: Exactly one scaler algorithm must be chosen

I am guessing they want you to use

-vfilters "scale=200:100"

something like that, again these are pretty massive changes and would require re-engineering the whole script to work with their new logic.  sucks.

---

### Post by alberto2172 on 2010-05-08
okay. thanks alot. do i have to uninstall/remove the new version of ffmpeg?
Thanks in Advance

---

### Post by HolyRoses on 2010-05-08
you can just compile/install over it.

again there is something wrong with scaler options though if you just revert back to 23049.

So something else has changed and I haven't researched it.  Go back to whatever rev you were using that worked until I can figure out all the changes and new logic which there will probably have to be a ton of it.

Most of the logic in this script is in regard to scaling (sizing), cropping, padding, etc to exact sizes and AR's.  With all these changes it will take a lot of work to redo all that.

---

### Post by HolyRoses on 2010-05-08
I can rapidshare some older x264 and ffmpeg source code later if you don't have a working copy that is compatible with this.

---

### Post by FakeOutdoorsman on 2010-05-08
When you checkout a specific FFmpeg revision, I believe you have to also checkout an appropriate libswscale revision to match.  Otherwise libswscale will always checkout the latest revision and won't work with whatever FFmpeg -r you choose.

I may be wrong.

---

### Post by HolyRoses on 2010-05-08
no you are right.  i am not sure how to checkout a lower rev libswscale.

---

### Post by HolyRoses on 2010-05-08
alberto2172

I made a torrent for you that has the following 2 files in it.

ffmpeg-21221.tar.gz
x264-0.83.1391.tar.gz

These are the 2 binary sets I am using.

compile x264 with
./configure --enable-shared
make
make install
ldconfig

my ffmpeg is compiled like this
./configure --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libx264 --enable-zlib --enable-bzlib --enable-version3 --enable-libmp3lame --enable-libxvid --enable-libtheora --enable-libvorbis
make
make install
ldconfig


The torrent is here

[http://rapidshare.com/files/385138535/encode-handheld-5.3-tools-openbittorrent.torrent]("http://rapidshare.com/files/385138535/encode-handheld-5.3-tools-openbittorrent.torrent")

This should get you up and running fine.  It isn't the newest but will work 100% fine with full compatibility to encode-handheld.pl

Let me know if you get it working ok.


To make it even easier I compiled ffmpeg statically for you  can download it here

[http://rapidshare.com/files/385149602/ffmpeg-21221-linux-static-compiled.tar.gz]("http://rapidshare.com/files/385149602/ffmpeg-21221-linux-static-compiled.tar.gz")

just do this

gzip -dc ffmpeg-21221-linux-static-compiled.tar.gz | tar xvf -
cd ffmpeg-21221-linux-static-compiled
sudo mv * /usr/local/bin

done

-HR

---

### Post by alberto2172 on 2010-05-09
okay. HolyRose i worked the x264 you provided had to do it with sudo, would allow with out it. and for the ffmpeg torret it didnt work me so i used the ffmpeg statically one you provied (2nd torrent). i used the command you provied as well... 


the commands i used to encode a new video. are "encode-handheld.pl -t psp -f Precious.avi " for test .


it worked 
ill post a link to the picture so you can tell me if everything is working fine... Thanx Alot HolyRoses!!!

---

### Post by alberto2172 on 2010-05-09
here is the link to the shot of encode-handheld-5.2 running with ubuntu 10.04 with your help HolyRoses link is "http://i934.photobucket.com/albums/ad186/alberto2172/encode-handheld.png"

---

### Post by HolyRoses on 2010-05-09
looks fine.  you should use script version 5.3 though instead of 5.2.

You aren't using many options ;-)  add -i if you want it to be iPod compatible.

you can install jhead

sudo apt-get install jhead

save that statically linked ffmpeg, thats all you need, it already has x264 linked to it.  I used to pack ffmpeg linked like this in older revisions, might of even been included in 5.2 pack.

---

### Post by area51manah on 2010-05-27
Hello
i have installed x264,[SIZE=1]FFmpeg[/SIZE] by [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846")
[http://ubuntuforums.org/showpost.php?p=9114176&postcount=967](http://ubuntuforums.org/showpost.php?p=9114176&postcount=967)

then i copy encode-handheld-5.3.pl to usr/local/bin/
then i ran ./encode-handheld-5.3.pl [IMG]http://bayimg.com/fANAKaAcB[/IMG]
and ./encode-handheld-5.3.pl -h
but it says permission denied
m i doing something wrong

here is  the screen shots
[IMG]http://bayimg.com/fANAKaAcB[/IMG]
[http://bayimg.com/fANAKaAcB](http://bayimg.com/fANAKaAcB)

---

### Post by HolyRoses on 2010-05-27
chmod 755 /usr/local/bin/encode-handheld-5.3.pl

use the ffmpeg provided above, the static binary, otherwise it wont work for you.

---

### Post by area51manah on 2010-05-27
operation not permited
screens here
[http://bayimg.com/gaNabAaCB](http://bayimg.com/gaNabAaCB)

encode-handheld-5.2-with-ffmpeg-and-atomicparsley.tar.gz
i ve uninstalled ffmpeg
what should i do next :confused:
should i copy contents of ffmpeg-SVN-r20562 into usr/local/bin

please help me 

still chmod is not working 
help here 
:)

---

### Post by HolyRoses on 2010-05-27
do the very bottom part of post #99 (to make it even easier)


you need to use sudo on the chmod

sudo <stuff to do>

---

### Post by area51manah on 2010-05-27
hello again 
can you please select a profile which is both playable on my 3gs and psp (no idea which firmware) with around 500kbps
I read the post #1 i dont understand input and output file.
eg: want both inputs and outs on desktop

thanks
Godbless
:)


Hope these means Success
[http://bayimg.com/kANAOAacb](http://bayimg.com/kANAOAacb)



i was really curious and i got this 
[http://bayimg.com/mANANaacB](http://bayimg.com/mANANaacB)
as i ran the command it created a folder called "Handheld-Video"
file to encode is in desktop 
and i tried with the file inside the handheld-video folder but to no success
help :confused:

---

### Post by HolyRoses on 2010-05-27
You are missing a bunch of optional installs.

Your -c is bunched next to psp, your -o is missing an argument, the -i wont actually work because of the missing AtomicParsley.  your file name should be encapsulated with "double quotes" or a direct path, escaping spaces with backslash, such as /mypath/to/my/file/which\ is\ named\ such.avi

you should just run it from your home directory

as encode-handheld-5.3.pl

install jhead, install AtomicParsley from here [http://bitbucket.org/wez/atomicparsley/overview](http://bitbucket.org/wez/atomicparsley/overview)

you will have to compile it, unpack the source, change to unpacked folder,  run ./configure, run make, run sudo make install.  Though AP may be in the 5.2 bundle.

just run encode-handheld.pl -t psp -f "Desktop/myfilename.avi" -n "testing crap" -z 30

Just cuz there are lots of options doesn't mean you need to run em.  i'm sure all this has to be mentioned someplace in this thread.

---

### Post by HolyRoses on 2010-05-28
if this is your first time using linux then dont get too upset about things because its nothing like windows and you have a lot to learn.  I'll try to help you with this program, but I can't teach you linux.

---

### Post by area51manah on 2010-05-28
Well i was here before post #65 i stay around for a while now and **** it still going anywhere 
p.s windows spoiled me and hate it for that
 



./encode-handheld-5.3.pl -t psp -n "movie" -f "/home/houruoha/desktop/movie.avi"
and was a huge success
though it tooks a very long time, 2+ hours
my specs
AMD Turion x2, 4gb ram, Ati 3650

i havent check check whether Atomicparsley an jhead was a success 
With post#71
move AtomicParsley to  /usr/local/bin
From encode-handheld-5.2-with-ffmpeg-and-atomicparsley.tar.gz

im not sure whether its a success 
but 
ran 
sudo apt-get install jhead

---

### Post by HolyRoses on 2010-05-28
i dont know if that is a fast cpu or not.  try changing the threads from the default to like -m4 see if the encoding FPS goes up, if it does, then try -m6, etc.  With a new i7 cpu you can run 12 threads at once, its quite zippy ;-)  You can encode while you are sleeping then it wont take any time at all!  Setup a batch script to do like 5 at once if you like.

---

### Post by area51manah on 2010-05-30
well my processor is real crap?
and i would surely loved the batch script
:)

---

### Post by HolyRoses on 2010-05-30
just make a text file.  each line should have the complete line you would normally type on the command line

example:

encode-handheld.pl -t psp -i -f "/home/mylogin/Desktop/myvideo.avi" -n "my video"
encode-handheld.pl -t psp -i -f "/home/mylogin/Desktop/forest.avi" -n "my forest"
encode-handheld.pl -t psp -i -f "/home/mylogin/Desktop/yard.avi" -n "my yard"
encode-handheld.pl -t psp -i -f "/home/mylogin/Desktop/mydogs.avi" -n "my dogs"

save the file
execute the file by typing

example:

sh mysavedfilename.sh

you can just append -z 10 to each line to first test that it works (it will make 10 second encodes)

---

### Post by alberto2172 on 2010-06-06
heya holyroses!! well remember when encode-handheld didnt work for me well the reason why i only used a little options was because if i did more it would say that the file does not exist so i stayed with simple format. (: but i recently made a clean install of my computer and i installed everything and i wa suprise that everything worked out really well. but when i chose a video i get an " Invalid and inefficient vfw-avi packed B frames" im just curious if there is something wrong with this or is it okay to keep encodeing vidoes if i get this same things. like to the [http://i934.photobucket.com/albums/ad186/alberto2172/RememberMe.png]("http://i934.photobucket.com/albums/ad186/alberto2172/RememberMe.png")
[IMG]http://i934.photobucket.com/albums/ad186/alberto2172/RememberMe.png[/IMG] 

thanks in advance !!! (:

---

### Post by HolyRoses on 2010-06-07
Its common to see that in avi files.  they dont support B frames far as I know and people made a hack to make b frames work.  ffmpeg is just complaining about your avi file, it will still be fine.

---

### Post by alberto2172 on 2010-06-26
hey HOLYROSES!!! man well just wanted to say HI! (: and thanks for the applications you created "encode-handheld!" it is so awsome man i already know how to encode movies for ipod psp and zune (: man :') its so great! man and well hope that one day you will return back!! to encodeing movies!!


long live HOLYROSES!!!;-)

---

### Post by HolyRoses on 2010-06-26
Well glad you are liking it.  Try the various options.  Might release a slight update soon.

---

### Post by alberto2172 on 2010-06-27
man i do like it i love it!!! (: i do have a question see. i want my videos to have better quality so i download vidoes that are HD like 1080p or 720p but i dont know if there might be a audio problem since HD have more than one audio.... idk if there is a problem or not like it is okay to encode normal.... or do i have to do something... hope you can advise me.

Thanx in Advance HolyRoses! (:

---

### Post by alberto2172 on 2010-06-27
man i hope you make it so we can encode .mkv files!!! (:

---

### Post by alberto2172 on 2010-06-28
heya holyroses... i was encodeing a movie which is 1080p and i got a problem i cant really exaplain what happened but i thinks it the video source. when i typed the commands in there was one error which said something about the audio have 6 channels and it cant encode them..  ill post a picture of it.. [IMG]http://i934.photobucket.com/albums/ad186/alberto2172/Encode%20Handheld/ThePrincessAndTheFrog.png?t=1277737625[/IMG]

Thanx in Advance :p

---

### Post by alberto2172 on 2010-06-28
this is the code that come outs. " ```
albert@ubuntu:~$ cd Desktop
albert@ubuntu:~/Desktop$ encode-handheld.pl -t psp -pi -f "The Princess And The Frog.mp4"
jhead not found.  Comment in the PSP thumbnail will remain.
This basically means the thumbail doesn't have a proper JPEG header.
Selected file: The Princess And The Frog.mp4
Defaulting frame rate to 23.976.
Defaulting threads to 0 (auto).
Selected Volume: No Change
Selected thumbnail time: 120
video dimensions = 1280x720
video aspect ratio = 1.77777777777778
Selected type: psp
Selected naming: simple
Selected thumbnail type: The Princess And The Frog.jpg
psp video dimensions = 480x270
psp video aspect ratio = 1.77777777777778
psp video height difference = 2 pixels
encoding file: The Princess And The Frog.mp4
output file = The Princess And The Frog.m4v
FFmpeg version SVN-r20562, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 21 2009 14:51:30 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libdc1394 --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-libspeex --enable-libopenjpeg --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-bzlib --enable-static --disable-shared --extra-libs=-static --extra-cflags=--static
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (66893/1395) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'The Princess And The Frog.mp4':
  Duration: 01:37:27.74, start: 0.000000, bitrate: 2158 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 1899 kb/s, 23.98 tbr, 66893 tbn, 47.95 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 6 channels, s16, 254 kb/s
  Metadata
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
[libx264 @ 0x9824d20]using SAR=1/1
[libx264 @ 0x9824d20]using cpu capabilities: MMX2 SSE2 SSE3 Cache64
[libx264 @ 0x9824d20]profile Baseline, level 2.1
Output #0, psp, to '/home/albert/Desktop/Handheld-Video/The Princess And The Frog.m4v':
    Stream #0.0(und): Video: libx264, yuv420p, 480x270 [PAR 1:1 DAR 16:9], q=10-51, pass 1, 384 kb/s, 24k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 2 channels, s16, 128 kb/s
  Metadata
    title           : My Video
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Resampling with input channels greater than 2 unsupported.
Can not resample 6 channels @ 48000 Hz to 2 channels @ 48000 Hz
FFmpeg version SVN-r20562, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 21 2009 14:51:30 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libdc1394 --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-libspeex --enable-libopenjpeg --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-bzlib --enable-static --disable-shared --extra-libs=-static --extra-cflags=--static
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (66893/1395) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'The Princess And The Frog.mp4':
  Duration: 01:37:27.74, start: 0.000000, bitrate: 2158 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 1899 kb/s, 23.98 tbr, 66893 tbn, 47.95 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 6 channels, s16, 254 kb/s
  Metadata
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
[libx264 @ 0xa794d20]using SAR=1/1
[libx264 @ 0xa794d20]using cpu capabilities: MMX2 SSE2 SSE3 Cache64
[libx264 @ 0xa794d20]ratecontrol_init: can't open stats file
Output #0, psp, to '/home/albert/Desktop/Handheld-Video/The Princess And The Frog.m4v':
    Stream #0.0(und): Video: libx264, yuv420p, 480x270 [PAR 1:1 DAR 16:9], q=10-51, pass 2, 384 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 2 channels, s16, 128 kb/s
  Metadata
    title           : My Video
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
Generating thumbnail for PSP.
thumb height is 90
thumb padding amount = 30
The thumb padtop: 15 is odd. Increasing value, decreasing padbottom.
thumb pad top = 16
thumb pad bottom = 14
FFmpeg version SVN-r20562, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 21 2009 14:51:30 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libdc1394 --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-libspeex --enable-libopenjpeg --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-bzlib --enable-static --disable-shared --extra-libs=-static --extra-cflags=--static
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (66893/1395) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'The Princess And The Frog.mp4':
  Duration: 01:37:27.74, start: 0.000000, bitrate: 2158 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 1899 kb/s, 23.98 tbr, 66893 tbn, 47.95 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 6 channels, s16, 254 kb/s
  Metadata
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
Output #0, image2, to '/home/albert/Desktop/Handheld-Video/The Princess And The Frog.jpg':
    Stream #0.0(und): Video: mjpeg, yuvj420p, 160x120 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    1 fps=  0 q=3.7 Lsize=      -0kB time=0.04 bitrate=  -4.2kbits/s    its/s    
video:6kB audio:0kB global headers:0kB muxing overhead -100.369251%
Setting iPod 5g high res iTunes atom
Setting iTunes atoms

AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).

Displaying AtomicParsley text data

AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).
```

thats what happens i can also give u the movie spec...

---

### Post by alberto2172 on 2010-06-28
Movie Info: 
```
General
Complete name                    : C:\Users\User\Downloads\The Princess And The Frog 2009 BRRip H264 AAC-SecretMyth (Kingdom-Release)\The Princess And The Frog.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 1.47 GiB
Duration                         : 1h 37mn
Overall bit rate                 : 2 159 Kbps
Encoded date                     : UTC 2010-02-26 00:11:23
Tagged date                      : UTC 2010-02-26 00:11:23

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 7 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1h 37mn
Bit rate mode                    : Variable
Bit rate                         : 1 900 Kbps
Maximum bit rate                 : 13.2 Mbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate mode                  : Constant
Frame rate                       : 23.976 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.086
Stream size                      : 1.29 GiB (88%)
Writing library                  : x264 core 88 r1462 7fcffde
Encoding settings                : cabac=1 / ref=8 / deblock=1:-1:-1 / analyse=0x3:0x113 / me=umh / subme=9 / psy=1 / psy_rd=1.00:1.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-4 / threads=3 / sliced_threads=0 / slices=4 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=4 / b_pyramid=1 / b_adapt=2 / b_bias=0 / direct=1 / wpredb=1 / wpredp=2 / keyint=300 / keyint_min=1 / scenecut=40 / intra_refresh=0 / rc_lookahead=60 / rc=2pass / mbtree=1 / bitrate=1900 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / vbv_maxrate=40000 / vbv_bufsize=30000 / ip_ratio=1.40 / aq=1:1.00
Encoded date                     : UTC 2010-02-25 12:48:02
Tagged date                      : UTC 2010-02-26 00:12:23

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 1h 37mn
Bit rate mode                    : Variable
Bit rate                         : 255 Kbps
Maximum bit rate                 : 358 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Rear: L R, LFE
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 178 MiB (12%)
Language                         : English
Encoded date                     : UTC 2010-02-26 00:12:10
Tagged date                      : UTC 2010-02-26 00:12:23
```

hope this helps

---

### Post by HolyRoses on 2010-06-30
the problem is due to your source file having 6 channel AAC audio.  ffmpeg cannot downmix 6 channel AAC to 2 channel AAC.  it is a limitation.

Use MKV file sources with AC3 or DTS audio and use option -M (will require you have mkvmerge, mkvextract installed and a52dec and dcadec).  If you do not use option -M and have mkv source and dts audio then your stereo track will be created improperly.

I don't think there will be any option ever made to create mkv file.  MKV requires more overhead to process and isn't supported on apple products and that is the main intent of this tool.

-HR

---

### Post by alberto2172 on 2010-08-31
hey holyroses i did what you told me about .mkv sources and i think its going okay i used this  code to coverte a movie ```
encode-handheld-5.3.pl -t psp -pi -f "21-The Movie.mkv" -N "21" -n "21" -M -k Albert -C twenty_one.jpg -d ""21" is the fact-based story about six MIT students who were trained to become experts in card counting and subsequently took Vegas casinos for millions in winnings." -D ""21" is the fact-based story about six MIT students who were trained to become experts in card counting and subsequently took Vegas casinos for millions in winnings." -y 2008 -q PG-13 -e Action
```

this is the MKV source info 

```
albert@albert-desktop:~$ mediainfo '/media/Local Disk/New Movies/21-The Movie.mkv' General
Complete name                    : /media/Local Disk/New Movies/21-The Movie.mkv
Format                           : Matroska
File size                        : 2.18 GiB
Duration                         : 2h 2mn
Overall bit rate                 : 2 548 Kbps
Encoded date                     : UTC 2010-08-12 18:10:17
Writing application              : mkvmerge v4.1.1 ('Bouncin' Back') &#32534;&#35793;&#20110; Jul  3 2010 22:54:08
Writing library                  : libebml v1.0.0 + libmatroska v1.0.0

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Muxing mode                      : Container profile=Unknown@4.1
Codec ID                         : V_MPEG4/ISO/AVC
Duration                         : 2h 2mn
Bit rate                         : 2 100 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.095
Stream size                      : 1.76 GiB (80%)
Writing library                  : x264 core 98 r1649 c54c47d
Encoding settings                : cabac=1 / ref=4 / deblock=1:-1:-1 / analyse=0x3:0x113 / me=umh / subme=6 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=6 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=3 / weightb=1 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=2pass / mbtree=1 / bitrate=2100 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / vbv_maxrate=50000 / vbv_bufsize=50000 / ip_ratio=1.40 / aq=1:1.00 / nal_hrd=none

Audio
ID                               : 2
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : A_AC3
Duration                         : 2h 2mn
Bit rate mode                    : Constant
Bit rate                         : 448 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Side: L R, LFE
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Stream size                      : 393 MiB (18%)
Title                            : &#33521;&#35821;

Text #1
ID                               : 3
Format                           : SSA
Codec ID                         : S_TEXT/SSA
Codec ID/Info                    : Sub Station Alpha
Title                            : &#20013;&#33521;&#23383;&#24149;

Text #2
ID                               : 4
Format                           : SSA
Codec ID                         : S_TEXT/SSA
Codec ID/Info                    : Sub Station Alpha
Title                            : &#33521;&#20013;&#23383;&#24149;

Text #3
ID                               : 5
Format                           : UTF-8
Codec ID                         : S_TEXT/UTF8
Codec ID/Info                    : UTF-8 Plain Text
Title                            : &#20013;&#25991;&#23383;&#24149;

Text #4
ID                               : 6
Format                           : UTF-8
Codec ID                         : S_TEXT/UTF8
Codec ID/Info                    : UTF-8 Plain Text
Title                            : &#33521;&#25991;&#23383;&#24149;
```

and this is how encode-handheld is handeling it tell me if its okay :) thanks 

encode-handheld-5.3.pl 

```
albert@albert-desktop:~$ cd /media/"Local Disk"/"New Movies"albert@albert-desktop:/media/Local Disk/New Movies$ encode-handheld-5.3.pl -t psp -pi -f "21-The Movie.mkv" -N "21" -n "21" -M -k Albert -C twenty_one.jpg -d ""21" is the fact-based story about six MIT students who were trained to become experts in card counting and subsequently took Vegas casinos for millions in winnings." -D ""21" is the fact-based story about six MIT students who were trained to become experts in card counting and subsequently took Vegas casinos for millions in winnings." -y 2008 -q PG-13 -e Action
Selected file: 21-The Movie.mkv
Selected poster artwork file: twenty_one.jpg
Choosing to extract audio from Matroska files
Defaulting frame rate to 23.976.
Defaulting threads to 0 (auto).
Selected title: 21
Selected Volume: No Change
Selected thumbnail time: 120
video dimensions = 1280x720
video aspect ratio = 1.77777777777778
Selected type: psp
Selected naming: modified title
Selected thumbnail type: 21.jpg
psp video dimensions = 480x270
psp video aspect ratio = 1.77777777777778
psp video height difference = 2 pixels
encoding file: 21-The Movie.mkv
output file = 21.m4v
FFmpeg version SVN-r20562, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 21 2009 14:51:30 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libdc1394 --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-libspeex --enable-libopenjpeg --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-bzlib --enable-static --disable-shared --extra-libs=-static --extra-cflags=--static
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x8f8baa0]max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (27956/583) -> 23.98 (24000/1001)
Input #0, matroska, from '21-The Movie.mkv':
  Duration: 02:02:41.40, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 6 channels, s16
    Stream #0.2: Subtitle: 0x0000
    Stream #0.3: Subtitle: 0x0000
    Stream #0.4: Subtitle: 0x0000
    Stream #0.5: Subtitle: 0x0000
[libx264 @ 0x8feb7c0]using SAR=1/1
[libx264 @ 0x8feb7c0]using cpu capabilities: MMX2 SSE2 SSE3 Cache64
[libx264 @ 0x8feb7c0]profile Baseline, level 2.1
Output #0, psp, to '/home/albert/Desktop/Handheld-Video/21.m4v':
    Stream #0.0(eng): Video: libx264, yuv420p, 480x270 [PAR 1:1 DAR 16:9], q=10-51, pass 1, 384 kb/s, 24k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 2 channels, s16, 128 kb/s
  Metadata
    title           : 21
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Press [q] to stop encoding
[matroska @ 0x8f8baa0]Invalid stream 6 or size 38.34 bitrate= 724.6kbits/s    /s
frame=17486 fps=21 q=26.0 size=45659 time= 762.89 bitrate=497.9kbits/s
```

hope you can tell me if im doing this right! Thanks alot man

---

### Post by HolyRoses on 2010-09-02
seems alright.  might need to escape the quote marks that are inside quotes.  like -d "this has \"quotes\" and may need to be escaped"

if in doubt just do 30 second encodes -z 30 see what happens.

---

### Post by alberto2172 on 2010-09-05
i get his error for this movie 


```
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 20 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 21 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 20 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 21 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 20 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 21 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 20 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
    Last message repeated 21 times
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[h264 @ 0x989ef00]AVC: nal size 0
[h264 @ 0x989ef00]no frame!
Error while decoding stream #0.0
[aac @ 0x989f690]channel element 0.0 is not allocated
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
Error while decoding stream #0.1
```

---

### Post by alberto2172 on 2010-09-05
This is the movie info for the error message above 

```
albert@albert-desktop:~$ mediainfo '/media/Local Disk/New Movies/Wonder Woman.mp4' General
Complete name                    : /media/Local Disk/New Movies/Wonder Woman.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 701 MiB
Duration                         : 1h 13mn
Overall bit rate                 : 1 330 Kbps
Encoded date                     : UTC 2009-03-04 08:15:01
Tagged date                      : UTC 2009-03-04 08:15:01

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1h 13mn
Bit rate mode                    : Variable
Bit rate                         : 1 212 Kbps
Maximum bit rate                 : 7 676 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate mode                  : Constant
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.055
Stream size                      : 643 MiB (92%)
Writing library                  : x264 core 66 r1115M 11863ac
Encoding settings                : cabac=1 / ref=4 / deblock=1:0:0 / analyse=0x1:0x111 / me=hex / subme=8 / psy_rd=1.0:0.0 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=3 / nr=0 / decimate=1 / mbaff=0 / bframes=4 / b_pyramid=0 / b_adapt=2 / b_bias=0 / direct=1 / wpredb=1 / keyint=250 / keyint_min=25 / scenecut=40(pre) / rc=abr / bitrate=1212 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.40 / pb_ratio=1.30 / aq=1:1.00
Encoded date                     : UTC 2009-03-03 22:48:52
Tagged date                      : UTC 2009-03-04 08:15:48

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 1h 13mn
Bit rate mode                    : Variable
Bit rate                         : 107 Kbps
Maximum bit rate                 : 145 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Stream size                      : 56.3 MiB (8%)
Encoded date                     : UTC 2009-03-04 08:15:46
Tagged date                      : UTC 2009-03-04 08:15:48


albert@albert-desktop:~$
```

---

### Post by HolyRoses on 2010-09-05
sounds like a junk source file.  or a poorly encoded source file.

---

### Post by alberto2172 on 2010-09-08
hey holyroses i want to encode this movie Shrek The Third and i check the source and i did convert it but there was just one problem that happened and that was with the output audio the source was .mkv file and had multiple audio

and audio #1 was in dutch so i guess that the audio for my output came in dutch. Is there a way i can use the second audio instead of the first one? 

```
albert@albert-desktop:~$ mediainfo '/media/Local Disk/New Movies/Shrek the Third.mkv' General
Complete name                    : /media/Local Disk/New Movies/Shrek the Third.mkv
Format                           : Matroska
File size                        : 7.38 GiB
Duration                         : 1h 32mn
Overall bit rate                 : 11.4 Mbps
Encoded date                     : UTC 2010-08-08 09:43:34
Writing application              : mkvmerge v3.3.0 ('Language') built on Mar 24 2010 14:59:24
Writing library                  : libebml v0.8.0 + libmatroska v0.9.0

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Muxing mode                      : Container profile=Unknown@4.1
Codec ID                         : V_MPEG4/ISO/AVC
Duration                         : 1h 32mn
Bit rate                         : 8 366 Kbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16:9
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.168
Stream size                      : 5.42 GiB (74%)
Title                            : x264
Writing library                  : x264 core 65 r1028M 83baa7f
Encoding settings                : cabac=1 / ref=4 / deblock=1:1:0 / analyse=0x3:0x113 / me=umh / subme=9 / psy_rd=1.0:0.0 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=6 / nr=0 / decimate=0 / mbaff=0 / bframes=5 / b_pyramid=1 / b_adapt=2 / b_bias=0 / direct=3 / wpredb=1 / keyint=250 / keyint_min=25 / scenecut=40(pre) / rc=crf / crf=17.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / vbv_maxrate=38000 / vbv_bufsize=30000 / ip_ratio=1.40 / pb_ratio=1.30 / aq=0
Language                         : English

Audio #1
ID                               : 2
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : A_AC3
Duration                         : 1h 32mn
Bit rate mode                    : Constant
Bit rate                         : 640 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Side: L R, LFE
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Stream size                      : 425 MiB (6%)
Title                            : AC3
Language                         : Dutch

Audio #2
ID                               : 3
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : A_AC3
Duration                         : 1h 32mn
Bit rate mode                    : Constant
Bit rate                         : 640 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Side: L R, LFE
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Stream size                      : 425 MiB (6%)
Title                            : AC3
Language                         : English

Audio #3
ID                               : 4
Format                           : DTS
Format/Info                      : Digital Theater Systems
Codec ID                         : A_DTS
Duration                         : 1h 32mn
Bit rate mode                    : Constant
Bit rate                         : 1 510 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Side: L R, LFE
Sampling rate                    : 48.0 KHz
Bit depth                        : 24 bits
Stream size                      : 1 002 MiB (13%)
Title                            : DTS
Language                         : English

Text #1
ID                               : 5
Format                           : UTF-8
Codec ID                         : S_TEXT/UTF8
Codec ID/Info                    : UTF-8 Plain Text
Title                            : Subtitles
Language                         : Dutch

Text #2
ID                               : 6
Format                           : UTF-8
Codec ID                         : S_TEXT/UTF8
Codec ID/Info                    : UTF-8 Plain Text
Title                            : Subtitles
Language                         : English

Menu
00:00:00.000                     : en:00:00:00.000
00:03:21.910                     : en:00:03:21.910
00:09:33.031                     : en:00:09:33.031
00:13:49.370                     : en:00:13:49.370
00:17:29.340                     : en:00:17:29.340
00:25:13.887                     : en:00:25:13.887
00:32:14.099                     : en:00:32:14.099
00:38:33.728                     : en:00:38:33.728
00:41:15.014                     : en:00:41:15.014
00:49:13.576                     : en:00:49:13.576
00:51:53.235                     : en:00:51:53.235
00:56:49.156                     : en:00:56:49.156
00:59:22.309                     : en:00:59:22.309
01:03:28.263                     : en:01:03:28.263
01:07:06.272                     : en:01:07:06.272
01:10:29.183                     : en:01:10:29.183
01:19:42.277                     : en:01:19:42.277
01:22:22.771                     : en:01:22:22.771
01:32:45.852                     : en:01:32:45.852


albert@albert-desktop:~$
```

---

### Post by alberto2172 on 2010-10-11
hello does anyone here now how to change the audio track that encode-handheld uses..lets say i have MKV sourve fill to encode. i dont want to use the  first audio track in the file for my encode. i want to use a different track lets say track 3 which is spanish. (just a example)... i have taken a look at encode-handheld script and found  this  ```
# I know this is hackey, shut it.
		# should be in the main match, but I no longer know how backwards compatible
		# ffmpeg is and this output line is.
		# this is only used for MKV files which do not have the video track as track 0
		if ( /Stream #(\d+)\.(\d+)/ ) {
			$video_source = $1;
			$video_track = $2;
```

should i change $video_track = $2 to different number like "$3" or something else??

---

### Post by HolyRoses on 2010-10-11
remux the mkv using the mkvtoolnix gui and reorder the tracks...  simpliest probably.   there are ways of doing it, but it will require me giving you some hackey code.

---

### Post by alberto2172 on 2010-10-11
alrite thanks alot! :) will try mkvtoolnix... is there a way i can try the code? i would like to see how it does.

---

### Post by alberto2172 on 2010-10-14
hey thanks alot i tried the mkvtoolnix and it worked amazing :) it make me change the track and was quite fast! thanks alot holyroses!

---

### Post by HolyRoses on 2010-10-14
glad that worked.

in order to fix it correctly i would have to code track handling options.  basically new 2 new options to specify video and audio track.  its not difficult, but i am running out of damn letters to use for options...


I have always just hacked at the code and modified audio_string


                # A couple map examples for DVD's
                #
                # Not another Teen Movie DVD
                #$audio_string = "-map 0.$video_track -map 0.4 -acodec $acodec -ab $abitrate -ac 2 -ar 48000 -alang $audio_lang";
                # Tommy Boy DVD & Cop Out DVD
                #$audio_string = "-map 0.$video_track -map 0.2 -acodec $acodec -ab $abitrate -ac 2 -ar 48000 -alang $audio_lang";

you can see these 2 example strings remap to use a different audio track.  basically just needs track handler made for $audio_track.

-HR

---

### Post by johnncappleseed on 2010-10-19
Holyroses,

First I would like to thank you for sharing your great wisdom, love your work.  I am using Mac OSX 10.6.4 and I am able to encode successfully with one minor drawback...no Dolby Digital 5.1 audio? I am using a source file of 720p .mkv ? What am I doing wrong?  Please help.  Thanks again for all your work!!

---

### Post by HolyRoses on 2010-10-19
If using encode-handheld.pl v5.3 and source MKV then specify these options at minimum.

-t appletv -M

It should automatically create you a 384Kbs DD track.  If you used -n "my new movie"  you should have a "my new movie.ac3".  You will then have to manually mux the DD audio using subler.

Right click on created .m4v file and select open with Subler.  Rename the first audio track to "Stereo".  Drag created AC3 track into Subler and rename it to "Dolby Digital" AND change the language to English.  Now save (command S) when all done adding new tracks.

You need unique handler names per track that is the same language, that is why we are calling one Stereo and one Dolby Digital.  At this point you can also add a .srt subtitle.  The subtitle I have found has to be unix formatted.  For carriage returns it cannot have CRLF, just LF.  If you extract a subtitle from MKV (mkvextract tracks whatever.mkv 3:mynewsub.srt) it will 99.9% be UNIX format.  However if you now edit the file on a PC with Aegisub and save it on a PC it will have CRLF formatting and will not import into Subler correctly (at least in my experience).  On a linux box you can run dos2unix, on mac you can install it from darwin ports

[http://dos2unix.darwinports.com/]("http://dos2unix.darwinports.com/")


I should just create a perl script to do this change as well, but haven't gotten to it.  One of these days i'll just make a tarball of my /usr/local/ and you can use it on any mac, will have all of my binaries.

Any standard Apple TV movie encode should use these options on a i7 cpu if source MKV

-t appletv -pbM -m12 -w 0093433 -f "my movie to encode.mkv"  -C "my movie poster.jpg" -n "blah movie" -N "blah movie (HD)" -q R -d "my description" -D "my long description optional" -y "my release date" -e genre

for ipod/psp use -t psp -piM

change -m and -w as applicable.  make sure to use -w to enable stacking.  for TV change -n "True Blood s03e12" -N "Episode name"

hopefully these options are correct as i'm recalling from memory as i'm at work.  encode-handheld.pl -h

---

### Post by johnncappleseed on 2010-10-19
Thank you for your quick reply and I will most certainly try that option when I get home.  I am encoding for an appletv 2.0 and here is what I was using.
 
encode-handheld-5.3.pl -t appletv -pbI -f "/users/path/downloads/movie.mkv" -n "Movie" -N "The Movie" -y 2010 -q R -e Action -d "The Movie Plot."  So I will try your recommendation to improve!!
 
Could you please explain on this string though: -w 0093433 ? Don't seem to be in the help file?  That would be great on the script or even the tarball..

---

### Post by HolyRoses on 2010-10-19
-w num    : iTunes Catalog ID number (suggest using [http://www.imdb.com/](http://www.imdb.com/) numbers)

its for stacking of sd/hd content.  In iTunes it will be treated as one entry.

you make one SD universal ipod encode (-t ipoddvd for instance) and one HD encode.  They will show up as SD/HD in itunes on one line.  When you sync to ipod it will automatically sync the highest version compatible with your device.

You dont have to specify -N if you already specified -n.  the value from -n will populate -N automatically if not specified.  its main purpose is for TV shows or if you are queuing multiple encodes of same name then specify different -N.  This isn't important though, just noting it for you.

Use date strings from IMDB, not generic 2010.  Also use date string for tv episode of when it air.  It populates fields better.

If encode for self you can skip -p you may not even notice a difference between 1 and 2 pass and it will be much quicker.  If encoding for mass release probably best run -p (2 pass).  I'm guessing most people wouldn't even know difference anyhow...

If encode from MKV that has DTS audio you must use -M because the ffmpeg downmix from dts to 2 channel is broken and you will have incorrect channel assignments.  With -M the audio is extracted and converted on the fly to DD and then processed by ffmpeg for the stereo track (least I think it is, been a while since I write routine).

---

### Post by HolyRoses on 2010-10-19
Rapidshare link to 5.4 and create torrents script.  Torrents script will require BitTornado-CVS in /usr/local/bin or transmissioncli  refer to script for details.

[create-torrents-1.0a and encode-handheld-5.4]("http://rapidshare.com/files/426071137/create-torrents-1.0a.and.encode-handheld-5.4.tar.gz")

to install:

cd /usr/local/bin
sudo gzip -dc ~/Desktop/create-torrents-1.0a.and.encode-handheld-5.4.tar.gz | tar xvf -

Main difference in encoder from 5.3 to 5.4 is creation of Dolby Pro Logic II 2 channel tracks vs pure stereo. Also some sanity checks.


Change these lines:

grep HolyRoses /usr/local/bin/encode-handheld.pl | egrep -v \(Written\|^#\)
$ripper = "HolyRoses";
$account_name = 'HolyRoses@mac.com';

grep HolyRoses /usr/local/bin/create-torrents.pl |egrep -v \(Written\|^#\)
$comment = "A HolyRoses Production";

---

### Post by johnncappleseed on 2010-10-19
Okay, yes subler works great and now I also have Dolby 5.1!!! On TV shows how can I get it to display proper air date -y "10/19/10" ??  

This is getting pretty exciting figuring all this out? btw just learned unix commands over the weekend in about a few hrs!!

---

### Post by HolyRoses on 2010-10-19
requires real date strings.  have fun with the unix stuff.

TB example

encode-handheld-5.4.pl -m12 -t appletv -pbMS -w 300000012 -f /Users/bigdog/Desktop/Share/true.blood.s03e12.720p.hdtv.x264-something.mkv -C /Users/bigdog/Desktop/Posters/True\ Blood\ Season\ 3\ Artwork.jpg -e "Sci-Fi & Fantasy" -q TV-MA -N "Evil Is Going On" -d "Eric plots his revenge against Russell; Sookie considers a new life without Bill; Tara discovers some surprising news about Sam; Jason finds a new calling; Lafayette turns to Jesus for help; Hoyt hopes for a future with Jessica." -y "August 12, 2010 9pm EST" -n "True Blood s03e12"

if you are doing a complete series just make a batch file that has 12 unique lines to it (provided series has 12 ep)  In this example I forced a stereo downmix with -S.

---

### Post by HolyRoses on 2010-10-19
simple dos2unix with perl

[http://technocage.com/~caskey/dos2unix/]("http://technocage.com/~caskey/dos2unix/")

The simplest perl script is this one: perl -pi -e 's/\r\n/\n/;' *.srt

This does the reverse: perl -pi -e 's/\n/\r\n/;' *.srt


tried it, seems to work.

---

### Post by johnncappleseed on 2010-10-20
All working now!! Thank you !!  Now trying to do a shell script to more automate the process but keep getting a font error or something along those lines?  Also still having trouble understanding how -w 300000012 works?  You are a great teacher Holyroses...

---

### Post by HolyRoses on 2010-10-20
Try the following 10 second encode example.  Notice the only values changing are (-t appletv) with (-t psp -i) and (-n "filename (HD)") and (-n "filename (PiZ)") all other values remain identical, same file, same artwork, same meta data.  catalog number is a number I simply made up in this example.  It is a unique number that you have never used before and if you publish on internet hopefully apple hasn't used before or some other encoder hasn't used before.  For movies I suggest using imdb number.  For TV show pick a range and stick to it. If you use duplicate numbers for different material you will have stacking issues.  When encode finishes drag both items to iTunes.  You will see they are now stacked and have a SDHD icon.  You would never use this catalog number again for different material.  Each video has unique catalog number.  Your next video increment catalog value by 1.

encode-handheld.pl -m12 -t appletv -w 310000001 -f /path/video.avi -C /path/artwork.jpg -e "Action" -q R -N "Name" -d "description" -y "August 12, 2010 9pm EST" -n "filename (HD)" -z 10
encode-handheld.pl -m12 -t psp -i -w 310000001 -f /path/video.avi -C /path/artwork.jpg -e "Action" -q R -N "Name" -d "description" -y "August 12, 2010 9pm EST" -n "filename (PiZ)" -z 10

-HR

---

### Post by johnncappleseed on 2010-10-20
oh okay....I got you now, I understand!  Could you please put up a sample of a sh script that I can edit and try I keep getting a font error or something like that?  Do you have to launch from /usr/local/bin/encode.sh ?  because if I place there then I can't edit, right?

---

### Post by HolyRoses on 2010-10-20
ghett0 script makin below (you prolly want to use a text editor):

```
[userid@hostname:~]$ mkdir ~/Desktop
[userid@hostname:~]$ echo '#!/bin/sh' > ~/Desktop/encode-stuff.sh
[userid@hostname:~]$ echo "encode-handheld.pl -lots of crappy options" >> ~/Desktop/encode-stuff.sh
[userid@hostname:~]$ echo "encode-handheld.pl -lots of crappy options" >> ~/Desktop/encode-stuff.sh
[userid@hostname:~]$ echo "encode-handheld.pl -lots more crappy stuff" >> ~/Desktop/encode-stuff.sh
[userid@hostname:~]$ chmod 755 ~/Desktop/encode-stuff.sh
[userid@hostname:~]$ cd ~/Desktop
[userid@hostname:~/Desktop]$ cat encode-stuff.sh
#!/bin/sh
encode-handheld.pl -lots of crappy options
encode-handheld.pl -lots of crappy options
encode-handheld.pl -lots more crappy stuff
[userid@hostname:~/Desktop]$ ls -ld encode-stuff.sh
-rwxr-xr-x   1 userid userid     139 Oct 20 22:05 encode-stuff.sh
[userid@hostname:~/Desktop]$ ~/Desktop/encode-stuff.sh
/home/userid/Desktop/encode-stuff.sh: encode-handheld.pl: not found
/home/userid/Desktop/encode-stuff.sh: encode-handheld.pl: not found
/home/userid/Desktop/encode-stuff.sh: encode-handheld.pl: not found

```

---

### Post by johnnycappleseed on 2010-10-21
Sh Script is Awesome I say.....and I added a .command on the end and now I can launch by just double clicking!

Any way we can more automate the adding of the Dobly Digital 5.1 track ?  Would be awesome to add a gui!!

---

### Post by HolyRoses on 2010-10-21
I'm sure it could be done.  There are some other tools that let you manipulate track data.

[http://mp4v2.googlecode.com/svn/doc/1.9.0/ToolGuide.html]("http://mp4v2.googlecode.com/svn/doc/1.9.0/ToolGuide.html")

`--hdlrname STR' this is useful bit.

Competitor to atomicparsley.  I submit code to AP so that's all i really support.

Subler also has a command line version but I have never bothered to learn how to use it.  Plus I use a really old version of it because upgrading gave me issues.

So yes I'm sure the hooks could be written.  Is it on my todo list? no.

Learn perl coding and hack away.  Make any good improvements post em.

---

### Post by johnnycappleseed on 2010-10-22
been playing around with sublercli but unless i'm missing something it only supports -s subtitle.srt?
ex: sublercli -i movie.m4v (need a way to add dolby.ac3) -n Dolby Digital 5.1 -l English
Would be great if we could script this!  Let me know if you could get a chance to take a peek?[http://code.google.com/p/subler/wiki/SublerCLIHelp](http://code.google.com/p/subler/wiki/SublerCLIHelp)

---

### Post by HolyRoses on 2010-10-22
Looks like it support chapter and subtitle only as inputs (based on that usage page).  Seems like it should accept any sort of track input.

I suggest you work with the developer damiog if you need more features added to that program.  This isn't on my radar to code, but easy enough to add additional lines to a batch file if another external program supports what you are trying to do.

---

### Post by johnnycappleseed on 2010-10-22
Trying to implement +o 10 switch on this argument.
  
encode-handheld.pl -m12 -t appletv -pbM -f "/users/john/downloads/the.vampire.diaries.s02e06.720p..mkv" -C "/users/john/pictures/posters/thevampirediaries.jpg" -e "Sci-Fi & Fantasy 
" -q TV-14 -N "Plan B" -D "Despite Elena&#8217;s efforts to keep Jeremy safe, he offers to help Damon and Alaric deal with Katherine. Sheriff Forbes and Caroline share a few rare moments of quality mother/daughter time. Bonnie accidentally discovers new information about Mason and shares it with Stefan, leading Damon to take matters into his own hands." -y "October 21, 2010 8pm EST" -n "The Vampire Diaries S02E06"

Where would I place?   Thanks for all your help.

---

### Post by HolyRoses on 2010-10-22
its -o +10 and it doesn't matter where you place arguments.

if you are doing an entire series i suggest you only do tiny encodes.

use -t appletv -z 10

if satisfied with output (no typos and it produced correctly) remove -z10 change to -pbM

-o +10 is up to u to you use.  sometimes increasing gain helps on handhelds as they can only be adjusted so much.

You can play around with it, adjusting it crazy high will make your ears pop.

run encode-handheld.pl -h to see all options and descriptions.  lots of options you will never use but rarely or never.  hell some might not even work anymore!  try auto 16:9 haven't tried that one in a while.

generally if its not working its cuz you have a typo, linux/unix isn't that friendly with typos.  its CaSe senSitivE and only does exactly what you tell it (even if its wrong).

---

### Post by johnnyapplec on 2010-10-24
feature request: possible to add a percentage % until complete like atomicparsley?  just a thought...

---

### Post by alberto2172 on 2010-10-24
does encode-handheld-5.4.pl converte all audio to AAC Dolby Pro Logic or is it only from .mkv file source?? just curious :)

---

### Post by HolyRoses on 2010-10-24
only if source is from MKV.  It creates 2 channel dolby pro logic II track instead of stereo.  To create stereo use -S.

I think it sounds a little different.  If you only are going to listen with a stereo device perhaps best just to use -S and force stereo downmix. I believe stereo sounds best because right now the bitrate isn't changing.  The Pro Logic track still is 128 but now has many channels inter weaved into it.  You can modify source to change that...

---

### Post by alberto2172 on 2010-10-24
oh okay thanks alot now i will try to get more .mkv sources. 
One more thing the last thing is..... never mind ill try to figure it out   :) 
thanks by the way m8

---

### Post by HolyRoses on 2010-10-24
I don't have a stereo that is capable of dolby pro logic II.  But I am told by others that have a newer stereo and a ps3 that by default their stereo switches mode to Dolby Pro Logic II with these new encodes and that it does sound better than standard stereo. On the PS3 though you could just go and select the Dolby Digital track if it was an Apple TV encode however.  So really I guess this Pro Logic II by default is only good on the Small sized releases with only one track.  It will give user a better audio experience.  I would mess with the audio bitrate though and make modifier to bitrate if encode is going to be using Dolby Pro Logic and change to like 224kbps.  Of course that is going to make a larger file :(  I would also do real work listening tests with the proper gear to see if it really makes any difference.

To me its not important stereo or pro logic.  Most people watch movie on a computer with headsets or just stereo speakers.  In this case it will sound the same if its pro logic or stereo.  Probably even worse in Pro Logic due to the low bitrate and multiple channels.  If you have stereo and an HDTV you should only be watching Apple TV movie with DD track anyhow.

---

### Post by johnnyapplec on 2010-11-22
Hello HolyRoses,

Whats new in your latest encode-handheld-5.5.pl ?  You putting it up for us?  Thanks for your work...

---

### Post by HolyRoses on 2010-11-22
naw, dev stuff.  maybe add an ipad specific profile.

---

### Post by alberto2172 on 2010-11-26
What?? Is there already A encode-handheld-5.3.pl?? :D
That would be awsome HR.  And the iPad would be also sweet. I Love this so much so much you can do with it!! :D Nice Job HR

---

### Post by HolyRoses on 2010-11-27
5.4 is latest publicly available version.  The iPad support would just be a profile limited to the iPad resolution and appropriate bitrate for resolution.  I recommend using the appletv profile currently for iPad.

---

### Post by johnnyapplec on 2010-12-02
I see you are now inserting chapters.  Could you please explain how we can?  Thanks

---

### Post by alberto2172 on 2010-12-05
I know its nice to have some chapters included you can easily change chapters by 5 minutes. :) Can you please explain how to HR.


Is this going to come out with encode-handheld-5.5.pl versions?

---

### Post by HolyRoses on 2010-12-05
Yes it will have chapter creation.  It is based on runtime. Still unsure how to break down the logic.  Can go with preset times for every video or make it do larger or smaller chaps based on runtime.

---

### Post by alberto2172 on 2010-12-05
that will be awsome HR! lol no need to explain logic it would be some what of a uncertenty... 
Nice job HR keep it up..
i hav a question... lets say i want to know what you know HR like know linux or command line.. what kinda of clases would you say would be recommened tk learn those kinds of things...?

---

### Post by johnnyapplec on 2010-12-06
Can you provide a line of sample.  I have created a file called Chapters.txt and have the following inside:

00:00:00:00 Chapter 1
00:05:00:00 Chapter 2

and then import in Subler but it does not seem to work like yours does?

Nevermind...was not using plaintext, that was the dealbreaker now it is working.

---

### Post by alberto2172 on 2010-12-10
Around what time will the encode-handheld-5.5.pl be released? Just out of curiosity.. :)

---

### Post by alberto2172 on 2010-12-16
Uhmm how do I say this HR...lol.. 
Who are your testers that test out your new versions of encode-handheld.pl :)

Man I swear I feel like I sometimes ask to many questions ROFL.

-Albert

---

### Post by alberto2172 on 2010-12-19
what is a command to encode handheld movies with 480p.. or what im trying to say is can you give me a example on how a 480p encode would look like m8.. :)

Thanks Alot for your help :)

---

### Post by HolyRoses on 2010-12-19
There are a few different types to handle this

Below are ipod anamorphic encodes:

ipoddvd - max frame 640x480
ipodntscdvd - max frame 720x480
ipodpaldvd - max frame 720x576

ipoddvd is the largest frame that is universally compatible with all ipod video devices to date.  It will actually create 853x480 viewable content (providing content fed is 16:9).  The other frame sizes are standard PAL and NTSC dvd frames.

These are the PSP only encodes, they do similar things.
psp640|psp640wide|psp768|psp480p|psp576p

if you want 4:3 in 480p use option

-t psp640 -x for ntsc
-t psp768 for pal

standard ntsc dvd for 4:3 material is 720x480 with a 4:3 AR applied to it.  Doesn't appear to be implemented in the ipod dvd part, odd.  Guess i got lazy.

do encode-handheld.pl -h to display the help data.

for fun try -t ipodwide ;)  dunno many things that support profile other than ipods though.

---

### Post by alberto2172 on 2010-12-21
Thanks for the advise i will try those :)... i have a question though i created a  encode with psp576p awhile back and was recently told that the encode was wrong something to do with MOD 16 AR??? Something about calculate the input DAR so you can figure out the AR??? can you give me some advise if this is true or not.. or maybe just a bad source..? 

ps - the source i dnt have any info as it was a while back...



```
General
Complete name                    : C:\Documents and Settings\user xp\My Documents\My Videos\Private Torrents\Chicken Little (2005).480p.BRRip.H264 by Albert\Chicken Little (PSP).m4v
Format                           : MPEG-4
Format profile                   : Sony PSP
Codec ID                         : MSNV
File size                        : 836 MiB
Duration                         : 1h 20mn
Overall bit rate                 : 1 445 Kbps
Movie name                       : Chicken Little (480p)
Performer                        : Albert
Genre                            : Animation
Encoded date                     : UTC 2005-01-21 08:00:00
Tagged date                      : UTC 2010-06-28 14:11:13
Writing application              : encode-handheld-5.3.pl
Copyright                        : © 2010 Albert. All Rights Reserved.
Cover                            : Yes
Comment                          : A Albert Production - http://thepiratebay.org/user/Albert/
desc                             : After ruining his reputation with the town, a courageous chicken must come to the rescue of his fellow citizens when aliens start an invasion. 
ldes                             : Albert for president!
purd                             : 2010-06-28T14:10:22Z
stik                             : 9
iTunEXTC                         : mpaa|G|100|
iTunMOVI                         : <?xml version="1.0" encoding="UTF-8"?> / <!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"> / <plist version="1.0"> / <dict> /     <key>copy-warning</key> /     <string>Help control the pet population. Have your pets spayed or neutered.</string> /     <key>studio</key> /     <string>A Albert Production</string> /     <key>producers</key> /     <array> /         <dict> /             <key>name</key> /             <string>Albert</string> /         </dict> /     </array> / </dict> / </plist>
apID                             : albertovaquera@ymail.com.com

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Format settings, GOP             : M=4, N=24
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1h 20mn
Bit rate mode                    : Variable
Bit rate                         : 1 280 Kbps
Width                            : 720 pixels
Height                           : 576 pixels
Display aspect ratio             : 16:9
Frame rate mode                  : Constant
Frame rate                       : 23.976 fps
Standard                         : PAL
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.129
Stream size                      : 741 MiB (89%)
Writing library                  : x264 core 78 r1318 fe83a90
Encoding settings                : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x1:0x131 / me=umh / subme=9 / psy=1 / psy_rd=1.0:0.0 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=2 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=1 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=2 / wpredb=32 / keyint=250 / keyint_min=25 / scenecut=40 / rc_lookahead=40 / rc=2pass / mbtree=1 / bitrate=1280 / ratetol=3.1 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.41 / aq=1:1.00

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 1h 20mn
Bit rate mode                    : Variable
Bit rate                         : 160 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Compression mode                 : Lossy
Stream size                      : 92.6 MiB (11%)
Language                         : English
```

---

### Post by HolyRoses on 2010-12-21
most people dunno what they are talking about either.

This looks ok other than the framerate is wrong.  you must of manually entered the frame rate, or that profile isn't defaulting to 25 fps like it should.  should of used -r 25 providing the source is actually PAL.

that encode should display at 1024x576 (16:9 PAL).  That isn't 480p.  480p has a max height of 480 pixels.  PAL containers are 1.25 ar.  ntsc containers are 1.5.  This is of course DVD specs, well standard DVD specs.  the viewing dimensions change though based on AR.  goooogle it!

Anyhow, the program calculates correct framing for everything.  If your source is junk though its going to output junk.  Like if your input is bad AR to begin with, its not going to know how to correct it.

Post a screenshot using the VLC snapshot button/option if you want me to eval if its framed properly.

---

### Post by alberto2172 on 2010-12-21
okay thanks. :) this is a snap shot of MPC its the same thing because idk why but VLC was giving me a totaly different picture   [IMG]http://leetleech.org/images/14612190289997156960.jpg[/IMG]   
hope it helps

---

### Post by alberto2172 on 2010-12-21
VLC gives me different snap shot though. Take a look 

[IMG]http://leetleech.org/images/89959182515306303496.png[/IMG]

---

### Post by HolyRoses on 2010-12-21
your player doesn't understand aspect ratio apparently as its displaying it at 1.25 AR.  Or its upset with you because you used a ntsc frame rate for a pal video.

update it or something.

VLC should display it properly or quicktime.  should work fine in media players as well.

---

### Post by alberto2172 on 2010-12-21
im updateing as week speak but i still am trying to figure this out because i want to encode some 480p.. im told that 480 has to be 720x(xxx) but idk why its 720x576?

---

### Post by HolyRoses on 2010-12-21
> **alberto2172 said:**
> im updateing as week speak but i still am trying to figure this out because i want to encode some 480p.. im told that 480 has to be 720x(xxx) but idk why its 720x576?

because you used psp576???  isn't it sort of obvious?  plus i have said it a few times.

if you want 480p for PSP/PC  use psp480p

the 480/576 options for ipod and psp are not compatible.  ipod cannot play the PSP videos at this encode and the PSP cant play the ipod at this encode.  the only compatible option is psp -i.

---

### Post by alberto2172 on 2010-12-21
Oh yea okay thanks m8 

this is a snap of what quicktime gave me

---

### Post by HolyRoses on 2010-12-21
quicktime output is *correctish*

FPS is wrong.  your title is wrong, its not 480p :)

1024x576 is correct for quicktime to say.

only use 576 profiles for true PAL sources (things that have 25 fps to begin with).

if people complain that its encoded wrong regarding framing then they just do not understand video or have limited knowledge.

---

### Post by alberto2172 on 2011-01-01
Hello HR! Man can you belive the people that say that everything is wrong...well thats from  my point of view. I did an encode that is 720p. The width is 1280 and height is 694.! and they told me that it was wrong..! :mad: That it wasnt in MOD16. That both height and weight have to be perfectly divisible my 16. I want to hear from the boss if this is really that important or just crazy to do them all encode mod16?? Or does it really matter HR.

[http://mewiki.project357.com/wiki/Computer_movie_files/Video/Mod16](http://mewiki.project357.com/wiki/Computer_movie_files/Video/Mod16)

---

### Post by HolyRoses on 2011-01-01
It's a scene rule. It is unimportant to end user. The green line issue is corrected in players now. There is mod 16 option if you really want to use it. Do 2 encodes one forcing mod16 and 1 without it. Mod16 should be very slightly smaller on bytes. In my mind the AR morphing is not worth the perceived improvements.

---

### Post by alberto2172 on 2011-01-01
If i want to try the mod16 option which option do i use. Would it be the'A' or 'a'. I will do two encode as said i havent really ever seen the green lines issue without  useing the mod16 option.
Thanks in Advance HR

---

### Post by HolyRoses on 2011-01-01
-g        : letterbox video to next macro block height (ex 480x202 -> 480x208)

you wont see any green line issue unless you use really really old version of vlc.  you can block to the 16th but its a waste of time in my opinion.

---

### Post by alberto2172 on 2011-01-01
Me too to much waste of time but scene and too many rule.rofl 
Ill do two encodes too see how it compares thanks HR.
waiting for encode-handheld-5.5 :D

---

### Post by alberto2172 on 2011-01-01
One more question. Will option -g automatically do the mod16 or would i have to lets say do something like 
'encode-handheld.pl -g 16 '??

---

### Post by HolyRoses on 2011-01-01
just -g, i would use like -z 10

make sure it does what you expect it to do before wasting 2hrs of your life.

---

### Post by alberto2172 on 2011-01-01
ROFL. Ill make sure i do -z 20/10 to check it does. Thanks for the pointer bud :)

---

### Post by alberto2172 on 2011-01-03
Hey HR do you know if i can use option 'i' with 480p? So the output can be ipod psp compatible just wondering if it can be done.. 
i did use the option -g and gave me mod16 so the scene can stop complaining. ;-) . But thanks for the help!

---

### Post by HolyRoses on 2011-01-03
psp can only play CABAC encodes at resolution above 480x272.  CABAC isn't compatible with iPod.  so no, the parameter isn't compatible.  the only compatible encodes for psp and ipod are, psp -i and ipod.


of course i haven't checked psp firmware since around 5.x they may have changed the h264 decoder to let it do other things.

cavlc was supported in psp firmware 4.01 and above for resolutions of 480x272 and below.

oh they may also complain that now the video isn't cropped :)

---

### Post by alberto2172 on 2011-01-03
Oh alright. The new psp firmware is 6.31! :0 long time lol. 
OKay ill see what happens than.

---

### Post by alberto2172 on 2011-01-07
You Guessed it HR. They complained that video isn't cropped! Bunch of scenes rules and there mod16. Do you think is possible to use option 'g' and crop it to get a mod16 encode??

---

### Post by HolyRoses on 2011-01-07
Just use the crop option(s) to crop to the nearest 16th.

-T XXX
-B XXX

It will maintain AR.  There isn't an automated crop like -g.  The only bummer is now you actually lose video data.  With -g you don't loose video data.  With -g it pads to the nearest 16th and keeps all original video data.  With -g I forget the max pad, but I think its like 14 pixels, 8top 6 bottom.  The pad is only noticed if you play video in a window, hardly anyone does this.  All retail videos are padded unless they are 16:9 AR.

---

### Post by alberto2172 on 2011-01-07
Hey HR i was wondering if you can help me out with this. Well the cropping with the mod16 seems pretty BS idk you cant even see it on the player :x. But okay here it goes. 

I am planning to encode HD content at 720p I was trying to encode and got everything working but the problem ended that there wasnt enough space in my HDD at the end since it extracted the .mkv audio and then created it and it ran out of space. So what i was think is if I can change the output folders to send hard drive on my PC since it has more space.? Would I just have to change the beging lines where it says where to put the encoded stuff...? 

```
# where to put the encoded stuff
$output_folder="$ENV{HOME}/Desktop/Handheld-Video";

# create the output folder if it doesn't exist
if ( ! -d $output_folder ) {
	print "Creating output folder $output_folder\n";
	mkdir $output_folder;
``` 
Would this be the only thing that I have to change? Or something else along the way?
Thanks Alot HR.

---

### Post by HolyRoses on 2011-01-07
just change $output_folder

to like /Volumes/My_Large_Disk/videos

---

### Post by alberto2172 on 2011-01-07
Yeah thats what i was thinking lol =) since everything outputed is linked to it.. Thanks HR!

---

### Post by alberto2172 on 2011-01-07
Is there a way i can mux ac3 5.1 audio to the video without loosing the medatdata the is in the video like name,date,description,etc. And does not require a Mac. [ I dont own one :/ ]. 
I was looking up at mp4v2.. and installed it correctly but i get a error:
```
error while loading shared libraries: libmp4v2.so.1: cannot open shared object file: No such file or directory
```...
Anything that can do the job in either linux or windows. ( I have tried YAMB but it removes the information..)

---

### Post by alberto2172 on 2011-01-07
Uhmm... well I guess that I googled it and its "libmp4v2" that is missing..obvious.. ;) But i guess im waiting to encode and install libmp4v2. But do you know where it should be install or does it do it automatically? mp4v2 got installed in ```
 'usr/local/bin' 
```

the same place where encode-handheld is and ffmpeg.
Am I on the right track or should i just go ahead and try out what happens and if it does I'm in good luck :-)

---

### Post by alberto2172 on 2011-01-14
tired and tired no success... 
Is there a way that I can mux the audio and video for Apple TV encodes.. The 384 DD track...
I was planning to use YAMB but the thing is that the meta data 
will be lost... 
so is there a way that i can mux the audio together with out loosing the data???


(i was going to try mp4box but the option aint there or i haven't tried it out  or found it out. Im using mp4box GUI for windows i also have mp4boxCLI.)

---

### Post by johnnyapplec on 2011-02-06
Hi Again HolyRoses,

It seems that Apple iTunes HD movies have a higher bitrate?  How can I get the same output?

encode-handheld.pl -t appletv -pbM ??

Also is there a way to change the script to auto rename the audio tracks to Stereo Track and Surround Track??

---

### Post by alberto2172 on 2011-02-06
Have you tried modifying the script to change the bit rate? test it out but look and see which one it is....
start with lines 1229.. I really wouldn't now but seems like a good start.
I'm waiting for the new release of encode-handheld.pl 
=) 
I'm guessing you are using a Mac! :) i'm not sure how to do that but if you are using subler CLI there must be a way to edit the script to do that at the end....

---

### Post by chenks on 2011-02-25
Guys, need some advice.
I'm using the following to create an AppleTV version (with encode-handheld-5.4.pl)

```
RES="HD"
TYPE="-t appletv -pbM -o +10"

encode-handheld.pl $TYPE -f $HOME/Desktop/movie.mkv -C $HOME/Desktop/cover.jpg -w 1231583 -m12 -n "Film Title ($RES)" -N "Film Title" -y "Date" -e Genre -q "R" -d "description" -k "artist"
```

The cnID is not getting written to the file, and I can see the following during conversion.

```
cnID not in AtomicParsley, will not encode iTunes catalog ID
```

Any ideas what the issue is ?

Also, are there any flags to use so I can write the Director and Cast metatags to the file?

---

### Post by alberto2172 on 2011-02-26
> **chenks said:**
> Guys, need some advice.
I'm using the following to create an AppleTV version (with encode-handheld-5.4.pl)

```
RES="HD"
TYPE="-t appletv -pbM -o +10"

encode-handheld.pl $TYPE -f $HOME/Desktop/movie.mkv -C $HOME/Desktop/cover.jpg -w 1231583 -m12 -n "Film Title ($RES)" -N "Film Title" -y "Date" -e Genre -q "R" -d "description" -k "artist"
```

The cnID is not getting written to the file, and I can see the following during conversion.

```
cnID not in AtomicParsley, will not encode iTunes catalog ID
```

Any ideas what the issue is ?

Also, are there any flags to use so I can write the Director and Cast metatags to the file?


The cnID is not much of a difference its just the catalog id for movies or in itunes. Im sure you can edit the script to add /Director/ and /Cast/ but you will need to make letter for the options. It would be that hard take a look at encode-handheld.pl script and scroll to line 588 you can see the option like discription and try to add it. Ill try to find how the director and cast would be and ill try to post the script here but TRY to find it... HR hasnt been here in weeks lol but im guessing he wants us to learn =)

---

### Post by alberto2172 on 2011-02-26
I edited the script to add the the option of 'Director' and 'Cast' But Since I am just trying to work it out you can only add on director and on cast member. The issue is that I don't know.


Wait a minute i think i got it figured out since it has to show up in the information panel on itunes =) so i would just have to add them and the 'string' to the Discription..  =)


It makes a lot of sense in my head! lol but ill try it ill post it here. For the  options I uses 'E' for 'Directore' and 'F' for 'Cast' 

HR WHERE ARE YOU! i'm trying...


the option would have to be added to the long description since short desp is limited to no more than 255 char's

---

### Post by chenks on 2011-02-26
no the director or cast would not be added to the long description.
"director" and "cast" are specific metatags (they are not visible in itunes), but appletv etc can read them and display them.

i message HR regularly via Demonoid, but the replies i get aren't always that helpful. it's as if he/she doesn't want to share the knowledge sometimes.

---

### Post by alberto2172 on 2011-02-26
Look ill attach two documents on is encode-handheld-5.4.pl which is my version of it. It has my name and basic stuff like encoder,Artist, etc..

I did add the option of added 'Director' and 'Cast' member. Both of those option are with either F or E one for each one =) 
With mediainfo i get..... Just look at the mediainfo.html where it says "iTunMOVI :" and read whats next to it you will notice it has  Cast as Leslie and Directors as Juan... i dont know if you can see that on appletv since i dont have an apple TV. Try to use my script that i will prorived to you as well.. Let me know if it works or not.
To try you can do 20 second encode.


code for encode with F and E
```
 encode-handheld.pl -t appletv -pMI -f "movie.mkv" -m 12 -n 'movie' -k Albert -E Albert -F Chenks -z 20
```
you see the E is for Director and F is for Cast.  Try to and let me know if it works m8 =) 

Click on the link to download both modified script of encode-handheld.pl and movie info. Its less than 2mb =) tiny... 


p.s If you do 'encode-handheld.pl -h' you can see the two options that are there. Look for F and E

[click here!]("http://rapidshare.com/files/449985826/encode-handhel_test.rar")

---

### Post by HolyRoses on 2011-03-16
chenks atomicparsley is older revision.  it is missing the cnID options.

[https://bitbucket.org/wez/atomicparsley](https://bitbucket.org/wez/atomicparsley)

i haven't compiled that in a long time, some things look dubious to me now.  looks like strange commits regarding xid

there is a tool and break down of iTunMOVI here:

[https://bitbucket.org/wez/atomicparsley/issue/1/itunes-atom-itunmovi](https://bitbucket.org/wez/atomicparsley/issue/1/itunes-atom-itunmovi)

These values are currently hard coded in encode-handheld.pl to only set producer and copy warning.

call the script provided in that issue above if you want to set the other parms.  Also compile a newer AtomicParsley with cnID support.

---

### Post by HolyRoses on 2011-03-17
I compiled the latest AtomicParsley for Mac.  It is a universal binary.

[http://rapidshare.com/files/453096689/AtomicParsley.zip](http://rapidshare.com/files/453096689/AtomicParsley.zip)

you can get it there.  Should fix your cnID.  I made some documentation changes to the current code before I compiled to better explain cnID.

-HR

---

### Post by alberto2172 on 2011-03-21
Hey HolyRoses.
When do you think you can have the new update out for us??
Thanks for the help!

---

### Post by HolyRoses on 2011-03-21
It's not crispy enough :)

out soon...

---

### Post by videox on 2011-03-22
Hi need some help HR i keep getting this error how can i fix this on my mac

Your version of ffmpeg located at /usr/local/bin/ffmpeg doesn't support AAC audio or H264 video.:confused:

---

### Post by HolyRoses on 2011-03-22
due to massive changes in ffmpeg I only use one old version of it.  could be you installed either a really old version or a new version.

Here is the source code, you will need xcode to compile it.  compile x264 first then ffmpeg linked against it.

[ffmpeg-21221.tar.gz]("http://rapidshare.com/files/385136990/ffmpeg-21221.tar.gz")

[x264-0.83.1391.tar.gz]("http://rapidshare.com/files/385137995/x264-0.83.1391.tar.gz")

Here it is static compiled for linux I dont have a packaged one for mac right now.

[ffmpeg-21221-linux-static-compiled.tar.gz]("http://rapidshare.com/files/385149602/ffmpeg-21221-linux-static-compiled.tar.gz")

---

### Post by videox on 2011-03-22
thanks for the files has i am a newbie to all this xcode is installed on my mac but not sure howto do the rest? do i type something in terminal ! little more howto info would be great thanks Holyroses

---

### Post by HolyRoses on 2011-03-22
The program is designed by a programmer (a bad one) for programmers.  It's not packaged or meant for release for regular end users.  Teaching you the skills necessary to effectively use this program is beyond the current scope.

There are guides online that will teach you how to compile software for mac (using xcode, which is gcc).  Try google search is my suggestion.  Think of it as a learning project.

---

### Post by alberto2172 on 2011-03-24
Can you guide me on the right direction onto how to compile my own version of AtomicParsley on Ubuntu. I don't. I have looked at wez website and read the read me file but can't get it straight. Help. Thanks with the update. I can't get it to link with encode-handheld.pl lol...
Will try to solve it soon m8.

---

### Post by alberto2172 on 2011-03-24
Can you remind me how to link encode-handheld.pl to encode-handheld-5.6.pl I forgot.

---

### Post by HolyRoses on 2011-03-24
> **alberto2172 said:**
> Can you remind me how to link encode-handheld.pl to encode-handheld-5.6.pl I forgot.

sudo su -
mv /home/alberto2171/Desktop/encode-handheld-5.6/encode-handheld-5.6.pl /usr/local/bin
cd /usr/local/bin
rm encode-handheld.pl
ln -s encode-handheld-5.6.pl encode-handheld.pl


To build AtomicParsley here are the steps I took.  This is from a brand new fresh install of ubuntu 10.10.

sudo apt-get update
sudo apt-get upgrade
sudo init 6
sudo apt-get install autoconf automake mercurial zlib1g-dev g++

hg clone [https://bitbucket.org/wez/atomicparsley](https://bitbucket.org/wez/atomicparsley)
cd atomicparsley
./autogen.sh
./configure
make
sudo make install
AtomicParsley --version
AtomicParsley version: 0.9.4 (utf8)

---

### Post by alberto2172 on 2011-03-27
Hey HR Thanks for the help. 
But I have a question. I have gotten AtomicParsley for windows. And I saw that there weren't a lot of options. I'm guessing since [http://atomicparsley.sourceforge.net/](http://atomicparsley.sourceforge.net/) hasn't updated since 2006 or so. But Ive tried many options and see that I can put custom meta data id's base on the 4 character number that I can use. So since AtomicParsley wasn't update for windows. There aren't many options like Movie Rating
And long Description. And Much more like the HD for HD encodes. 
So I looked on the site [http://atomicparsley.sourceforge.net/](http://atomicparsley.sourceforge.net/) and found "4 Character codes for KNOW apple meta data Atoms " And you can see that rtng is rating. So this is what my code looks like when I do it in windows. 
[code] AtomicParsley "/file/" --meta-uuid rtng "UNRATED" but after that the encode finish but after I check either on iTunes or Mediainfo I can see that the movie Rating was not in the file. I know some how it has to work Because I have manages to add Artist and Description BUT not long Description.

---

### Post by alberto2172 on 2011-03-27
What I'm trying to say is how can I use the option 
"--meta-uuid" to set other options like ldes' or 'others?

---

### Post by HolyRoses on 2011-03-27
the bitbucket project is based off the sourceforge project.  wez imported the sourceforge project and we have expanded on it.

you just need to compile it for windows.

use cygwin to compile on windows.

[http://www.cygwin.com/]("http://www.cygwin.com/")

---

### Post by KamalGurung on 2011-03-28
I am wondering if we can change the output format to .mp4 how to do it. Please help.

---

### Post by HolyRoses on 2011-03-28
it is MP4.

mv blah.m4v blah.mp4

if it makes you happier. Disable the AtomicParsley subroutine if that upsets you as well.

---

### Post by KamalGurung on 2011-03-29
> **HolyRoses said:**
> it is MP4.

mv blah.m4v blah.mp4

if it makes you happier. Disable the AtomicParsley subroutine if that upsets you as well.

I am actually trying to encode some movie for Nokia 5230 what would u suggest ?

---

### Post by HolyRoses on 2011-03-29
try -t ipod -z 30

see what it does :)

---

### Post by KamalGurung on 2011-03-31
After some file size I am getting the following : 

frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbitframe=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s

---

### Post by HolyRoses on 2011-03-31
dunno.  maybe you have installed the wrong ffmpeg.  use pastebin and post the entire output from what you are trying to do.  your message isn't useful.

---

### Post by KamalGurung on 2011-03-31
Ok this is the result, it encodes for some time and then everything gets 0 0 0 0, I am using Ubuntu 10.10 recently installed using the ffmpeg u have provided.

/encode-handheld-5.3.pl -t ipod -z 30 -f file.mp4 -n "title" -o 512 -r 24000/1001
jhead not found.  Comment in the PSP thumbnail will remain.
This basically means the thumbail doesn't have a proper JPEG header.
Selected file: file.mp4
Setting frame rate to -r 24000/1001
Defaulting threads to 0 (auto).
Encode time: 30
Selected title: title
Selected volume: 512
Selected thumbnail time: 120
video dimensions = 1280x720
video aspect ratio = 1.77777777777778
Selected type: ipod
Selected naming: modified title
Selected thumbnail type: file.jpg
psp video dimensions = 320x180
psp video aspect ratio = 1.77777777777778
psp video height difference = 60 pixels
encoding file: file.mp4
output file = file.m4v
FFmpeg version SVN-r20562, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 21 2009 14:51:30 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libdc1394 --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-libspeex --enable-libopenjpeg --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-bzlib --enable-static --disable-shared --extra-libs=-static --extra-cflags=--static
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'file.mp4':
  Duration: 00:06:20.18, start: 0.000000, bitrate: 2704 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, 2631 kb/s, 29.97 tbr, 2997 tbn, 59.94 tbc
    Stream #0.1(eng): Audio: aac, 44100 Hz, 2 channels, s16, 69 kb/s
  Metadata
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
[libx264 @ 0xa82e0f0]using SAR=1/1
[libx264 @ 0xa82e0f0]using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0xa82e0f0]profile Baseline, level 1.3
Output #0, psp, to '/home/user/Desktop/Handheld-Video/file.m4v':
    Stream #0.0(eng): Video: libx264, yuv420p, 320x180 [PAR 1:1 DAR 16:9], q=10-51, 384 kb/s, 24k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 2 channels, s16, 128 kb/s
  Metadata
    title           : Bella Fox
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  721 fps= 34 q=-1.0 Lsize=    1807kB time=30.07 bitrate= 492.3kbits/s        
video:1467kB audio:322kB global headers:0kB muxing overhead 1.021844%
[libx264 @ 0xa82e0f0]frame I:4     Avg QP:24.63  size:  8710
[libx264 @ 0xa82e0f0]frame P:717   Avg QP:27.35  size:  2046
[libx264 @ 0xa82e0f0]mb I  I16..4: 18.2%  0.0% 81.8%
[libx264 @ 0xa82e0f0]mb P  I16..4:  0.9%  0.0%  3.7%  P16..4: 37.4% 23.3% 13.6%  2.3%  1.8%    skip:17.0%
[libx264 @ 0xa82e0f0]final ratefactor: 23.57
[libx264 @ 0xa82e0f0]coded y,uvDC,uvAC intra: 59.3% 63.5% 33.3% inter: 27.8% 23.2% 7.8%
[libx264 @ 0xa82e0f0]i16 v,h,dc,p:  9% 42%  3% 46%
[libx264 @ 0xa82e0f0]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 39%  7%  7%  7%  9%  9%  9%  7%  7%
[libx264 @ 0xa82e0f0]ref P L0: 83.1% 10.1%  6.8%
[libx264 @ 0xa82e0f0]kb/s:399.51
Generating thumbnail for PSP.
thumb height is 90
thumb padding amount = 30
The thumb padtop: 15 is odd. Increasing value, decreasing padbottom.
thumb pad top = 16
thumb pad bottom = 14
FFmpeg version SVN-r20562, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 21 2009 14:51:30 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libdc1394 --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-libspeex --enable-libopenjpeg --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-bzlib --enable-static --disable-shared --extra-libs=-static --extra-cflags=--static
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'file.mp4':
  Duration: 00:06:20.18, start: 0.000000, bitrate: 2704 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, 2631 kb/s, 29.97 tbr, 2997 tbn, 59.94 tbc
    Stream #0.1(eng): Audio: aac, 44100 Hz, 2 channels, s16, 69 kb/s
  Metadata
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
Output #0, image2, to '/home/user/Desktop/Handheld-Video/file.jpg':
    Stream #0.0(eng): Video: mjpeg, yuvj420p, 160x120 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    0 fps=  0 q=0.0 size=      -0kB time=10000000000.00 bitrate=  -0.0kbits/s frame=    1 fps=  0 q=3.9 Lsize=      -0kB time=0.03 bitrate=  -5.3kbits/s    
video:6kB audio:0kB global headers:0kB muxing overhead -100.384011%
Setting iTunes atoms

---

### Post by KamalGurung on 2011-03-31
I followed the tutorial [HOWTO: Install and use the latest FFmpeg and x264 ]

and tried again now I am getting the following error.
./encode-handheld-5.3.pl -t ipod -f file.mp4 
jhead not found.  Comment in the PSP thumbnail will remain.
This basically means the thumbail doesn't have a proper JPEG header.
Selected file: file.mp4
Defaulting frame rate to 23.976.
Defaulting threads to 0 (auto).
Selected Volume: No Change
Selected thumbnail time: 120
video aspect ratio = 
Selected type: ipod
Selected naming: simple
Selected thumbnail type: file.jpg
Illegal division by zero at ./encode-handheld-5.3.pl line 1913.

---

### Post by HolyRoses on 2011-03-31
[http://ubuntuforums.org/showpost.php?p=10587823&postcount=211](http://ubuntuforums.org/showpost.php?p=10587823&postcount=211)

use the ffmpeg here, static binary.

its complaining on jpg creation.  I dont know why.  Seems to have worked though.

your encode-handheld isn't the newest either, but that wont matter much.

And you are also changing your fps 29.97 to 23.976.  Don't do that unless you absolutely have to.  Again this isn't related to your issue however.  If it created the JPG then it worked fine.

---

### Post by KamalGurung on 2011-03-31
Thank you very much everything good now and working :) I used ./encode-handheld-5.3.pl -t ipod -f Videos/file.avi -n "file" -o 768 -r 24000/1001 

What can I do to sharpen the quality ? Make it sharp like the vidoes shared in Nokia OVI store.

---

### Post by HolyRoses on 2011-03-31
-t ipod is the lowest possible quality.

try higher quality ipod encodes until they stop working.

|ipod|ipodwide|ipod480|ipod640|ipoddvd|ipodntscdvd|ipodpaldvd|

use -z 30 to make 30 second encode test files.

upgrade to [encode-handheld 5.6]("http://www.google.com/search?q=fcbe626293fe6e48875a17e1163d179f2200a29f")

---

### Post by KamalGurung on 2011-03-31
Just upgraded and will do as you suggest :) Thanks.

---

### Post by alberto2172 on 2011-06-13
When are you planning to release encode-handheld-5.7.pl to the public HR? 

I would really like to  get my hands on it ;):p

---

### Post by alberto2172 on 2011-06-27
I was wondering if you could help me out with setting up encode-handhed.pl into my Mac HolyRose. I cant seem to get it to mv or copy fils to /usr/local/bin. And I am not sure how i would install ffmpeg on my mac. I don't know if its the same as Ubuntu or if there is a different way to install ffmpeg. I did read about Ffmped X.I'm still not sure what I must do since I don't want to break my Mac =) 

Thanks HR

-Albert

---

### Post by Ipod_Touch on 2011-07-12
can anyone give me the command line so as to get Brrips of HR quality.i am a windows user and have ffmpeg installed.

---

### Post by alberto2172 on 2011-07-13
If you have ffmpeg installed there are presents that you can use that are shown here 

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) 

Scroll at the bottom and you can see some presents...

As for getting them like HR in Windows it wont be possible HR programs runs on linux. You have 4 options to use his tool:
1) Dual boot your PC
2)Formant and install Ubuntu ;)
3) Use VMware to install a virtual Machine in your Windows PC
4) Buy a mac...

Which one do you want to do.?

---

### Post by papo2 on 2011-08-08
Right now, I am currently using HandbrakeCLI and MakeMKV for an automated process I obtained from the following link:
[http://forums.macrumors.com/showthread.php?t=805573](http://forums.macrumors.com/showthread.php?t=805573)

This process works flawlessly. However, I would like to start ripping my BD's with the same settings as HR's.

Is there a way to use HR's settings on HandbrakeCLI so I can continue to use my automated process? or will I need to use HR's encode-handheld program?


Thanks!

---

### Post by alberto2172 on 2011-08-08
okay to make this as fast as possible i would want to use team viewer and do Ill set everything up. Trust me. that all I'm going to do . If you trust me than i will help you with what you need to do to encode the same way HolyRoses encodes.

---

### Post by alberto2172 on 2011-08-08
I will be here waiting for you until 5pm after that i will leave and i will most likely be back here 9:30pm (Pacific Time)

---

### Post by papo2 on 2011-08-08
> **alberto2172 said:**
> I will be here waiting for you until 5pm after that i will leave and i will most likely be back here 9:30pm (Pacific Time)

i am trying to pm you, but it is not going through. installing teamviewer now. pm me so that I can respond.

---

### Post by papo2 on 2011-08-08
> **alberto2172 said:**
> okay to make this as fast as possible i would want to use team viewer and do Ill set everything up. Trust me. that all I'm going to do . If you trust me than i will help you with what you need to do to encode the same way HolyRoses encodes.

Albert:

thanks for all your help! it is very much appreciated.

---

### Post by alberto2172 on 2011-08-09
no problem papo2

---

### Post by chenks on 2011-08-13
Alberto, i downloaded your Something Borrowed rip for AppleTV.
Can't seem to get the 5.1 audio track to work, only stereo. This is on AppleTV 2nd generation with only HDMI connection.

---

### Post by chenks on 2011-10-10
> **alberto2172 said:**
> When are you planning to release encode-handheld-5.7.pl to the public HR? 

I would really like to  get my hands on it ;):p

yes, i would like to know this too.
still have v2.4 installed as can't work what needs to be done to install v2.6 (as there is an atomic parsley update also required i think).

---

### Post by alberto2172 on 2011-10-11
I doubt that he will be releasing his new version to the public. Version 5.7 if not 5.8 is already in process. You should upgrade to version 5.4. If you need it I can supply that version for you along with 'Atomic Parsley'.  

What OS are you running?

---

### Post by chenks on 2011-10-11
> **alberto2172 said:**
> I doubt that he will be releasing his new version to the public. Version 5.7 if not 5.8 is already in process. You should upgrade to version 5.4. If you need it I can supply that version for you along with 'Atomic Parsley'.  

What OS are you running?

v5.4 is already installed. it's v5.6 that i have downloaded but never installed (that is the one that came with an atomic parsley file also).

OS is OSX 10.7.1

---

### Post by alberto2172 on 2011-10-11
So you want to install encode-handheld-5.6.pl right?

All you need to do is copy encode-handheld.pl to /usr/local/bin/

Make sure to back up encode-handheld-5.4.pl in case if encode-handheld-5.6.pl won't work.

---

### Post by chenks on 2011-10-11
> **alberto2172 said:**
> So you want to install encode-handheld-5.6.pl right?

All you need to do is copy encode-handheld.pl to /usr/local/bin/

Make sure to back up encode-handheld-5.4.pl in case if encode-handheld-5.6.pl won't work.

yeah that bit is easy, it's the atomic parsley update that i don't know what to do with.
the change file included says....

-----
--5.6
Implemented iTunes Genre ID for Movies, TV Shows and Music Videos

Genre validation.  No longer can you type whatever you want for a genre.

Requires AtomicParsley with geID support (Mac universal binary included)
everyone else go compile it yourself.
-----

there is an atomic parsley file included with the 5.6.pl file.

if you're on msn/yahoo then could chat about it on there ?

---

### Post by alberto2172 on 2011-10-11
If i were you i would just leave Atomic Parsley as "is" because if you do update it you will have to choose numbers for genres and what not. 
But if you want to use it just copy them them to your /usr/local/bin

Give me a screen shot of the code your trying to do. 
or the code.

---

### Post by chenks on 2011-10-11
> **alberto2172 said:**
> If i were you i would just leave Atomic Parsley as "is" because if you do update it you will have to choose numbers for genres and what not. 
But if you want to use it just copy them them to your /usr/local/bin

Give me a screen shot of the code your trying to do. 
or the code.

doesn't v5.6 require the new atomic parsley though? hence why it was included ?
in my /usr/local/bin i don't have a any file called "atomicparsley", i do have an atomicparsley file with a much long filename though

---

### Post by alberto2172 on 2011-10-11
I doubt it it should look for program called 'AtomicParsley*" and use that. But try this.

Make a copy of the AtomicParsley that was included with encode-handheld-5.6.pl just in case it gets deleted. :)

Okay lets assume you have atomic parsley in the folder on your desktop right.

Open terminal and navigate to your folder on the desktop

```
 cd /Desktop/encode-handheld-5.6.pl/AtomicParsley/
```

and after that do this:

```
 sudo mv AtomicParsley* /usr/local/bin/
``` that will move atomic parsley to that directory.

make of a copy of the folder just in case you delete the atomic parsley.

---

### Post by chenks on 2011-10-11
OK this is what is currently installed (v5.4)

[IMG]http://dl.dropbox.com/u/1499080/eh1.png[/IMG]

and this is what is included with the v5.6 download

[IMG]http://dl.dropbox.com/u/1499080/eh2.png[/IMG]

---

### Post by alberto2172 on 2011-10-11
just do 

sudo mv AtomicParsley /usr/local/bin/


it will ask you for you password.

---

### Post by chenks on 2011-10-11
on a related note.
i have downloaded a 720p MKV file.
what settings should I use to create an appletv version like HR and you have done?

---

### Post by alberto2172 on 2011-10-11
for appletv let me just  have in note that its takes time. Even on my MacBook Pro i7 its still takes time.


for appletv try using this code and replace with what you want.

```
encode-handheld.pl -t appletv -pbIM -f /Desktop/MKV/movie.mkv -n "My Movie" -N "Dog Tails" -k albert2172 -C /Desktop/dog.png -d "Marley goes on a long walk" -D "Marley goes on a long walk" -e Action -y "2011-11-10 EST" -w "0822832" -y 2008
``` 

This is a basic code. You have many more like make stereo track.  increase volume if MKV source is low. Crop and such stuff.

---

### Post by chenks on 2011-10-12
is HR still doing uploads?
he doesn't seem to be as prolific as previously.

---

### Post by videox on 2011-10-13
> **HolyRoses said:**
> -t ipod is the lowest possible quality.

try higher quality ipod encodes until they stop working.

|ipod|ipodwide|ipod480|ipod640|ipoddvd|ipodntscdvd|ipodpaldvd|

use -z 30 to make 30 second encode test files.

upgrade to [encode-handheld 5.6]("http://www.google.com/search?q=fcbe626293fe6e48875a17e1163d179f2200a29f")

does anyone have encode-handheld 5.6 or 5.7 on hotfile,RS,fileshare, ive tryed google torrent none seeding :(

---

### Post by videox on 2011-10-13
can anyone tell my why im getting this error


encode-handheld.pl -t appletv -pbIM -f /Users/Me/Desktop/MKV/movie.mkv -n "lethal weapon" -N "lethal weapon" -k albert2172 -C /Users/Me/Desktop/poster.png -d "Martin Riggs finally meets his match" -D "Martin Riggs finally meets his match" -e Action -y "2011-11-10 EST" -w "0104714" -y 1992
[COLOR="Red"]Unknown option: w[/COLOR]

    PSP & iPod h264 video and AAC audio encoder.
    PSP Motion JPG encoder.  (22min = 916mb vs 84mb using h264)
    PSP 640x480 16:9 & 4:3 encoder.
    PSP 720x480 16:9 & 4:3 encoder. (To get 4:3 use psp640 with -x)
    PSP 720x576 16:9 & 4:3 encoder. (use psp768 for 4:3 and psp576p for 16:9)
    iPod 720x576 16:9 "PAL DVD" encoder (no 5g/5.5g playback)
    iPod 720x480 16:9 "NTSC DVD" encoder (no 5g/5.5g playback)
    iPod 640x480 16:9 "near DVD" encoder (all iPod OK)
    iPod 480x320 16:9 "half DVD" encoder (all iPod OK)
    iPod 320x240 19:9 & 4:3 encoder (use ipod for 4:3 and ipodwide for 16:9) (all iPod OK)
    Apple TV HD encoder (use -pbI for best results)
    Zune 30GB Windows Media 8 A/V encoder.
    Cell phone 176x144 encoder.

    usage: /usr/local/bin/encode-handheld.pl [-hl] [-t psp|psp640|psp640wide|psp768|psp480p|psp576p|pspavi|ipod|ipodwide|ipod480|ipod640|ipoddvd|ipodntscdvd|ipodpaldvd|appletv|zune|zune30|3g2] [-s XXXXX] [-n title] [-f file]

     -h        : this (help) message
     -v        : displays version
     -a        : hard box the video
                 (pillarbox and letterbox the video, AR set to AR of screen size) 
     -A        : Auto 16:9 the video.  Your video will be cropped horizontally or vertically until
                 it is at a 16:9 AR.  Works with regular cropping commands as well.  You can crop
                 a DVD matte off and still use -A to force 16:9.
     -g        : letterbox video to next macro block height (ex 480x202 -> 480x208)
     -r        : frame rate (24000/1001 or 30000/1001 are suggested override values) (default 24000/1001)
     -l        : legacy psp file naming
     -s XXXXX  : 5 digit legacy numbering sequence
     -f file   : file to encode
     -n title  : psp title displayed when using legacy naming
                 or file is renamed to this value (if AtomicParsley then also atom)
     -t type   : psp, ipod, zune, zune30, psp640, 3g2 encoding
     -o num    : volume(gain) 1x=256, 2x=512, 3x=768, 4x=1024 (default: No Change)
                 when encoding audio from MKV this controls gain in decibels
                 I don't advise going over +20, as that is extremly loud.  +10 is fine.
     -c num    : thumbnail capture time in seconds (default: 120)
     -C str    : Poster art to add to M4V file. (specify path to jpg or png)
     -z num    : encode time in seconds (default: whole thing)
     -j num    : start encode time in seconds (default: beginning)
     -b        : encode using b frames (psp, appletv) (default: no)
     -p        : 2 pass encoding
     -i        : iPhone & iPod touch PSP compatible profile (switches coder to 0)
     -I        : Apple TV CABAC mode. (switches coder to 1 and trellis 2)
     -m num    : ffmpeg threads (example, dual core: -m2, quad core: -m4, default 0 (auto))
     -M        : Extract audio from Matroska video files (requires signifcant disk space)
                 only use this for MP4 files destination files.
     -x        : when using type psp640 it will put contents in 720x480 container
                 WARNING: as of PSP firmware v5.0 it does not respect the 8:9 PAR.
                 It will play the video with a 1.5 AR (720/480).
                 The effect is your video will play 80 pixels wider than it should be.
     -X        : force widescreen DVD detection
                     --  Crop options --
     -T num    : crop top (must be even number)
     -B num    : crop bottom (must be even number)
     -L num    : crop left (must be even number)
     -R num    : crop right (must be even number)
                     --  AtomicParsley options --
     -N str    : name (if not specified then -n is used)
               : this option is used for TV shows (-n "Family Guy s07e01" -N "Love Blactually")
               : example with quotes in title (-N "There's No \"We\" Anymore") 
     -k str    : artist (req AtomicParsley and type ipod, psp, 3g2)
     -K num/tot : sets tracknum (auto determined, only pass if you want to do a num/tot with example (-K 01/13)
     -u str    : album (req AtomicParsley and type ipod, psp, 3g2)
     -d str    : description (req AtomicParsley and type ipod, psp, 3g2)
     -D str    : long description (req AtomicParsley and type ipod, psp, 3g2)
               : example with quotes in description (-d "Escape \"quotes\" on command line.")
     -e str    : genre (req AtomicParsley and type ipod, psp, 3g2)
     -y value  : year (req AtomicParsley and type ipod, psp, 3g2)
               : pass 4 digits or pass a year string value to encode a Release Date also.
               : see examples below.  (If no value is passed then current year is used.)
     -q str    : US TV & Movie rating (req AtomicParsley and type ipod, psp)
                 us-tv: "TV-MA, TV-14, TV-PG, TV-G, TV-Y, TV-Y7"
                 mpaa: "UNRATED, NC-17, R, PG-13, PG, G" 

    note:
    If you end your titles for TV Shows with sXXeXX then it will be parsed correctly as a TV Show.
    If you end your titles for Music Videos with mvid then it will be parsed correctly as a Music Video.

    crop note:
    crop is done to the original video prior to encoding.  AR is recalculated on new crop size.

    year notes:
    If you pass -y XXXX your date will be converted to January 01 of that year.
    If you pass -y "string value" you will get a year timetamp and Release Date information on your MP4 file.
    All string values are converted to UTC.

    Some example valid year strings:
    "July 24, 2007 10pm EST"
    "Mon Jan 26 12:26:13 EST 2009"
    "2009-01-23 21:00:00 EST"
    "2009-01-23 9pm EST"
    "2009-01-23"
    "2009-01-23 EST"
    "19 Dec 1994 EST"
    "oct 2 1994"
    "october 2 1994"
    "october 2 1994 EST"
    "october 19 EST"
    "`date`"

    general usage examples:
    example: /usr/local/bin/encode-handheld.pl -t psp -l -s 10101 -n "My Video" -f file.avi -o 768 -c 120
    example: /usr/local/bin/encode-handheld.pl -t psp -f file.avi
    example: /usr/local/bin/encode-handheld.pl -t psp -f file.avi -n "hookah"
    example: /usr/local/bin/encode-handheld.pl -t zune30 -f file.avi
    example: /usr/local/bin/encode-handheld.pl -t zune30 -f file.avi -n "hookah"
    example: /usr/local/bin/encode-handheld.pl -t ipod -f file.avi
    example: /usr/local/bin/encode-handheld.pl -t ipod -f file.avi -n "hookah"
    example: /usr/local/bin/encode-handheld.pl -t 3g2 -f tvshow.avi -n "TV Show s04e16" -r 24000/1001
    example: /usr/local/bin/encode-handheld.pl -t psp -pi -f tvshow.avi -n "tvshow s01e13" -o 512 -r 24000/1001 -d "Jedi Crash" -q "TV-PG"
    example: /usr/local/bin/encode-handheld.pl -t psp -pi -f rounders.avi -n "Rounders" -o 512 -r 30000/1001 -T 106 -B 102 -L 2 -y 1998 -q R -e Drama -d "Damon plays poker."
    example: /usr/local/bin/encode-handheld.pl -t psp480p -pb -f rounders.avi -n "Rounders" -o 512 -r 30000/1001 -T 106 -B 102 -L 2 -y 1998 -q R -e Drama -d "Damon plays poker."

---

### Post by alberto2172 on 2011-10-13
What version of encode-handheld are you running. the option -w 
i believe won't work unless you have the updated version of AtomicParsley. 
but it seems that you don't have the updated version of the script. hum.
type in terminal 

```
encode-handheld.pl -v
```

---

### Post by videox on 2011-10-13
> **alberto2172 said:**
> What version of encode-handheld are you running. the option -w 
i believe won't work unless you have the updated version of AtomicParsley. 
but it seems that you don't have the updated version of the script. hum.
type in terminal 

```
encode-handheld.pl -v
```

Hi thanks for the reply 

ive installed encode-handheld.pl 5.2 (but need new version for mac) need help.

---

### Post by alberto2172 on 2011-10-13
your version of encode-handheld says that it doesn't have the option -w 

so imbd /  numbers 

won't work you can download HR version 5.4 or ask check if he can give you version 5.6  of encode-handheld.pl

Also try to get new version of AtomicParsley so you can use the option -w.

Chenks can give it to you PM him or write on this post. Or find one.

---

### Post by HolyRoses on 2011-10-13
-w requires a newer rev.  5.6 i think introduced new genre tagging and itunes store id support.

i have 5.6 someplace on my computer i'll send it sometime.

5.7 is very minor changes i think.

---

### Post by alberto2172 on 2011-10-13
awesome :) I've been reading the comments of version 5.4 :) looks like some good stuff!

---

### Post by chenks on 2011-10-14
here is v5.6

[http://dl.dropbox.com/u/1499080/encode-handheld-5.6.zip]("http://dl.dropbox.com/u/1499080/encode-handheld-5.6.zip")

---

### Post by videox on 2011-10-14
> **chenks said:**
> here is v5.6

[http://dl.dropbox.com/u/1499080/encode-handheld-5.6.zip]("http://dl.dropbox.com/u/1499080/encode-handheld-5.6.zip")

thanks will these files work on my mac?

if i just replace old files.

---

### Post by chenks on 2011-10-14
> **videox said:**
> thanks will these files work on my mac?

if i just replace old files.

yes those will work on mac

---

### Post by videox on 2011-10-14
> **chenks said:**
> yes those will work on mac

cool thanks

---

### Post by Atrophik on 2011-10-15
> **chenks said:**
> yes those will work on mac

Sorry for being a bit slow on all of this... But how? I've been religiously downloading HolyRoses' movies on my torrent site, but have run out of material. So I figured I'd try her methods for myself. I downloaded the encode-handheld.pl release (the updated one in this thread) and ffmpeg, but I'm stuck there. I'm not sure where to go from here and what to do. I can't seem to figure out how to install the perl file, or if that's what I'm supposed to do at all. I tried my good buddy "Google" but I came up with nothing but this forum thread.

Up until now I've never really needed to do any of this myself, so any help you could toss my way to get me rolling would be super appreciated.

I'm using OS X Lion, if that matters.

Thanks,
Mike

*EDIT*

To be clear, I tried a few things I read in this thread (put the encode-handheld.pl file into usr/local/bin), but I can't even tell if it's made a difference. Like, I don't see a difference in the program, such as a new format being available to encode to. Basically, what I'm trying to do is create .m4v video files in 720p to stream to my AppleTV2. I'd like to do it exactly as HolyRoses has done in her uploads. The quality is unmatched (in my experience).

---

### Post by videox on 2011-10-15
> **chenks said:**
> yes those will work on mac

hi installed new files :) but i think somethings wrong  tryed to encode my 1st movie i end up with 3 files in the output folder and in terminal its just sat there doing same thing... Stream mapping:for 8 hours and cpu at 100  is this normal?


Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
size=  288435kB time=3691.97 bitrate= 640.0kbits/s    sec (5.68 fps)
video:0kB audio:288435kB global headers:0kB muxing overhead 0.000000%
115371 frames in 21811.17 sec (5.29 fps), 3 last 0.68 sec (4.41 fps)

[IMG]http://img191.imageshack.us/img191/33/handheldvideo.jpg[/IMG]

[IMG]http://img685.imageshack.us/img685/6185/encodehandheld56.jpg[/IMG]

---

### Post by Atrophik on 2011-10-15
After installing the program, putting the encode-handheld.pl file in the usr/local/bin folder, and selecting the settings in ffmpeg, The process takes all of 2 seconds to complete and gives me 2 output files. One of which is a log, and the other is named as the movie, but is empty.

I'm no good with programming code, so most of this thread looks like Greek to me.

I just need someone to walk me through getting this whole thing setup and working on a Mac running OS X Lion.

If anybody is feeling kind enough to hold my hand a little, I'd be super grateful. I'm willing to beg... Hands. Knees. The whole nine yards.

Thanks in advance,
Mike

---

### Post by chenks on 2011-10-15
is this is way over your head then you might be better using something else to encode (such as Handbrake).

---

### Post by videox on 2011-10-15
> **chenks said:**
> is this is way over your head then you might be better using something else to encode (such as Handbrake).

i want to use encode-handheld just a bit stuck on what this means and does not complete 
Stream mapping:
Stream #1.0 -> #0.0
Stream #0.0 -> #0.1
size= 288435kB time=3691.97 bitrate= 640.0kbits/s sec (5.68 fps)
video:0kB audio:288435kB global headers:0kB muxing overhead 0.000000%
115371 frames in 21811.17 sec (5.29 fps), 3 last 0.68 sec (4.41 fps)

---

### Post by chenks on 2011-10-15
> **videox said:**
> i want to use encode-handheld just a bit stuck on what this means and does not complete 
Stream mapping:
Stream #1.0 -> #0.0
Stream #0.0 -> #0.1
size= 288435kB time=3691.97 bitrate= 640.0kbits/s sec (5.68 fps)
video:0kB audio:288435kB global headers:0kB muxing overhead 0.000000%
115371 frames in 21811.17 sec (5.29 fps), 3 last 0.68 sec (4.41 fps)

you do realise that the v5.6 files i supplied are just update files? you need other files installed as well (which are not included in the files i supplied). the files i supplied merely upgrade the existing version of encode-handheld that you already have installed.

---

### Post by videox on 2011-10-15
> **chenks said:**
> you do realise that the v5.6 files i supplied are just update files? you need other files installed as well (which are not included in the files i supplied). the files i supplied merely upgrade the existing version of encode-handheld that you already have installed.


hi chenks

yes i installed 5.2 then updated  your files in /usr/local/bin

then typed in terminal 

encode-handheld-5.6.pl -t appletv -pbIM -f /Users/My/Desktop/MKV/movie.mkv -n "lethal weapon" -N "lethal weapon" -k videox -C /Users/My/Desktop/poster.png -d "Martin Riggs finally meets his match" -D "Martin Riggs finally meets his match" -e Action -y "2011-11-10 EST" -w "0104714" -y 1992

am i missing something?
[IMG]http://img31.imageshack.us/img31/704/binx.jpg[/IMG]

thanks for helping

---

### Post by alberto2172 on 2011-10-16
@ Atrophik

After you did what this forum said to install ffmpeg then your good to go. If you are running a Mac computer than its completely different but also as easy. You need to install ffmpeg for mac. (google it and follow steps. use Youtube)
After that you have tp install Perian. (google that too.)
Important thing to remember before all of it is that you need Xcode for Mac's. after that just do move everything into the /usr/local/bin/ folder.
Example (assuming everything is in your Desktop.

```
 sudo mv /Desktop/encode-handheld.pl/encode-handheld.pl* /usr/local/bin/
```
Do the same thing for everything else just change the last part to the other files.
(/Desktop/encode-handheld.pl/other stuffs name..

----------------

@videox
you stopped the encoding before it was done. If you are encoding from .mkv source file and use the option -M will extract the audio  thats what you have there the .dts file. But it will delete it after its all done. And the 384kb.ac3 file is the 5.1 audio for apple TV. Im assuming you typed in something like
```
 encode-handheld.pl -t appletv .....options...
```
with that you have to mux that file using Subler (Mac Only) linux sorry but for now no way to mux.  Subler is free. (google that to.. and read all of this thread.!!!)
encode-handheld.pl is uses a lot of CPU because its encoding! uses a lot of horsepower! Get a faster i7 Mac ;)

----------------

@Atrophik

Yes it will create those log if anything if your folder where your source file is located but shouldn't. they are of no harm to your computer.  TO see if encode-handheld works. Try this code. just change the file to yours input. k . :)

```
encode-handheld.pl -t psp -pi -f /mycomputer/Desktop/movie/dog.mp4
```

simple with not that many options. If anything post a snap shot of what your screen looks like and ill give you guys a HAND!


@ videox

It appears as you are missing the ffmpeg files. m8. Try doing a simple encode to see if it works. if it complains  about ffmpeg than something went wrong. =/

---

### Post by papo2 on 2012-01-20
How can I create a batch text file with several filenames included, so I can leave them converting through encode-handheld.pl all weekend?

right now, I have only needed to do one at a time, but I have a full season series that I want to convert throughout the weekend.

Can you guys help? (OSX 10.6.8 )

I followed the instructions Holyroses provided in this thread, but I couldn't get it to work. Were those instructions for Linux and would it work for Mac too?

---

### Post by HolyRoses on 2012-01-20
just need a batch script.

create a file that looks like this

#!/bin/sh

encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>



save the file with a name like "series.sh"

change the permissions to be runnable

chmod 755 series.sh

execute the file

./series.sh

I recommend only doing 10 second encodes and validate the output files prior to committing to a long running job.


Read the encode-handheld.pl options as their are many you should incorporate for a series and there is builtin logic for handling series if you name the files correctly.

-HR

---

### Post by papo2 on 2012-01-20
> **HolyRoses said:**
> just need a batch script.

create a file that looks like this

#!/bin/sh

encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>
encode-handheld.pl <lots of arguments>



save the file with a name like "series.sh"

change the permissions to be runnable

chmod 755 series.sh

execute the file

./series.sh

I recommend only doing 10 second encodes and validate the output files prior to committing to a long running job.


Read the encode-handheld.pl options as their are many you should incorporate for a series and there is builtin logic for handling series if you name the files correctly.

-HR

Thanks, HolyRoses! I appreciate the quick response.

---

### Post by papo2 on 2012-01-24
The batch script worked perfectly.

I have another question for you. I think I remember reading that MKV is the prefered file to encode through encode-handheld.pl.

How about M2TS file from the Hauppauge HDPVR? What is the preffered method? 

Repack the file from an M2TS container to MKV, or just put the M2TS file straight through encode-handheld.pl?

I am trying to figure out the best way to encode my personal recordings with the Hauppauge HDPVR without losing quality.

Thanks again!

---

### Post by HolyRoses on 2012-01-24
Nothing wrong with mt2s.  There is some extra logic for mkv regarding audio track processing is about it.   The mt2s it will only make a stereo track for you.   That is due to no extra code written to specifically handle mt2s files.

---

### Post by papo2 on 2012-01-25
So to keep DTS, I would need to demux the M2TS and repack into an MKV container huh?

If so, what is the best program I can run on the Mac for this?

If there is none, I guess I would need to run "eac3to" with Parallels and Windows virtually.

---

### Post by papo2 on 2012-01-26
HolyRoses:

I need your help here. I have a few files that are wrapped in a MKV container and I am trying to switch over to an M4V container to play in the AppleTV. The MKV files have H264 video and AC3 audio. (I don't need to encode the video since it is already acceptable format for AppleTV  ....don't want to use unecessary resources.)

I am using Subler to repackage the files, but I need to get the audio down to AAC like you a currently do with the encode-handheld process. 

My question is, is there a way that I can use handheld to just extract and convert to AAC and not do the video? I tried looking at your script to see what you program you call to do the audio portion, but I can't figure it out. 

I appreciate all your help.



Thanks!


**UPDATE: Nevermind. I was able to do it within Subler. I needed to enable the option in the preferences.  <face palm>**

---

### Post by afranc on 2012-02-04
hey papo,
you can do this on subler. Go to preferences -> audio
I do the same many times. You can also use mp4tools

---

### Post by papo2 on 2012-03-07
Holyroses:

I know it's a bit early, considering they just announced the new AppleTV today, but will you be updating encode-handheld.pl to support 1080p files for the new Apple TV?

Thanks!

---

### Post by papo2 on 2012-04-10
> **papo2 said:**
> Holyroses:

I know it's a bit early, considering they just announced the new AppleTV today, but will you be updating encode-handheld.pl to support 1080p files for the new Apple TV?

Thanks!

anything?

---

### Post by HolyRoses on 2012-04-29
I don't have a newer apple tv to test this though it wouldn't be hard to add support.  Just make a new type like appletv-1080 and copy the appletv profile.  From there it would just be lots of testing of different bitrates and refs etc to see what the device can handle without glitches.  Also I would I probably test to make sure the 1080p encodes could play on the older atv 2 as well.

The atv2 plays 1080p files already just fine, its limitation is that it cannot output in 1080p for whatever reason.  I think its a memory issue or something.

It might be better just to use a ATV2 as your test platform and encode for that in 1080p.  If ATV2 can play it, then surely atv3 can play it.

In sum it wouldn't be hard, just time consuming tinkering with the encoder settings.  I would probably also bump the AC3 output to 448kb (to match DVD specs) or even 640kb...  If we are going to nearly double the file size then increasing the audio bitrate shouldn't be a big deal.   It is not currently in my agenda to update the program however (that is unless you feel like buying me an atv3, i can be bribed!)  

-HR

---

### Post by alberto2172 on 2012-05-01
Hey HR  can you upload the new script of encode-handheld.pl i kinda misplaced the one i was using. :/ 

also if you can put the AtomicParsley for the Mac :)

I finally got a Mac! :) and i can use Subler!!!! Woot!

---

### Post by chenks on 2012-05-06
i've given up on converting files.
i just download the 1080p MKV file (which 99% are h264 anyway), and remux it to M4V using MP4Tools.
the result is that I get a 1080p file with 448kbps AC3 5.1 audio that plays perfectly on both ATV2 and ATV3.

takes me about an hour to download the 1080p file (from usenet), and around 15 minutes to remux it.

i can't see any point in going thru the lengthy converting process any more.

---

### Post by alberto2172 on 2012-06-22
HolyRoses. I wonder if you are still here supporting your program? :/ :|

---

### Post by papo2 on 2012-06-26
> **alberto2172 said:**
> Hey HR  can you upload the new script of encode-handheld.pl i kinda misplaced the one i was using. :/ 

also if you can put the AtomicParsley for the Mac :)

I finally got a Mac! :) and i can use Subler!!!! Woot!

The latest one I have is 5.6. Let me know if you still need it.

---

### Post by papo2 on 2012-07-02
> **HolyRoses said:**
> 

In sum it wouldn't be hard, just time consuming tinkering with the encoder settings.  I would probably also bump the AC3 output to 448kb (to match DVD specs) or even 640kb...  If we are going to nearly double the file size then increasing the audio bitrate shouldn't be a big deal.   

-HR

I cannot find where in your script you are setting the AC3 DD track to 384kb. I want to bump it to 640kb to see if I can really tell the difference.   **Nevermind. Just saw it all the way at the top.. **



Also, any way you can just copy the appletv profile for 1080 and I'll tinker with the settings??

---

### Post by alberto2172 on 2012-07-06
Yes can i please have the 5.6 version. I have the 5.4 and im pretty sure im missing the upgrade.

Also to help you with your problem. If I'm not mistaken in the in the top of the script there is a line that says :

DD_track = 384 


just change that to what ever you want. Im pretty sure that it will do this if you are encoding for Apple TV, but for other formats like Zune, iPod, PSP you will need to go to that preset in the script and change the bit rate :)

---

### Post by papo2 on 2012-07-06
> **alberto2172 said:**
> Yes can i please have the 5.6 version. I have the 5.4 and im pretty sure im missing the upgrade.

Also to help you with your problem. If I'm not mistaken in the in the top of the script there is a line that says :

DD_track = 384 


just change that to what ever you want. Im pretty sure that it will do this if you are encoding for Apple TV, but for other formats like Zune, iPod, PSP you will need to go to that preset in the script and change the bit rate :)

Here you go: 

[https://dl.dropbox.com/u/2344021/encode-handheld-5.6.pl](https://dl.dropbox.com/u/2344021/encode-handheld-5.6.pl)

As far as the DD, I had found it on the script already... lol, but thanks!

---

### Post by alberto2172 on 2012-07-07
> **papo2 said:**
> Here you go: 

[https://dl.dropbox.com/u/2344021/encode-handheld-5.6.pl](https://dl.dropbox.com/u/2344021/encode-handheld-5.6.pl)

As far as the DD, I had found it on the script already... lol, but thanks!


Thanks. If you don't mind me asking. For what device do you encode for. And what settings do you  use? :)

---

### Post by alberto2172 on 2012-07-07
Do you happen to also have a working copy of AtomicParsley I keep getting this message for it.

```
 
Press [q] to stop encoding
frame=    1 fps=  0 q=2.8 Lsize=      -0kB time=0.04 bitrate=  -4.2kbits/s    its/s    
video:1kB audio:0kB global headers:0kB muxing overhead -101.433225%
Removing comment from PSP thumbnail to generate a proper JPEG header.
Setting iTunes atoms
Displaying AtomicParsley text data
APar_readX_noseek read failed, expect 12, got 8: No such file or directory
Alberto-Vaqueras-MacBook-Pro-5:~ albertovaquera$ 
```

and i cant put  movie descriptions and stuff of that sort. :/

---

### Post by papo2 on 2012-07-09
I'll send it to you when I get home tonight.

Also, I mostly encode for AppleTV2, but now starting to work on AppleTV3 1080P settings. So far, the 1080P encodes are working just fine on the AppleTV2. iTunes just downscales them to 720P.

Alberto: my PM's don't seem too be working. PM me when you have a chance.

---

### Post by papo2 on 2012-07-10
> **alberto2172 said:**
> Do you happen to also have a working copy of AtomicParsley I keep getting this message for it.


Here you go:

[https://dl.dropbox.com/u/2344021/AtomicParsley.zip](https://dl.dropbox.com/u/2344021/AtomicParsley.zip)

---

