---
title: "Does &quot;additional driver' ever work?"
date: 2013-10-21
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2013-10-21
They have replaced the old "additional driver" aka jockey with the new "additional driver" hidden in softeware-properties-gtk (usually accessed through synaptic or the usc) since 12.10 (?) Aside from the fact that it is hard to discover for the uninitiated, does it even work?? I tried several times but it never worked. I click "apply" and the thing just went on forever without really doing anything. I got impatient and simply closed it and installed the drivers directly from synaptic.

What is your experience? Does it ever work for you? BTW jockey always worked and it would popup to alert you, I don't know why they replace this great piece of software with something so crappy (even if it works it is still crappy because it is hidden, and I am not even sure that it works, hence the thread)

---

### Post by stalkingwolf on 2013-10-21
it has worked almost every time i used it.  have had a couple times i had to manually install the broadcom driver.

---

### Post by pqwoerituytrueiwoq on 2013-10-21
never had a issue with it here

---

### Post by qamelian on 2013-10-21
Works fine here for installing proprietary AMD/ATI drivers.

---

### Post by shantiq on 2013-10-21
> **monkeybrain20122 said:**
> They have replaced the old "additional driver" aka jockey with the new "additional driver" hidden in softeware-properties-gtk (usually accessed through synaptic or the usc) since 12.10 (?) Aside from the fact that it is hard to discover for the uninitiated, does it even work?? I tried several times but it never worked. I click "apply" and the thing just went on forever without really doing anything. I got impatient and simply closed it and installed the drivers directly from synaptic.

What is your experience? Does it ever work for you? BTW jockey always worked and it would popup to alert you, I don't know why they replace this great piece of software with something so crappy (even if it works it is still crappy because it is hidden, and I am not even sure that it works, hence the thread)


well monkeybrain   it does work but takes a long time and the problem is there are no messages so one does not know   that the download and install is happening
as you said synaptic at least "talks you through"

surely it is easy to add a monitor so people know what is happening ... since Ubuntu is clearly aiming at a larger audience steps need to be clearly explained always

also the nouveau default is probably not a good idea at a time when most users probably require vdpau


[B]for the ones new to this

[/B]look for Software & Updates  then pick Additional Drivers  and if you want to see HD content pick NVidia 319   described as the recommended choice   and then WAIT!   it will tell you when finished

then RELOAD  and now you have HD  ...     well on SMplayer and XBMC to 1080 and sadly only 720 on VLC and Videos/mplayer   still

[ATTACH=CONFIG]247116[/ATTACH]

---

### Post by grahammechanical on 2013-10-21
Do you mean that it fails to install the driver? Or do you mean that the newly installed proprietary driver breaks the desktop top. Ever since an update to a Nvidia driver broke my 12.04 desktop I no longer trust proprietary video drivers as I once did. I put in test installs of Ubuntu and I now never tick to install third party software because that brings in the proprietary video driver which often breaks the reboot. That does not happen with Nouveau.

Regards.

---

### Post by Beren Camlost on 2013-10-21
The most reliable way I've found for installing proprietary Nvidia drivers, is using the official installer from the Nvidia website. Granted, it comes with its own set of issues but at least I get a fully working driver with best possible hardware accelerated 3d graphics performance there is.

---

### Post by monkeybrain20122 on 2013-10-21
> **grahammechanical said:**
> Do you mean that it fails to install the driver? Or do you mean that the newly installed proprietary driver breaks the desktop top. Ever since an update to a Nvidia driver broke my 12.04 desktop I no longer trust proprietary video drivers as I once did. I put in test installs of Ubuntu and I now never tick to install third party software because that brings in the proprietary video driver which often breaks the reboot. That does not happen with Nouveau.

Regards.

It doesn't seem to be doing anything so I just close it and install with synaptic.Maybe it was actually working if I have waited it through since others say it takes a long time. I have never had an issue with Nvidia drivers but then I always get the latest from xorg-edgers.I tried the "additional driver" route several times only out of curiosity (I tried to install bcm-kernel-module on some machine the other day again I sat and waited forever nothing seemed to be happening so I close it and install it with synaptic)

---

### Post by monkeybrain20122 on 2013-10-21
> **shantiq said:**
> 
also the nouveau default is probably not a good idea at a time when most users probably require vdpau



