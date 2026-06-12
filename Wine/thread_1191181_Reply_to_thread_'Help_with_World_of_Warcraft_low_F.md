---
title: "Reply to thread 'Help with World of Warcraft low FPS"
date: 2009-06-18
forum: Wine
---

### Post by Dead_$partan on 2009-06-18
Hi,

I recently installed Ubuntu 9.04 and decided to give WoW a try, decided to download the web based installed and get it on the system that way, took hours but installed and patched all the way up to 3.1.2 but I have an issue with the video performance.

My FPS never goes above 25 but mostly sits around 18. I followed some instructions from some websites to help improve this but nothing seems to help. I have tried the following.

Added the following to config.wtf
 	Code:
 	SET gxApi "opengl" 
SET ffxDeath "0"
SET ffxGlow "0" 
Also tried creat5ing the registry value  	Code:
 	GL_ARB_vertex_buffer_object 
Have lowered the resolution to 800x600 and have tried vsync on and off(was on by default).

Refresh options only give me 69 and 70Hz which seems like an odd value and have also tried running the game with the -opengl switch from a terminal.

Oh and I am using nvidia drivers 180.44

Can anyone advise what else I can change?  Oh and latency has been 50ms so doesnt seem to be an issue.

Cheers

---

### Post by Dead_$partan on 2009-06-19
A friend advised me to try installing envy, even though i had the correct drivers installed, this seems to have resolved the fps to a degree as it has jumped to 120 at times but is a bit eratic.

I could get 98fps at one side of a room then ran to the other and drop to 28fps, does anyone have any suggestions I could try?

---

### Post by Bios Element on 2009-06-19
Sounds normal to me. It all depends on how much your system is having to process.

---

### Post by veedub on 2009-06-20
I am using NVIDIA drivers 180.44 and wine 1.1.23. and get avg FPS of 50-60 on WoW using a mobile 8600GT.

Make sure you are using the latest version of wine from WINEHQ.  (the ubuntu version from canonical's repo doesn't work very well) To do this you will need to add the WineHQ repositories:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

Then you will need scott Ritchie's GPG key:

[http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg](http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg)

Too add this, from Synaptic go "SETTINGS->REPOSITORIES->AUTHENTICATION->IMPORT KEY FILE"


Make sure that  NVIDIA drivers are running.  An Easy way to tell is if the NVIDIA X Server settings dialog will open (SYSTEM->ADMINISTRATION->NVIDIA X SERVER SETTINGS).  If it opens, you are running on NVidia drivers, if not, you are running with VESA or some other default driver).

In NVIDIA Xserver config make sure the following is enabled:

Xserver XVideo Settings:

Sync to VBLANK

OpenGL Settings:

Sync to VBLANK
Allow Flipping
Slider set to high performance

Anti-aliasing set to application.

HTH

---

### Post by Lord Noxarethor on 2009-06-20
Oh and disable Compiz while playing... it is known to eat up graphic resources!

---

### Post by Dead_$partan on 2009-06-21
Thanks for the replies people.

When you say to ensure  Anti-aliasing set to application, do you mean to make sure the 'Override Application Setting' is un-ticked?  Also there are 2 Sync to V Blank options, do both need to be selected?  Version of wine is 1.1.23, I will try .24

Many Thanks

---

### Post by Dead_$partan on 2009-06-21
Hmm I tried the above sugegstions but it seemed to make wow run worse. (I had prev deleted Cache/Interface/WTF which put me back to out of the box D3D options and it was running ok except for the eratic fps).

I seem to have another issue tho, not sure of this has been rpesent all the time or not as I have been restarting wow a lot with all the changes I have been making but the game will suddenly cut out.  The window just vanishes, process is no longer running.  I dont get any messages stating I have been logged out and I can log back in with no issues, does anyone have any ideas what might be casuing this?

---

### Post by NightMKoder on 2009-06-21
That's probably a crash. Run it from console and see if wine says something about a fatal error.

---

### Post by Dead_$partan on 2009-06-21
Ok ran it from terminal and get:
```
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc455f4
```

---

### Post by NightMKoder on 2009-06-21
Yep - that's a crash. Make sure you're running wow in opengl mode. It will help with stability.

---

### Post by Dead_$partan on 2009-06-21
Ok ran from terminal with -opengl and it didnt crash, ran Nexus and it was pretty stable all the way through.  Is running the -opengl switch the same as adding the opengl setting in config.wtf?  It may be just a perception thing on my part but the game seems to run better if I start it via a terminal with the -opegl switch as opposed to adding this option in the config file.

---

