---
title: "[SOLVED] Issues With 8.10 And Nvidia Video/Sound Drivers"
date: 2008-12-16
forum: Server Platforms
---

### Post by HotDogBunToo on 2008-12-16
Went with upgrading to Ubuntu Server since it'd utilize tapping into my 4GB upgrade without going 64bit.  

However my issues with my integrated Nvidia videocard (nforce 630i / GeForce 7100) is rendering me to a 800 x 600 screen. So far I tried installing the headers for this kernel then installing the video drivers from Nvidia themselves as well as installing the same propitiatory video drivers from the Synaptic and in System -> Hardware Drivers.  Sadly all I'm getting for my efforts is a message before login screen that says "(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!" :confused:.  Also worth noting is that my sound also isn't coming back up. :confused:

I had issues with Ubuntu Server before yet went to desktop route after giving up, now that I'm up to 4gigs RAM I'm moreso stuck with this issue until things are figured out (no way am I wasting 1gig of RAM) so any help would be GREATLY appreciated ):P

EDIT:

This isn't specifically a Server issue since I had same error message in desktop edition.  Fix is here @ [http://ubuntuforums.org/showthread.php?t=1013589](http://ubuntuforums.org/showthread.php?t=1013589) but in a nutshell was fixed by merely changing BIOS to read memory under 1.75GB.  Also, sound was just some random setting I had to fiddle with & was never an issue lol.

---

### Post by Cillys on 2009-05-23
I have been having the same issue with my Sony Vaio and GeForce 7600 .. and i too have 4Gig of ram ... so i will remove a stick and see if that works ....
 
i would never had thought of that .... thanks!   



UPDATE ... IT WORKS!!!! I removed the 2GB mem stick and i have NVIDIA drivers and multi displays now with my Sony VAIO ...   THANKS!!!

---

