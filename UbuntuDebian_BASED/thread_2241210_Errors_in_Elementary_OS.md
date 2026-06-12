---
title: "Errors in Elementary OS"
date: 2014-08-24
forum: Ubuntu/Debian BASED
---

### Post by luciano4 on 2014-08-24
I have a problem with my Elementary OS. Yesterday I installed a few drivers from Nvidia and since then I can't start my OS correctly. 
When I start the OS, throws me the following error: *"The system is running in low-graphics mode"*. [Screen here]("http://s2.postimg.org/yba8437x5/low_graphics.jpg")
If I close this window: [Screen here]("http://s11.postimg.org/7zls64tir/checking_battery_state.jpg") (the only think that I can do here, is ctrl+alt+F2)

I was reading that I can fix that by booting from the Recovery mode, but when I go in there, it throws the error *"fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver*" and I can't do anything. [Screen here]("http://postimg.org/image/keizl80c3/")

[I]My laptop: Asus N56VB (video card: Nvidia 740m)
[/I]
Please help

Thanks!

---

### Post by Stinger on 2014-08-25
Hi luciano4
Are you trying to run elementary Luna or Freya ?

---

### Post by luciano4 on 2014-08-25
> **Stinger said:**
> Hi luciano4
Are you trying to run elementary Luna or Freya ?

Luna !

---

### Post by Stinger on 2014-08-25
You need a newer kernel and x-sever for that laptop.
To try this you need a working network connection.
Boot your pc and hit ctrl+alt+F2 to get the command line.

To install the Trusty hardware enablement packages in Luna / Precise, please run the following command:

