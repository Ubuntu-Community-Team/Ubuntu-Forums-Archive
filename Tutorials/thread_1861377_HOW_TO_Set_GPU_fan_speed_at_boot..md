---
title: "HOW TO: Set GPU fan speed at boot."
date: 2011-10-15
forum: Tutorials
---

### Post by d4m1r on 2011-10-15
[SIZE=2][COLOR=Red]*NOTE: THIS WAS DONE USING AN NVIDIA CARD AND NATTY (11.04) BUT SHOULD WORK IN OCELOT (11.10) TOO*[/COLOR][/SIZE]


[FONT=Arial]Hey guys, so even though I only started using Ubuntu at home this month I am a hardcore Windows users and also have experience with Solaris 10 at work. Anyway, in my Windows 7 Ultimate partition, I have something called "EVGA Precision" for my EVGA GTX 260 which is basically a tool that allows me to change the fan boot (and overclock it) through a GUI interface.

My cards stock fan speed is 30% (don't ask me why) and it runs really hot so I set it to 80% in Windows 7. When I switched over to Ubuntu, I lost this tool because EVGA doesn't make a linux version but I have found something that works just as well that has dropped my idle temp from 55C+ to 45C.

First, you want to get something that allows you to easily monitor your hardware. For this I used indicator-sysmonitor (see code below to install it) and it looks like this:[/FONT]
[IMG]http://i.imgur.com/ksZkR.png[/IMG]

[FONT=Arial]Open a terminal session (ctrl+alt+f is default) and paste this to install it:[/FONT]

```
sudo add-apt-repository ppa:alexeftimie/ppa sudo apt-get update sudo apt-get install indicator-sysmonitor
```[FONT=Arial]To run it, search for "System monitor indicator", and to customize it like I have, just right click on it. I'll explain how to get it to run at boot too later.

Now for the fan speed part ([COLOR=Red]Note #2: No clue if this will work with ATI cards[/COLOR]).[/FONT] [FONT=Arial]Search for "nvclock" in the Ubuntu Software Centre and install it. It is a command line only application so you'll have to access its options using a terminal session.
The main option we are interested in is:

[/FONT][CODE[FONT=Arial]]nvclock -f -F 100[/CODE][/FONT]

[FONT=Arial]^That would set the fan speed to 100% in that case (I recommend 80%) and you should be able to hear the fan getting louder.
Unfortunately all these settings will be lost @ boot. However, 11.04 makes it easy to run these applications when you login so that what we will do next.
To get them to run at startup, go to **System Settings>Startup Applications**. You should get a window like this:
[IMG]http://i.imgur.com/ynJhg.png[/IMG]

Hit add and then enter these 2, save them, restart your PC and see if it works :D

[IMG]http://i.imgur.com/NTWdG.png[/IMG]

[IMG]http://i.imgur.com/pj8in.png[/IMG]
[/FONT]

---

