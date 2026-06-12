---
title: "How to convert .flv to .wmv with ffmpeg?"
date: 2009-02-18
forum: Ubuntu Studio
---

### Post by Nixie Pixel on 2009-02-18
Hi, I'm having a tough time figuring out how to convert a .flv file to .wmv using ffmpeg.  Here are the relevant outputs:

ffmpeg -formats
```
FFmpeg version UNKNOWN-svn16978+3:0.svn20090204-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn16978+3:0.svn20090204-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-xvmc --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb  5 2009 21:02:21, gcc: 4.3.3
File formats:
  E 3g2             3GP2 format
  E 3gp             3GP format
 D  4xm             4X Technologies format
 D  IFF             IFF format
 D  ISS             Funcom ISS format
 D  MTV             MTV format
 DE RoQ             id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw AC-3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            PCM A-law format
 DE alsa            ALSA audio output
 DE amr             3GPP AMR file format
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 DE asf             ASF format
  E asf_stream      ASF format
 DE ***             SSA/*** format
 DE au              SUN AU format
 DE avi             AVI format
  E avm2            Flash 9 (AVM2) format
 D  avs             AVS format
 D  bethsoftvid     Bethesda Softworks VID format
 D  bfi             Brute Force & Ignorance
 D  c93             Interplay C93
  E crc             CRC testing format
 DE daud            D-Cinema audio format
 DE dirac           raw Dirac
 DE dnxhd           raw DNxHD (SMPTE VC-3)
 D  dsicin          Delphine Software International CIN format
 DE dts             raw DTS
 DE dv              DV video format
 D  dv1394          DV1394 A/V grab
  E dvd             MPEG-2 PS format (DVD VOB)
 D  dxa             DXA
 D  ea              Electronic Arts Multimedia Format
 D  ea_cdata        Electronic Arts cdata
 DE eac3            raw E-AC-3
 DE f32be           PCM 32 bit floating-point big-endian format
 DE f32le           PCM 32 bit floating-point little-endian format
 DE f64be           PCM 64 bit floating-point big-endian format
 DE f64le           PCM 64 bit floating-point little-endian format
 DE ffm             FFM (FFserver live feed) format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw FLAC
 D  flic            FLI/FLC/FLX animation format
 DE flv             FLV format
  E framecrc        framecrc testing format
  E gif             GIF Animation
 D  gsm             GSM
 DE gxf             GXF format
 DE h261            raw H.261
 DE h263            raw H.263
 DE h264            raw H.264 video format
 D  idcin           id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
  E ipod            iPod H.264 MP4 format
 D  libdc1394       dc1394 v.2 A/V grab
 D  lmlm4           lmlm4 raw format
 DE m4v             raw MPEG-4 video format
 DE matroska        Matroska file format
 DE mjpeg           MJPEG video
 D  mlp             raw MLP
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             MOV format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG-4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             MP4 format
 D  mpc             Musepack
 D  mpc8            Musepack SV8
 DE mpeg            MPEG-1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG-2 video
 DE mpegts          MPEG-2 transport stream format
 D  mpegtsraw       MPEG-2 raw transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 D  msnwctcp        MSN TCP Webcam stream
 DE mulaw           PCM mu-law format
 D  mvi             Motion Pixels MVI format
 DE mxf             Material eXchange Format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             NUT format
 D  nuv             NuppelVideo format
 DE ogg             Ogg
 D  oma             Sony OpenMG audio
 DE oss             Open Sound System playback
  E psp             PSP MP4 format
 D  psxstr          Sony Playstation STR format
 D  pva             TechnoTrend PVA file and stream format
 D  r3d             REDCODE R3D format
 DE rawvideo        raw video format
  E rcv             VC-1 test bitstream
 D  redir           Redirector format
 D  rl2             rl2 format
 DE rm              RM format
 D  rpl             RPL/ARMovie format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           PCM signed 16 bit big-endian format
 DE s16le           PCM signed 16 bit little-endian format
 DE s24be           PCM signed 24 bit big-endian format
 DE s24le           PCM signed 24 bit little-endian format
 DE s32be           PCM signed 32 bit big-endian format
 DE s32le           PCM signed 32 bit little-endian format
 DE s8              PCM signed 8 bit format
 D  sdp             SDP
 D  shn             raw Shorten
 D  siff            Beam Software SIFF
 D  smk             Smacker video
 D  sol             Sierra SOL format
  E svcd            MPEG-2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             True Audio
 D  txd             txd format
 DE u16be           PCM unsigned 16 bit big-endian format
 DE u16le           PCM unsigned 16 bit little-endian format
 DE u24be           PCM unsigned 24 bit big-endian format
 DE u24le           PCM unsigned 24 bit little-endian format
 DE u32be           PCM unsigned 32 bit big-endian format
 DE u32le           PCM unsigned 32 bit little-endian format
 DE u8              PCM unsigned 8 bit format
 D  vc1             raw VC-1
 D  vc1test         VC-1 test bitstream format
  E vcd             MPEG-1 System format (VCD)
 D  video4linux     Video4Linux device grab
 D  video4linux2    Video4Linux2 device grab
 D  vmd             Sierra VMD format
  E vob             MPEG-2 PS format (VOB)
 DE voc             Creative Voice file format
 DE wav             WAV format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 D  x11grab         X11grab
 D  xa              Maxis XA File Format
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm             4X Movie
 D V D  8bps            QuickTime 8BPS video
 D A    8svx_exp        8SVX exponential
 D A    8svx_fib        8SVX fibonacci
 D A    aac             Advanced Audio Coding
 D V D  aasc            Autodesk RLE
 DEA    ac3             ATSC A/52A (AC-3)
 D A    adpcm_4xm       4X Movie ADPCM
 DEA    adpcm_adx       SEGA CRI ADX
 D A    adpcm_ct        Creative Technology ADPCM
 D A    adpcm_ea        Electronic Arts ADPCM
 D A    adpcm_ea_maxis_xa Electronic Arts Maxis CDROM XA ADPCM
 D A    adpcm_ea_r1     Electronic Arts R1 ADPCM
 D A    adpcm_ea_r2     Electronic Arts R2 ADPCM
 D A    adpcm_ea_r3     Electronic Arts R3 ADPCM
 D A    adpcm_ea_xas    Electronic Arts XAS ADPCM
 D A    adpcm_ima_amv   IMA AMV ADPCM
 D A    adpcm_ima_dk3   IMA Duck DK3 ADPCM
 D A    adpcm_ima_dk4   IMA Duck DK4 ADPCM
 D A    adpcm_ima_ea_eacs IMA Electronic Arts EACS ADPCM
 D A    adpcm_ima_ea_sead IMA Electronic Arts SEAD ADPCM
 D A    adpcm_ima_iss   IMA Funcom ISS ADPCM
 DEA    adpcm_ima_qt    IMA QuickTime ADPCM
 D A    adpcm_ima_smjpeg IMA Loki SDL MJPEG ADPCM
 DEA    adpcm_ima_wav   IMA Wav ADPCM
 D A    adpcm_ima_ws    IMA Westwood ADPCM
 DEA    adpcm_ms        Microsoft ADPCM
 D A    adpcm_sbpro_2   Sound Blaster Pro 2-bit ADPCM
 D A    adpcm_sbpro_3   Sound Blaster Pro 2.6-bit ADPCM
 D A    adpcm_sbpro_4   Sound Blaster Pro 4-bit ADPCM
 DEA    adpcm_swf       Shockwave Flash ADPCM
 D A    adpcm_thp       Nintendo Gamecube THP ADPCM
 D A    adpcm_xa        CDROM XA ADPCM
 DEA    adpcm_yamaha    Yamaha ADPCM
 DEA    alac            ALAC (Apple Lossless Audio Codec)
 D V    amv             AMV Video
 D A    ape             Monkey's Audio
 DEV D  asv1            ASUS V1
 DEV D  asv2            ASUS V2
 D A    atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
 D V D  avs             AVS (Audio Video Standard) video
 D V    bethsoftvid     Bethesda VID video
 D V    bfi             Brute Force & Ignorance
 DEV    bmp             BMP image
 D V D  c93             Interplay C93
 D V D  camstudio       CamStudio
 D V D  camtasia        TechSmith Screen Capture Codec
 D V D  cavs            Chinese AVS video (AVS1-P2, JiZhun profile)
 D V D  cinepak         Cinepak
 D V D  cljr            Cirrus Logic AccuPak
 D A    cook            COOK
 D V D  cyuv            Creative YUV (CYUV)
 D A    dca             DCA (DTS Coherent Acoustics)
 DEV D  dnxhd           VC3/DNxHD
 D A    dsicinaudio     Delphine Software International CIN audio
 D V D  dsicinvideo     Delphine Software International CIN video
 DES    dvbsub          DVB subtitles
 DES    dvdsub          DVD subtitles
 DEV D  dvvideo         DV (Digital Video)
 D V    dxa             Feeble Files/ScummVM DXA
 D A    eac3            ATSC A/52B (AC-3, E-AC-3)
 D V D  eacmv           Electronic Arts CMV Video
 D V D  eatgq           Electronic Arts TGQ Video
 D V    eatgv           Electronic Arts TGV Video
 D V D  escape124       Escape 124
 DEV D  ffv1            FFmpeg codec #1
 DEVSD  ffvhuff         Huffyuv FFmpeg variant
 DEA    flac            FLAC (Free Lossless Audio Codec)
 DEV D  flashsv         Flash Screen Video
 D V D  flic            Autodesk Animator Flic video
 DEVSD  flv             Flash Video
 D V D  fraps           Fraps
 DEA    g726            G.726 ADPCM
 DEV    gif             GIF (Graphics Interchange Format)
 DEV D  h261            H.261
 DEVSDT h263            H.263 / H.263-1996
 D VSD  h263i           Intel H.263
  EV    h263p           H.263+ / H.263-1998 / H.263 version 2
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 DEVSD  huffyuv         Huffyuv / HuffYUV
 D V D  idcinvideo      id Quake II CIN video
 D A    imc             IMC (Intel Music Coder)
 D V D  indeo2          Intel Indeo 2
 D V    indeo3          Intel Indeo 3
 D A    interplay_dpcm  Interplay DPCM
 D V D  interplayvideo  Interplay MVE Video
 DEV D  jpegls          JPEG-LS
 D V    kmvc            Karl Morton's video codec
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
 D A    libfaad         libfaad AAC (Advanced Audio Codec)
 DEA    libgsm          libgsm GSM
 DEA    libgsm_ms       libgsm GSM Microsoft variant
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
 DEV    libschroedinger libschroedinger Dirac 2.2
 D A    libspeex        libspeex
  EV    libtheora       libtheora Theora
  EA    libvorbis       libvorbis Vorbis
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libxvid         libxvidcore MPEG-4 part 2
  EV    ljpeg           Lossless JPEG
 D V D  loco            LOCO
 D A    mace3           MACE (Macintosh Audio Compression/Expansion) 3:1
 D A    mace6           MACE (Macintosh Audio Compression/Expansion) 6:1
 D V D  mdec            Sony PlayStation MDEC (Motion DECoder)
 D V D  mimic           Mimic
 DEV D  mjpeg           MJPEG (Motion JPEG)
 D V D  mjpegb          Apple MJPEG-B
 D A    mlp             Meridian Lossless Packing
 D V D  mmvideo         American Laser Games MM Video
 D V D  motionpixels    Motion Pixels Video
 D A    mp1             MP1 (MPEG audio layer 1)
 DEA    mp2             MP2 (MPEG audio layer 2)
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 D A    mpc7            Musepack SV7
 D A    mpc8            Musepack SV8
 DEVSDT mpeg1video      MPEG-1 video
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 DEVSDT mpeg2video      MPEG-2 video
 DEVSDT mpeg4           MPEG-4 part 2
 D VSDT mpegvideo       MPEG-1 video
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D VSDT mpegvideo_xvmc  MPEG-1 video XvMC (X-Video Motion Compensation)
 DEVSD  msmpeg4         MPEG-4 part 2 Microsoft variant version 3
 DEVSD  msmpeg4v1       MPEG-4 part 2 Microsoft variant version 1
 DEVSD  msmpeg4v2       MPEG-4 part 2 Microsoft variant version 2
 D V D  msrle           Microsoft RLE
 D V D  msvideo1        Microsoft Video 1
 D V D  mszh            LCL (LossLess Codec Library) MSZH
 DEA    nellymoser      Nellymoser Asao Codec
 D V D  nuv             NuppelVideo
 DEV    pam             PAM (Portable AnyMap) image
 DEV    pbm             PBM (Portable BitMap) image
 DEA    pcm_alaw        A-law PCM
 D A    pcm_dvd         signed 20|24-bit big-endian PCM
 DEA    pcm_f32be       32-bit floating point big-endian PCM
 DEA    pcm_f32le       32-bit floating point little-endian PCM
 DEA    pcm_f64be       64-bit floating point big-endian PCM
 DEA    pcm_f64le       64-bit floating point little-endian PCM
 DEA    pcm_mulaw       mu-law PCM
 DEA    pcm_s16be       signed 16-bit big-endian PCM
 DEA    pcm_s16le       signed 16-bit little-endian PCM
 D A    pcm_s16le_planar 16-bit little-endian planar PCM
 DEA    pcm_s24be       signed 24-bit big-endian PCM
 DEA    pcm_s24daud     D-Cinema audio signed 24-bit PCM
 DEA    pcm_s24le       signed 24-bit little-endian PCM
 DEA    pcm_s32be       signed 32-bit big-endian PCM
 DEA    pcm_s32le       signed 32-bit little-endian PCM
 DEA    pcm_s8          signed 8-bit PCM
 DEA    pcm_u16be       unsigned 16-bit big-endian PCM
 DEA    pcm_u16le       unsigned 16-bit little-endian PCM
 DEA    pcm_u24be       unsigned 24-bit big-endian PCM
 DEA    pcm_u24le       unsigned 24-bit little-endian PCM
 DEA    pcm_u32be       unsigned 32-bit big-endian PCM
 DEA    pcm_u32le       unsigned 32-bit little-endian PCM
 DEA    pcm_u8          unsigned 8-bit PCM
 DEA    pcm_zork        Zork PCM
 D V    pcx             PC Paintbrush PCX image
 DEV    pgm             PGM (Portable GrayMap) image
 DEV    pgmyuv          PGMYUV (Portable GrayMap YUV) image
 DEV    png             PNG image
 DEV    ppm             PPM (Portable PixelMap) image
 D V    ptx             V.Flash PTX image
 D A    qcelp           QCELP / PureVoice
 D A    qdm2            QDesign Music Codec 2
 D V D  qdraw           Apple QuickDraw
 D V D  qpeg            Q-team QPEG
 DEV D  qtrle           QuickTime Animation (RLE) video
 DEV    rawvideo        raw video
 D A    real_144        RealAudio 1.0 (14.4K)
 D A    real_288        RealAudio 2.0 (28.8K)
 D V D  rl2             RL2 video
 DEA    roq_dpcm        id RoQ DPCM
 DEV D  roqvideo        id RoQ video
 D V D  rpza            QuickTime video (RPZA)
 DEV D  rv10            RealVideo 1.0
 DEV D  rv20            RealVideo 2.0
 D V D  rv30            RealVideo 3.0
 D V D  rv40            RealVideo 4.0
 DEV    sgi             SGI image
 D A    shorten         Shorten
 D A    smackaud        Smacker audio
 D V    smackvid        Smacker video
 D V D  smc             QuickTime Graphics (SMC)
 DEV    snow            Snow
 D A    sol_dpcm        Sol DPCM
 DEA    sonic           Sonic
  EA    sonicls         Sonic lossless
 D V D  sp5x            Sunplus JPEG (SP5X)
 D V    sunrast         Sun Rasterfile image
 DEV D  svq1            Sorenson Vector Quantizer 1
 D VSD  svq3            Sorenson Vector Quantizer 3
 DEV    targa           Truevision Targa image
 D V    theora          Theora
 D V D  thp             Nintendo Gamecube THP video
 D V D  tiertexseqvideo Tiertex Limited SEQ video
 DEV    tiff            TIFF image
 D V D  truemotion1     Duck TrueMotion 1.0
 D V D  truemotion2     Duck TrueMotion 2.0
 D A    truespeech      DSP Group TrueSpeech
 D A    tta             True Audio
 D V    txd             Renderware TXD (TeXture Dictionary) image
 D V D  ultimotion      IBM UltiMotion
 D V    vb              Beam Software VB
 D V    vc1             SMPTE VC-1
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  vcr1            ATI VCR1
 D A    vmdaudio        Sierra VMD audio
 D V D  vmdvideo        Sierra VMD video
 D V    vmnc            VMware Screen Codec / VMware Video
 DEA    vorbis          Vorbis
 D V    vp3             On2 VP3
 D V D  vp5             On2 VP5
 D V D  vp6             On2 VP6
 D V D  vp6a            On2 VP6 (Flash version, with alpha channel)
 D V D  vp6f            On2 VP6 (Flash version)
 D V D  vqavideo        Westwood Studios VQA (Vector Quantized Animation) video
 D A    wavpack         WavPack
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V    wmv3            Windows Media Video 9
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
 D V D  wnv1            Winnov WNV1
 D A    ws_snd1         Westwood Audio (SND1)
 D A    xan_dpcm        Xan DPCM
 D V D  xan_wc3         Wing Commander III / Xan
 D V D  xl              Miro VideoXL
 D S    xsub            XSUB
 DEV D  zlib            LCL (LossLess Codec Library) ZLIB
 DEV    zmbv            Zip Motion Blocks Video

Bitstream filters:
 text2movsub remove_extra noise mov2textsub mp3decomp mp3comp mjpegadump imxdump h264_mp4toannexb dump_extra
Supported file protocols:
 file: http: pipe: rtp: tcp: udp:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.
```

