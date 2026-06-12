---
title: "ffmpeg newly installed"
date: 2009-10-18
forum: Server Platforms
---

### Post by adman4054 on 2009-10-18
I have installed, uninstalled, reinstalled......
My last attempt was today and I used Medibuntu I uninstalled ffmpeg but I notice from the attached log:

**built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)**

Does this mean that my install of today (Mar 18) didnt take?
```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
[wmv3 @ 0xb7eb96e8]Extra data: 8 bits left, value: 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from '/home/xxxxxxx/Public/xxxxx/admin/../movies/Movie_xxxxxxx.wmv':
  Duration: 00:04:53.5, start: 5.000000, bitrate: 242 kb/s
  Stream #0.0: Audio: wmav2, 32000 Hz, stereo, 24 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 320x240, 30.00 fps(r)
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, rawvideo, to '/home/xxxxx/Public/xxxxxx/admin/../flvfiles/245376.png':
  Stream #0.0: Video: png, rgb24, 110x90, q=2-31, 200 kb/s, 30.00 fps(c)
Stream mapping:
  Stream #0.1 -> #0.0
[wmv3 @ 0xb7eb96e8]Extra data: 8 bits left, value: 0
Press [q] to stop encoding
frame=    1 q=0.0 Lsize=       0kB time=0.0 bitrate=  26.2kbits/s    

video:0kB audio:0kB global headers:0kB muxing overhead 0.000000%

```
----------------------------------------------------------------
From the log above I have both audio and video input, but no output. I thought by downloading from Medibuntu, it would take care of that.

I also dont think I have the proper encoders:

from ffmpeg formats:

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

So my questions:

Did my new install of today not *Take*, for lack of a better term

If it didnt, how can I just start over?

Thanks for all the help on these issues

---

### Post by FakeOutdoorsman on 2009-10-18
What version of Ubuntu are you using?  I am guessing that you are using Ubuntu Hardy Heron.  Your output looks odd because your FFmpeg "configuration" line looks like FFmpeg from Medibuntu, but the list of formats looks like they are from FFmpeg from the Ubuntu repository.

Also, show your FFmpeg command.

Lastly, show the output of:
```
aptitude show ffmpeg
```

---

### Post by adman4054 on 2009-10-18
> **FakeOutdoorsman said:**
> What version of Ubuntu are you using?  I am guessing that you are using Ubuntu Hardy Heron.  Your output looks odd because your FFmpeg "configuration" line looks like FFmpeg from Medibuntu, but the list of formats looks like they are from FFmpeg from the Ubuntu repository.

Thanks for the reply, yes I'm using Hardy Heron




