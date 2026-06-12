---
title: "fresh install problems with 8.10 on serp4"
date: 2008-11-13
forum: System76 Support
---

### Post by eyecreate on 2008-11-13
I did a fresh install on my serp4 laptop of ubuntu, deciding to use the new 8.10. I've encountered a few problems with this install. One, the new network manager seems to disconnect me more than the manager in 8.04, or maybe it's just me, but I've had it crash every time I turn my network switch from on to off. I check in system manager, and it shows the applet and a program called "net" as uninterruptable. Even a kill -9 command to the processes doesn't stop them, only a full restart. Also, what seems new is that the light that I used in 8.04 next to the switch used to be orange if bluetooth was on but not wifi, and was purple if both were on. Now it is similar, but it blinks between the colors when I'm connected to a wifi spot, even though not all the time, almost like it's now a "monitor" for network traffic. Is this normal? I also had seen usplash on my factory setup I got the laptop in with a high resolution boot screen, now I get the default 640x480 low res screen, how do i change it to what i had when i first bought it? (this should change with the system76 driver so, when you restore to factory, much more things actually go back to "factory" setup) Suspend works fine it seems, but I now see the actual suspend text as it i suspending, whereas on 8.04, it was just black as it suspended.(i know it's a minor thing, but It makes it look nicer) As i read in another post, cheese is broken so I can't test if my webcam still works, but i'd assume it would. otherwise, I think everything else works fine. I'd really like to have my stuff still working in this great new ubuntu version, an on reinstalls, not just from factory. Thanks!

---

### Post by thomasaaron on 2008-11-13
> the new network manager seems to disconnect me more than the manager in 8.04, or maybe it's just me, but I've had it crash every time I turn my network switch from on to off. 

The wireless switch thing might be a bug. But you probably should run this command to prevent freezing due to the wireless card driver:
```
sudo apt-get install linux-backports-modules
```

> Also, what seems new is that the light that I used in 8.04 next to the switch used to be orange if bluetooth was on but not wifi, and was purple if both were on. Now it is similar, but it blinks between the colors when I'm connected to a wifi spot, even though not all the time, almost like it's now a "monitor" for network traffic. Is this normal? 

Yes. I don't fully understand it. But it is supposed to be functional in some way.

> I also had seen usplash on my factory setup I got the laptop in with a high resolution boot screen, now I get the default 640x480 low res screen, how do i change it to what i had when i first bought it?

[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

> As i read in another post, cheese is broken so I can't test if my webcam still works, but i'd assume it would. 

Try Applications > Internet > Ekiga Softphone

---

### Post by eyecreate on 2008-11-13
For the usplash item, I already looked at this post, but when I tried to change the resolution, it booted up blank instead of a loading bar. I'm gona try out the tool startup-manager to see if it does it anything.

---