ffmpeg -i doa4_christineending.flv
```
FFmpeg version UNKNOWN-svn16978+3:0.svn20090204-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn16978+3:0.svn20090204-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-xvmc --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb  5 2009 21:02:21, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'doa4_christineending.flv':
  Duration: 00:01:11.33, start: 0.000000, bitrate: 914 kb/s
    Stream #0.0: Video: flv, yuv420p, 448x336, 818 kb/s, 29.97 tb(r)
    Stream #0.1: Audio: mp3, 44100 Hz, mono, s16, 96 kb/s
At least one output file must be specified
```

Can anyone please help me figure out what I need to do to convert it?  I have never used ffmpeg before now...

Thanks!

---

### Post by mikewu on 2009-02-19
Try reading through this thread. Someone posted a nice bash script for multiple conversions, as well as a single command for one file.

[http://ubuntuforums.org/showthread.php?t=343537](http://ubuntuforums.org/showthread.php?t=343537)

They said that:
ffmpeg -i movie.flv -vcodec wmv1 -acodec adpcm_ima_wav movie.wmv

Try and see if that works. If it doesn't, the audio codec looks a bit strange. Maybe try switching it to one of the wmv audio codecs that you posted.

Also those wmv1 would be for Windows Media Video 7. Changing to wmv2 or wmv3 might affect whether the file plays. 

Good luck.

---

### Post by andrew.46 on 2009-02-19
Hi,

I am no expert but I believe that wmv videos are most commonly held in an asf container along with audio in Windows Media Audio format. Of course other containers are possible and some videos have the wmv suffix etc etc.

FFmpeg can deal with these:

```
ffmpeg -formats | grep -i wmv
[...]
  built on Feb 16 2009 17:19:19, gcc: 4.2.4
DEVSD  wmv1            Windows Media Video 7
DEVSD  wmv2            Windows Media Video 8
D V    wmv3            Windows Media Video 9
```

and:

```
ffmpeg -formats | grep -i wma
[...]
built on Feb 16 2009 17:19:19, gcc: 4.2.4
DEA    wmav1           Windows Media Audio 1
DEA    wmav2           Windows Media Audio 2
```

So one option is to convert to these formats:

```
$ ffmpeg -i infile.flv -vcodec wmv2 -sameq -acodec wmav2 -f asf outfile.asf
``` 

I will admit that I have not tested these on windows media player, in part because I loathe this software :-). I would be interested to hear if this works though?

