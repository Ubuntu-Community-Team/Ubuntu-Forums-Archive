---
title: "Simple guide to grab desktop with FFMPEG"
date: 2011-03-20
forum: Tutorials
---

### Post by shantiq on 2011-03-20
[SIZE="2"]**_How to grab desktop with FFMPEG[/SIZE]_**



1.  just desktop no sound
2.  desktop with microphone sound
3.  webcam with sound
4.  desktop with onboard sound (music **or** video)


1.    > 
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 25 -i :0.0 -sameq ./Desktop/mydesktop.mkv

higher quality

> ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 30 -qscale 1  -i :0.0  ./Desktop/mydesktop.mkv


2.  > ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x1024 -i :0.0 -acodec flac  -vcodec libx264  -threads 0 ./Desktop/mydesktop.mkv


make sure 1280x1024 matches your specs ....   if not change to suit your settings


3. > ffmpeg -f alsa -ac 2 -i pulse -f video4linux2 -i /dev/video0 -vcodec libx264 -acodec flac  -s 320x240 -r 30 -y ./Desktop/mywebcam.mkvi


4. > sudo apt-get install pavucontrol

find pavucontrol in applications/sound and video

click on recording/click on box/pick monitor of internal audio   

 *Nota Bene: [COLOR="Red"]you may need to run* [/COLOR] the code below in your terminal first to bring up the options on pavucontrol 

Then run as in 2.

> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x1024 -i :0.0 -acodec flac  -vcodec libx264  -threads 0 ./Desktop/mydesktop.mkv                       or .avi


**DO NOT** forget to reset your pavucontrol at the end otherwise next time you try do microphone recording settings will be wrong

---

### Post by Jose Catre-Vandis on 2011-03-22
Nice work :)

---

### Post by rocuan on 2011-04-15
Thank You !!

Dropped it in a bash script :
```

#!/bin/bash
dir="$HOME/Poker/Screens/Vids"
size=$( xdpyinfo | grep 'dimensions:' | awk '{print $2}' )
name=$( date +'%b.%d_%I:%M%#p' )
video="$dir/$name.mkv"
term="gnome-terminal --geometry 78x2+5-2 -t "recording" -x"
$term ffmpeg -f x11grab -s $size -r 30 -qscale 1  -i :0.0 $video

```Tied it to a hotkey( Ctrl+PrtSc ) :
  > - Main Menu->System->Preferences->Keyboard Shortcuts
  - add  the full path -> (ie) "/home/me/bin/screencap.sh"And caught a memory :

---

### Post by Jose Catre-Vandis on 2011-04-16
More options for x11grab - positioning of the grab area if less than your screen.

for example, if you want to capture 1024x768 from the middle of your 1920x1080 display

x position = 1920-1024 = 896 then /2 = 448
y position = 1080-768  = 312 then /2 = 156

