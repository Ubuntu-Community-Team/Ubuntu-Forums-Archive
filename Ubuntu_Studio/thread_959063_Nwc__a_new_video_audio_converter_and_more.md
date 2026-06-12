---
title: "Nwc  a new video audio converter and more"
date: 2008-10-26
forum: Ubuntu Studio
---

### Post by nowardev on 2008-10-26
screenshot
input

[[IMG]http://www1.mediafire.com/imgbnc.php/3dc7181d8f76b0d4af211d74287abf1c5g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=ucuumanommg&thumb=4)

mencoder
[[IMG]http://www2.mediafire.com/imgbnc.php/5459641afca8e7bf1e6e5990cd8a2d1c5g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=zmtfhnvolon&thumb=4)


ffmpeg

[[IMG]http://www2.mediafire.com/imgbnc.php/6a33add967d12437f963032fa9cc5f173g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=k9dxygjvcdj&thumb=4)

ffmpeg2theora

[[IMG]http://www2.mediafire.com/imgbnc.php/6e530cbdf2b6587b6ba0b70c528be0ed3g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=ymjg9nrjdom&thumb=4)

photoslider

[[IMG]http://www1.mediafire.com/imgbnc.php/31d3ba9d0b0e722b22fb4c8df1fa10df5g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=1jndmiqnwzm&thumb=4)

Option

[[IMG]http://www4.mediafire.com/imgbnc.php/d965c58e9c1330c5472b9647c11fcf285g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=mmmfjykzuwl&thumb=4)




VIDEO HOW TO PHOTO SLIDER :
[http://www.vimeo.com/2353925](http://www.vimeo.com/2353925)


Supported device (with preseting):

2.8 inch Touch Screen MP4 MP3 Player (china ipod?)
MEIZU M6 player
PSP            
Video ipod
sansaview  (sandisk mp4 mp3 player)

iphone (maybe)
NOKIA N73
NOKIA N800
MOTOROLA V3X
MOTOROLA V3i
Sony Ericsson k750i
zen creaative video(non tested well)
TOMplayer

**Well this software is not finished.**

a video from photos 
[http://www.youtube.com/watch?v=Uyz1dLxQKIc](http://www.youtube.com/watch?v=Uyz1dLxQKIc)
[B]
 USE ONLY FOR TEST[/B]

it's a bash script and it's a universal converter i hope

 




[SIZE="7"]  **installation :**[/SIZE]

-DOWNLOAD THIS 0.0.1
[http://www.mediafire.com/file/czoedjmg3yj/nwcalpharelease0.0.1.tar.gz](http://www.mediafire.com/file/czoedjmg3yj/nwcalpharelease0.0.1.tar.gz)

-just extract somewhere 

then open a terminal ,and obviously go on folder wher you have just extracted 

cd something

then just type

```
sudo ./ubuntuinstaller <option>
```



where option is 



-full install everything you have to install  

-nokde installation of dependences but with minimal kde softwares

-minimal it will be installed only the interface

-fullfix (use only if you have kde and if your kdenlive crashes on start NOT USE IF YOU DON'T KNOW )

-unistall ....


example :

```
sudo ./ubuntuinstaller full 
```

if you can't see this application on your audio video group open a terminal and type

```
kmdr-executor /usr/bin/nwc.kmdr
```

if you want remove 

 

```
sudo ./ubuntuinstaller unistall 
```

---

### Post by nowardev on 2008-11-03
some updates
this is version is  not finished yet..
3gp with mencoder is broken cuz amr_nb library is **kced

---

### Post by nowardev on 2008-11-05
gnome user on intrepid ibex

medibuntu repository has not ffmpeg so photo slider crash = wait for medibuntu

---

### Post by nowardev on 2008-11-07
udpate 

fixed installer
fixed .desktop file 
fixed gnome crash message kdenlive_render is crashed (maybe)
Changed color 
added rename for photo converter

---

### Post by duffrecords on 2008-11-08
Really cool.  I always find myself searching the man pages for correct syntax when using ffmpeg or mencoder; this makes it much simpler.

---

### Post by nowardev on 2008-11-11
well that it's true this can be used for manual (mencoder ffmpeg and ffmepg2theora ) expecially if you want create bash script 
or you can use it like encoder i remember your that this application is a bash script :)

---

### Post by nowardev on 2008-11-16
some work 
some fix 
i hope photo slider will work now on gnome desktop on my virtual machine it worked

---

### Post by nowardev on 2008-11-27
video tutorial for photo slider

[http://www.vimeo.com/2353925](http://www.vimeo.com/2353925)

---

### Post by nowardev on 2008-11-29
0.0.0.c
[http://www.mediafire.com/?mymm23nynmm](http://www.mediafire.com/?mymm23nynmm)
Some improvements on photos windows
 fixed (hope) psp h264 on mencoder
 some clean of nwc script
 some other little things

---

### Post by nowardev on 2008-12-04
added 
tomplayer support
 and video creative support (zen creative not well tested ..)

some work some help stuff added 
[http://www.mediafire.com/file/czoedjmg3yj/nwcalpharelease0.0.1.tar.gz](http://www.mediafire.com/file/czoedjmg3yj/nwcalpharelease0.0.1.tar.gz)

---

### Post by unoodles on 2008-12-04
Wow, very nice tool. You should start a project page for this. SourceForge or GoogleCode will work.

---

