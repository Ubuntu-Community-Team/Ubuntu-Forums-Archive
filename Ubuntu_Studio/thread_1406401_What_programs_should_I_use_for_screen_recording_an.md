---
title: "What programs should I use for screen recording and video editing?"
date: 2010-02-13
forum: Ubuntu Studio
---

### Post by S Man on 2010-02-13
I need a good screen recorder and a video editing program. Any ideas?

---

### Post by Revolutionary101 on 2010-02-13
For a screen recorder I use gtk-recordMyDesktop and for video editing I use Pitivi.

---

### Post by S Man on 2010-02-14
Thanks. I dled them and I'll see how they do.

---

### Post by S Man on 2010-02-14
How do you edit with Pitivi? There's nothing there. No transitions or effects or anything. What's it good for?

---

### Post by kyle-buntu on 2010-02-14
use openshot for video editing it has transitions and effects even chroma keying! (green screen image filling) its MUCH superior to pitivi:popcorn:

---

### Post by Hoora on 2010-02-14
> use openshot for video editing

Openshot did the thing for me too, thx kyle-buntu.

---

### Post by howefield on 2010-02-14
Kdenlive for video editing.

It is a KDE application so will pull in KDE dependancies, if this doesn't bother you, it is a pretty good and full featured piece of software.

[http://www.kdenlive.org/](http://www.kdenlive.org/)

---

### Post by prokoudine on 2010-02-14
> **S Man said:**
> How do you edit with Pitivi? There's nothing there. No transitions or effects or anything. What's it good for?
It's good for clean non-bloat videos that let you focus on content. Yeah, transitions like simple fades would be a nice addition, but effects... Um, thanks, but no - I don't mind if they will be added, I just won't use them.

---

### Post by howefield on 2010-02-14
> **S Man said:**
> There's nothing there. No transitions or effects or anything. What's it good for?

I don't think it is there yet, but given that it is the default video editor for Lucid Lynx, one would hope that development of the features that you would expect to find in such an application would be given a boost.

---

### Post by zeeshan_2011 on 2010-02-15
openshot

---

### Post by yodermk on 2010-02-15
I'm still a fan of Cinelerra but haven't used any of the others. Maybe openshot can do almost as much with less fuss?

Also interested in Blender; just wish I had time to learn it. :(

---

### Post by LuridCinema on 2010-02-15
Openshot is for amateur video work..nice package.. cinelerra is pro level, has many features that openshot simply does not have. openshot is simple and will do wonders, it has a place as not all people want or need all the features of cinelerra.

---

### Post by dmfagan9 on 2010-02-16
Hi All-

Sorry I can't figure out how to get Openshot? I usually use synaptic package manager but its not coming up in search. I use 8.10. Thanks a lot!

---

### Post by LuridCinema on 2010-02-16
**[*OpenShot* Video Editor: *Download*]("http://www.openshotvideo.com/2008/04/download.html")**

---

### Post by dmfagan9 on 2010-02-16
I went to openshot website and downloaded the program, dependencies and help manual. I installed the help manual withno problems. Then i tried installing the program and there is an error that says

Error dependency is not satisfiable : openshot - mlt

I imagine I have to do something with the dependencies but im not sure what to do. Greatly appreciate the help. Thanks

Dylan

---

### Post by dmfagan9 on 2010-02-16
So I've downloaded the wizard to help with this and there is a caveat in the download that says make sure you extract the contents of the wizard to folder ~/openshot_wizard/

am i supposed to create that folder or is it already supposed to exist and i have to locate it? I searched and it is not already on the comp and when i tried to create it i received an error message.

Thanks

Dylan

---

### Post by howefield on 2010-02-16
If it doesn't already exist, simply create it, open Nautilus by going to Places > Home and right click in the window, select Create Folder, name it accordingly and you are golden.

---

### Post by mango42 on 2010-02-16
> **dmfagan9 said:**
> So I've downloaded the wizard to help with this and there is a caveat in the download that says make sure you extract the contents of the wizard to folder ~/openshot_wizard/

am i supposed to create that folder or is it already supposed to exist and i have to locate it? I searched and it is not already on the comp and when i tried to create it i received an error message.

Thanks

Dylan

Did you try creating the folder using Nautilus, first? Worked okay for me (remember to set permissions - from the 'properties' menu option). 

I'm stuck with a 'detuned, white noise screen' when I try to start up Openshot - apparently Melt didn't install the **av_format** module and I don't have a clue where to go from here!

---

### Post by dmfagan9 on 2010-02-16
I am getting closer...... am running the python install... but I dont know if I am in 32 or 64 bit Ubuntu 8.10. Is there a place to look and see which one I'm running?

---

### Post by howefield on 2010-02-16
Open a terminal and look at the output of

```
uname -m
```

Post it here.

---

### Post by dmfagan9 on 2010-02-16
So I made it through the whole install. At the end it asks to try some of these sample commands and I receive errors :

dylan@dylan-laptop:~/openshot_wizard$  ffplay PATH_TO_A_VIDEO 
FFplay version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2003-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
PATH_TO_A_VIDEO: no such file or directory
dylan@dylan-laptop:~/openshot_wizard$ python ~/openshot/main/OpenShot.py
python: can't open file '/home/dylan/openshot/main/OpenShot.py': [Errno 2] No such file or directory


Any ideas? THANKS!

---

### Post by dmfagan9 on 2010-02-16
There is also a line about how you need to avformat in your output for a command to show that MLT worked but mine doesnt

dylan@dylan-laptop:~/openshot_wizard$ melt -query producers
---
producers:
  - pgm
  - slowmotion
  - abnormal
  - color
  - colour
  - consumer
  - loader
  - hold
  - noise
  - ppm

---

### Post by dmfagan9 on 2010-02-16
closer still....

Still having a problem importing the MLT

dylan@dylan-laptop:~$ python
Python 2.5.2 (r252:60911, Jan 20 2010, 23:16:55) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> >> import mlt
  File "<stdin>", line 1
    >> import mlt
     ^
SyntaxError: invalid syntax
>>> 


Any ideas? Thanks

---

### Post by mango42 on 2010-02-16
leave out the >> (my first and hopefully last dip into python - I am not a programmer!)

eg:-
>>> import mlt


also where you did "ffplay PATH_TO_A_VIDEO" I believe the stuff in capitals could be referred to as a 'pseudo environment variable", that is you're supposed to provide path to a video

eg:-
$ ffplay ~/videos/V_for_Vendetta.avi

;-)

---

### Post by littlepeon on 2010-03-31
@ Pros_to

Way to troll!!!! 
Not only did you recommend a WINDOWS program in a Ubuntu forum........
but an expensive and  NON-FREE (as in speech as well as 'beer') one as well....

there is a special zone in Hades for that......

now for the original poster:

gtk-recordmydesktop is a great screen recorder
kdenlive is a great editor

for other software needs or alternatives to what i've suggested you can go to:

[HTML]http://alternativeto.net[/HTML]

and find windows/linux/mac alternatives to software needs

later
-Peon

---

