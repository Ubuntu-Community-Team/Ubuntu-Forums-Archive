---
title: "Any pangolins on Jaunty?  Shutdown/Restart issue"
date: 2009-04-08
forum: System76 Support
---

### Post by abulluck on 2009-04-08
I upgraded to Jaunty recently and have a recurring issue I can't seem to solve.

First of all, when I shut down or restart now, after the ubuntu log out splash screen, my screen goes white for a bit.  Didn't do that before.

Sometimes (not all the time and can't figure out patterns) when I shut down or do a restart the system hangs on the white screen and goes no further.  If I leave it, the white screen starts dulling (for a lack of a better term) in random areas around the screen too.

A hard reset gets me out, and the system loads fine after that, but this is annoying.

Anyone else have this?

---

### Post by thomasaaron on 2009-04-08
Which Pangolin do you have?

Has there been a suspend/hibernate-resume cycle before the shutdown?

---

### Post by Lee_Machine on 2009-04-08
Im running the PanP4n, Jaunty 64 bit, and I have the same issues. I recently got an x.org update and I have yet to have the white screen hangs, but still every time I shutdown the screen goes wacky after the splash screen. By wacky I mean odd colors. (but still shutdown properly) 


I haven't looked into it as its not a major issue and I figured it was just a bug in the beta that will be fixed. 

Also this is the first I have heard of anyone else having it.

To answer thomasaaron's question this happens in all instances. The shop Pangolin's get this?

---

### Post by thomasaaron on 2009-04-08
I'm not sure yet. Haven't gotten to the PanP4n yet.

---

### Post by Lee_Machine on 2009-04-08
Yeah, these times must be crazy for you guys. Trying to test all your machines to make sure everything works and is good to go the day a new release comes. 

I take it this is when the S76 driver is in heavy dev? :lolflag:

Well hopefully some of the comments I have made about how great the panp4n runs with Jaunty (besides the tiny shutdown issue gives you some relief. (without the S76 driver) 

Overall I would say the laptop runs much better than with 8.10. Faster, more responsive, and more stable!

---

### Post by thomasaaron on 2009-04-08
Yep! This is game time. SuperBowl Sunday for System76. :lolflag:

---

### Post by abulluck on 2009-04-08
I have the panp4n.  

thomas, I don't expect you to have an answer on my issue as I know you guys are working the drivers for the full release.

I just wanted to see if there were any other eager folks out there who made the jump and have the same issue.

Thanks for your input Lee_machine.  I will look for the x.org update or try to go get it and see if that works.  The screen is pretty funky and I would like to get it fixed regardless of the the shutdown issue as it just doesn't look clean like the rest of ubuntu.

---

### Post by thomasaaron on 2009-04-08
Just curious, did you you go to System > Administration > Hardware Driver and enable the nVidia driver? If not, you're probably running nv, which would explain a lot.

---

### Post by abulluck on 2009-04-08
Yeah, I am running the nvidia driver.

---

### Post by Brian_Newbie on 2009-04-27
I'm having the same issue. I first upgraded to Jaunty from Intrepid on my Panp4n and got lilo errors and such which I thought may be the issue. 

So I uninstalled via synaptic the lilo bootloader but my computer still retained those funky colours on shutdowns and restarts. Although I get the wierd colour combo on shutdowns/restarts, I find my computer restarts ok everytime.

This is not the case with shutdowns though. Half the time my pangolin shuts down despite the colours. The other half of the time it simply hangs on the wierd colour screen and I have to hold the power button down to turn off the computer. 

I thought that this was due to upgrade errors I was getting so I used a live CD and did a fresh install of Jaunty. 

Unfortunately, the fresh install did not correct the issue and I still get the fancy colour screen, 50% of the time it hangs until I hold the power button, the other 50% of the time it shuts down ok. 

Does anyone know yet what the underlying problem is?

---

### Post by Brian_Newbie on 2009-04-27
I followed instructions from Tom in this thread: [http://ubuntuforums.org/showthread.php?t=1136484](http://ubuntuforums.org/showthread.php?t=1136484) and found my Panp4n no longer hangs with several shutdowns using the Nvidia 173 driver. 

Here's hoping that Nvidia can fix the funky colour screen issue on shutdown so the computer shuts down as cleanly as Intrepid did.

---

### Post by abulluck on 2009-04-27
Yep, going back to Nvidia 173 seems to have everything back to normal.  I also did a fresh install.

Sorry for not getting back sooner.

---

### Post by gila_monster on 2009-04-27
I have seen the white screen, but haven't otherwise had problems on my panp4n.

Only real issue I'm having right now is getting wicd to see my WAP. That might be a function of the router, though.

---

### Post by xakh on 2009-04-28
Every time I try to start the Hardware Drivers section, it crashes. It loads a few inches, then dies. I can't access my proprietary drivers. Help?

---

### Post by stewpac on 2009-04-28
Yeah, I have the same problem, running the nvidia driver on my panp4n. Sometimes the screen is white sometimes there's a strip of color but mine has never shutdown or restarted correctly since the upgrade. (I did not do the fresh install.) I'm able to see my hardware drivers section though.

When I upgraded, after I got the errors about lilo which I ignored and then uninstalled, and the update completed I attempted to restart and immediately got very strange video errors. I was asked to do something to reconfigure the driver (I'm not sure what because I couldn't see all of the box). I think I ended up with a 'default configuration' for whatever the box was talking about.

So I guess I'll just wait like everyone else for a solution. On the upside, it's amusing that suspend works fine but shutdown doesn't - at least to me :)

---

### Post by Brian_Newbie on 2009-04-28
I guess some others are having similar white screen shut down issues in this thread:

[http://ubuntuforums.org/showthread.php?t=1135997&highlight=sudo+shutdown](http://ubuntuforums.org/showthread.php?t=1135997&highlight=sudo+shutdown)

It appears related to the Nvidia driver from what people including myself have been experiencing. 

I decided to do a fresh install from the Jaunty live CD a 2nd time and have not yet installed any one of the Nvidia drivers or for that matter the system76 driver. 

I can safely state that I no longer get the white screen on my panp4n computer now and it shuts down as quickly as it did with Intrepid Ibex without any delays or errors (10 test shutdowns so far). 

I'm kind of afraid to install an Nvidia driver again either the 173 or the 180. Eventually I'll have to if I want the benefits (and drawbacks) of Nvidia.

---

### Post by thomasaaron on 2009-04-28
Brian_Newbee,

Correct, if you want desktop effects, you will need to install the 173 driver. You might still get the white/striped screen, but you should be able to shut down.

You also will need to install the System76 driver if you want to be able to use your fingerprint reader.

---

### Post by stewpac on 2009-04-29
I also found out that I couldn't use the ubuntu display app to adjust resolution and/or use my external monitor. When I used the nvidia settings app to do it, Ubuntu froze. I just told the nvida app what resolution to use on the *laptop* screen (it was already running at the correct 1680x1050 resolution) rather than use 'auto' and the *external* monitor worked. I used the option to Save to X Config file after backing up my old one without the external monitor connected or in use and now my computer shuts down correctly after the short ugly grayish screen that some have reported. Mine previously never shut down correctly. This is with the 180.44 driver, by the way.

The Xorg file is *much* larger now than it was before and has many more entries. I also have to put up with an Nvidia splash screen at startup for some reason. Anyway, I'm glad I can use my extenal monitor...

---

### Post by thomasaaron on 2009-04-30
Stewpack,

Downgrade to the 173 driver via System > Admin > Hardware Drivers.

---

### Post by garuhhh on 2009-04-30
is this not related to this?
[http://ubuntuforums.org/showthread.php?t=996719&highlight=nvidia+driver](http://ubuntuforums.org/showthread.php?t=996719&highlight=nvidia+driver)
though it doesn't really solve the problem, it gave me an idea.

when i shutdown/restart/hibernate i get weird screen artifacts. I posted my problem in youtube [here]("http://www.youtube.com/watch?v=_b9xxmg_02o") and [here]("http://www.youtube.com/watch?v=LBjT7Pye36I").

my problem was solved by adding "vga=791" to the boot options.

---

### Post by stewpac on 2009-04-30
I can try that now with the new xorg.conf file. I should have mentioned that I tried downgrading before doing what I said in the last post and found it didn't help at all.

I'll have to reply later with the status of my external monitor but I'll check the restart/shutdown issue now.

Update: I tried with both the 173 and 177 drivers and I experienced the same hang at shutdown as before on the 173 driver, the 177 didn't make a difference. With the 180 driver I get a decent shutdown (at least every time so far ~5 that I've tried). I doubt I will bother trying the external monitor at home with the 173 driver. Maybe this means my problem is somewhat different from others, I dont' know.

---

### Post by gila_monster on 2009-04-30
Something I've tried that seems to fix the screen update problems is the following:

[INDENT]Go to System=>Preferences=>CompizConfig Settings Manager

Go to Utility and select Workarounds

Check the box for "Force synchronization between X and GLX"

[/INDENT]

I don't know that this does anything for the White Screen of Doom, as I haven't done a reboot since trying this.

For what it's worth....

---

### Post by stewpac on 2009-05-01
Are there any other suggestions for this or are we all just blaming Nvidia for now?

---

### Post by thomasaaron on 2009-05-04
To fix this problem, please run...

sudo apt-get install linux-backports-modules-jaunty

It may not fix the coloration problems, but it should allow you to run the 180 drivers without hanging on shutdown.

---

### Post by PGScooter on 2009-05-09
Could this help?

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

HowTo: NViDIA 185.19 Beta Drivers in Ubuntu
> 
This HowTo is intended for Intrepid and/or Jaunty users who are experiencing oddball issues, such as glyphs, artifacts, and glitches from applications that use lots of small pixmaps/images.


---

