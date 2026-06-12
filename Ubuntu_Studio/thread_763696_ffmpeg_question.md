---
title: "ffmpeg question"
date: 2008-04-23
forum: Ubuntu Studio
---

### Post by pedrotuga on 2008-04-23
I am trying a video picture size using ffmpeg but i migt be mssing something.

The video is encoded in
H.264 / AVC
352 x 252

The audio is:
MPEG-4 AAC audio

I want to use the same wncoding for the ouput execpt fot the picture size which i want to be 'qcif' size-

Now this is the command i am using:

```
ffmpeg -i vegetal.mp4 -s 'qcif'  vegeral_mobile2.mp4
```

But for some reason it thrws an "unsuported codec" error message. AFAIK this codec is supported by ffmpeg, i've just checked ffmpeg documentation.

Do need to install any extra packages?

What am i missing in here?

```
p@p-laptop:~/Desktop$ ffmpeg -i vegetal.mp4 -s 'qcif'  vegeral_mobile2.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'vegetal.mp4':
  Duration: 00:02:05.9, start: 0.000000, bitrate: 429 kb/s
  Stream #0.0(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(und): Video: h264, yuv420p, 352x252, 25.00 fps(r)
Output #0, mp4, to 'vegeral_mobile2.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 176x144, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mpeg4 @ 0xb7e86ac8]removing common factors from framerate
Unsupported codec for output stream #0.1
p@p-laptop:~/Desktop$ 

```

---

### Post by FakeOutdoorsman on 2008-04-23
I believe the ffmpeg package in Ubuntu universe is compiled without x264 and aac support (among other codecs like mp3).  You can see how it is compiled on the "configuration" line in your post or when you try to encode.  You will need to recompile ffmpeg, or use the version available in the [**Medibuntu**]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") repository.  You can try *-vcodec copy* and *-acodec copy* to simply copy the streams:
```
ffmpeg -i vegetal.mp4 -s 352x252 -vcodec copy -acodec copy vegeral_mobile2.mp4
```

---

### Post by pedrotuga on 2008-04-23
mmmm... i added medibuntu repos, updated apt, and replaced ffmpeg with the version from medibuntu but i still get the same error.


```
$ ffmpeg -i vegetal.mp4 -s 'qcif'  vegeral_mobile2.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'vegetal.mp4':
  Duration: 00:02:05.9, start: 0.000000, bitrate: 429 kb/s
  Stream #0.0(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(und): Video: h264, yuv420p, 352x252, 25.00 fps(r)
File 'vegeral_mobile2.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'vegeral_mobile2.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 176x144, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mpeg4 @ 0xb7e27ac8]removing common factors from framerate
Unsupported codec for output stream #0.1
p@p-laptop:~/Desktop$ 

```

Here are the ffmpeg -formats output
am i missing some codecs?

```
p@p-laptop:~/Desktop$ ffmpeg -formats
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 D  RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
 D  avs             avs format
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 D  nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 D V D  aasc
  EA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_sbpro_2
 DEA    adpcm_sbpro_3
 DEA    adpcm_sbpro_4
 DEA    adpcm_swf
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D V D  avs
 DEV    bmp
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEA    gsm
 D A    gsm_ms
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    jpegls
 D V    kmvc
  EV    libtheora
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    targa
 D V    theora
 D V D  tiertexseqvideo
 D V    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V D  ultimotion
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V    vp5
 D V    vp6
 D V    vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 DEV D  zlib
 DEV    zmbv

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1 hex umh iter

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse
p@p-laptop:~/Desktop$ 


```

---

### Post by FakeOutdoorsman on 2008-04-23
I've never seen "Audio: 0x0000" before.  Seems to me that it is trying to encode audio to the "0x0000" codec, but of course that generates an error.  I'm at the work computer now with no ffmpeg access, but what do you get when you try this?
```
ffmpeg -i vegetal.mp4 -s 176x144 -sameq -vcodec copy -acodec copy vegeral_mobile2.mp4
```

---

### Post by pedrotuga on 2008-04-23
I get this... it appears that the only problem is the size

```
$ ffmpeg -i vegetal.mp4 -s 176x144 -sameq -vcodec copy -acodec copy vegeral_mobile2.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'vegetal.mp4':
  Duration: 00:02:05.9, start: 0.000000, bitrate: 429 kb/s
  Stream #0.0(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(und): Video: h264, yuv420p, 352x252, 25.00 fps(r)
File 'vegeral_mobile2.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'vegeral_mobile2.mp4':
  Stream #0.0: Video: avc1 / 0x31637661, yuv420p, 352x252, q=2-31, 25.00 fps(c)
  Stream #0.1: Audio: mp4a / 0x6134706D, 44100 Hz, stereo
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mp4 @ 0xb7f925d0]track 1: codec frame size is not set
Could not write header for output file #0 (incorrect codec parameters ?)
p@p-laptop:~/Desktop$ 

```

