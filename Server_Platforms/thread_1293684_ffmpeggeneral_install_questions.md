---
title: "ffmpeg/general install questions"
date: 2009-10-17
forum: Server Platforms
---

### Post by adman4054 on 2009-10-17
Attention site moderators, I originally posted this in the "general help" forum. I think that was the wrong place to receive assistance. I checked the faq and site policies section for guidance in a situation like this and couldnt find anything, my apologies if I have broken a rule, it is not my intention.


I reinstalled ffmpeg because I needed a missing library for the vids to play audio. 
A couple of things-- 

I noticed the program is installed in root and the name of the folder that contains all the files is ffmpeg-0.cvs20070307, I assume it shouldnt be in the root and should I have changed the name at some point during the install. 
from the Apache log:
sh: /usr/bin/ffmpeg: not found

From the browser that uploads and converts the vid:

Warning: Module 'ffmpeg' already loaded in Unknown on line 0
Can't load extension /usr/lib/php5/20060613+lfs/ffmpeg.so 

I think I have almost got it, but these items are problems, can someone point me in the right direction?

Thanks in advance

---

### Post by Bachstelze on 2009-10-17
> **adman4054 said:**
> 
I reinstalled ffmpeg because I needed a missing library for the vids to play audio. 

Please explain in more detail what you did.

---

### Post by adman4054 on 2009-10-17
> **Bachstelze said:**
> Please explain in more detail what you did.

Thanks for the reply. I followed these instructions: [http://www.kookdujour.com/blog/details/59](http://www.kookdujour.com/blog/details/59)

---

### Post by Bachstelze on 2009-10-17
Okay. First, that directory you have in /root contains the source code, not the compiled binary. Second, ffmpeg got installed in /usr/local/bin. To install it in /usr/bin, pass the --prefix=/usr argument to ./configure.

---

### Post by adman4054 on 2009-10-17
> **Bachstelze said:**
> Okay. First, that directory you have in /root contains the source code, not the compiled binary. Second, ffmpeg got installed in /usr/local/bin. To install it in /usr/bin, pass the --prefix=/usr argument to ./configure.

Thanks for helping me out, but I'm very new to Ubuntu, linix and line commands. Sorry, but can you explain what I need to do?

---

### Post by Bachstelze on 2009-10-17
First uninstall your existing ffmpeg

```
sudo apt-get remove ffmpeg
```

Then go through the tutorial again, but instead of doing

```
./configure --enable-gpl --enable-pp --enable-libvorbis \
--enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 \
--enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad \
--enable-libfaac --enable-xvid --enable-pthreads --enable-x264
```

do

```
./configure --prefix=/usr --enable-gpl --enable-pp --enable-libvorbis \
--enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 \
--enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad \
--enable-libfaac --enable-xvid --enable-pthreads --enable-x264
```

When you'll be done, you should have a file at /usr/bin/ffmpeg.

---

### Post by adman4054 on 2009-10-17
> **Bachstelze said:**
> First uninstall your existing ffmpeg

```
sudo apt-get remove ffmpeg
```

Then go through the tutorial again, but instead of doing

```
./configure --enable-gpl --enable-pp --enable-libvorbis \
--enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 \
--enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad \
--enable-libfaac --enable-xvid --enable-pthreads --enable-x264
```

do

```
./configure --prefix=/usr --enable-gpl --enable-pp --enable-libvorbis \
--enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 \
--enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad \
--enable-libfaac --enable-xvid --enable-pthreads --enable-x264
```

When you'll be done, you should have a file at /usr/bin/ffmpeg.

Sorry, maybe didnt do something correctly in the original install--

```
sudo apt-get remove ffmpeg
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ffmeg


when I type ffmpeg at the prompt

```

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

---

### Post by Bachstelze on 2009-10-17
Hmm, qince you still have your source directory, try moving to it and doing

```
sudo make uninstall
```

---

### Post by adman4054 on 2009-10-17
> **Bachstelze said:**
> Hmm, qince you still have your source directory, try moving to it and doing

```
sudo make uninstall
```
Sorry, dont mean to make you regret answering. Move it? how do I do that?

---

### Post by Bachstelze on 2009-10-17
I mean use cd to navigate to the directory that contains the ffmpeg source, just like you did when you installed it.

---

### Post by adman4054 on 2009-10-17
> **Bachstelze said:**
> I mean use cd to navigate to the directory that contains the ffmpeg source, just like you did when you installed it.

Well, I didnt get the sound I was hoping for, but thats a differnce issue, no more errors, installed just as you said it would. Thanks for all the help!!:)

---

