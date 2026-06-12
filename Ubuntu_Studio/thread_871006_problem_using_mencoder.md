---
title: "problem using mencoder"
date: 2008-07-26
forum: Ubuntu Studio
---

### Post by dlmoak on 2008-07-26
I'm trying to record audio/video with mencoder.  I am running 64-bit Ubuntu 8.04.  luvcview works fine.  I installed Ekiga to test and both audio and video work fine, I just have no need of Ekiga. I cannot get vlc to record either audio or video.  Camorama says "cannot connect to device /dev/video0." 

I have a logitech webcam which is recognized by lsusb as:
Bus 005 Device 004: ID 046d:0991 Logitech, Inc. 

lsmod returns the following:
uvcvideo               62084  0 
snd_usb_audio         100384  0 
snd_usb_lib            21120  1 snd_usb_audio
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev

When attempting to record audio and video I entered the following command (which I copied from another thread):

 mencoder tv:// -tv driver=**v4l2**:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/**audio1** -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

The two bold items are changes I made to the command due to error messages received.  The result of the command was as follows:

v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:0991)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Input/output error
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

I also tried recording only video and got the same failure.
Any suggestions?

---

### Post by Creative2 on 2008-07-27
:)
 try to see here 

[http://www.linuxtv.org/v4lwiki/index.php/Mencoder](http://www.linuxtv.org/v4lwiki/index.php/Mencoder)

---

### Post by dlmoak on 2008-07-27
Thanks, I'll check it out.

---

### Post by dlmoak on 2008-07-27
Thanks Creative2 -
I've used the following command to record a nice quality video:
mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -ofps 60 -nosound -ovc lavc -lavcopts vcodec=mjpeg -o test.avi

However, when I try different options to also record sound, I only get errors.  I have tried setting the adevice to both /dev/audio1 and also /dev /dsp1.  Do you have any suggestions?

---

### Post by dlmoak on 2008-07-27
> **dlmoak said:**
> Thanks Creative2 -
I've used the following command to record a nice quality video:
mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -ofps 60 -nosound -ovc lavc -lavcopts vcodec=mjpeg -o test.avi



I do get error messages with this command, but the video recording is fine - terminal output is below:

```
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:0991)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
[V] filefmt:9  fourcc:0x32595559  size:640x480  fps:60.00  ftime:=0.0167
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xdda790]SwScaler: BICUBIC scaler, from yuyv422 to yuv420p using MMX2
[swscaler @ 0xdda790]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xdda790]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xdda790]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xdda790]SwScaler: 640x480 -> 640x480
videocodec: libavcodec (640x480 fourcc=47504a4d [MJPG])
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
v4l2: select timeout

Skipping frame!
Pos:   0.0s      1f ( 0%)  0.96fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      2f ( 0%)  1.28fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Writing header...3f ( 0%)  1.67fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

4 duplicate frame(s)!
Pos:   0.1s      4f ( 0%)  2.09fps Trem:   0min   0mb  A-V:0.000 [0:0]
4 duplicate frame(s)!
Pos:   0.2s      5f ( 0%)  2.53fps Trem:   0min   0mb  A-V:0.000 [0:0]
4 duplicate frame(s)!
Pos:   0.2s      6f ( 0%)  2.93fps Trem:   0min   0mb  A-V:0.000 [0:0]

```

I've tried this command to include audio and get neither audio nor video.  Is the format correct?

```
 mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0:forceaudio -ofps 60 -oac lavc -ovc lavc -lavcopts vcodec=mpeg4:acodec=mp3 -o test.avi

The terminal response is:
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:0991)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Floating point exception
```

---

### Post by Creative2 on 2008-07-28
well first donì't use fps 60 (LOL)

then could you record something with audacity and at the same time open a terminal and type this 

```
 lsof /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/* 
```

and report what this command give you

---

### Post by dlmoak on 2008-07-28
Thanks, I'll try it out after I get home from work.  Just to be clear, I start the recording in audacity and simultaneously enter the command in terminal?

---

### Post by Creative2 on 2008-07-28
yep

---

### Post by dlmoak on 2008-07-29
Well, I cannot get audacity to record.  I get the error message that audacity is unable to access the input device.

---

### Post by Creative2 on 2008-07-30
mm that's means you have some problem with audio and so i think is not a mencoder problem ...but to be sure you should try with this

open a terminal and type and then execute:

```
rec /tmp/test.wav 
```

CRTL C to stop recording

if seems it have worked play the file /tmp/test.wav 


(if nothing is working plz make sure you have installed : 
```
sudo apt-get install sox libsox-fmt-all
```)

---

### Post by dlmoak on 2008-07-30
Thanks, I'll try it out tonight.

---

### Post by dlmoak on 2008-07-30
It created a file, but no sound when I played it.  I did have to install sox.

---

### Post by Creative2 on 2008-07-31
well the problem is your audio card it's not set very well  so mencoder cannot open your device to capture audio . 

you have to fix this problem first. IT very important install sox library to record better and set volumes on gnome-mixer or in kmix (kde)

---

### Post by dlmoak on 2008-07-31
Thanks for spending so much time to help.  The audio controller is built on the motherboard, not a separate card.  Ekiga doesn't seem to have any trouble recording.  I'll keep plugging away at it, but for now I think this will not be a first priority for me.

---

### Post by Creative2 on 2008-07-31
maybe you could find out what kind of input erika uses and so try somethings ... i don't know

---