Also, show your FFmpeg command.
```

startcode               .DV..
   pts                     .DV..
   er                      .DV.. error resilience
   mmco                    .DV.. memory management control operations (H.264)
   bugs                    .DV..
   vis_qp                  .DV.. visualize quantization parameter (QP), lower QP are tinted greener
   vis_mb_type             .DV.. visualize block types
-vismv             <int>   .DV.. visualize motion vectors (MVs)
   pf                      .DV.. forward predicted MVs of P-frames
   bf                      .DV.. forward predicted MVs of B-frames
   bb                      .DV.. backward predicted MVs of B-frames
-mb_qmin           <int>   E.V.. obsolete, use qmin
-mb_qmax           <int>   E.V.. obsolete, use qmax
-cmp               <int>   E.V.. full pel me compare function
   sad                     E.V.. sum of absolute differences, fast (default)
   sse                     E.V.. sum of squared errors
   satd                    E.V.. sum of absolute Hadamard transformed differences
   dct                     E.V.. sum of absolute DCT transformed differences
   psnr                    E.V.. sum of squared quantization errors (avoid, low quality)
   bit                     E.V.. number of bits needed for the block
   rd                      E.V.. rate distortion optimal, slow
   zero                    E.V.. 0
   vsad                    E.V.. sum of absolute vertical differences
   vsse                    E.V.. sum of squared vertical differences
   nsse                    E.V.. noise preserving sum of squared differences
   w53                     E.V.. 5/3 wavelet, only used in snow
   w97                     E.V.. 9/7 wavelet, only used in snow
   dctmax                  E.V..
   chroma                  E.V..
-subcmp            <int>   E.V.. sub pel me compare function
   sad                     E.V.. sum of absolute differences, fast (default)
   sse                     E.V.. sum of squared errors
   satd                    E.V.. sum of absolute Hadamard transformed differences
   dct                     E.V.. sum of absolute DCT transformed differences
   psnr                    E.V.. sum of squared quantization errors (avoid, low quality)
   bit                     E.V.. number of bits needed for the block
   rd                      E.V.. rate distortion optimal, slow
   zero                    E.V.. 0
   vsad                    E.V.. sum of absolute vertical differences
   vsse                    E.V.. sum of squared vertical differences
   nsse                    E.V.. noise preserving sum of squared differences
   w53                     E.V.. 5/3 wavelet, only used in snow
   w97                     E.V.. 9/7 wavelet, only used in snow
   dctmax                  E.V..
   chroma                  E.V..
-mbcmp             <int>   E.V.. macroblock compare function
   sad                     E.V.. sum of absolute differences, fast (default)
   sse                     E.V.. sum of squared errors
   satd                    E.V.. sum of absolute Hadamard transformed differences
   dct                     E.V.. sum of absolute DCT transformed differences
   psnr                    E.V.. sum of squared quantization errors (avoid, low quality)
   bit                     E.V.. number of bits needed for the block
   rd                      E.V.. rate distortion optimal, slow
   zero                    E.V.. 0
   vsad                    E.V.. sum of absolute vertical differences
   vsse                    E.V.. sum of squared vertical differences
   nsse                    E.V.. noise preserving sum of squared differences
   w53                     E.V.. 5/3 wavelet, only used in snow
   w97                     E.V.. 9/7 wavelet, only used in snow
   dctmax                  E.V..
   chroma                  E.V..
-ildctcmp          <int>   E.V.. interlaced dct compare function
   sad                     E.V.. sum of absolute differences, fast (default)
   sse                     E.V.. sum of squared errors
   satd                    E.V.. sum of absolute Hadamard transformed differences
   dct                     E.V.. sum of absolute DCT transformed differences
   psnr                    E.V.. sum of squared quantization errors (avoid, low quality)
   bit                     E.V.. number of bits needed for the block
   rd                      E.V.. rate distortion optimal, slow
   zero                    E.V.. 0
   vsad                    E.V.. sum of absolute vertical differences
   vsse                    E.V.. sum of squared vertical differences
   nsse                    E.V.. noise preserving sum of squared differences
   w53                     E.V.. 5/3 wavelet, only used in snow
   w97                     E.V.. 9/7 wavelet, only used in snow
   dctmax                  E.V..
   chroma                  E.V..
-dia_size          <int>   E.V.. diamond type & size for motion estimation
-last_pred         <int>   E.V.. amount of motion predictors from the previous frame
-preme             <int>   E.V.. pre motion estimation
-precmp            <int>   E.V.. pre motion estimation compare function
   sad                     E.V.. sum of absolute differences, fast (default)
   sse                     E.V.. sum of squared errors
   satd                    E.V.. sum of absolute Hadamard transformed differences
   dct                     E.V.. sum of absolute DCT transformed differences
   psnr                    E.V.. sum of squared quantization errors (avoid, low quality)
   bit                     E.V.. number of bits needed for the block
   rd                      E.V.. rate distortion optimal, slow
   zero                    E.V.. 0
   vsad                    E.V.. sum of absolute vertical differences
   vsse                    E.V.. sum of squared vertical differences
   nsse                    E.V.. noise preserving sum of squared differences
   w53                     E.V.. 5/3 wavelet, only used in snow
   w97                     E.V.. 9/7 wavelet, only used in snow
   dctmax                  E.V..
   chroma                  E.V..
-pre_dia_size      <int>   E.V.. diamond type & size for motion estimation pre-pass
-subq              <int>   E.V.. sub pel motion estimation quality
-me_range          <int>   E.V.. limit motion vectors range (1023 for DivX player)
-ibias             <int>   E.V.. intra quant bias
-pbias             <int>   E.V.. inter quant bias
-coder             <int>   E.V..
   vlc                     E.V.. variable length coder / huffman coder
   ac                      E.V.. arithmetic coder
-context           <int>   E.V.. context model
-mbd               <int>   E.V.. macroblock decision algorithm (high quality mode)
   simple                  E.V.. use mbcmp (default)
   bits                    E.V.. use fewest bits
   rd                      E.V.. use best rate distortion
-sc_threshold      <int>   E.V.. scene change threshold
-lmin              <int>   E.V.. min lagrange factor (VBR)
-lmax              <int>   E.V.. max lagrange factor (VBR)
-nr                <int>   E.V.. noise reduction
-rc_init_occupancy <int>   E.V.. number of bits which should be loaded into the rc buffer before decoding starts
-inter_threshold   <int>   E.V..
-flags2            <flags> EDVA.
   fast                    E.V.. allow non spec compliant speedup tricks
   sgop                    E.V.. strictly enforce gop size
   noout                   E.V.. skip bitstream encoding
   local_header            E.V.. place global headers at every keyframe instead of in extradata
   bpyramid                E.V.. allows B-frames to be used as references for predicting
   wpred                   E.V.. weighted biprediction for b-frames (H.264)
   mixed_refs              E.V.. one reference per partition, as opposed to one reference per macroblock
   8x8dct                  E.V.. high profile 8x8 transform (H.264)
   fastpskip               E.V.. fast pskip (H.264)
   aud                     E.V.. access unit delimiters (H.264)
   brdo                    E.V.. b-frame rate-distortion optimization
   skiprd                  E.V.. RD optimal MB level residual skiping
   ivlc                    E.V.. intra vlc table
   drop_frame_timecode         E.V..
   non_linear_q            E.V.. use non linear quantizer
-error             <int>   E.V..
-antialias         <int>   .DV.. MP3 antialias algorithm
   auto                    .DV..
   fastint                 .DV..
   int                     .DV..
   float                   .DV..
-qns               <int>   E.V.. quantizer noise shaping
-threads           <int>   EDV..
-mb_threshold      <int>   E.V.. macroblock threshold
-dc                <int>   E.V.. intra_dc_precision
-nssew             <int>   E.V.. nsse weight
-skip_top          <int>   .DV.. number of macroblock rows at the top which are skipped
-skip_bottom       <int>   .DV.. number of macroblock rows at the bottom which are skipped
-profile           <int>   E.VA.
   unknown                 E.VA.
-level             <int>   E.VA.
   unknown                 E.VA.
-lowres            <int>   .DV.. decode at 1= 1/2, 2=1/4, 3=1/8 resolutions
-skip_threshold    <int>   E.V.. frame skip threshold
-skip_factor       <int>   E.V.. frame skip factor
-skip_exp          <int>   E.V.. frame skip exponent
-skipcmp           <int>   E.V.. frame skip compare function
   sad                     E.V.. sum of absolute differences, fast (default)
   sse                     E.V.. sum of squared errors
   satd                    E.V.. sum of absolute Hadamard transformed differences
   dct                     E.V.. sum of absolute DCT transformed differences
   psnr                    E.V.. sum of squared quantization errors (avoid, low quality)
   bit                     E.V.. number of bits needed for the block
   rd                      E.V.. rate distortion optimal, slow
   zero                    E.V.. 0
   vsad                    E.V.. sum of absolute vertical differences
   vsse                    E.V.. sum of squared vertical differences
   nsse                    E.V.. noise preserving sum of squared differences
   w53                     E.V.. 5/3 wavelet, only used in snow
   w97                     E.V.. 9/7 wavelet, only used in snow
   dctmax                  E.V..
   chroma                  E.V..
-border_mask       <float> E.V.. increases the quantizer for macroblocks close to borders
-mblmin            <int>   E.V.. min macroblock lagrange factor (VBR)
-mblmax            <int>   E.V.. max macroblock lagrange factor (VBR)
-mepc              <int>   E.V.. motion estimation bitrate penalty compensation (1.0 = 256)
-bidir_refine      <int>   E.V.. refine the two motion vectors used in bidirectional macroblocks
-brd_scale         <int>   E.V.. downscales frames for dynamic B-frame decision
-crf               <float> E.V.. enables constant quality mode, and selects the quality (x264)
-cqp               <int>   E.V.. constant quantization parameter rate control method
-keyint_min        <int>   E.V.. minimum interval between IDR-frames (x264)
-refs              <int>   E.V.. reference frames to consider for motion compensation (Snow)
-chromaoffset      <int>   E.V.. chroma qp offset from luma
-bframebias        <int>   E.V.. influences how often B-frames are used
-trellis           <int>   E.VA. rate-distortion optimal quantization
-directpred        <int>   E.V.. direct mv prediction mode - 0 (none), 1 (spatial), 2 (temporal)
-complexityblur    <float> E.V.. reduce fluctuations in qp (before curve compression)
-deblockalpha      <int>   E.V.. in-loop deblocking filter alphac0 parameter
-deblockbeta       <int>   E.V.. in-loop deblocking filter beta parameter
-partitions        <flags> E.V.. macroblock subpartition sizes to consider
   parti4x4                E.V..
   parti8x8                E.V..
   partp4x4                E.V..
   partp8x8                E.V..
   partb8x8                E.V..
-sc_factor         <int>   E.V.. multiplied by qscale for each frame and added to scene_change_score
-mv0_threshold     <int>   E.V..
-b_sensitivity     <int>   E.V.. adjusts sensitivity of b_frame_strategy 1
-compression_level <int>   E.VA.
-use_lpc           <int>   E..A. sets whether to use LPC mode (FLAC)
-lpc_coeff_precision <int>   E..A. LPC coefficient precision (FLAC)
-min_prediction_order <int>   E..A.
-max_prediction_order <int>   E..A.
-prediction_order_method <int>   E..A. search method for selecting prediction order
-min_partition_order <int>   E..A.
-max_partition_order <int>   E..A.
-timecode_frame_start <int>   E.V.. GOP timecode frame start number, in non drop frame format
AVFormatContext AVOptions:
-probesize         <int>   .D...
-muxrate           <int>   E.... set mux rate
-packetsize        <int>   E.... set packet size
-fflags            <flags> ED...
   ignidx                  .D... ignore index
   genpts                  .D... generate pts
-track             <int>   E....  set the track number
-year              <int>   E.... set the year
-analyzeduration   <int>   .D...


```







