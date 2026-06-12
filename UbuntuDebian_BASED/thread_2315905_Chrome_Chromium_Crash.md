---
title: "Chrome Chromium Crash"
date: 2016-03-03
forum: Ubuntu/Debian BASED
---

### Post by daviddsmith82 on 2016-03-03
I'm running 32-bit Zorin OS 9 built off Ubuntu 14.04 on an Intel Vaio laptop and need some help with some Google chrome and Chromium issues.


The problem started when ended support for 32 bit Google chrome recently took effect. To remedy, I opted to install 32-bit Chromium instead. 


So, I  first used apt-get autoremove to clear out some space, then 


used apt-get purge google-chrome-stable to delete existing chrome install.


Then I used apt-get install chromium-browser . All above went off without issue. 


My issue reared its head when I tried to sign in to Chromium through settings. The browser froze then the laptop screen went black and the hard drive stopped spinning. I had to hard reboot to resolve. 


To try to remedy I've done the following:


deleted /.config and .cache  files for google-chrome AND Chromium
Tried chromium-browser --disable -gpu
Tried turning off some GPU related flags


I was eventually able to sign-in by changing some flags , but sites like the chrome web store and aol.com still crash the system. 


I've not yet tried turning off hardware acceleration , but I feel this will also be another fail, as it was turned on and working fine before the switch to Chromium. 


Could this be related to something in gnome3? Is there a way to restart gnome or delete existing gnome cache or profiles? 


Any help is much appreciated!


David

---

### Post by howefield on 2016-03-03
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

