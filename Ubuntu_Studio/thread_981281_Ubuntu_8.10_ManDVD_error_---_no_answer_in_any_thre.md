---
title: "Ubuntu 8.10 ManDVD error --- no answer in any threads"
date: 2008-11-13
forum: Ubuntu Studio
---

### Post by zombieman1982 on 2008-11-13
Hello all

I do regard myself as a newbie to ubuntu still, i have been using Ubuntu since 6.10. I am not to good with the terminal parts of linux.

I have just tried to use ManDVD 2.5.4 in Ubuntu 8.10 for the first time and it will not complete the DVD no matter all my efforts to try to solve the issue. I have checked other threads and no one seems to have an answer to this issue.


Error I receive after the DVD encoding has completed:

"Error when generating menu. Check the console for more details."

CONSOLE REPORTS THE FOLLOWING:

--> Output from encoding files ------------------------------------------------------------
Limiting audio preload to 0.4s.
Increasing audio density to 4.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0xe1f8d0]SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
[swscaler @ 0xe1f8d0]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xe1f8d0]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xe1f8d0]SwScaler: using n-tap MMX scaler for vertical scaling (YV12 like)
[swscaler @ 0xe1f8d0]SwScaler: 720x384 -> 720x576

1 duplicate frame(s)!

1 duplicate frame(s)!
--> Output from generation of menu  ------------------------------------------------------------
1920+0 records in
1920+0 records out
7680 bytes (7.7 kB) copied, 0.0024434 s, 3.1 MB/s
Warning: unsupported audio format
jpegtopnm: WRITING PPM FILE
   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  25:1
   INFO: [ppmtoy4m]     pixel aspect ratio:  59:54
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [ppmtoy4m] Output Stream parameters:
   INFO: [ppmtoy4m]     frame size:  720x576 pixels (622080 bytes)
   INFO: [ppmtoy4m]         chroma:  4:2:0 MPEG-2 (horiz. cositing)
   INFO: [ppmtoy4m]     frame rate:  25/1 fps (~25.000000)
   INFO: [ppmtoy4m]      interlace:  top-field-first
   INFO: [ppmtoy4m]   sample aspect ratio:  59:54
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Interlaced input - selecting interlaced encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to genmenu.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 576 pel
   INFO: [mpeg2enc] Aspect ratio code: 2 = 4:3 display
   INFO: [mpeg2enc] Frame rate code:   3 = 25.0 (PAL/SECAM VIDEO / converted FILM)
   INFO: [mpeg2enc] Bitrate: 7500 KBit/s
   INFO: [mpeg2enc] Quality factor: 8 (Quantisation = 9) (1=best, 31=worst)
   INFO: [mpeg2enc] Field order for input: top-field-first
   INFO: [mpeg2enc] Sequence unlimited length
   INFO: [mpeg2enc] Search radius: 16
   INFO: [mpeg2enc] DualPrime: no
   INFO: [mpeg2enc] Using one-pass rate controller
   INFO: [mpeg2enc] GOP SIZE RANGE 9 TO 15 
   INFO: [mpeg2enc] Setting colour/gamma parameters to "PAL B/G"
   INFO: [mpeg2enc] Progressive format frames = 0
   INFO: [mpeg2enc] Using default unmodified quantization matrices
   INFO: [mpeg2enc] Buffering 33 frames
   INFO: [mpeg2enc] Signaling last frame = 0
   INFO: [mpeg2enc] SETTING MMX and MMX for QUANTIZER!
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame     0     0 I q=8.00 sum act=329.90669    
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 35383

DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_GB.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000

   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to open file silent.mpa for reading.
INFO: Picture survolee.png had 2 colors
INFO: Picture cliquee.png had 2 colors
INFO: Constructing blank img
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: 0 subtitles added, 0 subtitles skipped, stream: 32, offset: -0.00

Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 0 bytes.



I believe the error is related to this section of the console printout:
[B]   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to open file silent.mpa for reading[/B].

I have used ManDVD 2.4.1 and the latest version 2.5.4 and still the same error. I have also tried creating an exact copy of a dvd I did in Ubuntu 7.10 using ManDVD that worked, but alast it still errors in 8.10.

This leads me to believe it is solely an issue with the new Ubuntu 8.10 distribution.

PLEASE HELP!

---

### Post by Paulix on 2008-11-23
Hi Zombieman,

I had this problem and got around it by choosing an mp3 when you define the background for the menu as background music.  Give that a go I think it will resolve your problem.

paul (ix)

---

### Post by komodojay on 2008-12-01
Paulix and Zombieman,

I can confirm this trick works. I was having the same error "error generating menu" and had the same missing silent.mpa in the console. I jst recorded about 4 seconds of nothing and saved it as silent.mp3 and told ManDVD to use that as the background music and I was finally able to create a correct DVD.

---

### Post by aeiah on 2008-12-02
i think this may be because mandvd tells ffmpeg to make a silent .mpa audio file, and the version of ffmpeg that ships doesnt like doing it. you could try compiling your own up to date version of ffmpeg, there should be some guides for doing so on here because doing so has other benefits (or used to with older versions of ubuntu, such as x264 encoding).

---

### Post by mart1n on 2008-12-04
Hello,
the problem is caused by Lame 3.98. if you backlevel to Lame 3.97 (well, actually synaptic then removes both lame 3.98 and ManDVD) and re-install ManDVD is works as designed. 
One of the statements in the script is missing an option required for Lame 3.98 => backleveling to 3.97 solved the issue for me. I found this in a German forum:
es wird
| dd if=/dev/zero bs=4 count=1920 | lame -b 128 -s 48 /dev/stdin silent.mpa
| aufgerufen, um eine leere Sound-Datei fuer das Menu zu erschaffen.
| Nach dem Update auf lame 3.98 ist dies bei mir nicht mehr moeglich.
| Abhilfe verschafft statt dessen der Aufruf
| dd if=/dev/zero bs=1920 count=4 | lame -b 128 -s 48 -r - silent.mpa
| Der Parameter "-r" muss fuer das Raw-Format gesetzt werden, /dev/stdin
kann
| dafuer durch das "-"-Zeichen ersetzt werden.

---

### Post by brotherajnin on 2008-12-20
I too was having this problem... I re-installed lame 3.97 and no more errors!

---

### Post by nicsmr on 2009-03-03
well I did everything described above and still no video.

I uninstalled lame 3.98 which uistalled mandvd.  I downloaded lame 3.97 and installed it.  then i installed maandvd then ran everything again and same error.

WhaT am i doing wrong?

Nick

---

### Post by bhoth on 2009-03-05
Nick, I also uninstalled lame 3.98 then reinstalled Mandvd and mine failed again. Then I checked and sure enough, lame 3.98 was re-installed again. Then I just went and re-installed lame 3.97 (i think it stomped on lame 3.98 ) and now it works.

---

### Post by IngoRatsdorf on 2009-08-30
Hi.

I had the same error.
First time, it was caused by a space in the pathname of the project dir :oops:.
Once resolved, the same error happened again, because of exactly the above described situation :sad:.
Although using the directions given in the german forum, ManDVD did not recognise the generated SILENT.MPA and was requesting a SILENT.PCM, which of course wasn't there either. So I just recorded 4 seconds of silence with Sound Recorder and saved it as an MP3 file and specified it as background music.
WORKED. :)

---