Andrew

---

### Post by Nixie Pixel on 2009-03-01
By the way, I forgot to mention this, but your instructions worked like a charm, thank you!

---

### Post by angelsguitar on 2009-03-01
Hi. I know you already solved this, but, have you tried WinFF? It is a GUI front-end to ffmpeg.  I've been using it and works very nice.  Although it has a name that suggests it is a Win application, they have versions for different plataforms, including Linux.  See here for more info on how to install:

[http://winff.org]("http://winff.org")

BTW, nice blog!

---

### Post by andrew.46 on 2009-03-01
Hi Nixie Pixel,

> **Nixie Pixel said:**
> By the way, I forgot to mention this, but your instructions worked like a charm, thank you!

My solution or mikewu's :-). BTW I have just had a look though your blog and saw the references to the Ubuntu Forums there, you have probably heard of [the Beginner's Team]("http://ubuntuforums.org/showthread.php?t=848814") which attempts to make the Ubuntu experience a little smoother on these forums? Besides being a generally good guy I am a part of this team :-).

All the best,

Andrew

---

### Post by Nixie Pixel on 2009-05-19
It was your solution, Andrew - you were the inspiration for my latest video.  I gave you a shout out at the end :)

[Video tutorial - converting files with ffmpeg]("http://www.youtube.com/watch?v=iIalNEW-LQ8&fmt=18")

