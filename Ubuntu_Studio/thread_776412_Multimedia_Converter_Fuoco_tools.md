---
title: "Multimedia Converter: Fuoco tools"
date: 2008-04-30
forum: Ubuntu Studio
---

### Post by Creative2 on 2008-04-30
[SIZE="6"][CENTER]**[COLOR="Blue"][B]Fuoco Tools**[/COLOR]
[/B][/CENTER][/SIZE]

[SIZE="5"][B] 
video promo   [/B][/SIZE]
 [http://www.youtube.com/watch?v=YtFWdlphAs8](http://www.youtube.com/watch?v=YtFWdlphAs8) 
[B]
-for problems you can find more here : [http://fuocotools.byethost13.com/index.php?board=4.0](http://fuocotools.byethost13.com/index.php?board=4.0)[/B]

[B]
screenshoot
[/B]

Converter tool 

[[IMG]http://www2.mediafire.com/imgbnc.php/5ac4a6f9484e2364fe449640a3694ebf5g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=92vxlsrogmj&thumb=4)




[SIZE="3"]**What is Fuoco tools?**[/SIZE]

Fuoco tools is born from The same ideas of ConvertIT, i rewrote every functions.. so is mainly a converter,but i have added some features, like Dvdwizard and Images2mpg plug in. I thinked to Fuoco like a faster way to learn mencoder , ffmpeg and company (basic learning) 



[CENTER]
**[SIZE="5"]Editing function with interface [/SIZE]**[/CENTER]
You can edit , delete or ADD fuction with this interface how you can see here 



[CENTER][B][SIZE="3"]To load a fuctioon double click on the commandline 
[/SIZE][/B][/CENTER]


[[IMG]http://www2.mediafire.com/imgbnc.php/74c222c2105347a921c6ae842bbbde653g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=reoxojn2dwj&thumb=4)



sometime it can happend commanline is not modified as you want, be carefull when you modify commandline with special characters if you have some problem you can edit one file as you can see below

[CENTER][SIZE="5"]**Editing function without interface**[/SIZE][/CENTER]

you can manage your function wiht a text editor with this 

```
nano $HOME/.fuoco/treestore.txt
```
Fuoco has a button to open your prefered text editoryou can choose 

 gedit or kate or nano (gnome or kde) 

a little example  :

```


YouTube?To DOWNLOAD?FLV to AVI Tag Download and convert!example avi conversion?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; mencoder 'OUTDIR/NUMBEROFTHEFILE.flv'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o 'OUTDIR/NUMBEROFTHEFILE.avi'


```

?= is a separator so we have

YouTube= **cathegory**
TO DOWNLOAD =** subcathegory**
FLV to AVI =**kind of conversion**  
 Download and convert!example avi conversion  =**tag**
youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; mencoder 'OUTDIR/NUMBEROFTHEFILE.flv'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o 'OUTDIR/NUMBEROFTHEFILE.avi'= **commandline**



note the command line 
```

youtube-dl  etc etc ; mencoder etc etc 
```
if you put      [SIZE="5"]; [/SIZE]        that command wil be used for every file in your list fist youtube and then mencoder 
instead if i put 
```

youtube etc etc ENDLOOP  mencoder etc etc 
```

This will execute  youtube-dl for every files in your list AND THEN  only 1 time mencoder etc etc 



[CENTER]**[SIZE="6"]INSTALLATION[/SIZE]**[/CENTER]


[SIZE="5"][B] 
Video [HOW TO] install   [/B][/SIZE]
[http://www.youtube.com/watch?v=dYVOd6GfSMM](http://www.youtube.com/watch?v=dYVOd6GfSMM)

If you have not medibuntu repo turned on you can use configurator (First loading and documentation)


[CENTER]
[SIZE="4"]--FIRST STEP ADD MEDIBUNTU REPO [/SIZE][/CENTER]




Below are the instructions to add the Medibuntu repository to your system's list of APT repositories. 
Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution. 

**Hardy 8.04**

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```


** Ubuntu 7.10 "Gutsy Gibbon":** ```

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```
[B]
 Ubuntu 7.04 "Feisty Fawn":[/B] 
```

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
```





[CENTER][SIZE="4"]--SECOND STEP, add the GPG Key  [/SIZE] [/CENTER]
 ```

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```



[CENTER][SIZE="4"]--THIRD STEP INSTALL THESE "SHELL PROGRAMS"[/SIZE][/CENTER]



this command line installs maybe everythings that you need (NB THERE IS K3B)

```
sudo apt-get install ffmpeg2theora mencoder mplayer  libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tools mp32ogg ffmpeg  imagemagick youtube-dl poppler-utils dvdauthor sox mjpegtools ffmpeg toolame gddrescue dvdbackup ccd2iso nrg2iso mdf2iso bchunk transcode k3b kipi-plugins kommander xterm 
```


[B]
youtube-dl issue[/B] i these days youtube has made something...so youtube-dl from ubuntu repo doesn't work anymore , if you are interested, here how fix youtube-dl 
[http://ubuntuforums.org/showthread.php?t=652843&page=5](http://ubuntuforums.org/showthread.php?t=652843&page=5)




i have installed all these programs and all works fine anyway :

ffmpeg2theora---------------------------------------------------------->ESSENTIAL
mencoder---------------------------------------------------------------> ESSENTIAL 
mplayer----------------------------------------------------------------->ESSENTIAL
libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tools-------> ESSENTIAL
mp32ogg--------------------------------------------------------------->faster mp3 to ogg encoder 
ffmpeg ----------------------------------------------------------------->ESSENTIAL
imagemagick-----------------------------------------------------------> converter for  photo
youtubedl---------------------------------------------------------------> download youtube video 
poppler-utils------------------------------------------------------------>text converter 
dvdauthor sox mjpegtools ffmpeg toolame------------------------->to run dvdwizard 
 transcode-------------------------------------------------------------->ESSENTIAL (avimerge avisplit are in this pack)
gddrescue dvdbackup ccd2iso nrg2iso mdf2iso bchunk---------> with this you can make dvd back up and convert iso image (nero image etc etc ..)
kipi-plugins--------------------------------------------------------------> to run make a video from my picture, it gets you images2mpg package
kommander-------------------------------------------------------------->ESSENTIAL if you have not you can't use fuoco tools 
k3b----------------------------------------------------------------------->it needs fot dvdwizar and to create a dvd with divx but if you don't plane to use that command line you don't need to install it
xterm-------------------------------------------------------------------->ESSENTIAL ...i know it should be installed by default but i have put in list....
axel----------------------------------------------------------------------> download with serveral connections usefull to download fast 






######################################
**OPTIONAL STEP YOU CAN SKIP THIS **

[CENTER]
[B]
[SIZE="3"]-- FOURTH STEP dvdwizard  installation [/SIZE][/B][/CENTER]



you need also of this 

[http://www.debian-multimedia.org/pool/main/d/dvdwizard/dvdwizard_0.5-0.0_all.deb](http://www.debian-multimedia.org/pool/main/d/dvdwizard/dvdwizard_0.5-0.0_all.deb) 

to install just right button on the file and install it
#####################################################################



[CENTER][B]
[SIZE="4"]-- FIVETH STEP  Interface's installation [/SIZE][/B][/CENTER]




you can CHOOSE AND download your version  

**full version** version has converter and images2mpg and dvdwizard--->1.3  MB

**only converter** version has  converter            --------------------->340  KB 

latest version :

atest version :

full 0.0.7e **[color=red]NEW![/color]** contains converter 1.0.0        (updated some things..)
[http://www.mediafire.com/?gpedy2oybki](http://www.mediafire.com/?gpedy2oybki)

only converter 1.0.0 **[color=red] NEW![/color]**
[http://www.mediafire.com/?1bqmmlxx9j4](http://www.mediafire.com/?1bqmmlxx9j4)

[size=4pt]OLD
full 0.0.7d  contains converter 1.0.0c        ( fixed progress bar..)
 [http://www.mediafire.com/?2uxzxyonyrx](http://www.mediafire.com/?2uxzxyonyrx)
only converter 1.0.0c 
[http://www.mediafire.com/?rl3xd9spzdd](http://www.mediafire.com/?rl3xd9spzdd)[/size]

*debian package (still OLD for 0.0.7c )
[http://fuocotools.byethost13.com/index.php?board=14.0](http://fuocotools.byethost13.com/index.php?board=14.0)




then EXTRACT somewhere and for example we consider this folder
/home/Tigre/Desktop/FuocoTools0.0.0.7d

so type 


```
cd /home/Tigre/Desktop/FuocoTools0.0.0.7d 
```

 
```
sudo ./install.sh 

```

 
 

 if you want unistall it : 

```
sudo ./uninstall.sh

```


[SIZE="6"][B]
END [/B][/SIZE]
[SIZE="5"]**-do you need of APE support ?**[/SIZE]
see [http://fuocotools.byethost13.com/index.php?topic=76.0](http://fuocotools.byethost13.com/index.php?topic=76.0)


[SIZE="5"]**-do you need of MIDI converter  ?**[/SIZE]
see [here ](http://fuocotools.byethost13.com/index.php?topic=107.0)

[SIZE="5"]**-do you need of AMV converter  ?**[/SIZE]
[http://fuocotools.byethost13.com/index.php?topic=155.0](http://fuocotools.byethost13.com/index.php?topic=155.0)




[SIZE="5"]Useful documentation  [/SIZE]

ffmpeg :
[http://ffmpeg.mplayerhq.hu/faq.html](http://ffmpeg.mplayerhq.hu/faq.html)

mencoder

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#encoding-guide](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#encoding-guide)

---

### Post by Creative2 on 2008-05-16
just updated

---

### Post by thewolf32 on 2008-07-01
Amazing. Keep up the great work!

---

### Post by Stochastic on 2008-07-02
Do you have a webpage for this project/software?  Why don't you package this software and make it part of the MEDIBUNTU (as you like to shout it) repository?  Make a launchpad page for it etc..?  You may find more people chipping in to help on the project if you do.  Maybe it could prove to be so useful to the video crowd that it's incorporated into the ubuntustudio-video repository; it seems like you've been working on it for a long time now.

---

### Post by Creative2 on 2008-07-02
i have a forum [http://fuocotools.byethost13.com/index.php](http://fuocotools.byethost13.com/index.php) and on kde app there is another page [http://www.kde-apps.org/content/show.php/Fuoco+Tools?content=73886](http://www.kde-apps.org/content/show.php/Fuoco+Tools?content=73886)

a guy i think has made package (rpm) debian package is still old... 
anyway the installation , i think, is very easy
 
mm i have just made another version 0.0.8 with renaming and some other stuff but i am testing...then i am actually working , on fuoco's bash script \ konqueror service menu because of a silly issue on the file's name with special characters -.- many guys asked to me why it didn't work and the most time it was because on files name there were stuff like : !"£$%&/()=?^|\ into...,  

but it's a bit fragmentated work because i am always busy so i really need of help xD 

for lauchpad i am doing something right now :)

---

### Post by thewolf32 on 2008-07-05
I'd like to help by translating this app to spanish. How can I do that? Via Launchpad?

---

### Post by Creative2 on 2008-07-05
i am sorry but translation.... well because i am very lazy translation issue is not so easy as you could think , i should rewrite fuoco  to make it easier...so you should edit fuoco with kommander  for that issue...and it's not so easy.. if you don't know .

---

### Post by nowardev on 2008-10-19
This project was merged with this :)

[http://www.nowardev.netsons.org/?q=node/1](http://www.nowardev.netsons.org/?q=node/1)

---

### Post by rylleman on 2008-10-19
> **nowardev said:**
> This project was merged with this :)

[http://www.nowardev.netsons.org/?q=node/1](http://www.nowardev.netsons.org/?q=node/1)
Fuoco tools is merged into No War Converter, or the other way around?
How do you install No War Converter? Any debs?

---

### Post by nowardev on 2008-10-19
well in other words no war converter is the evolution of fuoco tools 

now there is not a debian package because is still in developing and it's not completed

---

### Post by nowardev on 2008-10-27
now there is a prealpha release

[http://ubuntuforums.org/showthread.php?t=959063&highlight=nwc](http://ubuntuforums.org/showthread.php?t=959063&highlight=nwc)

---

### Post by KanineN on 2008-10-27
Can this program convert .wmv to .mp4?

---

### Post by nowardev on 2008-10-27
of course

---

### Post by KanineN on 2008-11-02
When I try from .avi to .mp4 it doesn't work. 

I get this wrong message

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from 'msm1136_widescreen.avi':
  Duration: 00:18:24.2, start: 0.000000, bitrate: 356 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 320x180 [PAR 1:1 DAR 16:9], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Output #0, mp4, to 'msm1136.mp4':
    Stream #0.0: Video: 0x0000, yuv420p, 320x240 [PAR 4:3 DAR 16:9], q=2-31, 500 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0

i used ```
ffmpeg -i msm1136_widescreen.avi -b 500k -s 320x240 msm1136.mp4
```

---

### Post by KanineN on 2008-11-02
When I try from .avi to .mp4 it doesn't work. 

I get this wrong message

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from 'msm1136_widescreen.avi':
  Duration: 00:18:24.2, start: 0.000000, bitrate: 356 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 320x180 [PAR 1:1 DAR 16:9], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Output #0, mp4, to 'msm1136.mp4':
    Stream #0.0: Video: 0x0000, yuv420p, 320x240 [PAR 4:3 DAR 16:9], q=2-31, 500 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0

i used ```
ffmpeg -i msm1136_widescreen.avi -b 500k -s 320x240 msm1136.mp4
```

---

### Post by nowardev on 2008-11-03
```
configuration: --enable-gpl --enable-pp --enable-swscaler 
--enable-x11grab --prefix=/usr --enable-libgsm 
--enable-libtheora --enable-libvorbis --enable-pthreads 
--disable-strip --enable-libfaad --enable-libfaadbin
 --enable-liba52 --enable-liba52bin --enable-libdc1394
 --disable-armv5te --disable-armv6 --disable-altivec 
--disable-vis 
--enable-shared --disable-static
```

tha's is not a problem of fuoco tools ....

neither of nwc...

it's your version of ffmpeg..omg.. i see well:

**DON'T POST HERE PROBLEM IF YOU ARE NOT USING THE INTERFACE!** WE HAVE NOT TIME TO FIX YOUR PROBLEM

PLEASE POST HERE ONLY IF YOU HAVE PROBLEM WITH OFFICIAL INTERFACE AND OFFICIAL PACKAGES (**MEDIBUNTU PACKAGES FOR FFMPEG**).

Nwc team

(nwcdev   and creative2)

---

### Post by EmperorMoo on 2009-01-19
Great work, many thanks!

I managed to convert two mp4s to avis in about 15mins from install.

---

### Post by KanineN on 2009-01-19
Hello! When I am converting a .flv file to a .mp4 the sound gets unsynced.


I use the code



```
ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 700k -ab 192k -y OUTPUT
```


Is there any chance to fix it?

---

### Post by KanineN on 2009-01-23
excuse me for double post but I really want help because now fuocoTools wont convert .flv to .mp4. It say "unsupported video format (7)".

---

### Post by nowardev on 2009-01-24
fuoco tools is not supported anymore .... we are working on nwc

anyway... your problem is ffmpeg that's is 

see on out website here

[http://www.nowardev.netsons.org/?q=node/12](http://www.nowardev.netsons.org/?q=node/12)

---

