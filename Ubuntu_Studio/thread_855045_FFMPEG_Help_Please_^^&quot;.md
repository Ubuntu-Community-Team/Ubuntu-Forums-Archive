---
title: "FFMPEG Help Please ^^&quot;"
date: 2008-07-10
forum: Ubuntu Studio
---

### Post by aflog on 2008-07-10
Hey guys (and girls :P)

Im *trying* to convert an avi video of mine to .wmv using ffmpeg. The problem is the audio is AAC format. Ive searched google and the net, and im a complete noob at video conversion using command line and their complex talk confuzzles me. Ill give you my output:

> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
[wmv3 @ 0xb7e3d6e8]WMV3 Complex Profile is not fully supported
[wmv3 @ 0xb7e3d6e8]1 for reserved RES_X8 is forbidden
[wmv3 @ 0xb7e3d6e8]0 for reserved RES_FASTTX is forbidden
[wmv3 @ 0xb7e3d6e8]Extra data: 16 bits left, value: 402F
Input #0, avi, from 'Mahoromatic_S1_03.DVD(AAC)[KAA][76BEAFA3].avi':
  Duration: 00:24:21.1, start: 0.000000, bitrate: 1335 kb/s
  Stream #0.0: Video: wmv3, yuv420p, 704x396, 23.98 fps(r)
  Stream #0.1: Audio: 0x00ff, 48000 Hz, stereo, 146 kb/s
Output #0, asf, to 'Mahoro_3.wmv':
  Stream #0.0: Video: msmpeg4, yuv420p, 320x240, q=2-31, 200 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[wmv3 @ 0xb7e3d6e8]WMV3 Complex Profile is not fully supported
[wmv3 @ 0xb7e3d6e8]1 for reserved RES_X8 is forbidden
[wmv3 @ 0xb7e3d6e8]0 for reserved RES_FASTTX is forbidden
[wmv3 @ 0xb7e3d6e8]Extra data: 16 bits left, value: 402F
Unsupported codec ( id=86018 ) for input stream #0.1


The problem appears to be the bottom line.

If anyone can help thatd be great ^^

thanks

Jayden

PS: i suppose the command i gave would help too ^^"
> ffmpeg -i "Mahoromatic_S1_03.DVD(AAC)[KAA][76BEAFA3].avi" -s 320x240 -sameq "Mahoro_3.wmv"


---

### Post by kostkon on 2008-07-10
You'll have to install the version of *FFmpeg* that is offered by the [*Medibuntu* repository]("http://medibuntu.org/") and has the support for restricted formats enabled.

Just add this repository and then you will get an update notification for this new version. If not, just remove your old version and install the one from *Medibuntu* or something similar (it depends).

---

### Post by aflog on 2008-07-10
I did that. Updated ffmpeg... ran the same command and got:

> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
[wmv3 @ 0xb7ed46e8]WMV3 Complex Profile is not fully supported
[wmv3 @ 0xb7ed46e8]1 for reserved RES_X8 is forbidden
[wmv3 @ 0xb7ed46e8]0 for reserved RES_FASTTX is forbidden
[wmv3 @ 0xb7ed46e8]Extra data: 16 bits left, value: 402F
Input #0, avi, from 'Mahoromatic_S1_03.DVD(AAC)[KAA][76BEAFA3].avi':
  Duration: 00:24:21.1, start: 0.000000, bitrate: 1335 kb/s
  Stream #0.0: Video: wmv3, yuv420p, 704x396, 23.98 fps(r)
  Stream #0.1: Audio: 0x00ff, 48000 Hz, stereo, 146 kb/s
Output #0, asf, to 'Mahoro_3.wmv':
  Stream #0.0: Video: msmpeg4, yuv420p, 320x240, q=2-31, 200 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[wmv3 @ 0xb7ed46e8]WMV3 Complex Profile is not fully supported
[wmv3 @ 0xb7ed46e8]1 for reserved RES_X8 is forbidden
[wmv3 @ 0xb7ed46e8]0 for reserved RES_FASTTX is forbidden
[wmv3 @ 0xb7ed46e8]Extra data: 16 bits left, value: 402F
Unsupported codec ( id=86018 ) for input stream #0.1


The main point i think is:
> Unsupported codec ( id=86018 ) for input stream #0.1

Thanks

---

### Post by kostkon on 2008-07-10
Try to specify a codec with the *vcodec* option, instead of relying on the *.wmv* file extension.

You have the option to use two *wmv* codecs: *wmv1* and *wmv2*. I assume that wmv2 is better but I may be wrong.

There is also a *wmv3* one but *FFmpeg* can only decode such a codec.

You can check yourself by doing
```
ffmpeg -formats
```
for all the supported codecs.

---

### Post by aflog on 2008-07-11
Tried it... same message

---

### Post by Creative2 on 2008-07-11
why you don't use fuoco tools you can only download and if you extract and go on config folder you can see a file txt called treestore.txt in that file there are all function of fuoco tools for conversion ...

for example 
any to avi

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT

if you search on this forum you will find a topic to install it.. if you prefer ..just search fuoco tools mywebsite is down now

---

### Post by angelsguitar on 2008-07-11
If you have ffmpeg already installed from the medibuntu repositories, try installing WinFF. It's a GUI front end to ffmpeg and has worked really great for me.  You can find the Ubuntu/Debian version (.deb file) [here]("http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=54").

---

### Post by heathenx on 2008-07-12
How about giving mencoder a try?

mencoder Mahoromatic_S1_03.DVD(AAC)[KAA][76BEAFA3].avi -ovc lavc -ofps 26000/1001 scale=320:240 -oac pcm -o Mahoro_3.wmv

---

### Post by solitaire on 2008-08-04
did any of these options work?

I'm getting the same error ```
Unsupported codec (id=86018)
```
The mp4 was made using a Nokia N95 anyone know of a compatible codec?

---

### Post by Creative2 on 2008-08-04
if you have fuoco tools , put the file on your list and click on Info file 
if you have not installed 

ffmpeg -i INPUTFILE 2>&1 | grep Stream

---