then your command would read (using 1. from shantiq's examples):
> ffmpeg -f x11grab -s 1024x768 -r 25 -i :0.0+448,156 -sameq ./Desktop/mydesktop.mkv

---

### Post by rocuan on 2011-04-21
Jose, I tried the modification you suggested```
ffmpeg -f x11grab -s 1024x768 -r 25 -i :0.0+448,156 -sameq ./Desktop/mydesktop.mkv
```but it failed & threw this error
> 
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3
[x11grab @ 0x9619a60]device: :0.0+448,156 -> display: :0.0 x: 448 y: 156 width: 1024 height: 768
[x11grab @ 0x9619a60]shared memory extension  found
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  11


---

### Post by FakeOutdoorsman on 2011-04-21
> **Jose Catre-Vandis said:**
> More options for x11grab - positioning of the grab area if less than your screen.

for example, if you want to capture 1024x768 from the middle of your 1920x1080 display

x position = 1920-1024 = 896 then /2 = 448
y position = 1080-768  = 312 then /2 = 156
You can use *xwininfo* to figure out the coordinates for you by simply clicking on the window. More info about that (and much more):

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

> **Jose Catre-Vandis said:**
> then your command would read (using 1. from shantiq's examples):
```
ffmpeg -f x11grab -s 1024x768 -r 25 -i :0.0+448,156 -sameq ./Desktop/mydesktop.mkv 
```

**-sameq** does not mean same quality. The documentation was misleading, but it has been changed in recent FFmpeg to "use same quantizer as source". It's generally recommended to use -qscale instead of -sameq, and "-qscale 2" is generally considered visually lossless for MPEG-1/2/4.

---

### Post by shantiq on 2011-04-21
thnx for clarification Fake One


Yes [Verb3k]("http://ubuntuforums.org/showthread.php?t=1392026") knows his stuff


This is the section you refer to no doubt

> FAQ:

Q: How do I get the exact size and coordinates of a specific window I want to capture?
A: Use a command called &#8220;xwininfo&#8220;. Basically, you run this command and then click on the window that you want to capture. It will then print the window information to the terminal. This command prints a lot of information, but what you need are the following lines:

Absolute upper-left X:
Absolute upper-left Y:
Width:
Height:

If the command, for example, prints:

Absolute upper-left X: 383
Absolute upper-left Y: 184
Width: 665
Height: 486

Then, you will adapt it to FFmpeg like this:

```
-s 664x486 -i :0.0+383,184

```
Note that we used 664 instead of 665 for the width since ffmpeg only accepts resolutions divisible by 2.
You can use the following command line combination with "xwininfo" to only print the information you&#8217;ll be needing:

```
xwininfo | grep -e Width -e Height -e Absolute

```


Works like a dream! Great tool

---

### Post by rocuan on 2011-04-21
Love the forums. 
Thanks everyone

---

### Post by shantiq on 2011-07-16
also i find sometimes one wants to just grab desktop sound 


and this here really works well


[B]
1.[/B] Install pavucontrol and sox  ( pavucontrol for sound monitoring and sox for recording)



   ```
sudo apt-get install pavucontrol sox
```

**2.** Play music or video on desktop

**3.** open pavucontrol    ```
pavucontrol
``` or from applications/sound and video

4. 

 Run ```
rec nameyouwant.flac
```  


5.  On pavucontrol click on recording then pick "Monitor of analogue internal audio stereo "  **see image**

6.  Stop recording and start again now you have the correct sound monitoring
[B]
7.  At the end [/B] make sure to return pavucontrol to original setting of "internal analogue audio stereo"



===================================
===================================

**ps** if you want other formats

for lossless sound use flac above or for a thinner file ogg (112k) ```
rec nameyouwant.ogg
```

you can override settings thus

> By  default the encoding quality level is 3
              (which gives an encoded rate of approx. 112kbps), but  this  can
              be changed using the -C option (see above) with a number from -1
              to  10;  fractional  numbers  (e.g.   3.6)  are  also   allowed.


[B]example
[/B]   ```
rec   -c 9  nameyouwant.ogg

```





**OR** if you want a 128k mp3 you can add this functionality to sox thus (thanx Andrew46)   ```
sudo apt-get install sox libsox-fmt-all

```   then run ```
rec nameyouwant.mp3
```


And override this too

>   MP3 compression parameters can be selected using SoX's -C option
              as follows (note that the current syntax is subject to change):

              The primary parameter to the LAME encoder is the  bit  rate.  If
              the  value  of the -C value is a positive integer, it's taken as
              the bitrate in kbps (e.g. if you specify 128, it uses 128 kbps).
   **Example   **```
rec   -C 256 nameyouwant.mp3
```  or  ```
rec   -C 320  nameyouwant.mp3
```



other formats info **[here]("http://manpages.ubuntu.com/manpages/hardy/man7/soxformat.7.html") formats like dat cdda ircam are available if you like really high-end formats**

```
rec nameyouwant.dat
```   gives you a really heavy file of extremely good quality

---

### Post by X_Splinter on 2012-01-14
Thanks shantiq now I can record my desktop without problems

---

### Post by Yesirom on 2012-01-23
Thanks for opening a topic like this! :D

It's just what I need. To bad it doesn't work for me.
I start the script and it crashes (I think it's the pulse part because I have a identical script that works but the only difference is that instead of pulse it's hw:0,0).

I would like to have a working script that records the desktop, microphone and desktop sounds at the same time. 

Can someone help?

---

### Post by Sarys on 2012-08-03
Is it possible to record desktop, mic, desktop sound and webcam?

EDIT: and how do I know ffmpeg is recording and how to make it record?

---

### Post by brownd7380 on 2012-12-13
Hi! Can I stream my desktop live via udp in ffmpeg? Any help would be greatly apeciated!

---

### Post by FakeOutdoorsman on 2012-12-13
A good start might be:
```
ffmpeg -framerate ntsc -video_size 640x480 -f x11grab -i :0.0 -vcodec libx264 -crf 26 -preset fast -f mpegts udp://<hostname>:<port>
```

---

### Post by Jay_Kemper on 2013-10-02
I'm running into a problem where I can't capture more than 2048 pixels of my screen.  My screen width is 2560x1600.  Is there any way to downscale the resolution before I record/stream it live?

For option "-s 2560x1600', I get the error "swScaler: Compile time max width is 2048 change VOF/VOFW and recompile".

---

### Post by FakeOutdoorsman on 2013-10-02
Please include your ffmpeg command and the complete console output.

---

### Post by Jay_Kemper on 2013-10-03
ffmpeg -f x11grab -s woxga -r 20 -i :0.0 -f mpegts udp://192.168.4.111:1234


FFmpeg version SVN-r15261, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --incdir=/usr/include/ffmpeg --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --arch=x86_64 --extra-cflags=-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -fasm -std=c99 -fno-math-errno --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-avfilter --enable-avfilter-lavf --enable-postproc --enable-swscale --enable-pthreads --disable-static --enable-shared --enable-gpl --disable-debug --disable-optimizations --disable-stripping
  libavutil     49.10. 0 / 49.10. 0
  libavcodec    51.71. 0 / 51.71. 0
  libavformat   52.22. 1 / 52.22. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 1. 0 /  0. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb  4 2009 19:41:05, gcc: 4.1.2 20071124 (Red Hat 4.1.2-42)
[x11grab @ 0x191521b0]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 2560 height: 1600
[x11grab @ 0x191521b0]shared memory extension  found
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1380813980.541533, bitrate: -2147483 kb/s
    Stream #0.0: Video: rawvideo, rgb32, 2560x1600, -2147483 kb/s, 20.00 tb(r)
[B]swScaler: Compile time max width is 2048 change VOF/VOFW and recompile
Cannot get resampling context[/B]

When I change the resolution, (example 1280x800 half of screen), I only get the upper right quadrant.  I just want to know how I can resample the whole screen to a lower resolution.

---

### Post by FakeOutdoorsman on 2013-10-03
> **Jay_Kemper said:**
> 
```
FFmpeg version SVN-r15261, Copyright (c) 2000-2008 Fabrice Bellard, et al.
```
Wow, this is absolutely ancient. Where did you find this? What is your distro?

There have been at least 41582 updates to ffmpeg since your graybeard version. Not to be blunt, but you're wasting your time (and mine) using this.

Please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code).

---

### Post by Jay_Kemper on 2013-10-03
Turns out that the source code needs to be downloaded and built.  The version available from their git repo seems to handle higher resolutions.  In their compilation instructions, they do miss some required package that need to be installed.

From the original ffmpeg installed from the distribution repo

$ ffmpeg

FFmpeg version 0.6.5, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jan 29 2012 23:55:02 with gcc 4.1.2 20080704 (Red Hat 4.1.2-51)
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --disable-avisynth --extra-cflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -fPIC' --enable-avfilter --enable-avfilter-lavf --enable-libdirac --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-shared --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

$ git clone git://source.ffmpeg.org/ffmpeg.git ffmpeg

$ yum remove ffmpeg

$ cd ffmpeg

$ ./configure --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64  --mandir=/usr/share/man --incdir=/usr/include --disable-avisynth  --extra-cflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions  -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -fPIC'  --enable-avfilter --enable-avfilter-lavf --enable-libdirac  --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm  --enable-libmp3lame --enable-libopencore-amrnb  --enable-libopencore-amrwb --enable-libx264 --enable-gpl  --enable-nonfree --enable-postproc --enable-pthreads --enable-shared  --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab


It may say that some options aren't valid, just delete them and try again.  You might also get 

Xext not found

Open up your package manager and search for xext and install the dev packages.  Same for Xfiles.

$ make

....


$ make install

$ ffmpeg -f x11grab -s 2560x1600 -r 20 -i :0.0 -s 1280x800 -f mpegts udp://192.168.0.1:1234

---

### Post by Merrattic on 2013-10-03
and ?

---

### Post by alf31 on 2013-10-04
great tutorial dude :D

---

