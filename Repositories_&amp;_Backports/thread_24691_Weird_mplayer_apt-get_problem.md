---
title: "Weird mplayer apt-get problem"
date: 2005-04-08
forum: Repositories &amp; Backports
---

### Post by volfro on 2005-04-08
I'm a Debian newbie; just had Ubuntu installed since last night (and, as a matter of fact, installed it on my dad's machine because I was sick of cleaning up the viruses in Windows), and I love it--Synaptic is pure genius and a pleasure to use.

However, I'm trying to install mplayer via synaptic, and I get this weird error.

```
The following packages have unresolvable dependencies...blah blah blah

mplayer-k6:
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
```

It's strange that it's telling me that because I have the Hoary universe, Multiverse, and Marillat all enabled and working.

What's the deal?

thanks for any and all help :)  I am LOVING Hoary.  Apt-get is so much better than yum, from what I've experienced (was a fedora core user before I found ubuntu).  Wow.

---

### Post by Gandalf on 2005-04-08
[QUOTE=volfro]I'm a Debian newbie; just had Ubuntu installed since last night (and, as a matter of fact, installed it on my dad's machine because I was sick of cleaning up the viruses in Windows), and I love it--Synaptic is pure genius and a pleasure to use.

However, I'm trying to install mplayer via synaptic, and I get this weird error.

```
The following packages have unresolvable dependencies...blah blah blah

mplayer-k6:
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
```

It's strange that it's telling me that because I have the Hoary universe, Multiverse, and Marillat all enabled and working.

What's the deal?

thanks for any and all help :)  I am LOVING Hoary.  Apt-get is so much better than yum, from what I've experienced (was a fedora core user before I found ubuntu).  Wow.[/QUOTE]
 if you type [color=blue]sudo apt-get install -f[/color] does it work?

---

### Post by NeoChaosX on 2005-04-08
Do a "Force Version" in Synaptic and select a version that has "ubuntu" in the version number.

---

### Post by volfro on 2005-04-08
The force version option worked.  It installed, but it won't actually play any movies.  The program just crashes.

Not understanding the problem here.  I'll try again, but I think I'm going to break my Ubuntu.  

I guess that's how we learn...

---

### Post by volfro on 2005-04-08
I decided to ditch Mplayer and go with VLC, as I've had good experience with it in Windows, and know it's reliable.

Now, the DVD gets mounted if there's a DVD in the drive (wasn't happening before), and I can play videos, but I get no audio.  DVDs won't play; the window resizes for a second, then closes. 

Suggestions, anybody?

---

### Post by aburda on 2005-04-08
I have the same broken package problem when I try to do an apt-get on mplayer-386.      I can't get "The Daily Show" to play video, so I am primarily interested in firefox inline and not DVD or VCD playing

Aaron

---

### Post by speedman on 2005-04-08
If you are using Christian Marillat's repository at nerim.net for mplayer change your sources.list to point at the testing branch instead of unstable:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main


Regards,

SM

---

### Post by volfro on 2005-04-08
[quote=speedman]If you are using Christian Marillat's repository at nerim.net for mplayer change your sources.list to point at the testing branch instead of unstable:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main[/quote]

Checked out my sources.list and commented out the unstable branch.  It installed smoothly enough, but still a no-go.  It froze whenever I tried to play a video--I can't even move either window when I open a file.

Still no sound in VLC--and, in fact, WMV 9 files don't work, nor do some MPGs.  

Totem, ironically enough, plays the audio to most of my videos, (excepting DVDs, which it says it can't read at all), but I get nothing but a visualizer with the audio, not video.

Any more help?

---

### Post by chronusdark on 2005-04-09
in totem did you try installing the w32codecs package!!! all my videos work fine....P.S im using the xine flavor of totem

---

### Post by volfro on 2005-04-09
Okay.  I installed the correct codecs in VLC, and it works nicely.  I get audio and video.  However, in VLC, if I open a file, and then open another file (whether the original file is stopped or playing), VLC exits spontaneously.  Also, I get no audio during DVD playback in VLC.  Is that my computer screwing up or VLC?

Besides that, xine-totem works okay.  DVD playback is jerky, and with quicktime videos, sound is out of sync.  Any way to fix either problem?

---

### Post by c_dog on 2005-04-09
[QUOTE=volfro]I decided to ditch Mplayer and go with VLC, as I've had good experience with it in Windows, and know it's reliable.

Now, the DVD gets mounted if there's a DVD in the drive (wasn't happening before), and I can play videos, but I get no audio.  DVDs won't play; the window resizes for a second, then closes. 

Suggestions, anybody?[/QUOTE]

HAL and Gnome Volume Manager seem the be working together again in the past few days

Try shutting down the esd sound daemon 'System>Preferences>Sound> uncheck Enable sound startup' I'll assume you've got libcss2, libdvdread3, and libnav4 loaded. You won't get far on a encrypted DVD without them

---

### Post by titus on 2005-04-09
if you just do apt-get upgrade then try to install it should work. Did for me.

:)

---

### Post by volfro on 2005-04-10
Well, everything works, for the most part.  Just that jerky DVD issue and delayed sound in general, not just .mov files.  Thank you all for your help though :) time to start another thread

---

### Post by desheikh on 2005-04-11
I managed to install mplayer..  just disabled nerim.net servers
gedit /etc/apt/sources.list -> apt-get update -> apt-get upgrade -> apt-get install mplayer

---

### Post by zwaardmeester on 2005-04-15
[QUOTE=desheikh]I managed to install mplayer..  just disabled nerim.net servers
gedit /etc/apt/sources.list -> apt-get update -> apt-get upgrade -> apt-get install mplayer[/QUOTE]

This doesn't work for me.. I need the nerim.net server

leo@zwaardmeester:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer

---

### Post by speedman on 2005-04-15
[QUOTE=zwaardmeester]This doesn't work for me.. I need the nerim.net server[/QUOTE]

I take it you don't have the Ubuntu multiverse repository listed in /etc/apt/sources.list?

As you can see it is available there:

chris@i8500:~ $ apt-cache show mplayer-586
Package: mplayer-586
Priority: extra
Section: multiverse/graphics

You might want to double check your sources.list against this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse

HTH


Regards,

SM


EDIT - fixed a typo.

---

### Post by zwaardmeester on 2005-04-15
Yes that's it! Everything's working now finally...  ;-)

---

### Post by Virtual DarKness on 2005-04-15
[QUOTE=volfro]The force version option worked.  It installed, but it won't actually play any movies.  The program just crashes.[/QUOTE]

Hi,
I had the same problem but fixed opening gmplayer and then in the preferences -> codecs I set "Win32/VfWex video codecs" as video codec family.. 
(this way [I suppose] it uses the w32codecs..)

hope it helps ;)

bye,
Giovanni.

---

### Post by speedman on 2005-04-15
[QUOTE=zwaardmeester]Yes that's it! Everything's working now finally...  ;-)[/QUOTE]

Good deal.  :grin: 


Regards,

SM

---

