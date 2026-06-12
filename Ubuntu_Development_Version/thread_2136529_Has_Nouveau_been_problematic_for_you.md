---
title: "Has Nouveau been problematic for you?"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by Roasted on 2013-04-17
I'm running an i3 desktop with an Nvidia GT440, using 1920x1080 and 1440x900 monitors. I booted up 13.04 64 bit and within 30 minutes I had three Unity crashes. On one occasion, everything was upside down and locked up. I was just using it and BAM - Chromium, Empathy, and Clementine - upside down. Then they locked up a few seconds later. Two hard reboots later (the first reboot brought me into single monitor mode with a seemingly horrible 640x480 esque resolution), I was back on. At this point I decided to install Nvidia drivers. I didn't want to install Nvidia drivers mostly because I wanted to give Nouveau a fair chance seeing as though some reviews indicated that Nouveau is pretty darn close to Nvidia these days in terms of performance. I installed Nvidia 313 + updates and things load much faster and operate more smoothly. I also noticed that the applications lens when scrolling through all applications is smoother as well.

With all of that being said, has anybody ran into any issues like this where your graphics with 13.04 and Nouveau just acts rather wild? I have a ton of faith in Nouveau and I'm sure bug fixes will come about. I just wanted to check in with other users to see what their current experiences were.

---

### Post by Frogs Hair on 2013-04-17
Nouveau works as much as I have used it , but the splash screen looks like a black purple flash so I use Nividia instead. 3.13 has been the best on my hardware and Ive tested them all.

---

### Post by stinkeye on 2013-04-17
Nouveau works great here.
I have tried nvidia-current and noticed little difference and switched back to nouveau.

```
glen@Raring:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 351a
	Kernel driver in use: nouveau
```

---

### Post by Roasted on 2013-04-18
> **stinkeye said:**
> Nouveau works great here.
I have tried nvidia-current and noticed little difference and switched back to nouveau.

```
glen@Raring:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 351a
	Kernel driver in use: nouveau
```

What for monitors are you using? I wonder if the screen size I'm dealing with is having a factor. I noticed that Unity effects, such as the dash, scrolling in the application lens, etc., is a bit quicker on the 19" than the main 24"...

---

### Post by stinkeye on 2013-04-18
> **Roasted said:**
> What for monitors are you using? I wonder if the screen size I'm dealing with is having a factor. I noticed that Unity effects, such as the dash, scrolling in the application lens, etc., is a bit quicker on the 19" than the main 24"...

Samsung 22" 1680x1050 native res

In ccsm > unity try disabling Dash blur to see if that makes a difference.

---

### Post by Rukiri on 2013-04-18
If you use gimp you'll notice that the brush will lag painting rapidly on a canvas(will start to lag once you increase the brush size) no issues with the nvidia drivers.

---

### Post by sgage on 2013-04-18
Nouveau performs adequately for my needs, and seems stable enough. However, it does not allow my computer to resume properly from suspend, so I use nvidia-313.

---

### Post by grahammechanical on 2013-04-18
Just look at this thread and see just what is the greatest problems, Nouveau or Nvidia?