---

### Post by andrew.46 on 2009-05-19
Hi Nixie Pixel,

> **Nixie Pixel said:**
> It was your solution, Andrew - you were the inspiration for my latest video.  I gave you a shout out at the end :)

[Video tutorial - converting files with ffmpeg]("http://www.youtube.com/watch?v=iIalNEW-LQ8&fmt=18")

Wooo hoooo I am famous!! I had a look at the other youtube clips you have put together, looks great!

All the best,

Andrew

---

### Post by KanineN on 2009-05-19
I have the same problem but I want to convert it to .mp4. How do I do that?

---

### Post by lukeiamyourfather on 2009-05-20
> **KanineN said:**
> I have the same problem but I want to convert it to .mp4. How do I do that?

Change the output codec and the output filename to MP4. So instead of using this:

```
ffmpeg -i movie.flv -vcodec wmv1 -acodec adpcm_ima_wav movie.wmv
```

Use this:

```
ffmpeg -i movie.flv -vcodec mp4 -acodec aac movie.mp4
```

It might not work depending on where FFMPEG came from since MP4 is a proprietary codec. Downloading all of the codec libraries and then building FFMPEG from source is the best way to get support for the most formats and codecs. Cheers!

---

### Post by FakeOutdoorsman on 2009-05-24
> **lukeiamyourfather said:**
> Change the output codec and the output filename to MP4. So instead of using this:

