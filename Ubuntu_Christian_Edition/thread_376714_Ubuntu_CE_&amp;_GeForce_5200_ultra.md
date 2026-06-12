---
title: "Ubuntu CE &amp; GeForce 5200 ultra"
date: 2007-03-05
forum: Ubuntu Christian Edition
---

### Post by ivrey on 2007-03-05
Hi.
When I start my computer with Ubuntu CE CD my monitor is turn off.
System loading is complete (I have sound).
My video adapter is GeForce 5200 ultra.
I try any video mode, but I have this problem again and again.
sorry for my english.

---

### Post by eric_n_va on 2007-03-06
Does your motherboard also have integrated video?  On one of my computers I have an add on Nvidia card and sometimes Live CD's find only the integrated video and not my Nvidia card.  I have to do the following:

1 - boot PC and go into the bios
2 - change the bios to probe the onboard video
3 - save changes and reboot to the Live CD
4 - complete the installation (unless you're just taking a look without installing it to your hard drive.  If that's the case, skip to step 10 when you're finished) 
5 - reboot into the new installation
6 - do your updates - I use the console
     a) sudo apt-get update
     b) sudo apt-get upgrade (may take awhile)
7 - reboot
8 - Install the Nvidia drivers.  I usually use a program called Envy - [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)  This has worked better for me than the Nvidia-glx drivers.
9 - After installing your video drivers (whichever method you use), update your xorg.conf file but don't restart x yet.
10 - Reboot your machine and go into the bios again.  Change it to probe for the add-on card.
11 - After you save your bios changes quickly move your monitor cable back to the vga port on your video card (if you don't catch it in time use ctrl+alt+del)
12 - Hopefully you'll be up and running.

P.S.
If on-board video isn't causing your issue then I apologize for the lengthy reply :)

---

### Post by ivrey on 2007-03-21
I have not integred video card :(

---

