---
title: "Can't encode with Mencode via h264enc......"
date: 2009-09-20
forum: Ubuntu Studio
---

### Post by newIsle on 2009-09-20
Hey all..

Having problems with encoding video files using h264enc (shell script for Mencoder).....This works on my debian lenny install....trying to get it to work in Ubuntu 9.04....

I think the error is referring to some ffmpegs libavcodec Dependices are missing....but i checked and all i could find was: 

:libavcodec-unstripped-52...

not sure really what other Dependices are missing.... 

(error output at the bootom of this quotation)
error opening video decoder (ffmpeg)
> newisle@dell-desktop:~$ h264enc -1p -p hq







+=============================================================+
|<<<<<<< h264enc - the interactive shell script ripper >>>>>>>|
|-------------------------------------------------------------|
|<<<<<< version: 9.0.1 - (C) 2006-2009, Grozdan Nikolov >>>>>>|
+=============================================================+


Select the Input type [file/dir/dvd/vcd]: file
Provide the Input Video File: /home/newisle/out.ogv
Provide a name for the Output File [default is /home/newisle/out(1)]: 
Scan for multiple video streams? [y/n]: n
Would you like to use Pre/Postprocessing video filters? [y/n]: n
Would you like to Crop the video file? [y/n]: n
Would you like to include/rip a Subtitle? [y/n]: n

-> Detecting source FPS value...
(standard_in) 1: syntax error
-> Failed to detect source FPS value!

Would you like to set/force the Output Frame Rate (FPS)? [y/n]: n
Would you like to do Frame Rate Conversion? [y/n]: n
Apply a Telecine/3:2 Pulldown/IVTC/Pullup process (NTSC only!)? [y/n]: n

-> Detecting original resolution...
-> Failed to detect original resolution!
-> You have to provide it yourself!

Specify the desired Resolution [default is ??]: 1280x800

Available Software Scalers
~~~~~~~~~~~~~~~~~~~~~~~~~~
0 --> Fast Bilinear
1 --> Bilinear
2 --> Bicubic
3 --> Experimental
4 --> Nearest Neighbor/Point
5 --> Area Averaging
6 --> Luma Bicubic/Chroma Bilinear
7 --> Gaussian
8 --> Sinc
9 --> Lanczos
10 -> Natural Bicubic Spline

-> Storage Aspect Ratio (SAR): 1.6000:1
(standard_in) 1: syntax error
-> Pixel Aspect Ratio (PAR): :1
-> Total pixels: 1024000

Select a Software Scaler [default is 10]: 
Specify the Display size/aspect [press 'Enter' to skip]: 
Specify the Expand filter parameters [press 'Enter' to skip]: 
Would you like to set/force the input Video Aspect Ratio? [y/n]: n

+=============================+
| H.264 Encoder Configuration |
+=============================+

Specify the desired Video Bitrate in kbps [default is 1000]: 

(standard_in) 1: syntax error
-> Bits Per Pixel value:  bpp
(standard_in) 1: syntax error
(standard_in) 1: syntax error
-> Bits Per Block value:  bpb
-> Using "High Quality" preset

Specify the H.264 Level [default is 4.1]: 
Would you like to use Predefined/Custom Quantization Matrices (cqm)? [y/n]: n
Would you like to set the encoder Priority Level? [y/n]: n

+=====================+
| Audio Configuration |
+=====================+

Scan for multiple Audio streams? [y/n]: n

Available Audio Codecs
~~~~~~~~~~~~~~~~~~~~~~
MP3 -----> Container support: AVI, MKV, MP4, OGM, TS
AC3 -----> Container support: AVI, MKV, MP4, OGM, TS
AAC -----> Container support: AVI, MKV, MP4, TS
AAC+ ----> Container support: MP4, MKV
neroAAC -> Container support: MP4, MKV
VORBIS --> Container support: MP4, MKV, OGM
FLAC ----> Container support: MKV
PCM -----> Container support: AVI, MKV, OGM
COPY ----> Container support: Depends on audio codec
NOSOUND -> Container support: AVI, MKV, MP4, OGM, TS

Track 1: Select the Audio Codec [default is AAC]: NOSOUND

+=============================+
| Miscellaneous Configuration |
+=============================+