[http://ubuntuforums.org/showthread.php?t=2133507](http://ubuntuforums.org/showthread.php?t=2133507)

I have been using Raring since November. I have only been able to use an Nvidia driver for about 4 weeks. At present I have had to replace Nvidia with Nouveau. I would not recommend anyone installing Ubuntu and bringing in the third party software as that will install a proprietary video driver and that often results in a broken desktop on first reboot. Just look around the posts all over this forum. People install 12.04 or 12.10 and the first reboot = broken system But things worked fine in the live session. And just what is the video driver in the live session? - Nouveau.

So, from my experience I would say the Nvidia drivers and Nouveau drivers have changed places with Nvidia not being as trustworthy as it once was and Nouveau making tremendous improvement.

I would like to add, if you are using Nvidia and get a kernel update, then expect a broken desktop. 

Regards.

---

### Post by ventrical on 2013-04-18
Here , on my two machines with Nvidia it's the other way around. Nouveau with it's limitations and nVidia with full effects.

---

### Post by Roasted on 2013-04-18
> **grahammechanical said:**
> Just look at this thread and see just what is the greatest problems, Nouveau or Nvidia?

[http://ubuntuforums.org/showthread.php?t=2133507](http://ubuntuforums.org/showthread.php?t=2133507)

I have been using Raring since November. I have only been able to use an Nvidia driver for about 4 weeks. At present I have had to replace Nvidia with Nouveau. I would not recommend anyone installing Ubuntu and bringing in the third party software as that will install a proprietary video driver and that often results in a broken desktop on first reboot. Just look around the posts all over this forum. People install 12.04 or 12.10 and the first reboot = broken system But things worked fine in the live session. And just what is the video driver in the live session? - Nouveau.

So, from my experience I would say the Nvidia drivers and Nouveau drivers have changed places with Nvidia not being as trustworthy as it once was and Nouveau making tremendous improvement.

I would like to add, if you are using Nvidia and get a kernel update, then expect a broken desktop. 

Regards.

I have heard of kernel updates breaking AMD, but never Nvidia, and I've used Ubuntu/Nvidia exclusively since about 2006. Likewise, I haven't personally had an issue with Nvidia. It's always been the safest bet for me, and one I'll blindly go with again due to my success with it, despite the fact it's seemingly opposite of what you mentioned you ran into. 

I'm just glad that I can run Unity without it being painfully slow. I couldn't say that with Nouveau (and it pains me to say that since I'm rooting for Nouveau all the way).

EDIT - Another fun fact about Unity being slow, it's significantly faster on my laptop now that I disabled blur via Unity Tweak Tool. Fortunately since I use a custom background color @ 75% transparency it didn't make a visible difference anyway besides speeding things up. :D

---

### Post by ventrical on 2013-04-18
I just reloaded the nouveau driver and it turned my system to  molases - 'painfully slow'.  nVidia back in and  it flys.

---

### Post by P-I H on 2013-04-18
Nouveau has never worked with my Geforce GTS250. Always have to reboot with Recovery, Resume Normal Boot, to start in low graphics [COLOR=#000000]and then change to an Nvidia closed driver.[/COLOR]

---

### Post by Lfekey2 on 2013-04-18
Suspend doesn't work with GT230M. I heard it's fixed in 3.9 kernel.

---

### Post by ventrical on 2013-04-18
Suspend works with GeForce 210/218 but network will not come up.

---

### Post by Roasted on 2013-04-18
Well it helps to know that I'm not alone. When I read the recent reports about Nouveau stacking up with Nvidia in certain areas of performance I expected it to run wicked fast. I will say though... I AM super curious as to how my desktop would run on Nouveau in the event that I had the Unity dash blur turned off. I only just discovered that in the Unty Tweak Tool an hour ago on my laptop and haven't tried my desktop yet. Then again, my desktop had the entire UI locking up and crashing at random times. I'm sure the blur being off helps with speed, but I doubt it would help wth that sort of behavior. :P

---

### Post by Elfy on 2013-04-18
No problems with nouveau nor nvidia in Ubuntu.

Nvidia creates merry havoc with themes in Xubuntu, using nouveau.

GeForce 210

---

### Post by Roasted on 2013-04-19
> **Elfy said:**
> No problems with nouveau nor nvidia in Ubuntu.

**Nvidia creates merry havoc with themes in Xubuntu, using nouveau.**

GeForce 210

Pardon my ignorance, but are you indicating that you currently use Nouveau, or that Nouveau (not Nvidia) was the one creating merry havoc? I read that a few times and still wasn't sure I caught your angle. :)

---

### Post by Elfy on 2013-04-19
Xubuntu is happy with nouveau :)

---

### Post by linux4me on 2013-05-16
This thread poses exactly the question I wanted to ask. I'm running a clean install of 13.04 with an Nvidia GT440 on an LG 1280 x 1024 monitor.

I really wanted to give nouveau a good try, and I've been using it for about a week. However, it causes corruption of the graphics including loss of icons, menus appearing for the wrong program or not appearing in the correct location in the right program, upside-down remnants of programs I've closed (including Evince, Firefox, and Meld), and consistent hanging on restart and occasional hanging on shutdown that require a hard reset or hard shutdown.

I tried the nvidia 304 driver, which worked for me in 12.10, and thought I had bricked my system. It took several hard reboots before I could even enter recovery mode. I got in a loop of the error “udev [406]: timeout: killing /sbin/smartprobe -bv pci... [429]." The recovery menu would eventually appear, but that error message would over-write it so that I couldn't make a selection. Reboots hung right after the line “Syncronizing SCSI cache.” I was about to give up, but the last reboot got me to the recovery menu and I was able to remove the 304 driver.

I tried the nvidia 310 driver, and it gave me 640 x 480 graphics in grub if it booted at all, but would usually give me the black screen routine and wouldn't switch to a tty despite repeated attempts, requiring a hard reboot. Fortunately, I was able to get into recovery mode and remove it without the errors I had with 304.

Finally, I tried the nvidia 313-updates driver. It gave me 640 x 480 graphics in grub, but it works fine otherwise so far, and I can restart and shut down the machine, at least in my testing thus far. I added the GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX lines in /etc/default/grub to set the correct resolution for grub during boot. I am hoping for the best.

---

### Post by cariboo on 2013-05-16
> **linux4me said:**
> This thread poses exactly the question I wanted to ask. I'm running a clean install of 13.04 with an Nvidia GT440 on an LG 1280 x 1024 monitor.

I really wanted to give nouveau a good try, and I've been using it for about a week. However, it causes corruption of the graphics including loss of icons, menus appearing for the wrong program or not appearing in the correct location in the right program, upside-down remnants of programs I've closed (including Evince, Firefox, and Meld), and consistent hanging on restart and occasional hanging on shutdown that require a hard reset or hard shutdown.

I tried the nvidia 304 driver, which worked for me in 12.10, and thought I had bricked my system. It took several hard reboots before I could even enter recovery mode. I got in a loop of the error “udev [406]: timeout: killing /sbin/smartprobe -bv pci... [429]." The recovery menu would eventually appear, but that error message would over-write it so that I couldn't make a selection. Reboots hung right after the line “Syncronizing SCSI cache.” I was about to give up, but the last reboot got me to the recovery menu and I was able to remove the 304 driver.

I tried the nvidia 310 driver, and it gave me 640 x 480 graphics in grub if it booted at all, but would usually give me the black screen routine and wouldn't switch to a tty despite repeated attempts, requiring a hard reboot. Fortunately, I was able to get into recovery mode and remove it without the errors I had with 304.

Finally, I tried the nvidia 313-updates driver. It gave me 640 x 480 graphics in grub, but it works fine otherwise so far, and I can restart and shut down the machine, at least in my testing thus far. I added the GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX lines in /etc/default/grub to set the correct resolution for grub during boot. I am hoping for the best.

You'll have to upgrade to Saucy, if you want any answers to your questions here. Seeing as Raring has been released, it would be better if you asked your question in [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334"), or [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331").

---

### Post by ventrical on 2013-05-16
> **linux4me said:**
> This thread poses exactly the question I wanted to ask. I'm running a clean install of 13.04 with an Nvidia GT440 on an LG 1280 x 1024 monitor.

I really wanted to give nouveau a good try, and I've been using it for about a week. However, it causes corruption of the graphics including loss of icons, menus appearing for the wrong program or not appearing in the correct location in the right program, upside-down remnants of programs I've closed (including Evince, Firefox, and Meld), and consistent hanging on restart and occasional hanging on shutdown that require a hard reset or hard shutdown.

I tried the nvidia 304 driver, which worked for me in 12.10, and thought I had bricked my system. It took several hard reboots before I could even enter recovery mode. I got in a loop of the error “udev [406]: timeout: killing /sbin/smartprobe -bv pci... [429]." The recovery menu would eventually appear, but that error message would over-write it so that I couldn't make a selection. Reboots hung right after the line “Syncronizing SCSI cache.” I was about to give up, but the last reboot got me to the recovery menu and I was able to remove the 304 driver.

I tried the nvidia 310 driver, and it gave me 640 x 480 graphics in grub if it booted at all, but would usually give me the black screen routine and wouldn't switch to a tty despite repeated attempts, requiring a hard reboot. Fortunately, I was able to get into recovery mode and remove it without the errors I had with 304.

Finally, I tried the nvidia 313-updates driver. It gave me 640 x 480 graphics in grub, but it works fine otherwise so far, and I can restart and shut down the machine, at least in my testing thus far. I added the GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX lines in /etc/default/grub to set the correct resolution for grub during boot. I am hoping for the best.


  I had been experimenting with Mir and 13.04. Did a fresh install (13.04)the other day. Every time (after update) it rolls over to llvmpipe and completely destroys the performance. Then, after installing nvidia 310 (updates) it works great for a while and then just crashes out. I was testing Facebook, clicked ,<add-friend> and then .. boom !! blackspace - no desktop , nada.. no terminal .. recovery gives me nada.

Some big problems I think with jockey.

Nvidia geForce 210/218

---