BTW, I am trying to format a video so t can be played in a nokia 3110 classic
[http://www.forum.nokia.com/devices/3110_classic](http://www.forum.nokia.com/devices/3110_classic)

both h263 and h264 should work.
when it comes to video i still don't know which specifications refer to  the container format and which ones to the codecs. On top of that there a lot of naming inconsistence due to poor file extension usage which makes it particulary difficult to sort things out.
The .3gp files that are often used in mobiles? which container do they use? and which codec?

I wouldn't mind not using mpeg4

---

### Post by jdforsythe on 2008-04-23
from wikipedia:

3GP is a multimedia container format defined by 3GPP for use on 3G mobile phones. It is a simplified version of MPEG-4 Part 14 (MP4). 3GP files have the filename extension .3gp or .3g2.

3GP stores video streams as MPEG-4 or H.263, and audio streams as AMR-NB or AAC-LC formats. 3GP files are always big-endian. 3GP also describes image sizes and bandwidth, so content is correctly sized for mobile display screens.

---

### Post by pedrotuga on 2008-04-24
See, that's the problem with wikipedia, it's an impresive information repository, but if you want to get a bit deeper in any subject you need a more trustable source.

That quote is very vage. Besides having no tecnical details at all it uses the acronym "MPEG4" in an unclear way.
First is a container, then is codec.

---

### Post by pedrotuga on 2008-04-27
I hope it's ok to bump this thread...
anybody?

---

### Post by MonkeeSage on 2008-05-05
> **pedrotuga said:**
> I get this... it appears that the only problem is the size

I'm having the same problem with some mp4 files (H.264 [AVC1] video / AAC audio, downloaded from google video). 

The simplest solution would be to just copy the streams to a different container format like matroska. I'm fairly sure a phone media player would not support those formats though. You might try anyway, just to see:

```

ffmpeg -i somefile.mov -acodec copy -vcodec copy outfile.mkv

```


Apart from that (and see technical discussion below if interested), the only thing I know of is to recode the aac stream, which might be OK for a low-quality stream on a low-quality device (I don't mean that your phone is crappy, mine can't even play videos, heh -- I mean low quality as compared to a Cerwin-Vega surround system). For example, to recode the audio stream at 96kbps and 22050Hz in mono channel, you'd do:

```

ffmpeg -acodec mpeg4aac -vcodec copy -i somefile.mov -ac 1 -ab 96k -ar 22050 outfile.mp4

```


And this also brings up another point: you can't scale the video without recoding the video stream as well (at least, not as far as I know--maybe with QuickTime Pro or some studio-quality linear editing programs [...maybe]--but not with ffmpeg). So, in that case, you'd need something like this to scale and recode the video:

```

ffmpeg -acodec mpeg4aac -vcodec h264 -i somefile.mov -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile.mp4

```


This produces a video with a size of about 2 megs per minute of video. Adjust the audio (-ab) and video (-vb) bitrates to taste.

*Ps. Note that the order of the options is important!*


If you want a really small file, use the paired-down mp4 container known as 3gp, which is targeted at mobile devices.

```

ffmpeg -i somefile.mov -s qcif -ac 1 -ab 12.2k -ar 8000 -vb 100k outfile.3gp

```


Using this format with the options given above produces a file size of a little under a meg per minute (don't worry about the -acodec and -vcodec, ffmpeg selects the right ones automatically based on the container and options). Of course, the quality degrades quite a bit, but it may be sufficient for your purposes.


***Technical***:

I've not looked too much into the problem, but it appears that the MOV demuxer or muxer in ffmpeg (i.e., [libavformat/mov.c]("http://svn.mplayerhq.hu/ffmpeg/trunk/libavformat/mov.c?view=log") and [libavformat/movenc.c]("http://svn.mplayerhq.hu/ffmpeg/trunk/libavformat/movenc.c?view=log")) is not properly finding or parsing the trak.stsd.mp4a.esds atom, which contains [the information about the samples per packet rate]("http://wiki.multimedia.cx/index.php?title=Understanding_AAC#Packaging.2FEncapsulation_And_Setup_Data") (--which the muxer is calling "frame size" for some strange reason--which is especially confusing since there is an option called -frame_size that sets the internal video scaling size and has nothing at all to do with the error).

I don't know if this is due to a missing or malformed atom, or an error in the demuxer or what. I have cobbled together a hackish "band-aide" patch for current SVN. It basically just sets codec->frame_size to 960 for the MODE_MP4 / MODE_IPOD muxers and sets track->audio_vbr to true for all AAC streams. This seems to work properly, and I'll see about maybe submitting a patch upstream once I understand what is happening a little better. As always, patch is public domain. Use at your own risk; I'm not responsible for anyone (or anything) that breaks, explodes, dies or suffers from PSD because of it.

Patch is attached.

---

### Post by pedrotuga on 2008-05-18
MonkeeSage, big thanks, that was an informative and helpful reply.

Sorry I took a while to repply, i didn't have an SD card with enough memory to perform these tests, and have been lazy to buy one.
Today I finally did and I am playing around a bit with the cell phone.

This workded
```

ffmpeg -acodec mpeg4aac -vcodec h264 -i somefile.mov -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile.mp4

```

But only with mpeg files. I tryed with a video downloaded from video.google.com and with worked fine. Youtube now has the option of downloading to mp4 so that's fine to. Still I would like this solution to be as versatile as possible.
It didn't work with FLVs i downloaded from youtube just for testing purposes. Also, I didn't have any mpep2 videos to test.
Also, I guess mpeg4 videos don't use all the same codec.

But allow me to come up with these ignorant questions:
Is it possible to use the same ffmpeg snippet to all supported video inputs? I guess not because if it would the above command would work fine regardless the input format, as long as supported of course.
From what i red in ffmpeg manpage all those parameters in the above command concern the output file. Why am I getting errors depending on the input file format if the filetype when I am only working with supported formats?

---

### Post by MonkeeSage on 2008-05-19
> **pedrotuga said:**
> . . .
Is it possible to use the same ffmpeg snippet to all supported video inputs? I guess not because if it would the above command would work fine regardless the input format, as long as supported of course.
From what i red in ffmpeg manpage all those parameters in the above command concern the output file. Why am I getting errors depending on the input file format if the filetype when I am only working with supported formats?

Hmmm....that command should work with any container / codec combination supported by libavformat / libavcodec, which should support parsing the Flash Video container format (used in .flv files), and should support both FLV1 (Sorenson Spark/H.263) and FLV4 (On2 VP6) video decoding, as well as all the standard audio decoding (mp3 is the most common in flvs). And it obviously can produce files using the output codecs and container, since it worked with other files. Please link to an example video on youtube that doesn't work (not the actual flv, just the youtube link), and I'll try to see what's going on.

Since mplayer and vlc both use libavformat / libavcodec for playing back flv files (they'll call it something like ffflv, or FLV1), you might try playing the offending file in one of those players and see what you get. I think there is such a thing as compressed / encrypted flvs, but I don't know anything about that. If it plays back though, then (in theory) it can be decoded and recoded by ffmpeg into an mp4.

---

### Post by FakeOutdoorsman on 2008-05-19
> **pedrotuga said:**
> 
This workded
```

ffmpeg -acodec mpeg4aac -vcodec h264 -i somefile.mov -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile.mp4

```

From what i red in ffmpeg manpage all those parameters in the above command concern the output file. Why am I getting errors depending on the input file format if the filetype when I am only working with supported formats?

Your above example is applying "-acodec mpeg4aac -vcodec h264" to the input file.  From man ffmpeg: "As a general rule, options are applied to the next specified file."

If you want to apply those options to the output, then they should go after the input file:
```
ffmpeg -i somefile.mov -acodec mpeg4aac -vcodec h264 -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile.mp4
```
or if using a newer ffmpeg:
```
ffmpeg -i somefile.mov -acodec libfaac -vcodec libx264 -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile.mp4
```

What are the errors you are getting?

---

### Post by MonkeeSage on 2008-05-19
> **FakeOutdoorsman said:**
> Your above example is applying "-acodec mpeg4aac -vcodec h264" to the input file.  From man ffmpeg: "As a general rule, options are applied to the next specified file.

Ahh, yup. My bad. I even stressed that order is important and then told him the wrong order, doh. #-o

---

### Post by pedrotuga on 2008-05-19
mmm... still not working :(

```
p@p-laptop:~$ ffmpeg -i feni.flv -acodec mpeg4aac -vcodec h264 -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile2.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
feni.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
p@p-laptop:~$ 

```

here's the video.
[http://www.youtube.com/watch?v=MJbqzugYEGM](http://www.youtube.com/watch?v=MJbqzugYEGM)

---

### Post by FakeOutdoorsman on 2008-05-20
Your ffmpeg command works for me.  How are you retrieving feni.flv?  I got it by visiting the youtube page in Firefox and then looking for the file in /tmp after it loaded.  It was named "FlashvHkWab".  In the past I've also used the [youtube-dl]("http://www.arrakis.es/~rggi3/youtube-dl/") script.
```
md5sum feni.flv
015736e8d9e882f9aa991e70ea0a1f63  feni.flv
```
```
ffmpeg -i feni.flv 
FFmpeg version SVN-r13184, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-postproc --enable-libvorbis --enable-libtheora --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264 --disable-ffserver --disable-ffplay --disable-ipv6 --disable-vhook
  libavutil version: 49.6.0
  libavcodec version: 51.56.0
  libavformat version: 52.13.0
  libavdevice version: 52.0.0
  built on May 16 2008 17:39:36, gcc: 4.3.0

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'feni.flv':
  Duration: 00:04:51.75, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Must supply at least one output file
```

---

### Post by pedrotuga on 2008-05-20
I downloaded it using keepvid.com, I past the link and they output the downloadable link.

I deleted that video because I only downloaded it for testing purposes.
Anyway, I want on youtube, looked for the same video, downloaded it and check  the md5 sum. It matches yours, its the same video.

I gave it a last try in case there was really something wrong with the file I had before, and this time it actually worked.
I should have tried more carefully before. Sorry.

Anyway. Big thanks!
It works now! Yay!

---

### Post by pedrotuga on 2008-06-10
Ok, I'll need to bump tis thread.
I updated to hardy and i think my ffmpeg was replaced again. I already added medibuntu as a source and updated ffmpeg but the damn codecs are missing for pretty much all the video formats out there.

Can somebody link me to a more complete ffmpeg deb package? By 'more complete' I mean with support for all thos proprietary formats and stuff.

---

### Post by FakeOutdoorsman on 2008-06-10
I have a guide on the forums that you may be interested in:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

If you use my guide, you should know that some encoding option names have changed since the Medibuntu version was compiled, so your example from post #14 would now be:
```
ffmpeg -i feni.flv -acodec mpeg4aac -vcodec libx264 -s qcif -ac 1 -ab 96k -ar 22050 -vb 150k outfile2.mp4
```

---

### Post by eye208 on 2008-06-11
> **pedrotuga said:**
> Can somebody link me to a more complete ffmpeg deb package? By 'more complete' I mean with support for all thos proprietary formats and stuff.
This thread has been running since April. Maybe you should consider switching the tools. What you are trying to do with FFMPEG could have been handled by Ubuntu's MEncoder within minutes and without linking to any external repositories.

---

### Post by pedrotuga on 2008-06-11
thank you FakeOutdoorsman, but i think I'll avoid installing stuff using gnu build.
I like to be able to keep track of everything installed on my system, therefore I prefer to use deb packages.

eye208, sure, I wouldn't mind. Can you show me a snippet equivalent to the one Fakeoutdoorsman just wrote but using mencoder?

---

### Post by FakeOutdoorsman on 2008-06-11
The tutorial creates deb packages using checkinstall for the programs you compile and adds the appropriate information to Synaptic, apt, aptitude, etc.

---

### Post by eye208 on 2008-06-12
> **pedrotuga said:**
> Can you show me a snippet equivalent to the one Fakeoutdoorsman just wrote but using mencoder?
```
mencoder feni.flv -vf scale=176:144 -af channels=1,resample=22050:0:2 -ovc x264 -oac faac -x264encopts bitrate=150 -faacopts br=96 -srate 22050 -mc 0 -noskip -o tmp.avi
MP4Box -new outfile2.mp4 -add tmp.avi
```
MP4Box is part of the "gpac" package. Both mencoder and gpac are in the multiverse repository.

---

### Post by pedrotuga on 2008-06-13
> **eye208 said:**
> ```
mencoder feni.flv -vf scale=176:144 -af channels=1,resample=22050:0:2 -ovc x264 -oac faac -x264encopts bitrate=150 -faacopts br=96 -srate 22050 -mc 0 -noskip -o tmp.avi
MP4Box -new outfile2.mp4 -add tmp.avi
```
MP4Box is part of the "gpac" package. Both mencoder and gpac are in the multiverse repository.

Thank you. That worked.
Just out of curiosity, MP4Box utility is used just to change the container, right?

---

### Post by eye208 on 2008-06-14
> **pedrotuga said:**
> Just out of curiosity, MP4Box utility is used just to change the container, right?
Yes.

---