Would you like to set a target file size? [y/n]: n
Would you like to inspect the MEncoder options? [y/n]: n
Would you like to encode a Sample? [y/n]: n
Would you like to save the MEncoder options to a file? [y/n]: y
Where to store the options? [default is /home/newisle/batchfile]: 
Would you like to convert the final encode from AVI to MKV? [y/n]: n
Would you like to convert the final encode from AVI to MP4? [y/n]: n
Would you like to convert the final encode from AVI to TS? [y/n]: n
Would you like to convert the final encode from AVI to OGM? [y/n]: n

-> Starting to encode the video file in 1-pass mode
-> Using "High Quality" preset
-> Will use '/home/newisle/out(1).avi' as output file

Starting to encode in: 5 4 3 2 1 
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option x264encopts: Unknown suboption mbtree
success: format: 0  data: 0x0 - 0x9ea68e0
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
Ogg file format detected.
VIDEO:  [theo]  1280x800  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1280x800  fps:15.00  ftime:=0.0667
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=1280 h=800 interlaced=0 chr-drop=0]
Opening video filter: [softskip]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88423b0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1280 x 800 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect.
[swscaler @ 0x883d3d0]SwScaler: using unscaled yuv420p -> yuv420p special converter
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x6F656874.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...
-> MEncoder has exited with a non-zero value!
-> Exiting in function: mencoder_exit()

Also i know that all depencies other than that are met for h264enc

> newisle@dell-desktop:~$ h264enc -sc

-> Checking for 'MPlayer'..................... OK
-> Checking for 'MEncoder'.................... OK
-> H.264 video support in MEncoder............ YES
-> AAC (FAAC) audio support in MEncoder....... YES
-> MP3 (LAME) audio support in MEncoder....... YES
-> AC3 (lavc) audio support in MEncoder....... YES
-> PCM audio support in MEncoder.............. YES

-> Checking for 'bc'.......................... OK
-> Checking for 'pv'.......................... OK
-> Checking for 'dd'.......................... OK
-> Checking for 'neroAacEnc'.................. OK
-> Checking for 'aacplusenc'.................. OK
-> Checking for 'oggenc'...................... OK
-> Checking for 'flac'........................ OK
-> Checking for 'less'........................ OK
-> Checking for 'lsdvd'....................... OK
-> Checking for 'dvdxchap' (from ogmtools).... OK
-> Checking for 'mkvmerge' (from mkvtoolnix).. OK
-> Checking for 'ogmmerge' (from ogmtools).... OK
-> Checking for 'MP4Box' (from gpac).......... OK
-> Checking for 'tsMuxeR'..................... OK

If you have installed a required program but the script
can't find it, run 'h264enc -r' to reset the config file.


so im trying to convert ogg theroe videos(ogv) to avi's

any help would be great thanks!!!!

PS:
I'm running a :
Dell inspiron 1525 notebook
1 gb ram
Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
32_bit

---

### Post by newIsle on 2009-09-20
okay, so I installed the xvidenc shell scripter, and that seems to be working fine.....encodes to a .avi but with the xvid codec...

i cant understand whats the issue with ffmpeg's dependentcies on ubuntu...no issues with debian (lenny) at all,....what am i missing here?

hmmm.....whats the better codec, h264 or xvid??

also gonna test divxenc....just for fun....probally wont need to ever use it though...

---

### Post by cooper77z on 2009-09-20
One possible issue could be the version of ffmpeg that you are using. I'd suggest a version from openshot libraries or better that I don't know about yet. :) Please do tell when you install better libraries.:popcorn: ps Mplayer don't work no more after installing the openshot libraries.

---

### Post by newIsle on 2009-09-20
oh...forgot to mention...install a ffmpeg2theora liberies(didn't help)....other than that dont really know what else to install

---

### Post by andrew.46 on 2009-09-20
Hi newIsle,

I believe the h264enc script uses a *recent* version of MPlayer/MEncoder and x264:

[http://h264enc.sourceforge.net/faq.html#problems](http://h264enc.sourceforge.net/faq.html#problems)

If you are using the Ubuntu Repository versions of any of these this is more than likely the reasons for the encoding failure as these versions will be quite old. If you are keen there is [a guide]("http://ubuntuforums.org/showthread.php?t=1081070") on these forums for the newest versions.

All the best,

Andrew

---

### Post by newIsle on 2009-09-20
thanks andrew.46.....gonna read this a few times and attempt it i think

---

