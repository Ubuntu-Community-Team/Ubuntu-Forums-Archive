---
title: "Sound Earplug buzzling noise on Ubuntu(16.04) with Asus UX501vw"
date: 2016-11-20
forum: Ubuntu Development Version
---

### Post by curiouscod3 on 2016-11-20
I am using Asus Zenbook UX501VW.
Recently, I installed **Ubuntu 16.04** and up-to-date kernel.
I eventually fixed some issues such as maximum cpu speed problem, wifi issue after updating latest kernel. 
I used to install kernel 4.3.5 because I read an article that someone recommended this kernel version to fix some issue.However, this downgraded kernel has also problem. So, I installed latest stable kernel **4.8.6.**


In fact, I am satisfied with this kernel except for one issue.
After suspend(sleeping) my laptop and waking up, buzzling noise(like cpu core-wire noise) from earplug starts right away. This issue doesn't exist when I reboot. Only after suspend sleeping.
I did many instructions to fix this issue such as updating nVidia driver, and Mute microphone something with Alsa  ... But still the noise problem exists. 
I think that this issue is related to not reload some driver after waking up from suspend. I really don't know now.


Please help me to solve this issue... 


 - Asus Zenbook UX501VW
 - Ubuntu 16.04 Desktop Ver.
 - Kernel Ver : 4.8.6-040806-generic #201610310831 SMP Mon Oct 31 12:33:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
 - Using NVIDIA binary driver - version 370.28 from nvidia-370

---

### Post by ventrical on 2016-11-22
It could be some kind of CEMF  (if you are leaving the ear-plug lines *in* while in suspend mode) .  I am not saying for sure but before you suspend could you remove your ear-plugs  from the jack - then wake and insert earplugs and see if the problem still perisist.?

Regards..

---

### Post by curiouscod3 on 2016-11-29
I did exactly what you mentioned. Unfortunately, no progress.. it is same. When I powered off completely and start again, noisy sound is gone.. I don't know why only after waking up from suspend sleeping. Do you have any item?

---

### Post by curiouscod3 on 2016-12-01
I solved this tricky issue my self after performing all  semi-solutions available on the Internet by myself.


The way to resolve this is just type on the Terminal.


**> sudo alsa force-reload**


That's IT.


Good Luck!

---

