---
title: "VDPAU playback in Gnome MPlayer and SMPlayer"
date: 2010-05-25
forum: System76 Support
---

### Post by tmette on 2010-05-25
I have VDPAU set as the output video driver for both of these applications.  However, only SMPLayer only runs 1080p files smoothly.  Is there a reason why Gnome MPlayer runs it really choppy?  Thinking about just un-installing MPlayer since I like SMPlayer better anyways.

Also, I get an error code every time a file ends in SMPlayer and I believe it has something to do with the VDPAU output driver.  Anyone know how to resolve this?  Here is the error log I receive:

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 62914903 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/todd/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -nocache -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/todd/Downloads/i_am_legend-1080p_trailer/I Am Legend - Trailer.mp4

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/todd/Downloads/i_am_legend-1080p_trailer/I Am Legend - Trailer.mp4.
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] Video stream found, -vid 0
ID_AUDIO_ID=1
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  1920x816  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: I Am Legend - Trailer
ID_CLIP_INFO_NAME0=name
ID_CLIP_INFO_VALUE0=I Am Legend - Trailer
 author: Warner Bros.
ID_CLIP_INFO_NAME1=author
ID_CLIP_INFO_VALUE1=Warner Bros.
 genre: Science-Fiction
ID_CLIP_INFO_NAME2=genre
ID_CLIP_INFO_VALUE2=Science-Fiction
ID_CLIP_INFO_N=3
ID_FILENAME=/home/todd/Downloads/i_am_legend-1080p_trailer/I Am Legend - Trailer.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=816
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=255
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=123.24
ID_SEEKABLE=1
ID_CHAPTERS=0
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=faad
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1920 x 816 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=2.3529
VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 
[Mixer] No hardware mixing, inserting volume filter.



MPlayer interrupted by signal 11 in module: unknown
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]
```


EDIT:

I found something else I'm going to need help with.  As of now, whenever I plug my headphones into the front panel of the Meerkat, it doesn't mute the volume coming through my LCD speakers.  Is there any way to have it mute the LCD speakers whenever I plug in headphones?



I know I'm having a lot of problems, but I'm so new with Ubuntu!

---

### Post by rvm4000 on 2010-05-26
Try to update your mplayer to see if it fixes the crash.

You can find a newer version here:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by tmette on 2010-05-26
> **rvm4000 said:**
> Try to update your mplayer to see if it fixes the crash.

You can find a newer version here:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Hmm..I will try this out this evening.  Wouldn't the one I obtained through the Ubuntu Software Center be the most up-to-date version though?

---

### Post by rvm4000 on 2010-05-26
> **tmette said:**
> Wouldn't the one I obtained through the Ubuntu Software Center be the most up-to-date version though?

No. Look at the date in the version number: MPlayer SVN-r1.0~rc3+svn**20090426**. It's more than a year old.

The one in my ppa is 2:1.0~rc3+svn**20100416**-0lucid3, a month old.

(Ubuntu usually includes very old versions of mplayer)

---

### Post by isantop on 2010-05-26
Also, there's the usual "Make sure your System is updated"

Open a terminal (Applications > Accessories > Terminal) and enter```
sudo apt-get update && sudo apt-get upgrade -y
``` followed by enter.

About the Headphones. Is your monitor connected with HDMI? If so, try plugging your headphones into the monitor. Alternatively, try plugging your LCD speakers into the sound jack in the back of the computer.

---

### Post by tmette on 2010-05-26
> **rvm4000 said:**
> No. Look at the date in the version number: MPlayer SVN-r1.0~rc3+svn**20090426**. It's more than a year old.

The one in my ppa is 2:1.0~rc3+svn**20100416**-0lucid3, a month old.

(Ubuntu usually includes very old versions of mplayer)

Ahh, I see it now.  Thanks for the tip!

> **isantop said:**
> Also, there's the usual "Make sure your System is updated"

Open a terminal (Applications > Accessories > Terminal) and enter```
sudo apt-get update && sudo apt-get upgrade -y
``` followed by enter.

About the Headphones. Is your monitor connected with HDMI? If so, try plugging your headphones into the monitor. Alternatively, try plugging your LCD speakers into the sound jack in the back of the computer.

Cool, doing the update & upgrade now.  No, my sound is coming out of the green port in the back into a stereo audio in in the back of my Monitor/TV.

---

### Post by YuiDaoren on 2010-06-10
> **rvm4000 said:**
> Try to update your mplayer to see if it fixes the crash.

You can find a newer version here:
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")
***Thank you*** for this PPA, it has saved me some headaches. :KS

---

