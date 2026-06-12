---
title: "Feisty/Beryl/8000GTX questions?"
date: 2007-03-05
forum: Ubuntu Customization Guide
---

### Post by Sinister006 on 2007-03-05
I Tried to install beryl on edgy but i could not get it to work no matter what i tried. I have tried every "how to " i could find.

The problem with edgy i was having was when i would start beryl-manager the icon would load in the tray and then the desktop would freeze. The cursor would work but i could not do any actions.

This was done with the latest nivida driver ver 1.0-9746. To load the drivers i used envy. 
  here are my specs

edgy x86 "should i have used 64bit?" see below

Core 2 duo extreme x6800 overclocked to 3.46 ghz
3 gb 6400 800mhz ram
2x nvidia 8800 gtx 768mb in sli mode
nvidia 680i SLI mobo with p25 bios

So as of right now i have decided to upgrade to feisty and see if i can get beryl to work on this monster.
I guess my question is has anyone with the same setup or close to the same problem found a way to resolve this issue. And also has anyone tried beryl on feisty with this type of set up.If so what method of installation  did you use. Also would Would it be better to use the 64 bit version of ubuntu for my system. "Im a Linux noob, but I do like what I have seen so far."

Thanks in advance

---

### Post by marrabld on 2007-03-05
What version of Beryl are you running.  Are you trying to get it to run on your customized live disc or just install?

I am running 0.2 preview on edgy with Nvidia 7800gt with out too many problems on a live Disc and install.

Try running the Beryl manager and turning off all of the features.  Then load the Desktop, if it loads then turn on the features you want one by one.  I had problems with the trailing windows, it kept crashing my machine until I turned it off.

---

### Post by The Noble on 2007-03-05
Try reinstalling the drivers, using a manual approach as the envy script may have caused a problem. Just make sure you have graphics acceleration (glxinfo) and that all of the extra options are added to xorg.conf. Feisty may provide you with more luck, becuase th latest drivers are included in the repos.

---

### Post by pastaq on 2007-03-06
I had the same problem with my 8800gts. Found the solution in another thread.

sudo gedit /home/(your username)/.beryl/settings

change s_sync_to_vblank=false

There have been a lot of cases with the screen or windows going black. to fix it log into a failsafe gnome and change these values

Beryl Manager- Advanced Beryl Options- Composite Overlay Window- Use COW
Beryl Manager- Advanced Beryl Options- Rendering Platform- Force AIGLX

It's a workaround for a bug in the Nvidia drivers. tends to make the system laggy tho. Theres another solution that i haven't tried thats supposed to be less devastating to the frame rates. its in this thread

[http://www.ubuntuforums.org/showthread.php?t=344766&highlight=beryl+8800](http://www.ubuntuforums.org/showthread.php?t=344766&highlight=beryl+8800)

---

