---
title: "why is video editing such a task?"
date: 2010-02-04
forum: Ubuntu Studio
---

### Post by rwltrz4 on 2010-02-04
I mean after 4 installs I have tried:

cinellerra
kdenlive
kino
opnshot editor
pitivi

and god knows what else

my video requirements are simple:

I have 180 gigs of "dv footage" organized, dated and made into dv clips (home movies) and all I want to do is import said clips one by one or batch (even better), no edits needed on most if not all as I already did this with the dv files, I then once imported  want to export each clip to h.264 mp4 for 1) upload to youtube and or picasa web albums and maybe even motionbox (not sure yet) 2) for viewing on my tv via xbox and or boxee 3) Just so I have smaller files of each clip

In all of these programs where is mp4?  Should i  even be using mp4? 

 If I install ubuntu restricted drivers and such then my whole
install gets buggy, weird colors, artifacts, freezing in vlc, totem, mplayer and no matter what i encode to it looks like garbage, then i find out i cant organize my videos in picasa because video isnt supported with linux, wtf? Also sometimes the dv files are seen and other times they are not (external hd)

I so want to leave the mac world and become 100% linux, please help me make this transition.


It cant be this hard I must be doing somethng wrong. HELP!! 


I am reinstalling karmic and will do the system updates, then after that what should i install, what programs and what drivers, etc?

Thanks

---

### Post by indytim on 2010-02-04
Beyond the re-install, I would recommend two things to do before attempting to build any of the movie editors:

1.  Make sure your video card is properly installed.  If not get the appropriate drivers to make things happy.

2. Install Mediabuntu.  You will probably need the codec's along the line.

You might want to also post back what kind of hardware you are currently using.

Just a few of my recommended startting points.

IndyTim

---

### Post by rwltrz4 on 2010-02-04
I am using a 1.83 ghz Core Duo 2 intel  mac mini which I believe has a gm950 video card (integrated), 2 gigs ram, connected via firewire to 1 tb maxtor drive which is where my video files are


Also should i be installing 32 or 64 version?

---

### Post by cooper77z on 2010-02-04
@rwltrz4,

At the risk of encouraging you to abandon Ubuntu for a short time, try downloading and installing avlinux 3. Experiment with some of the programs, especially winff and devede. You can probably just convert everything from DV to mp4 with winff, then upload to the net. You can also just make a DVD out of all of your DV clips with the devede program. You should be able to use the same programs in Ubuntu 9.04. I usually have trouble with my computer and 9.10, the sound on boot up is even choppy so I don't use Karmic. After you get accustomed to the video apps in avlinux 3 then switch back to Ubuntu because Ubuntu is better in the long run :)

---

### Post by cotcot on 2010-02-04
If you are not afraid from command line you could use ffmpeg directly. To have the codecs compiled in ffmpeg it is good to install ffmpeg like describe [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095").

```
ffmpeg -i cliptobeconverted.dv clipconverted.mp4
``` should do the job for 1 clip. 

[[COLOR="Red"]This thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=867670") can help you for batch converting with ffmpeg.

I hope this gives some inspiration.

---

