---
title: "Peavey ReValver MKIII on linux"
date: 2008-09-30
forum: Ubuntu Studio
---

### Post by cb951303 on 2008-09-30
hi everyone,

I currently purchased ReValver MKIII. For people who doesn't know what this is, its a modeling and effect processing software for PC. Basically you connect your guitar to your PC and start playing. It simulates amps, cabinets and effects etc... I tried GT3, AT2 and GTR3 and so far for me ReValver sounds the most realistic among all of them (especially the cabinet simulator)

The thing is, ReValver already has a MacOS version and it relies on wxWidgets 2.6.3 for GUI, so it's really possible to make it run on Linux with minimum effort.

If anyone is interested to see this software on Linux please send a request to Peavey from here: [http://www.alienconnections.com/support_enter.htm](http://www.alienconnections.com/support_enter.htm)

Thanks

PS: They already replied me so I'm sure they control their mails daily :)

> 
Hi,
I have forwarded your comment to the project manager, but I can make no promises.

Thanks,
/Michael Ljunggren
Peavey Electronics


---

### Post by GrantsV on 2008-10-09
Load up Wine.
Install low latency kernel.
Load Jack from Synaptic (with its GUI).

Reboot, start Jack
Install Reaper
Install WineASIO
Install Revalver

Please search for WineASIO for full instructions, there is quite a few steps to it but above is in a nutshell.  The hard part is getting low latency to work, I got some glitching.

I got RevalverII working just fine.

It would be much easier to install Ubuntu Studio which does low latency out of the box.  Then you just install wine, reaper, wineasio and Revalver.

All the best,
GrantsV

---

### Post by thorgal on 2008-10-09
no need of reaper. A light host like savihost.exe would do, which still requires wineasio. If you want a linux native VST host, dssi-vst is your best bet. I use it a lot for VSTis and it works really great. But if your VST does not have its internal preset saving mechanism, you may be in trouble, in which case the wineasio route is safer (vsthost.exe, savihost.exe or reaper can save VST confs).

---

### Post by cb951303 on 2008-10-09
thanks for both. even though I didn't try to run it through wine I knew it could be run (I had bad experiences with wineasio though). However I made this thread so that people interested in this software may request a linux version from peavey. Wine is always an option, it's better than nothing but a native version is the best :)

cheers

---

