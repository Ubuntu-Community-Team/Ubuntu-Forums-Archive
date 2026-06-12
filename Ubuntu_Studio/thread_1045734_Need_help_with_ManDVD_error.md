---
title: "Need help with ManDVD error"
date: 2009-01-20
forum: Ubuntu Studio
---

### Post by mikejaegerster on 2009-01-20
I tried converting an MPEG video and generating my first DVD last night.  When I checked the results, I found there was an error generating the menu.  The results are detailed below.  I did create a menu screen with the tool but apparently something went wrong.

Can someone help point me in the right direction?

Thanks, Mike

*********
--> Output from generation of menu  ------------------------------------------------------------
1920+0 records in
1920+0 records out
7680 bytes (7.7 kB) copied
, 0.00459508 s, 1.7 MB/s
Warning: unsupported audio format
   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  30000:1001
   INFO: [ppmtoy4m]     pixel aspect ratio:  10:11
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
jpegtopnm: WRITING PPM FILE
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Interlaced input - selecting interlaced encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to genmenu.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 480 pel
   INFO: [mpeg2enc] Aspect ratio code: 2 = 4:3 display
   INFO: [mpeg2enc] Frame rate code:   4 = 30000.0/1001.0 (NTSC VIDEO)
   INFO: [mpeg2enc] Bitrate: 7500 KBit/s
   INFO: [mpeg2enc] Quality factor: 8 (Quantisation = 9) (1=best, 31=worst)
   INFO: [mpeg2enc] Field order for input: top-field-first
   INFO: [mpeg2enc] Sequence unlimited length
   INFO: [mpeg2enc] Search radius: 16
   INFO: [mpeg2enc] DualPrime: no
   INFO: [mpeg2enc] Using one-pass rate controller
   INFO: [mpeg2enc] GOP SIZE RANGE 9 TO 18 
   INFO: [mpeg2enc] Setting colour/gamma parameters to "NTSC"
   INFO: [mpeg2enc] Progressive format frames = 0
   INFO: [mpeg2enc] Using default unmodified quantization matrices
   INFO: [mpeg2enc] Buffering 39 frames
   INFO: [ppmtoy4m] Output Stream parameters:
   INFO: [ppmtoy4m]     frame size:  720x480 pixels (518400 bytes)
   INFO: [ppmtoy4m]         chroma:  4:2:0 MPEG-2 (horiz. cositing)
   INFO: [ppmtoy4m]     frame rate:  30000/1001 fps (~29.970030)
   INFO: [ppmtoy4m]      interlace:  top-field-first
   INFO: [ppmtoy4m]   sample aspect ratio:  10:11
   INFO: [mpeg2enc] Signaling last frame = 0
   INFO: [mpeg2enc] SETTING MMX and MMX for QUANTIZER!
   INFO: [mpeg2enc] NEW GOP INIT length 18
   INFO: [mpeg2enc] Frame     0     0 I q=8.00 sum act=274.77226    
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 23112

   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
****ERROR: [mplex] Unable to open file silent.mpa for reading.**
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000

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

---

### Post by mikejaegerster on 2009-01-20
It looks like there may already be a solution to this problem.  I am going to try out what I found in

[http://ubuntuforums.org/showthread.php?t=981281]("http://ubuntuforums.org/showthread.php?t=981281")

Mike

---

