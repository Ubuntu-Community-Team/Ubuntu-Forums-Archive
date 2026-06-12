---
title: "Jaunty VM Monitor Resolution limited"
date: 2009-08-05
forum: Virtualisation
---

### Post by gawdin on 2009-08-05
I just recently decided to run a Virtual Machine of Ubuntu 9.04 Jaunty on my Windows XP laptop. (I love using Linux but need Windows for work and games). Everything is working more than great except the monitor display. It is limited to just 640x480 and 800x600 resolution. I have used other distributions in the past on this computer and the monitor was able to go at least up to 1024x768 without any additional setup. I tried Detecting Monitor under the Display setup, and the Hardware Drivers. Neither of these were able to fix it. I currently have the video card set to 50MB and RAM set to 1GB, which these settings were fine on other distros.

Could someone help me get this so that I could have at least 1024x768 resolution or at least link me to a guide to do it? Thanks for the help. 

Not Related:Also the search function on the forums doesn't seem to be turning any results, it just keeps redirecting me back to the advanced search settings, if I am posting about something that has already been resolved could you just link me, thank you.

---

### Post by gawdin on 2009-08-06
Update: I have also installed the guest additions and that doesn't seem to allow it either. Update Manager and System Test didn't offer monitor stuff either.

What confuses me most is that other distributions worked just fine without additional setup.

---

### Post by gawdin on 2009-08-06
It would seem that for whatever reason Xorg had either be corrupted or not installed, I vote corrupted as I had other problems with the install. A clean install and update fixed this issue.

---

