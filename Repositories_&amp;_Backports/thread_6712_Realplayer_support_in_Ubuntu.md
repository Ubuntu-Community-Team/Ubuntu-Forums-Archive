---
title: "Realplayer support in Ubuntu?"
date: 2004-11-30
forum: Repositories &amp; Backports
---

### Post by artAlexion on 2004-11-30
neither apt-get nor synaptic can find either realplayer nor the community supported helixplayer. :(  Are packages available to play real media files?

How about old reliable mplayer?  Can't find it either.   :sad:  

So far I haven't found an mpeg nor mov that totem can play.  Similar problem with Rhythmbox.  Plays OGG, but not MP3.  Why, in current enviornment, would a capable mp3 player, like xmms, not be part of the default install?

---

### Post by jiyuu0 on 2004-11-30
take a look at:
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

---

### Post by artAlexion on 2004-11-30
Thanks.  Was hoping to keep the apt database complete for the system, but the script install for realplayer worked fine.  

Should I install xine instead of mplayer (instructions for xine; none for mplayer)?

The Rhythmbox app looked promising.  Is there a way to add an mp3 plugin or codec?

---

### Post by bob k on 2004-11-30
[QUOTE=artAlexion]Thanks.  Was hoping to keep the apt database complete for the system, but the script install for realplayer worked fine.  

Should I install xine instead of mplayer (instructions for xine; none for mplayer)?

The Rhythmbox app looked promising.  Is there a way to add an mp3 plugin or codec?[/QUOTE]
 I'm using mplayer for mpeg and other web based video because it has a firefox plugin, and using xmms of audio CD's and MP3. XMMS MP3s play great but audio CDs don't play that well (clicking and dropped packets) so I am still searching for an audio cd pgm that works, and since most of my audio collection has been converted to MP3 I am not look until I have a few other things working and install the apps that are not included in the distro.

EDIT

I got myself thinking about audio CDs and XMMS, so I went thru my setup and I had the wrong mount point for my CD player, once that was corrected that fixed audio CDs.

EDIT

That wasn't the problem it was the damn cable to the header on the MB from the cdrom. I built the damn thing how did forget something that simple.

I was cleaning up and going thru my hardware when I found this cable pluged in to the to the AUX header. I said self how did that happen. I then traced the cable to an empty end, and then self said you bumb ass, you wasted 3 nights on a ****** cable that you should have checked first.

I did make some headway in the process, I did fix alot of software along the way.

This has to be one of the best distros out in the wild. I already have two people (don't know anything) that want me to set it up. I think it is a no brainer. get the media stuff working right off the bat. and you got a Ubuntu lifer

And accrording to GPL I will do this at no charge


Bob

---

### Post by artAlexion on 2004-11-30
[QUOTE=bob k]I'm using mplayer for mpeg and other web based video because it has a firefox plugin,
Bob[/QUOTE]

So you installed mplayer from source?

---

### Post by TravisNewman on 2004-11-30
mplayer is in the universe repository. See the HOWTO section for how to enable that.

Install gstreamer-mad for mp3 support in Rhythmbox.

---

### Post by kris kincaid on 2004-11-30
artAlexion, try this. It is an awesome how-to for mplayer. I have tried and failed several times until I got ahold of these instructions

[http://ubuntuforums.org/showthread.php?t=94](http://ubuntuforums.org/showthread.php?t=94)

---

### Post by bob k on 2004-12-01
[QUOTE=artAlexion]So you installed mplayer from source?[/QUOTE]
 I do believe that the apt-get's install gcc so I would assume that it gets compiled as part of the installation.

Now that I think about it mplayer did compile, but it works great have no problems with it.

---

### Post by adbak on 2004-12-01
You can also add ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
```
to your /etc/apt/sources.list.  Then
```
sudo apt-get update
sudo apt-get install mplayer
```
to install mplayer from apt-get.

---

### Post by artAlexion on 2004-12-01
[QUOTE=panickedthumb]mplayer is in the universe repository. See the HOWTO section for how to enable that.

Install gstreamer-mad for mp3 support in Rhythmbox.[/QUOTE]
 Thanks.  Had apt configured ror universe, but not multiverse.  Some of the required packages were in the multiverse, not the universe.

Installed successfully thanks to your help.

---

### Post by artAlexion on 2004-12-01
[QUOTE=kris kincaid]artAlexion, try this. It is an awesome how-to for mplayer. I have tried and failed several times until I got ahold of these instructions

[http://ubuntuforums.org/showthread.php?t=94](http://ubuntuforums.org/showthread.php?t=94)[/QUOTE]
 Thank you so much.  I have bookmarked it.

---

### Post by artAlexion on 2004-12-01
[QUOTE=jiyuu0]take a look at:
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)[/QUOTE]
 This is a fantastic document.  It helped me solve my samba problems that I hadn't even gotten around to asking.  Thanks to the help with this thread, my Ubuntu installation, in about 3 weeks is where my Red Hat 7.3 took a couple of years to get right.

---

