---
title: "Linux HTPC, anyone got one?"
date: 2009-11-16
forum: The Cafe
---

### Post by Kdar on 2009-11-16
I am planning to build HTPC one of those days (possibly during winter vacation, after exams) for my TV in the leaving room. And I am also thinking to use Linux there (for media center.. etc).

Have anyone tried this before (using Linux)?

Any ideas, recommendation for Linux side of it (hardware I got pretty much figured out). Should I use Ubuntu or something else? What kind of software would I need (like media center.. etc)?

---

### Post by HappyFeet on 2009-11-16
I use mythtv and it's pretty good.

---

### Post by cariboo on 2009-11-16
I use vlc for everything, I use a custom built Intel atom powered system. It's plugged into my 32" LCD HDTV and my Technics surround sound receiver.

---

### Post by Kdar on 2009-11-17
How were you able to steam tv channels.. etc? (I am not sure if I will use HTPC for this..but I might. Maybe I will just use it for music, movie on HardDrive and what not).
Also by VLC? or you need something else for this?

---

### Post by kreggz on 2009-11-17
I have a htpc with MythTV and it can play and record Digital TV but also play dvds and *.avi files. I use a remote control to navigate menus.

My video card is a ATI HD 3650 using VGA and my sound goes to an amp.

---

### Post by cariboo on 2009-11-17
I don't have a tv tuner card in the system, as it is too small. All recording is done on a server located in my garage, I just mount the movie and music partitions on boot and use vlc to watch video and use playlists I have created for music.

---

### Post by Crunchy the Headcrab on 2009-11-17
I really like MythTV.  My brother uses it.  It's great.

---

### Post by Paqman on 2009-11-17
MythTV is good if you're intending to use the machine as a PVR, but it's overkill if you're not. I built a media centre PC a little while ago:

[How to build a media centre PC]("http://andyduffell.com/techblog/?p=415")

---

### Post by markp1989 on 2009-11-17
I use moovida on a basic ubuntu install. looks nice on my tv  :D

---

### Post by MJWitter on 2009-11-17
Take a look at XBMC, I have a system running it with no issues.  At the moment it doesn't do tv recording, but I believe they are testing a PVR function for future inclusion.

[XBMC]("http://www.xbmc.org")

---

### Post by Kdar on 2009-11-17
> **Paqman said:**
> MythTV is good if you're intending to use the machine as a PVR, but it's overkill if you're not. I built a media centre PC a little while ago:

[How to build a media centre PC]("http://andyduffell.com/techblog/?p=415")

Thanks for the link.

Can I watch TV channels using XBMC? (like channels from my cable provider?)

---

### Post by laceration on 2009-11-17
When I switched over to Ubuntu a couple of years ago one of my main objectives was to watch TV with Myth.  I was very disappointed.  I never succeeded in getting it to work.  I also found it to be a beast of a program.  So I tried to find something else, but did not.  XBMC was the only software I ever tried on Ubuntu that crashed my whole system and does not do over the air or cable TV.
Eventually what I did was author my own solution, OSTV.  OSTV started as some scripts to control MPlayer.  It turned out so good that I packaged it as a program.  There is nothing that comes close to OSTV in that it is a small, simple program that still has a lot of features.
OSTV rethinks the whole notion of a HTPC or media center though.  It is just another program on your computer that does TV and video yet has the traditional TV experience of full screen, remote control and slouching on the sofa.

---

### Post by Paqman on 2009-11-17
> **Kdar said:**
> Thanks for the link.

Can I watch TV channels using XBMC? (like channels from my cable provider?)

Nope.

I have my XBMC box and my satellite TV PVR plugged into the same TV. If I want to watch the TV I just switch inputs. I can see why some people would like one box that does both, but since i've got the PVR already i've never bothered.

---

### Post by cdekter on 2009-11-17
IMHO there are no good PVR packages for Linux. MythTV is fiendishly complex, takes a long time to setup and even then is still quite buggy (not to mention not particularly easy to use). I run Win7 media center on my HTPC and it works flawlessly - 10 minutes to set up and you're ready to go (I'm using a Haupage MC remote with it).

---

### Post by laceration on 2009-11-17
> MythTV is fiendishly complex, takes a long time to setup and even then is still quite buggy (not to mention not particularly easy to use).
I'm with ya there!  There is a guy in my town, who owns an isp, has been doing unix/linux for 30 years and used to be a rocket scientist.  He couldn't get Myth going.  Though, because I have put together a pvr I can sympathize with some of the difficulties, the fact is that Myth has not succeeded with ease of use or install after all these years and all those developers.  I considering going back to Windows as there are a few good pvr apps...but then I would have had to go back to Windows, so I rolled my own.  
> IMHO there are no good PVR packages for Linux.
I wrote one! I'm taking umbrage here!;)  OSTV is installable in 10 minutes...but configuring your dvb card, scanning for channels and setting up your remote still can take some work in Linux.

---

### Post by northwestuntu on 2009-11-17
xbmc :popcorn:

---

### Post by wirepuller134 on 2009-11-17
We have had very good luck with mythdora for a few years then  compiling myth on Ubuntu starting with 9.04.  We're using one backend with directv, with frontends.  each frontend has 2 tuners assigned to it.  It took a bit to set up with all of the directv boxes, and the hallway closet is full of hardware.  After it was all set up we took an image of the OS drive just incase of disk failure.  We have the backend running on a Dell poweredge 2850 with hauppauge pvr500 cards.  We are also using 2 Freenas servers to hold media that are mounted by the frontends at boot.
   Sage has a Linux client as well, can't speak for it, but have a few friends whom use it and like it.

---