```
sudo apt-get install --install-recommends linux-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
```
Remember to reboot to activate the new kernel and x-server.
[LTS Enablement Stack page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") 

I'll try to deal with your hybrid graphics later.
noxit2 had a similar problem [here]("http://ubuntuforums.org/showthread.php?t=2213023") but that was before the Trusty LTS Enablement Stack was released.

Hope it works, unfortunately I can't try it myself :)
Nice laptop you got though.

---

### Post by luciano4 on 2014-08-25
It didn't work :(
In the regular boot continues in the same way.


And now, in Recovery mode, I can access to this menu: [Screen here]("http://i.stack.imgur.com/R5oV8.png"), but when I enter in failsafeX option, throws me the window *"The system is running in low-graphics mode"*. 
If I press ctrl+alt+F2/F3/F4/F5/F6, the screen remains in black. 
If I press ctrl+alt+F1: [Screen here]("http://s30.postimg.org/ggrje1amp/image.jpg")
If I press ctrl+alt+F7: [Screen here]("http://s28.postimg.org/3lboyigdp/image.jpg")

---

### Post by buzzingrobot on 2014-08-25
Try "sudo nvidia-xconfig", then reboot. If it says it found an existing 'xorg.conf', tap 'Enter' to make a new one.

A longshot, but sometimes all the necessary files aren't created.

---

### Post by luciano4 on 2014-08-25
> **buzzingrobot said:**
> Try "sudo nvidia-xconfig", then reboot. If it says it found an existing 'xorg.conf', tap 'Enter' to make a new one.

A longshot, but sometimes all the necessary files aren't created.

I try it but didn't works

---

### Post by Stinger on 2014-08-25
Can you make a screenie of this command ? Tells a lot about your graphics:
```
lspci | grep VGA & sudo lshw -C video
```
Remember to type in your password when asked for.

And then let's try to remove the nvidia driver thats causing the trouble.
Follow this guide to do it and follow it to the letter please.
[Problem: Need to fully remove -nvidia and reinstall -nouveau from scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch")

---

### Post by luciano4 on 2014-08-25
> **Stinger said:**
> Can you make a screenie of this command ? Tells a lot about your graphics:
```
lspci | grep VGA & sudo lshw -C video
```
Remember to type in your password when asked for.


[Screen here]("http://postimg.org/image/sanpq7jrv/")

> **Stinger said:**
> And then let's try to remove the nvidia driver thats causing the trouble.
Follow this guide to do it and follow it to the letter please.
[Problem: Need to fully remove -nvidia and reinstall -nouveau from scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch")

When I do this:
```
  
  sudo nvidia-settings --uninstall  [COLOR=#ff0000]**COMMAND NOT FOUND**[/COLOR]
  sudo apt-get remove --purge nvidia*[COLOR=#00ff00]**OK**[/COLOR]
  sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-nv [COLOR=#00ff00]**OK**[/COLOR]
  sudo apt-get install nvidia-common [COLOR=#00ff00]**OK**[/COLOR]
  sudo apt-get install xserver-xorg-video-nouveau [COLOR=#00ff00]**OK**[/COLOR] 
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core [COLOR=#00ff00]**OK**[/COLOR]
  sudo dpkg-reconfigure xserver-xorg [COLOR=#00ff00]**OK**[/COLOR]

```

However, now I can see de screen of Login, but when I put mi password, it redirect me for 1 second to a black screen with an error and it come back to the screen of Login.
In the last line of this black screen say [I]"starting ntp server ntpd"

[Video here]("http://es.tinypic.com/r/70w6sl/8")[/I]

---

### Post by Stinger on 2014-08-26
Ok, your graphics are working now else you wouldn't get the login screen, It seems to be using the on board intel chip of your [hybrid graphics]("https://wiki.ubuntu.com/X/Config/HybridGraphics"), but there is something wrong with you user profile since it throws you of every time.
Maybe some leftovers from the nvidia driver in ~/.nvidia-settings-rc ,  ~/.xinitrc . It's described [here]("http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-current-settings.1.html#contenttoc4") scroll down to where it says  **_3. Loading Settings Automatically_**.
I think your best option would be to make a fresh install, to clear out all the garbage, and then upgrade kernel and x-server to the Trusty LTS version before any attempt to install the nvidia driver is made.

---

### Post by Stinger on 2014-08-26
Just thought of another way that might work, that's if you haven't made a fresh install already ;)
I'll post later when I'm on my own pc.

---

### Post by luciano4 on 2014-08-26
> **Stinger said:**
> Just thought of another way that might work, that's if you haven't made a fresh install already ;)
I'll post later when I'm on my own pc.

Ok, I'll wait to try that way (:

---

### Post by Stinger on 2014-08-26
When you are at the login screen, try hitting ctrl+alt+F1 this should get you to the command line login promt, now type your user id hit enter, then you are asked for your password, now type your password ( it won't show ) and hit enter. you shold now be logged in.
Are you able to do that ?
Ps. ctrl+alt+F7 gets you back in graphical mode again.

---

### Post by luciano4 on 2014-08-26
It didn't works:/

When I come back to the login screen, I'm still loged out

---

### Post by Stinger on 2014-08-26
Yeah I know that, but are you able to login using the command line ? when you login it should say something like 'welcome to elementary OS' to confirm that you are logged in. don't go back to graphical mode yet, stay on the command line ;)

---

### Post by luciano4 on 2014-08-26
Yes yes, sorry . I can use[COLOR=#000000] the command line[/COLOR]

---

### Post by Stinger on 2014-08-26
Ok fine, you user profile seems to be ok. It must be some sort of mix up where the graphics don't know which chip to load (Intel or Nvidia) or the nuveaou driver that doesn't recognize your nvidia chip.
I'll try to guide you through installing the  nvidia-331 driver and nvidia-prime so that you can switch between Intel and Nvidia depending on your 3D needs.
Before we do that please try this command when you are logged in using the command line:
```
lspci | grep VGA & sudo lshw -C video
```
And post the output if you can.

---

### Post by luciano4 on 2014-08-26
[Screen here]("http://postimg.org/image/wrmxfh6f9/")

---

### Post by Stinger on 2014-08-26
The nvidia chip has 'physical id: 0' seems to be the preferred one.
Lets try to install the driver. Login again using the command line, do this to remove any bumblebee remains.
```
sudo apt-get purge bumblebee-nvidia
``` 
and then try to install the nvidia packages:
```
sudo apt-get install nvidia-331 nvidia-settings nvidia-prime
```
Then:
```
sudo reboot 
```
to restart
Hope it works !

---

### Post by luciano4 on 2014-08-26
[Screen here]("http://s2.postimg.org/yba8437x5/low_graphics.jpg") this window again =(

---

### Post by Stinger on 2014-08-26
You seem to be stuck between a rock and a hard place.
We have tried with the open source nuveaou driver = No go
The new nvidia 331 and nvidia prime = still No go
I think it must be the old code base from Ubuntu 12.04 that's causing the trouble.

I would recommend you to try [elementary OS Freya]("http://elementaryos.org/journal/freya-beta-1-available-for-developers-testers") instead but I can't do it officially because it's in beta.
But if you are willing to be a beta tester like me it's completely up to you. It has a [UEFI bug]("https://bugs.launchpad.net/elementaryos/+bug/1355698") though so it might not work either.
The best option, until Freya is released, might be Ubuntu 14.04 for you

---

### Post by Stinger on 2014-08-26
And now...
Coffee break ;)

---

### Post by luciano4 on 2014-08-26
I just installed Elementary OS Luna again and works OK. But now in the grub menu, I can't access to my Windows 8 :/ 
I installed Elementary like the last time..[URL="http://s23.postimg.org/jb83o6c0r/20140826_171720.jpg"]

Screen here[/URL]

Helpp

and thanks for everything!

---

### Post by Stinger on 2014-08-26
You are welcome.
Regarding your windows access trouble, I'm really no expert, I could be that you disabled secure boot somewhere along the line, I think windows 8 depends on it ?
But I would advice you to open a new thread on the subject and let someone with a UEFI pc and more expertise guide you.
More info on UEFI and Ubuntu can be found [here]("https://help.ubuntu.com/community/UEFI")

---