I must say nouveau is actually getting very good. Other than vdpau (I don't play very gpu demanding games) I find it smoother than nvidia's blob for 'normal' desktop use. Graphic is really smooth and fluid in 13.10. I have an external drive which I install some versions of Linux on (Debian and Ubuntu at the moment) which I boot off different machines as a portable I can't install proprietary graphic card on that one (or it won't work with machines with a different card) so I am always interested in the state of the open drivers. Read that some vdpau support will be coming to nouveau (already in the alpha channel)

---

### Post by shantiq on 2013-10-22
good news on vdpau support MKB  ;   i love 720/1080 videos and i guess many others too ...

---

### Post by buzzingrobot on 2013-10-22
It often seems slow because it has a lot to do besides downloading a driver and moving it into place.  It doesn't display the progress of each intermediate step, only a general progress bar. I've seen that appear to stall for several minutes before sprinting to completion. 

Plus, the servers it pulls from may be slow at the time.

I've noticed a potential problem with all Nvidia driver installs, not just via Additional Drivers and not just on Ubuntu:  Sometimes the needed xorg.conf file is not created. This will lead to a black or broken screen on reboot.  So, now, as a matter of course, after the install completes, I open a terminal and run "sudo nvidia-xconfig", which is the little program that creates the correct xorg.conf. If the file was, in fact, successfully created, a duplicate will be made and the original backed up.

---

### Post by su:bhatta on 2013-10-24
Has worked everytime for my AMD driver ! Never had a problem.

Considering the kind of effort I had to put in installing Catalyst in Fedora 19, I am happy to click on the radio button and wait for 20 minutes for it to complete all the settings and I reboot into a great system.

 But Fedora experience made me understand all the steps it has to perform in order to complete the task, considering that the 20 minutes it takes is quite normal I should think.

---

### Post by monkeybrain20122 on 2013-10-24
> **bhattabhishek said:**
> Has worked everytime for my AMD driver ! Never had a problem.

Considering the kind of effort I had to put in installing Catalyst in Fedora 19, I am happy to click on the radio button and wait for 20 minutes for it to complete all the settings and I reboot into a great system.

 But Fedora experience made me understand all the steps it has to perform in order to complete the task, considering that the 20 minutes it takes is quite normal I should think.
20 minutes? That is crazy. If you install the driver from synaptic it would take may be a minute. With things like bcml-kernel-source it may take a bit longer but still much faster than waiting for "additional driver". I thought that it wasn't working because I abort after waiting for about 5 minutes or so,

Re. Fedora, I have not installed Catalyst on Fedora, but to install Nvidia driver is pretty straight forward, activate the rpmfusion rawhide repo, install the driver and the akmod package and reboot that' it (need to remove noveau first) It took a few minutes.

---

### Post by su:bhatta on 2013-10-24
> **monkeybrain20122 said:**
> 20 minutes? That is crazy. 

Ah ! but you don't know my net download speed, do you !

---

### Post by lz1dsb on 2013-10-24
To me the Additional Drivers has always worked... the issues I have are with the drivers, but otherwise... it has always worked.

---

### Post by monkeybrain20122 on 2013-10-24
> **bhattabhishek said:**
> Ah ! but you don't know my net download speed, do you !

That is true, but I wonder how long it would take if you use the terminal or synaptic. It would be interesting to find out.

---

### Post by su:bhatta on 2013-10-24
> **monkeybrain20122 said:**
> That is true, but I wonder how long it would take if you use the terminal or synaptic. It would be interesting to find out.

That's an idea for the next time.

---

### Post by deadflowr on 2013-10-24
The speed would be relatively same, whether using the terminal, synaptic or jockey.
The differences would be you can see point for point progress in a terminal or even synaptic, where as jockey does it's thing without telling you what's going on.

---

### Post by su:bhatta on 2013-10-24
> **deadflowr said:**
> The speed would be relatively same, whether using the terminal, synaptic or jockey.
The differences would be you can see point for point progress in a terminal or even synaptic, where as jockey does it's thing without telling you what's going on.

Ah, good to know, then I will stick to using the radio button ;)

---

### Post by monkeybrain20122 on 2013-10-24
> **deadflowr said:**
> The speed would be relatively same, whether using the terminal, synaptic or jockey.
The differences would be you can see point for point progress in a terminal or even synaptic, where as jockey does it's thing without telling you what's going on.

That has not been my experience. To install any Nvidia driver from synaptic took less than a minute, with the "additional button" takes more than 4 to 5 minutes (I don't know how much longer as I assumed that it didn't work and aborted at that point) It has nothing to do with whether I can see the progress or not.

---