```
ffmpeg -i movie.flv -vcodec wmv1 -acodec adpcm_ima_wav movie.wmv
```

Use this:

```
ffmpeg -i movie.flv -vcodec mp4 -acodec aac movie.mp4
```

I bet you meant *-vcodec mpeg4* since there is no *-vcodec mp4* option as far as I know.

> It might not work depending on where FFMPEG came from since MP4 is a proprietary codec. Downloading all of the codec libraries and then building FFMPEG from source is the best way to get support for the most formats and codecs. Cheers!

This describes how to enable most encoders in FFmpeg:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by zeeler on 2009-06-04
by the way, how to convert .flv to .wmv(wmv3)?

---

### Post by igorzwx on 2009-06-05
wmv3 might be a problem :)

Do you really need such things?

On Terminal: ffmpeg -formats

Google mencoder for high quality settings

MEncoder seems to be a universal solution to all such problems (flv, ogg, theora, etc.).
It is also a great video editor (command line).
FFmpeg is also great!

EXAMPLES:

Grab screen to wmv2 (on Ubuntu 8.10 and Ubuntu 9.04, better grab to avi on Ubuntu 9.04)

ffmpeg -s 800x600 -r 25 -f x11grab -i :0.0 -s 800x600 -r 25 -vcodec wmv2 -aspect 1.3333 -sameq grab-to-wmv2.wmv

