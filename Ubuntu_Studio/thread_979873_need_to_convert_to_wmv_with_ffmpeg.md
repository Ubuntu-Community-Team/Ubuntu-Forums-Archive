---
title: "need to convert to wmv with ffmpeg"
date: 2008-11-12
forum: Ubuntu Studio
---

### Post by ricemark20 on 2008-11-12
I need to convert avi to wmv to play on Real Player
I am using Ubuntu 7.10

---

### Post by FakeOutdoorsman on 2008-11-12
I don't have 7.10, so you'll have to provide some info before I can give you a command to use.  Show the output of:
```
ffmpeg -formats
```
Also show the output of:
```
ffmpeg -i your_avi_file.avi
```

---

### Post by nowardev on 2008-11-12
better

> **FakeOutdoorsman said:**
> I 
```
ffmpeg -i your_avi_file.avi 2>&1 | grep Stream
```

---

### Post by ricemark20 on 2008-11-12
```
mark@mark-locutus:~$ ffmpeg -i 11-08-08\ Hannah2.avi 2>&1 | grep Stream
  Stream #0.0: Video: mpeg4, yuv420p, 480x320, 29.97 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, stereo, 128 kb/s

```

---

### Post by nowardev on 2008-11-13
you have to post ffmpeg -formats too !!!!

anyway here there is a command line to create wmv with mencoder ...

mencoder  -forceidx  -ofps 25  -oac lavc  -lavcopts acodec=wmav2:abitrate=128  -srate 44100  -vf scale=720:576,harddup -ovc lavc -lavcopts vcodec=wmv2:vbitrate=900 INPUT -o OUTPUT

---

### Post by ricemark20 on 2008-11-13
> **nowardev said:**
> you have to post ffmpeg -formats too !!!!

anyway here there is a command line to create wmv with mencoder ...

mencoder  -forceidx  -ofps 25  -oac lavc  -lavcopts acodec=wmav2:abitrate=128  -srate 44100  -vf scale=720:576,harddup -ovc lavc -lavcopts vcodec=wmv2:vbitrate=900 INPUT -o OUTPUT

```
mark@mark-locutus:~$ ffmpeg -formats
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Aug 10 2008 11:11:16, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
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

```

---

### Post by ricemark20 on 2008-11-13
> **nowardev said:**
> 
anyway here there is a command line to create wmv with mencoder ...

mencoder  -forceidx  -ofps 25  -oac lavc  -lavcopts acodec=wmav2:abitrate=128  -srate 44100  -vf scale=720:576,harddup -ovc lavc -lavcopts vcodec=wmv2:vbitrate=900 INPUT -o OUTPUT

```
mark@mark-locutus:~$ mencoder -forceidx -ofps 25 -oac lavc -lavcopts acodec=wmav2:abitrate=128 -srate 44100 -vf scale=720:576,harddup -ovc lavc -lavcopts vcodec=wmv2:vbitrate=900 11-08-08\ Hannah.mpeg -o 11-08-08\ Hannah.wmv
MEncoder 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (Family: 15, Model: 107, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x2fc5000
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=720 h=576]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio LAVC, couldn't find encoder for codec wmav2.

```

---

### Post by unutbu on 2008-11-13
```
ffmpeg -sameq -i "11-08-08 Hannah2.avi" "11-08-08 Hannah2.wmv"
```

---

### Post by nowardev on 2008-11-13
please read medibuntu documentation

and update mencoder ffmpeg

---

### Post by ricemark20 on 2008-11-13
> **unutbu said:**
> ```
ffmpeg -sameq -i "11-08-08 Hannah2.avi" "11-08-08 Hannah2.wmv"
```

```
mark@mark-locutus:~$ ffmpeg -sameq -i "11-08-08 Hannah2.avi" "11-08-08 Hannah2.wmv"
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Aug 10 2008 11:11:16, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from '11-08-08 Hannah2.avi':
  Duration: 00:00:59.4, start: 0.000000, bitrate: 1028 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x320, 29.97 fps(r)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 128 kb/s
Output #0, asf, to '11-08-08 Hannah2.wmv':
  Stream #0.0: Video: msmpeg4, yuv420p, 480x320, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
No accelerated IMDCT transform found
Press [q] to stop encoding
[msmpeg4 @ 0xb7edba68]warning, clipping 1 dct coefficients to -127..127
[msmpeg4 @ 0xb7edba68]warning, clipping 1 dct coefficients to -127..127
[msmpeg4 @ 0xb7edba68]warning, clipping 1 dct coefficients to -127..127
[msmpeg4 @ 0xb7edba68]warning, clipping 1 dct coefficients to -127..127
[msmpeg4 @ 0xb7edba68]warning, clipping 1 dct coefficients to -127..127

frame= 1782 q=0.0 Lsize=       1kB time=59.3 bitrate=   0.1kbits/s    
video:13170kB audio:463kB global headers:0kB muxing overhead -99.995953%

```

---

### Post by ricemark20 on 2008-11-14
I get the file to convert, but get this message from Real Player when I try to play it.  

[IMG]http://i445.photobucket.com/albums/qq171/ricemark20/Screenshot_error.png[/IMG]

---

### Post by unutbu on 2008-11-14
Well, there are two ways you could go from here:

1) How important is it that you stick with Real Player? I find mplayer and vlc (both in the official repos) are both capable of playing movies -- at least in all formats I've encountered.

2) If you wish to get it to play on Real Player, then please tell us which version of Real Player you are using. According to [http://service.real.com/help/faq/rp8/rpb8gen.html](http://service.real.com/help/faq/rp8/rpb8gen.html)
support for AVI and WMV depend on whether the appropriate codec is installed. However, it appears to handle MPEG-1 "out-of-the-box". 
Therefore, perhaps try 
```
ffmpeg -sameq -i "11-08-08 Hannah2.avi" "11-08-08 Hannah2.mpg"
```

---

### Post by ricemark20 on 2008-11-14
> **unutbu said:**
> Well, there are two ways you could go from here:

1) How important is it that you stick with Real Player? I find mplayer and vlc (both in the official repos) are both capable of playing movies -- at least in all formats I've encountered.

2) If you wish to get it to play on Real Player, then please tell us which version of Real Player you are using. According to [http://service.real.com/help/faq/rp8/rpb8gen.html](http://service.real.com/help/faq/rp8/rpb8gen.html)
support for AVI and WMV depend on whether the appropriate codec is installed. However, it appears to handle MPEG-1 "out-of-the-box". 
Therefore, perhaps try 
```
ffmpeg -sameq -i "11-08-08 Hannah2.avi" "11-08-08 Hannah2.mpg"
```

It's the only player my mother in law gets at work, I think it's version 11
I'm using the standard linux realplayer 11 for testing.
Is there a standalone hack for vlc so she wouldn't have to install it?

---

### Post by unutbu on 2008-11-14
Is she using Ubuntu? If so, installing vlc (or mplayer) is easily done through clicking System>Administration>Synaptic Package Manager.

Also try:
```

ffmpeg -sameq -i "11-08-08 Hannah2.avi" "11-08-08 Hannah2.rm"
```

According to the FAQ I posted previously, RM, RA, RAM are the original Real Player formats.

You might get a lot of messages
```

[rv10 @ 0xb7ec3a68]warning, clipping 1 dct coefficients to -127..127
```
but try playing the .rm file anyway.

---

### Post by ricemark20 on 2008-11-14
> **unutbu said:**
> Is she using Ubuntu? If so, installing vlc (or mplayer) is easily done through clicking System>Administration>Synaptic Package Manager.



They only gave her windoze.  She doesn't know anything else but that.

---

