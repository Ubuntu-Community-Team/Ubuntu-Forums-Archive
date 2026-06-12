---
title: "Howto: Enable Lenovo Y500 Backlight Control Under Ubuntu"
date: 2014-03-04
forum: Tutorials
---

### Post by andrewkoz on 2014-03-04
Hi guys,

New Ubuntu Forums user here so please forgive any ignorance. I've had the issue of my backlight being stuck on full, not changing with either the function keys or the GUI utility in Ubuntu since I first installed Ubuntu on the laptop. It seems to be a fairly common problem with Lenovos. Strangely, the backlight control works fine in Kubuntu and Xubuntu, but not in Unity or GNOME. I had actually moved to Xubuntu just because my laptop was practically unusable in the dark as the brightness of the screen was greatly straining on the eyes. Recently moved back to Ubuntu to give the backlight issue another go. 

I managed to get it working (sort of) using this tutorial: [http://forum.notebookreview.com/ideapad-essential/716609-tutorial-lenovo-y500-ubuntu-linux-brightness-key-fix.html](http://forum.notebookreview.com/ideapad-essential/716609-tutorial-lenovo-y500-ubuntu-linux-brightness-key-fix.html)
Was a fairly hacky solution though as brightness was only controllable from the function (fn) keys and not the slider utility, however, the brightness moved in jerky increments but at least it was a start. However, I soon found the xbacklight utility which for some reason could change the brightness where everything else had failed (still have no idea why). With a small shell script (not mine) and the inotify-tools util I was able to get my backlight control working perfectly from the GUI slider and the fn keys.

**PS: I take no credit for this guide. All credit goes to the creator of xbacklight, inotify-tools and Esteban Roloff (creator of the shell script)**

_My setup:_
- Lenovo Y500 (Intel i7-3630QM, 8GB RAM, Nvidia GT650M GPU, 1366x768 display)
- Ubuntu 12.04 LTS x86_64
- Nvidia 331.20 driver

_**The Guide:**_


[LIST]
[*]Install the latest proprietary Nvidia driver from "Additional drivers" under Ubuntu's settings or by running *sudo apt-get install nvidia-current* in the Terminal and ensure nvidiabl is not installed. 
[/LIST]

[LIST]
[*]Install xbacklight and inotify-tools by entering *sudo apt-get install xbacklight inotify-tools *in the Terminal. 
[*]Create a shell script using an editor of your choice (I used nano for simplicity) with the contents from [http://pastebin.com/RCbNPUhC](http://pastebin.com/RCbNPUhC). Save the script anywhere with a name of your choosing (I saved it as .xbacklight.sh in ~). 
[/LIST]

[LIST]
[*]Make the script executable by typing* chmod +x scriptname.sh *into the Terminal, replacing scriptname with the name of your script. Ensure your working directory matches the location of the script. 
[*]Test the script by typing *./scriptname.sh *into the Terminal, again ensuring your working directory is correct and replacing scriptname with the name of your script. 
[*]Leave the script running in the Terminal and try and change your brightness using the fn keys or the slider util. If all went well it should be working now! :) 
[*]If all is well, set the script to run at startup by adding the script as a startup application. 
[/LIST]

Hope this helps someone! :)

---

### Post by andrew103 on 2014-03-17
had my uncle`s lenovo with a fresh copy of ubuntu, can`t seem to manage to work on his laptop. any suggestion? i mean, what am I doing wrong? followed all of your steps. thanks for your reply

---

### Post by andrewkoz on 2014-03-30
> **andrew103 said:**
> had my uncle`s lenovo with a fresh copy of  ubuntu, can`t seem to manage to work on his laptop. any suggestion? i  mean, what am I doing wrong? followed all of your steps. thanks for your  reply

Does the backlight change when executing "xbacklight -dec 10" or "xbacklight -inc 10" in terminal?

---