Result: grab-to-wmv2.wmv

NOTE: this wmv file is not likely to be played by Totem, but it can be converted to mpg2.
      VLC plays this wmv without problems.

Convert wmv2 to mpg2

ffmpeg -i input-wmv2.wmv -f mpeg2video -sameq output-mpg2.mpg

Result: output-mpg2.mpg

!!!!!!!!  -sameq means same video quality !!!!!!!!

-f means format

Convert mpg2 to avi

mencoder -forceidx -mc 0 -noskip -skiplimit 0 -ovc lavc -lavcopts vcodec=msmpeg4v2:vhq -o output.avi input-mpg2.mpg

Result: output.avi  (it is said to be Windoze-friendly)

or

mencoder -forceidx -mc 0 -noskip -skiplimit 0 -ovc lavc -lavcopts vcodec=mpeg4:vhq:mbd=2:trell:v4mv:vbitrate=9800 -o output.avi input-mpg2.mpg

Result: output.avi

I do not know what all these abracadabra really mean, but it works well.


WinFF is also great, but it is of little help.

1. it is easy to use

2. but the default settings produce low quality results

3. it is virtually impossible to understand how to get a better quality encoding

4. no video tutorials, e.g. screencasts

5. it seems to be mostly Windoze app

The blog [http://winff.org](http://winff.org) is very nice indeed!
Some more docs and sceencasts, and it may become the most popular blog in the web.

---

### Post by andrew.46 on 2009-06-09
Hi Nixie,

> **Nixie Pixel said:**
> It was your solution, Andrew - you were the inspiration for my latest video.

One small correction to my own syntax is that the *-f asf* is not really necessary here as FFmpeg will normally create an asf container based on the *.asf* suffix on the output file. Really I guess this option is used to *force* a format against default FFmpeg behaviour. But this is a minor point :-).

Andrew

---