Lastly, show the output of:
```
aptitude show ffmpeg
```

```

Package: ffmpeg
State: installed
Automatically installed: yes
Version: 3:0.cvs20070307-5ubuntu7.3+medibuntu1
Priority: optional
Section: free/graphics
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Uncompressed Size: 664k
Depends: libavcodec1d (>= 0.cvs20070307), libavformat1d (>= 0.cvs20070307), libavutil1d (>=
         0.cvs20070307), libc6 (>= 2.7), libfreetype6 (>= 2.3.5), libimlib2,
         libsdl1.2debian (>= 1.2.10-1), libswscale1d (>= 0.cvs20070307)
Description: multimedia player, server and encoder - Medibuntu package
 This package contains the ffplay multimedia player, the ffserver streaming server and the
 ffmpeg audio and video encoder. They support most existing file formats (AVI, MPEG, OGG,
 Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3, DV...).

 This package is built with the "risky" option, to enable mp3/mp4/h264/amr support.
 Therefore, it is in Medibuntu as it might violate patents.

 This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!

 Please report any bug to our bug tracker instead:
 https://bugs.launchpad.net/medibuntu/+bugs


```

---

### Post by FakeOutdoorsman on 2009-10-18
Sorry, I meant to show your FFmpeg conversion command.

---

### Post by adman4054 on 2009-10-18
> **FakeOutdoorsman said:**
> Sorry, I meant to show your FFmpeg conversion command.

