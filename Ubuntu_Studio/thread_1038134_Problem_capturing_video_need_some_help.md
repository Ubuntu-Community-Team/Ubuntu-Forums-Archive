---
title: "Problem capturing video need some help"
date: 2009-01-12
forum: Ubuntu Studio
---

### Post by roberto.eiberle on 2009-01-12
I am using tvtime to capture video from VCR, everything works kind of, but I get  dirty video with frequent horizontal streaks.I read just about everything available about ffmpeg and transcoder and ended up more confused than before. the command I use is

&#65279;#!/bin/sh
killall tvtime
sleep 4 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute &

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

gnome-terminal --execute transcode -x v4l2,v4l2 \
        -M 2 \
        -g 720x576 \
        -i /dev/video0 \
        -p /dev/dsp \
        -e 48000,16,2 \
        -N 0x1 \
        -J resample,levels,smartyuv \
        -w 6000 \
        -y ffmpeg \
        -F mjpeg \
        --lame_preset high \
        -o /home/roberto/Videos/-${TODAY}-${NOW}.avi \




amixer -q set "Line" 0% mute &



what I really would like to do is - capture to mpeg for DVD with audio included (not in a seperate file) and see the movie onscreen while capturing.the movie is clean as seen in tvtime without capturing, so my problem should arise in transcoding. I used to do this with xdtv - much easier - but I can't make it capture since I upgraded to 8.10. Please help.

---

### Post by soniccj7 on 2009-01-21
I am also trying to use xdtv to capture video. I am using a DVC100 capture card. 

I downloaded the source and was able to compile it on my system running Ubuntu 8.10 x64, but it always crashes. 


Thanks,

ED

$ xdtv -version
xdtv v2.4.1cvs14 running on Linux/x86_64 (2.6.27-9-generic)

error:


$ xdtv

This is xdtv 2.4.1cvs14 running on Linux/x86_64 (2.6.27-9-generic).
scandir: No such file or directory
filename = /home/ecook/.xdtv/xdtvrc
WARNING: xdtv_v4l-conf is compiled without DGA support.
/dev/video0 [v4l2]: no overlay support
xdtv_v4l-conf had some trouble, trying to continue anyway
xinerama 0: 1366x768+0+0
Warning: Missing charsets in String to FontSet conversion
wmhooks: netwm detected
wmhooks: netwm state above supported
wmhooks: netwm fullscreen supported
wmhooks: nothing found...
VidMode: server=2.2, include=2.2
  available video mode(s): 1366x768 1024x768 960x540 840x525 800x600 800x512 720x450 700x525 680x384 680x384 640x512 640x480 640x480 576x432 512x384 400x300 320x240
ioctl VIDIOC_G_FBUF: Invalid argument
classical overlay is disabled*** GRABBER DEVICE TYPE = v4l2
/home/ecook/.xdtv/xdtvrc:4: invalid value for norm: NTSC(null)
/home/ecook/.xdtv/xdtvrc:6: invalid value for source: DVC100 
Warning: Cannot convert string "-xxl-ledfixed-medium-r-semicondensed--39-120-75-75-c-180-*-*" to type FontStruct
Warning: Missing charsets in String to FontSet conversion
No MMX detected
Method glibc
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:593:(snd_pcm_dsnoop_open) unable to open slave
*** AUDIO DEVICE TYPE = dummyaudio
*** MIXER DEVICE TYPE = alsa

 You should launch XdTV with the -mixer_tvchan parameter.
 Goto the man page to get more informations about that switch.
 Your Alsa mixer doesn't propose any of those channels:

   Line, PCM, Capture, Aux, Wave Surround, Line-1
   SB Live Analog/Digital Output Jack or Master

 Select the good one for your own audio card.
 Or use OSS with the -noalsa parameter.

ioctl VIDIOC_S_STD: Invalid argument
VIDIOC_S_FREQUENCY: Invalid argument
asked for 384x576, and I have 352x288
try to run with -capt_width 352 -capt_height 288
      or -force_capt_width 352 -force_capt_height 288
      or -only_capt_width 352 -only_capt_height 288


Config File:

#
# Global options
#
norm = NTSC(null)
capture = grab
source = DVC100 
deinterlace = Linear Blend
subpage = 888
freqtab = secam-france

# You should uncomment this line
# and modify it by your own specific channel:
mixer_tvchan = Jack 

restoresnd = off
respectnullsnd = off
vop_autograb = on

xawpopup = on
message_timer = 3000
decoration = on
stayontop = off
subtitles = off
theme = (null)

#
# Fullscreen options
#
fullscreen = 640 x 480
fullscreen_mode = 3
pixsize = 128 x 96
windowsize = 384 x 288
colorkey = 123456
capture_size = 768 x 576
force_ratio = off
adjust_width = off

#
# Grab options
#
grab_filepath = /opt/xdtv/bin

#
# XOSD options
#
xosd = off

#
# record options
#
container = AVI
codec = FFMpeg Mpeg4
width = 384
height = 288
bitrate = 900
quality = 4
stereo_mode = no
audio_codec = UnCompressed
mp3_bitrate = 128
mp3_quality = 5
mp3_vbr_mode = no
mp3_vbr_quality = 8
fps = 25000
max_gap = 80
audio_fragments = 48
audio_sizefragment = 2048
min_quantizer = 2
max_quantizer = 8
audio_buffer_size = 1764
audio_freq = 44100
audio_fmt = s16le
display_frame = yes
record_sub = no
record_chg = no
record_delay = 0
streaming_mode = no
streaming_http_port = 63427
preview_player = mplayer -nofs -quiet -nosound 

#
# record advanced options
#
ffmpeg_v4mv = no
ffmpeg_naq = no
ffmpeg_gray = no
ffmpeg_gmc = no
ffmpeg_qpel = no
ffmpeg_ildct = no
ffmpeg_keyint = 250
ffmpeg_vmax_b_frames = 0
ffmpeg_vlelim = 0
ffmpeg_vcelim = 0
ffmpeg_lumi_mask = 0
ffmpeg_dark_mask = 0
ffmpeg_tcplx_mask = 0
ffmpeg_scplx_mask = 0
ffmpeg_dia = 0
ffmpeg_cmp = 0
ffmpeg_subcmp = 0
ffmpeg_trell = no
ffmpeg_last_pred = 0
ffmpeg_predia = 0
ffmpeg_precmp = 0
ffmpeg_umv = no
ffmpeg_aic = no
ffmpeg_mbd = 0
ffmpeg_cbp = no
ffmpeg_obmc = no
ffmpeg_ss = no
ffmpeg_aiv = no
ffmpeg_loop = no
ffmpeg_ilme = no

#
# eventmap
#

#
# alevt options
#
alevt_defaultpage = (null)
alevt_finetune_mode = none
alevt_finetune = (null)
alevt_error_reduction = yes
alevt_error_bell = yes
alevt_vbioffset = yes
alevt_charset = latin-1

# For each channel define at least following information
# [Channel Name]
# channel = Channel Number
# norm = PAL|NTSC|SECAM|AUTO
# key = key to press to switch the channel on (KP_End, KP_Next,...)
# capture = off|grabdisplay|overlay

---

