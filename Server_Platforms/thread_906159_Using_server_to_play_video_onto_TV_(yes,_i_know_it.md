---
title: "Using server to play video onto TV (yes, i know it's a strange setup)"
date: 2008-08-31
forum: Server Platforms
---

### Post by markdavidoff on 2008-08-31
I am running ubuntu server as a fileserver in my room. I use a standard resolution TV as a monitor (with hardware RCA output, which is pretty neat).

That aside, since my server is connected to a TV I thought it would be cool to be able to play the videos on it through the TV, and so I have two questions:

1. How to i install and configure MPlayer (noGUI)?

2. How do I get sound to work?

I havent changed any resolution settings.

thanks

---

### Post by windependence on 2008-08-31
[http://www.go2linux.org/mplayer-command-line-music-video-player](http://www.go2linux.org/mplayer-command-line-music-video-player)

[http://mostlycli.blogspot.com/2007/09/images-and-videos-on-command-line-yes.html](http://mostlycli.blogspot.com/2007/09/images-and-videos-on-command-line-yes.html)

[http://ubuntuforums.org/showpost.php?p=5540466&postcount=4](http://ubuntuforums.org/showpost.php?p=5540466&postcount=4)

You don't need X for this, just follow the guides to use framebuffer.

-Tim

---

### Post by markdavidoff on 2008-08-31
ok cool

i added vga=786 at the end of the kernel line in the /boot/grub/menu.lst

how do i get video to scale itself full screen?

```
mplayer -vo fbdev -fs -vf scale=640:-3 FileName
``` didn't do it

also, how do i install codecs?

and more importantly, how do i get sound to work?

---

### Post by windependence on 2008-08-31
For the codecs and to play DVDs:

```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs
```

For sound, hmmmm.. you could try installing PulseAudio if it's in the repositories, I'm not sure. This may help:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

As for full screen, I don't have clue as I don't run anything GUI from any of my servers but your situation is different of course. Maybe someone out there has an idea.

-Tim

---

### Post by markdavidoff on 2008-08-31
medibuntu-keyring and w32codecs couldn't be found. I think there is a problem with that source file you directed me to.

and i had to install ubuntu-restricted-extras and libdvdcss2 separately (each on its own apt-get install command) for some reason.

Pulse Audio wasn't the answer - installing alsa works fine:

first, i installed ALSA and alsa-utils:

```
sudo apt-get install alsa alsa-utils
```

then i ran **alsamixer** and played around with the settings until i got sound output (tested using **aplay <sound file>**) and **speaker-test** (see [http://alsa.opensrc.org/index.php/Speaker-test](http://alsa.opensrc.org/index.php/Speaker-test) )

I then modified a MPlayer config file i found on the net as follows:

```
#General setup

ao="alsa" #audio out
mixer-channel="Master"
srate=48000

vo="fbdev" #video out
aid="1" #audio channel
sid="0" #subtitle set

fs=yes #Play Videos Full-Screen
zoom="1" #Allow sofware scaling if I use x11 for vo
monitoraspect="4:3" # Set to "16:9" for widescreen
vf="scale=640:-3" #Scales the video, and keeps the video's aspect ratio. Change "640" to your screen's resolution width

#Display

#double="yes" #double buffering(recommended for subtitles)
framedrop="1" # For slow machines
hardframedrop="0" #Make sure hard frame drop is off but can turn on easily now

#This sets the postprocessing into overdrive using all possible spare cpu cycles to make the movie look better
#autoq=100
#vf=pp=de,hqdn3d

#Subtitles

#Truetype fonts rock! (sudo apt-get msttcorefonts)
#font=/usr/share/fonts/truetype/msttcorefonts/impact.ttf

ffactor="10" #black outline
sub-bg-alpha="0" #background color ala closed captions
sub-bg-color="0" #black to white
subfont-text-scale="3.7" #truetype font scaling
subfont-blur="1" #Slight blur

subpos="90" #By default subtitles are too low
subalign="2"

```

---

### Post by markdavidoff on 2008-09-01
ok i got medibuntu-keyring and w32codecs to install (the server must have been down for a while yesterday)

still can't get my movie to play though:
I don't have a problem with most other videos, and I can play it with VLC (although it is rendered in coloured ASCII :P )

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2600+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.

Playing 300.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  720x576  12bpp  25.000 fps  998.0 kbps (121.8 kbyte/s)
Clip info:
 Software: MediaCoder 0.6
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 32.0 kbit/2.08% (ratio: 4000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0x886e8f0]SwScaler: BICUBIC scaler, from yuv420p to rgb32 using MMX2
[swscaler @ 0x886e8f0]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x886e8f0]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x886e8f0]SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
[swscaler @ 0x886e8f0]SwScaler: using MMX YV12->BGR32 Converter
[swscaler @ 0x886e8f0]SwScaler: 720x576 -> 1024x576
VO: [fbdev] 1024x576 => 1024x576 BGRA  [fs] [zoom]
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [fbdev] 1024x576 => 1024x576 BGRA  [fs] [zoom]
FATAL: Could not initialize video filters (-vf) or video output (-vo).)
Exiting... (End of file)

```

Does anyone know how to get full-screen scaling to work?

---

### Post by markdavidoff on 2008-09-01
Ok i figured out how to get full-screen scaling!

in your mplayer config file (in /home/<user>/.mplayer)

add/modify the following lines:

```
fs=yes #Play Videos Full-Screen
zoom="1" #Allow sofware scaling if I use x11 for vo
monitoraspect="4:3" # Set to "16:9" for widescreen
vf="scale=640:-3" #Scales the video, and keeps the video's aspect ratio. Change "640" to your screen's resolution
```

I changed the config file above to reflect these changes

Still can't get the codec to work...unless it's a different problem.

---

### Post by markdavidoff on 2008-09-03
*BUMP*

Any help?

I just need to get my video to play (missing codecs)

---

### Post by trash on 2008-09-10
i get fullscreen but really not sure how or why lol but here are the only 2 things different in out config..

vga=0x0314 as boot option(for whatever reason vga=0x0317 won't work for me)
and
scale=800:-3 anything higher than 800 doesn't work for me

no idea if this will help at all but i figured you wouldn't mind the bump

EDIT: forgot to mention i have no config file in ~/.mplayer

---

### Post by cariboo on 2008-09-10
To make sure you got all the codecs needed install the ubuntu-restricted extras meta package.

```
sudo aptitude install ubuntu-restricted-extras
```

Jim

---

### Post by trash on 2008-09-11
how did you get alsa and alsa-utils to install... i keep getting dependency problems??

---

### Post by markdavidoff on 2008-09-11
> **trash said:**
> how did you get alsa and alsa-utils to install... i keep getting dependency problems??

```
sudo apt-get build-dep alsa alsa-utils
```

---

### Post by markdavidoff on 2008-09-11
> **trash said:**
> i get fullscreen but really not sure how or why lol but here are the only 2 things different in out config..

vga=0x0314 as boot option(for whatever reason vga=0x0317 won't work for me)
and
scale=800:-3 anything higher than 800 doesn't work for me

no idea if this will help at all but i figured you wouldn't mind the bump

EDIT: forgot to mention i have no config file in ~/.mplayer


```
  VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits  640x480  800×600  1024×768  1152×864  1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   16   vga=785  vga=788   vga=791   vga=355   vga=794    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799
```

you can create your own config

nano /home/<username>/.mplayer/config

---

### Post by markdavidoff on 2008-09-11
> **cariboo907 said:**
> To make sure you got all the codecs needed install the ubuntu-restricted extras meta package.

```
sudo aptitude install ubuntu-restricted-extras
```

Jim

I installed that.

Still can't get 300.avi to work (I posted the Mplayer output when i mentioned this a few posts back)

works in vlc with acsii rendering though ;)

---

### Post by trash on 2008-09-11
> **markdavidoff said:**
> ```
sudo apt-get build-dep alsa alsa-utils
```

i still get negativity lol, no source package available for alsa... will just have to go n get it from their site which is what i was avoiding form the begining haha.

yes I did try a couple of configs but just never got it right till finally i got what i needed without.. will probably want to tweak eventually but onething at a time lol

---

### Post by markdavidoff on 2008-09-12
> **trash said:**
> i still get negativity lol, no source package available for alsa... will just have to go n get it from their site which is what i was avoiding form the begining haha.

yes I did try a couple of configs but just never got it right till finally i got what i needed without.. will probably want to tweak eventually but onething at a time lol

You may need to add or enable more sources in your repository list in /etc/apt/sources.list

look here:
[https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html](https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html)

don't forget to type:

sudo apt-get update

then try again

---

### Post by trash on 2008-09-12
> **markdavidoff said:**
> You may need to add or enable more sources in your repository list in /etc/apt/sources.list

look here:
[https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html](https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html)

don't forget to type:

sudo apt-get update

then try again

I tried everything, got too frustrated and reinstalled the server. 2nd time around Alsa installed no problem. :)

---

### Post by markdavidoff on 2008-09-12
I installed the codecs

i also installed ffmpeg

still can't get 300.avi to play with mplayer

any help?

---

### Post by markdavidoff on 2008-11-04
For those who upgraded to ubuntu 8.10, don't forget that to get the new medibuntu repository, use:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

and then don't forget to:

```
sudo apt-get update
```

and then re-install medibuntu-keyring and w32codecs (i did anyways):

```
sudo apt-get install medibuntu-keyring
sudo apt-get install w32codecs
```

if things don't work, you may need to re-enable your framebuffer by adding vga=xxx to your /boot/grub/menu.list at the end of the kernel line

```
  VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits  640x480  800×600  1024×768  1152×864  1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   16   vga=785  vga=788   vga=791   vga=355   vga=794    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799
```

---

