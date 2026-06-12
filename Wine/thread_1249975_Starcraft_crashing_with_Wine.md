---
title: "Starcraft crashing with Wine"
date: 2009-08-26
forum: Wine
---

### Post by razorboy5 on 2009-08-26
Hi

I just recently had Starcraft installed on my Ubuntu 9.04

first time i start Starcraft it works fine however after i quit the 1st time and try to start Starcraft again it always crashes and "blacks" my computer screen which then i resort to restarting my laptop

every once in a while this happens when i'm trying to quit starcraft the 1st time and crashes during the exiting process

is there any fix to this problem?

thx

---

### Post by beastrace91 on 2009-08-27
What wine version are you running? 

Also perhaps the first time you exit Starcraft it isn't fully exiting? Try checking your system processes to see if it is hanging around.

As for your screen going black when it does crash, if you open your wine cfg and set starcraft to run in a virtual desktop it will not crash X when SC dumps OR if you really want to run it full screen instead of rebooting you can press control+alt+f1 to get a terminal loggin and then run ```
sudo /etc/init.d/gdm restart
``` to restart your X server.

~Jeff

---

