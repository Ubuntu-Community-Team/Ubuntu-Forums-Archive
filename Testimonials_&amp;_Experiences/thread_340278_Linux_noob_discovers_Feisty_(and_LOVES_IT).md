---
title: "Linux noob discovers Feisty (and LOVES IT)"
date: 2007-01-17
forum: Testimonials &amp; Experiences
---

### Post by Severa on 2007-01-17
You're looking at one happy Linux noob 
(started out a month ago with Ubuntu Edgy as my VERY FIRST Linux distro!)

I just got done about an hour ago installing Feisty Herd 2 from ISO (x86 desktop), a clean install.

(For the record I have an Athlon 2600+, 1GB RAM, 80GB HD, GeForce FX 5900 XT)

Got all my pics and music loaded up, then installed nvidia-glx and flashplugin-nonfree.

I then installed the Restricted Formats codecs:

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui 
```

and 

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

After that I tried out CNN.com videos, but they were choppy as hell. Took out totem-gstreamer and switched it with totem-xine.

THEY PLAYED! where they're SUPPOSED to play. WITHOUT FIrefox's Mediaplayerconnectivity plugin! *HappyDance*

Then I took it for an ultimate test....WWE.com. Clicked on my personal favorite, the Undertaker, and checked out a few videos there. THEY WORK! No choppiness, looks and sounds awesome!

Cheers for Ubuntu and Feisty, and for the great help I've received on these forums! Couldn't have done it without you!

---

### Post by discord on 2007-01-17
nice to hear feisty is coming along nicely.  It's almost upgrade time again. Maybe I can keep my files this time...

---

### Post by ubuntu27 on 2007-01-19
> **Severa said:**
> You're looking at one happy Linux noob 
(started out a month ago with Ubuntu Edgy as my VERY FIRST Linux distro!)

I just got done about an hour ago installing Feisty Herd 2 from ISO (x86 desktop), a clean install.

(For the record I have an Athlon 2600+, 1GB RAM, 80GB HD, GeForce FX 5900 XT)

Got all my pics and music loaded up, then installed nvidia-glx and flashplugin-nonfree.

I then installed the Restricted Formats codecs:

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui 
```

and 

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

After that I tried out CNN.com videos, but they were choppy as hell. Took out totem-gstreamer and switched it with totem-xine.

THEY PLAYED! where they're SUPPOSED to play. WITHOUT FIrefox's Mediaplayerconnectivity plugin! *HappyDance*

Then I took it for an ultimate test....WWE.com. Clicked on my personal favorite, the Undertaker, and checked out a few videos there. THEY WORK! No choppiness, looks and sounds awesome!

Cheers for Ubuntu and Feisty, and for the great help I've received on these forums! Couldn't have done it without you!

That's nice to hear! 

BUt, one warning though: FEISTY IS NOT EVEN BETA YET. It's still under development, so things could go wrong at any time. Make sure to backup your files frequently.

---

### Post by Severa on 2007-01-20
> **ubuntu27 said:**
> That's nice to hear! 

BUt, one warning though: FEISTY IS NOT EVEN BETA YET. It's still under development, so things could go wrong at any time. Make sure to backup your files frequently.

Oh yeah, I'm fully aware of that. I've got my music saved to a DVD-R, pics and stuff saved to CD-R, and I've still got my Edgy LiveCD in case things get REALLY messed up.

---

### Post by sethvath on 2007-01-20
Instead of the above mentioned updates I prefer 

sudo aptitude install ubuntu-restricted-extras

---

### Post by Enverex on 2007-01-20
> **ubuntu27 said:**
> That's nice to hear! 

BUt, one warning though: FEISTY IS NOT EVEN BETA YET. It's still under development, so things could go wrong at any time. Make sure to backup your files frequently.

For Alpha software it works rather well. Using it as my every day desktop here without issue (runs better than Edgy due to the new kernel and updated software). So that's nice. But I also know alot about Linux so if it did go wrong I could fix it, heh.

---

### Post by WorkingOnWise on 2007-01-21
glad to hear feisty isn't too feisty on breaking things.... my production laptop, my main work machine, is right now as i post this, upgrading to feisty. I changed all the sources to feisty from edgy,  and away we went! I needed OO 2.1 and there wasn't a deb from ubuntu except for feisty, so i figured whats the worst? Smoke my os? have to reload everthing? have to restore my data? So what! I've gone thru that many times in, well, you know- cuz they broke something and I got to fix it! At least this time it will be in the quest for productivity!

WhooWhOOO! Yipe! (please sir Feisty, be kind to my lil' ol' laptop, please...)

Oh, btw, Do Not Dive into alpha software like an idiot, just cuz it seemd kewl! It's Not! It's foolish! And can cause severe head trama if you don't have one of those neato lcd monitors to slam your head into! Them galss crt monitors are deceptively tough! Just trust me. Step away slowly from the alpha software and nobody has to get hurt today...

Now what was the path to that nightly kernel tar ball? I hear it will enable holographics on my ATI GPU!

---

### Post by bobbybobington on 2007-01-21
And it's only going to get better...:D

---

### Post by Severa on 2007-01-21
Yeah but I don't have ATI, I've got NVIDIA.

Kinda feel sorry for those of you who have ATI. You REALLY gotta jump through some hoops to get your stuff to work, from what I can see.

So far so good here. Even got the latest version of Beryl working now. Now if I can just figure out WINE (geez that program is a headache and a half. I had better luck getting Beryl to run...)

---

### Post by Pobega on 2007-01-22
Mmm, Feisty may not be the best distribution for a "*Linux noob*". It's pretty broken from what I understand, but if it works for you stick with it I guess. Since you're new to Linux though I would probably recommend 6.06, as it's more stable then Feisty.

---

### Post by Severa on 2007-01-22
> **Pobega said:**
> Mmm, Feisty may not be the best distribution for a "*Linux noob*". It's pretty broken from what I understand, but if it works for you stick with it I guess. Since you're new to Linux though I would probably recommend 6.06, as it's more stable then Feisty.

Really? I started out with 6.10 and didn't have a single problem. Lucky me I guess.

---

### Post by total wormage on 2007-03-17
mm, there doesn't seem to be a general feisty loving thread (or a subforum for that matter, it deserves it!)

i
love
feisty!

*^_^*
really is going to make it a LOT easier for new users to get the hang of linux :]
ehm...

*dances*
:KS :KS :KS :KS

---

### Post by 3rdalbum on 2007-03-17
> **Severa said:**
> 
Kinda feel sorry for those of you who have ATI. You REALLY gotta jump through some hoops to get your stuff to work, from what I can see.

That's funny - I run ATI, and although I hate how the driver makes my computer crash occasionally, I keep hearing about instances where software and kernel updates have broken Xorg for Nvidia users; whereas I've never heard about those problems for ATI and Intel users. I kinda feel sorry for those who've got Nvidia :-)

---

