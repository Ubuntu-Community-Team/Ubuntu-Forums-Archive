---
title: "Simple way of making a stop animation?"
date: 2008-06-06
forum: Ubuntu Studio
---

### Post by J05HYYY on 2008-06-06
Hello all,

Today I got bored and with enough free time on my hands; wanted to make a stop animation but couldn't figure out how to. I have taken enough photographs for the video which I intend to put on youtube.  (will post the link when it's finished)

Does anyone know of a package which will allow me to select the jpegs I want 
to create an animation?

I want to give each one a batch transition time of .25 seconds.

Any help would be gratefully accepted.

---

### Post by Stochastic on 2008-06-06
Try ```
sudo apt-get install stopmotion
```

---

### Post by meatlegs on 2008-06-07
Wow, this post was what exactly what I needed, and it was the first one on the list...weird.
Anyway, I'm trying to use Stopmotion in Gutsy, and am getting this message when I try to turn the camera on:
'Warning you do not have the given grabber on your system'

What the???

---

### Post by J05HYYY on 2008-06-07
Hmm, I installed the program and started to try and use it but It doesn't want to import any ".jpg"s.

When I click the add frame button, and select a picture - it adds a blank black frame?! I'm confused ... am I doing something wrong?

---

### Post by Stochastic on 2008-06-07
> **J05HYYY said:**
> Hmm, I installed the program and started to try and use it but It doesn't want to import any ".jpg"s.

When I click the add frame button, and select a picture - it adds a blank black frame?! I'm confused ... am I doing something wrong?

I've never used the program, but according to their user manual: [http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.php?grp=2&&side=10](http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.php?grp=2&&side=10) To add a picture, press Ctrl+F (the screenshot shows .jpeg as an option.

---

### Post by J05HYYY on 2008-06-08
Well okay, guess I've found a new bug. Then again; i'm using the 64 bit version of gusty. It might be more efficient trying to make some shell script which could do this instead. Hmm, just a thought.
I don't think the program has the documentation to fix this so yeah ... if I find a nice solution I'll post but if any other suggestions would be welcome.

---

### Post by quelx on 2008-06-08
I've used **mencoder** to create time lapse movies (same concept) from a series of jpeg's.  Run from the folder where the *.jpg* files live, adjust **fps** to your needs.

```
mencoder "mf://*.jpg" -ovc lavc -fps xx -o x.avi
```

---

### Post by J05HYYY on 2008-06-08
After a 

```
sudo-apt get install mencoder
```

i browse to my directory with the .jpegs in and type

```
mencoder "mf://*.jpg" -ovc lavc -fps 04 -o x.avi
```

the output i get is

```

MEncoder 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 3.00GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```

---

### Post by J05HYYY on 2008-06-08
Oops; sorry that worked wonders ... I just forgot that it's case sensitive, thats all. So yeah, thanks very much for that :)

---

### Post by J05HYYY on 2008-06-08
[Here's my bad attempt at making a video]("http://www.youtube.com/watch?v=xXC3HOuZyCI")

---

### Post by J05HYYY on 2008-06-09
First I wrote the music.
Then I took lots of photos in .jpeg format.
Then I used the code quelx provided to link them together into an avi (stop animation).
Afterwards, I opened the avi in Kdenlive.
I put a mirror effect on the stop animation and added music.
I then converted it into .ogg format using OggConvert.
And uploaded the video to youtube.

I hope this clears things up ... didn't really understand the question or who it was directed at so yeah.

---

### Post by yknivag on 2008-08-03
> **quelx said:**
> I've used **mencoder** to create time lapse movies (same concept) from a series of jpeg's.  Run from the folder where the *.jpg* files live, adjust **fps** to your needs.

```
mencoder "mf://*.jpg" -ovc lavc -fps xx -o x.avi
```

quelx, thank you! I've been looking for a simple way to do this for months. :KS

---

### Post by okey666 on 2008-10-27
Thanks quelx. I will use this until the program stopmotion starts working in intrepid properly for 64-bit. It crashes whenever I click the take picture button.

PS. I would thank you but the forum won't let me.

---

### Post by xchecker on 2008-11-09
I can't this to work yet.  When I try the code recommended I get:

```
crichmond@brichmond-desktop:/home/brichmond/Photos/2008/09/13$ mencoder "mf://*.jpg" -ovc lavc -fps 4 -o x.avi
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
[mf] number of files: 106 (424)
[demux_mf] file type was not set! trying 'type=jpg'...
VIDEO:  [IJPG]  0x0  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:25.00  ftime:=0.0400
Input fps will be interpreted as  4.00 instead.
File not found: 'x.avi'
Failed to open x.avi.
Cannot open output file 'x.avi'.

```

Help please!?

---

### Post by treesurf on 2009-03-18
The mencoder command that quelx posted returned an empty file for me.  However, this produced what I was looking for:

mencoder "mf://*.JPG" -vf scale=640:480 -o timelapse.avi -of lavf -ovc lavc -lavcopts vcodec=mjpeg -lavfopts format=avi -fps xx

---

### Post by neilevan814 on 2009-03-21
Why not give kdenlive a try.  It is more like a Windows moviemaker application, but it is completely gui and very easy to use still shots for stop motion pproduction as well as .avi's to do other things with.  There are a ton of transition effects as well.  I use Gnome even though this is a KDE application synaptic will install the needed dependencies to run this app in gnome.

---

### Post by neilevan814 on 2009-03-28
Jo5hyyy...I think I see spots before my eyes....good start on your video production....what did you use to compose your music....that is really good...?

---

### Post by J05HYYY on 2009-08-21
I cheated and used Cubase SL3 (with the master re-arrange) :P

---

### Post by swiftsam on 2009-10-22
> **treesurf said:**
> The mencoder command that quelx posted returned an empty file for me.  However, this produced what I was looking for:

mencoder "mf://*.JPG" -vf scale=640:480 -o timelapse.avi -of lavf -ovc lavc -lavcopts vcodec=mjpeg -lavfopts format=avi -fps xx

thank you!  I tried so many different mencoder commands that crashed for one reason or another, but this one worked like a charm!

---