Appreciate you spending the time:)

[code]
//upload video
if(isset($_POST['submit'])) { 

/***************Load FFMPEG *********************************/

$extension = "ffmpeg";

$extension_soname = $extension . "." . PHP_SHLIB_SUFFIX;

$extension_fullname = PHP_EXTENSION_DIR . "/" . $extension_soname;





// load extension

if (!extension_loaded($extension)) {

dl($extension_soname) or die("Can't load extension $extension_fullname\n");

}



/***********************************************************/



/*****************Get the path to Extention ****************/



$array_path = explode("/",$_SERVER['SCRIPT_FILENAME']);

$dynamic_path = "";

for ($i=0;$i<sizeof($array_path)-1;$i++)

if($array_path[$i]!="")

$dynamic_path =$dynamic_path."/".$array_path[$i];

/**********************************************************/



/******************set folders*****************************/

$flvpath = "../flvfiles/";
$moviepath = "../movies/" ;

/*********************************************************/



/******************Upload and convert video *****************************/
if(isset($_FILES["x_URL"]))

{

$fileName = $_FILES["x_URL"]["name"];

$fileNameParts = explode( ".", $fileName );

$fileExtension = end( $fileNameParts );

$fileExtension = strtolower( $fileExtension );

if($fileExtension=="avi" || $fileExtension=="wmv" || $fileExtension=="mpeg" 
|| $fileExtension=="mpg" || $fileExtension=="mov" )

{

if ( move_uploaded_file($_FILES["x_URL"]["tmp_name"],$moviepath.$_FILES["x_URL"]["name"]) 
)

{


// Make multiples function
function makeMultipleTwo ($value)
{
$sType = gettype($value/2);
if($sType == "integer")
{
return $value;
} else {
return ($value-1);
}
}


// Set our source file
$srcFile = $dynamic_path."/".$moviepath."".$fileName;
$destFile = $dynamic_path."/".$flvpath ."".$listingID.".flv";
$ffmpegPath = "/usr/bin/ffmpeg";
$flvtool2Path = "/usr/bin/flvtool2";

// Create our FFMPEG-PHP class
$ffmpegObj = new ffmpeg_movie($srcFile);

// Save our needed variables
$srcWidth = makeMultipleTwo($ffmpegObj->getFrameWidth());
$srcHeight = makeMultipleTwo($ffmpegObj->getFrameHeight());
$srcFPS = $ffmpegObj->getFrameRate();
$srcAB = intval($ffmpegObj->getAudioBitRate()/1000);
$srcAR = $ffmpegObj->getAudioSampleRate();

// Call our convert using exec()
exec($ffmpegPath . " -i " . $srcFile . " -ar " . $srcAR . " -ab " . $srcAB . " -f flv -s " . $srcWidth . "x" . $srcHeight . " " . $destFile);


/******************create thumbnail***************/
exec($ffmpegPath ." -y -i ".$dynamic_path."/".$moviepath."".$fileName." -vframes 1 -ss 00:00:03 -an -vcodec png -f rawvideo -s 110x90 ".$dynamic_path."/".$flvpath.$listingID.".png");

$videoPath =$listingID.".flv";
$imagePath =$listingID.".png";

//insert into db here
$insertquery = sprintf
("INSERT INTO video (
listingID, videoPath, imagePath
) VALUES (
'%s', '%s', '%s')", 						
quote_for_safety($listingID),
quote_for_safety($videoPath),
quote_for_safety($imagePath)
);

mysql_query($insertquery);

//delete Original Video
	$pathToMovieFile = "../movies";
	
    $old = getcwd(); // Save the current directory
    chdir($pathToMovieFile);
    unlink($fileName);
    chdir($old); // Restore the old working directory

---

### Post by FakeOutdoorsman on 2009-10-18
Ruh roh.  I didn't know you were using PHP.  Did you write this PHP code?  Are you using *php5-ffmpeg*?  I have no experience with this package, but a quick and dirty test made it seem compatible with *libavcodec1d* and *libavformat1d* from the Medibuntu repository.  I don't think *php5-ffmpeg* even uses the FFmpeg binary, but it uses the *libav** library files from FFmpeg.

I found your other post: [ffmpeg/make/checkinstall?](http://ubuntuforums.org/showthread.php?p=8126762)  Your error looks like it is related to the PHP script and not any actual problem with FFmpeg, libavcodec1d, or libavformat1d (unless it is an odd package management error).

However, I'm unsure why your FFmpeg version and format outputs don't seem to match.  Maybe I'm missing something obvious.

---

### Post by adman4054 on 2009-10-19
> **FakeOutdoorsman said:**
> Ruh roh.  I didn't know you were using PHP.  Did you write this PHP code?  Are you using *php5-ffmpeg*?  I have no experience with this package, but a quick and dirty test made it seem compatible with *libavcodec1d* and *libavformat1d* from the Medibuntu repository.  I don't think *php5-ffmpeg* even uses the FFmpeg binary, but it uses the *libav** library files from FFmpeg.

I found your other post: [ffmpeg/make/checkinstall?](http://ubuntuforums.org/showthread.php?p=8126762)  Your error looks like it is related to the PHP script and not any actual problem with FFmpeg, libavcodec1d, or libavformat1d (unless it is an odd package management error).

However, I'm unsure why your FFmpeg version and format outputs don't seem to match.  Maybe I'm missing something obvious.

Thanks for the reply-- Yes PHP5, When I look for the matching codec, for example an avi file, it isnt there, are codecs part of the library you are refering to? Is it possible that during these installs and reinstalls I didnt get he rights libs, what is the best way to check?

Thanks for all the help!

---

### Post by adman4054 on 2009-10-19
I looked around at the ffmpeg php5 docs and in this paticular script it appears to me that we are using php just to move things around. Does that make sense?
From the script:
```

// Set our source file
$srcFile = $dynamic_path."/".$moviepath."".$fileName;
$destFile = $dynamic_path."/".$flvpath ."".$listingID.".flv";
[B]$ffmpegPath = "/usr/bin/ffmpeg";
$flvtool2Path = "/usr/bin/flvtool2";[/B]

// Create our FFMPEG-PHP class
$ffmpegObj = new ffmpeg_movie($srcFile);

// Save our needed variables
$srcWidth = makeMultipleTwo($ffmpegObj->getFrameWidth());
$srcHeight = makeMultipleTwo($ffmpegObj->getFrameHeight());
$srcFPS = $ffmpegObj->getFrameRate();
$srcAB = intval($ffmpegObj->getAudioBitRate()/1000);
$srcAR = $ffmpegObj->getAudioSampleRate();

// Call our convert using exec()
exec($ffmpegPath . " -i " . $srcFile . " -ar " . $srcAR . " -ab " . $srcAB . " -f flv -s " . $srcWidth . "x" . $srcHeight . " " . $destFile);

```

---

### Post by adman4054 on 2009-10-19
I'm trying to see if I have a script issue by running ffmpeg from the command line: 

```
ffmpeg -i video.avi -ar 22050 -ab 32 -f flv -s 320×240 video.flv
```

Where is ffmpeg looking for this example avi file. In other words where would I upload an example video to test this.

Thanks

---

### Post by adman4054 on 2009-10-19
I figured out where I needed to put the video:

I ran this command:
```

ffmpeg -i /tmp/AANQ11.mov -ar 22050 -ab 32 -f flv -s 320×240 video.flv

```
and received this:
```

root@stuff2:~# ffmpeg -i /tmp/AANQ11.mov -ar 22050 -ab 32 -f flv -s 320×240 video.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/AANQ11.mov':
  Duration: 00:02:06.1, start: 0.000000, bitrate: 731 kb/s
  Stream #0.0(eng): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(eng): Video: svq3, yuv420p, 360x240, 29.97 fps(r)
Output #0, flv, to 'video.flv':
  Stream #0.0: Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 29.97 fps(c)
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
frame= 3778 q=10.8 Lsize=    3465kB time=126.1 bitrate= 225.2kbits/s
video:3406kB audio:0kB global headers:0kB muxing overhead 1.738636%

```
Which looks like it worked fine except the audio.
Any thoughts?
Thanks!

---

### Post by adman4054 on 2009-10-19
Testing othetr inputs:

**MP4**

```

root@stuff2:~# ffmpeg -i /tmp/birdman_512kb.mp4 -ar 22050 -ab 32 -f flv -s 320×240 video.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/birdman_512kb.mp4':
  Duration: 00:00:27.3, start: 0.000000, bitrate: 566 kb/s
  Stream #0.0(und): Video: h264, yuv420p, 320x240, 15.00 fps(r)
  Stream #0.1(und): Audio: mp4a / 0x6134706D, 16000 Hz, stereo
File 'video.flv' already exists. Overwrite ? [y/N] y
Output #0, flv, to 'video.flv':
  Stream #0.0: Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 15.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=  410 q=11.9 Lsize=     911kB time=27.3 bitrate= 272.9kbits/s
video:904kB audio:0kB global headers:0kB muxing overhead 0.728777%

```
**WMV**
```

root@stuff2:~# ffmpeg -i /tmp/Movie_mobilegraphics.wmv -ar 22050 -ab 32 -f flv -s 320×240 video.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
/tmp/Movie_mobilegraphics.wmv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
root@stuff2:~# ffmpeg -i /tmp/Movie_mobilegraphics.wmv -ar 22050 -ab 32 -f flv -s 320×240 video.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
/tmp/Movie_mobilegraphics.wmv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
root@stuff2:~#

```

---

### Post by adman4054 on 2009-10-19
I entered a codec on the line command according to a posting I found Googling and received audio output! still doesnt play, but does that help to narrow down the problem?

Thanks

```

root@stuff2:~# ffmpeg -i /tmp/AANQ11.mov -vcodec copy -acodec ac3 -ab 384k test.mpg -acodec mp2 -ab 192k -newaudio

```
```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/AANQ11.mov':
  Duration: 00:02:06.1, start: 0.000000, bitrate: 731 kb/s
  Stream #0.0(eng): Audio: aac, 44100 Hz, stereo
  Stream #0.1(eng): Video: svq3, yuv420p, 360x240, 29.97 fps(r)
Output #0, mpeg, to 'test.mpg':
  Stream #0.0: Video: SVQ3 / 0x33515653, yuv420p, 360x240, q=2-31, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 44100 Hz, stereo, 384 kb/s
  Stream #0.2: Audio: mp2, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
  Stream #0.0 -> #0.2
Press [q] to stop encoding
frame= 3778 q=0.2 Lsize=   18390kB time=126.1 bitrate=1195.1kbits/s    /s
video:9353kB audio:8865kB global headers:0kB muxing overhead 0.944348%

```

---

### Post by FakeOutdoorsman on 2009-10-19
Your error from your other post made it look like a PHP script error because FFmpeg doesn't automatically know what format an output file named 0 should be.  You need to have your script give a valid extension such as *0.mpg*, or manually tell FFmpeg what 0 should be with the *-f* option as in *-f mp4 0*.  That solves the **Unable for find a suitable output format for '0' error**.

Your WMV file is most likely corrupt or damaged which results in FFmpeg not reading it.  The MP4 and FLV may have DRM audio.  I'm not sure.  You should also know that your version of FFmpeg is quite old and may simply have a hard time decoding these files.  However, it still doesn't explain the discrepency between your format list and FFmpeg version.

Give the full output of:
```
aptitude show libavcodec1d
```

It should say that it is from Medibuntu.  Also check in the Synaptic Package Manager for any conflicting or broken packages.

Give the full output of:
```
ffmpeg -formats
```

---

### Post by adman4054 on 2009-10-19
> **FakeOutdoorsman said:**
> Your error from your other post made it look like a PHP script error because FFmpeg doesn't automatically know what format an output file named 0 should be.  You need to have your script give a valid extension such as *0.mpg*, or manually tell FFmpeg what 0 should be with the *-f* option as in *-f mp4 0*.  That solves the **Unable for find a suitable output format for '0' error**.

Your WMV file is most likely corrupt or damaged which results in FFmpeg not reading it.  The MP4 and FLV may have DRM audio.  I'm not sure.  You should also know that your version of FFmpeg is quite old and may simply have a hard time decoding these files.  However, it still doesn't explain the discrepency between your format list and FFmpeg version.

Give the full output of:
```
aptitude show libavcodec1d
```
```

root@stuff2:~# aptitude show libavcodec1d
Package: libavcodec1d
State: installed
Automatically installed: no
Version: 3:0.cvs20070307-5ubuntu7.3+medibuntu1
Priority: optional
Section: free/libs
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Uncompressed Size: 4743k
Depends: liba52-0.7.4, libavutil1d (>= 0.cvs20070307), libc6 (>= 2.7), libfaac0
         (>= 1.26), libgsm1 (>= 1.0.12), liblame0 (>= 3.97), libtheora0,
         libvorbis0a (>= 1.2.0), libvorbisenc2 (>= 1.1.2), libx264-57 (>=
         1:0.svn20071224), libxvidcore4 (>= 1:1.0.0-0.0), zlib1g (>=
         1:1.2.3.3.dfsg-1)
Description: ffmpeg codec library - Medibuntu package
 This is the codec library from the ffmpeg project. It supports most existing
 encoding formats (MPEG, DivX, MPEG4, AC3, DV...).

 This package contains a Debian-specific version of the libavcodec shared object
 that should only be used by Debian packages.

 This package is built with the "risky" option, to enable mp3/mp4/h264/amr
 support. Therefore, it is in Medibuntu as it might violate patents.

 This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!

 Please report any bug to our bug tracker instead:
 https://bugs.launchpad.net/medibuntu/+bugs


```






It should say that it is from Medibuntu.  Also check in the Synaptic Package Manager for any conflicting or broken packages.

Give the full output of:
```
ffmpeg -formats
```

```

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
 DEA    aac
 D V D  aasc
 DEA    ac3
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
 DEA    amr_nb
 DEA    amr_wb
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
 DEV DT h264
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
 DEA    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
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
  EV    xvid
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

```

I did a couple of other tests, the first one was converting from mov to fla and the second one was mov to mov (maybe there isnt really a conversion process with the second because they are both mov files) but I did receive audio with the second if that helps. Thank you for your assistance!!!!

```


root@stuff2:~# ffmpeg -i /tmp/AANQ11.mov -ar 22050 /tmp/test.flv


FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/AANQ11.mov':
  Duration: 00:02:06.1, start: 0.000000, bitrate: 731 kb/s
  Stream #0.0(eng): Audio: aac, 44100 Hz, stereo
  Stream #0.1(eng): Video: svq3, yuv420p, 360x240, 29.97 fps(r)
Output #0, flv, to '/tmp/test.flv':
  Stream #0.0: Video: flv, yuv420p, 360x240, q=2-31, 200 kb/s, 29.97 fps(c)
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
frame= 3778 q=12.9 Lsize=    3508kB time=126.1 bitrate= 227.9kbits/s
video:3448kB audio:0kB global headers:0kB muxing overhead 1.717171%


root@stuff2:~# ffmpeg -i /tmp/AANQ11.mov -ar 22050 /tmp/test.mov


FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/AANQ11.mov':
  Duration: 00:02:06.1, start: 0.000000, bitrate: 731 kb/s
  Stream #0.0(eng): Audio: aac, 44100 Hz, stereo
  Stream #0.1(eng): Video: svq3, yuv420p, 360x240, 29.97 fps(r)
Output #0, mov, to '/tmp/test.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 360x240, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 22050 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame= 3778 q=4.7 Lsize=    4362kB time=125.9 bitrate= 283.8kbits/s
video:3441kB audio:867kB global headers:0kB muxing overhead 1.235430%

```

---

### Post by adman4054 on 2009-10-19
Sorry, I'm not sure how to do this:

"Also check in the Synaptic Package Manager for any conflicting or broken packages"

You mention that my version of ffmpeg is old, if you can point me in the right direction to "undo" the stuff I have done and "redo" to a new version, I'd be more then happy to do that. I noticed you have quite a tutorial on how to install ffmpeg, me being such a newbie to Ubuntu I think I would just need a little help with the undo.

Thanks a a bunch!

PS-- on the formats I provided, is that everything or am I cutting some stuff off at the top because its so long.

---

### Post by FakeOutdoorsman on 2009-10-19
Now your formats list looks correct and it appears that you have the correct *libavcodec1d*.  Why is the formats list different than the one on your original post (*D A mp3* vs *DEA mp3* for example)?  I believe there is nothing wrong with your FFmpeg package.

If you want to undo what you did then follow the **D. Uninstalling FFmpeg and the Medibuntu Repository** section of:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now follow the FFmpeg installation guide:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by adman4054 on 2009-10-19
> **FakeOutdoorsman said:**
> Now your formats list looks correct and it appears that you have the correct *libavcodec1d*.  Why is the formats list different than the one on your original post (*D A mp3* vs *DEA mp3* for example)?  I believe there is nothing wrong with your FFmpeg package.

If you want to undo what you did then follow the **D. Uninstalling FFmpeg and the Medibuntu Repository** section of:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now follow the FFmpeg installation guide:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

I appreciate all the help Fakeoutdoorsman, just one more question. What would you recommend? If I'm testing on the command line and it isnt working, would you reinstall from medibuntu? compile the latest version? My only concern is all the libs and any other dependencies that I could screw up.
Thanks again!

---

### Post by FakeOutdoorsman on 2009-10-20
> **adman4054 said:**
> I appreciate all the help Fakeoutdoorsman, just one more question. What would you recommend? If I'm testing on the command line and it isnt working, would you reinstall from medibuntu? compile the latest version? My only concern is all the libs and any other dependencies that I could screw up.
Thanks again!

I always use a compiled FFmpeg, but I am using it directly and not with a PHP script or with php5-ffmpeg.  I use a recent FFmpeg because I do a good amount of video encoding at work.  You may want to use whatever will work best with php5-ffmpeg, if that is what you are using, and that is probably FFmpeg from the Ubuntu repository, but it is crippled with fewer encoders.  The version from Medibuntu would be a good second choice.  Compiling may work, but you may need to change the compile options from what I show in the guide.  php5-ffmpeg is a third-party application not related to the FFmpeg project and I really have no experience with it.

If it is not working from the command line, then it could be a number of problems including working with uncommon formats, your FFmpeg could be too old, or your FFmpeg command could be bad.

---

