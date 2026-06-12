---
title: "A question to those who were able to update flawlessly"
date: 2007-04-20
forum: The Cafe
---

### Post by PartisanEntity on 2007-04-20
If you were able to update flawlessly what system are you running? The most important questions for me would be:

1. Are you using any proprietary drivers ? (for example for wifi card or graphics card?)
2. Do you have multiple monitors set up? (TwinView, Xinerama etc...)
3. Do you have Beryl installed?

I have never upgraded before and am just wondering how this works. Does the upgrade process rewrite my xorg.conf file and thereby wipe the code needed to run two monitors for example?

Does anything need to be recompiled after the upgrade process or is this done automatically?

My current set up:

An Asus laptop running Edgy. Nvidia GeForce Go 6200. A TFT monitor attached to my laptop each using a seperate X display. BCM4306 wifi card using ndiswrapper. 

Anyone know from experience if any of the above will mess with the upgrade?

Thanks for the input.

---

### Post by beniwtv on 2007-04-20
> **PartisanEntity said:**
> If you were able to update flawlessly what system are you running?

Running Feisty here (the only OS on the lappy), and loving every minute.

> **PartisanEntity said:**
> 
1. Are you using any proprietary drivers ? (for example for wifi card or graphics card?)

Yes, using the Nvidia drivers (nvidia-glx from Restricted manager), as my GeforeGo 6150 won't work properly with any other driver. 

> **PartisanEntity said:**
> 
2. Do you have multiple monitors set up? (TwinView, Xinerama etc...)

Yes, the new Nvidia tool allows me easily change these settings from the GUI. I'm using the TFT of the lappy and a 19" TFT with the external VGA connector.

> **PartisanEntity said:**
> 
3. Do you have Beryl installed?

No, but Compiz comes by default. But it's not enabled. It gives me randomly black windows, even after enabling the required options in Xorg and Compiz.

> **PartisanEntity said:**
> 
I have never upgraded before and am just wondering how this works. Does the upgrade process rewrite my xorg.conf file and thereby wipe the code needed to run two monitors for example?

It depens. Normally, it should ask you to replace or keep old configuration files you modified. The default is to not overwrite them, I think.

> **PartisanEntity said:**
> 
Does anything need to be recompiled after the upgrade process or is this done automatically?


If you have everything installed via apt, it shouldn't be necessary. If you installed any drivers manually, you will have to recompile them, because the kernel version has changed.

> **PartisanEntity said:**
> 
An Asus laptop running Edgy. Nvidia GeForce Go 6200. A TFT monitor attached to my laptop each using a seperate X display. BCM4306 wifi card using ndiswrapper. 

Anyone know from experience if any of the above will mess with the upgrade?

I'm not talking from experience here, but if you installed the Nvidia drivers from Synaptic (nvidia-glx) and ndiswrapper from Synaptic as well, you should be good to go.

I recommend though that you at least try your wifi card without Ndidwrapper, it could be working! On my friend's Asus laptop, the broadcom card works fine with the native driver just after installing the firmware.

---

### Post by PartisanEntity on 2007-04-20
I used Envy to install the Nvidia drivers. Also, I booted from the Feisty live CD to test it and as it was starting up there was an error message about broadcom firmware. Upon loading the desktop it could not find any wifi networks so I assuming the card won't work without some 'help' on my part.

However one thing I noticed is that when I tried to install ndiswrapper off of the Edgy live CD it complained about not being able to access the internet, so it seems Feisty is not very friendly when it comes to wifi.

---

### Post by prizrak on 2007-04-20
> No, but Compiz comes by default. But it's not enabled. It gives me randomly black windows, even after enabling the required options in Xorg and Compiz.


That's an nVidia driver issue not a Compiz/Beryl/X.org issue.
> I used Envy to install the Nvidia drivers. Also, I booted from the Feisty live CD to test it and as it was starting up there was an error message about broadcom firmware. Upon loadind the desktop it could not find any wifi networks so I assuming the card won't work without some 'help' on my part.
If Envy installs them from official repos it will be no problem. If not you might have an issue. They are compiled against a certain kernel by the devs and you need them to be compatible. Broadcomm will most likely not work out of the box. Some cards should becaue of the new driver but you might be on the unlucky list. 

You could try the upgrade I think it will be OK (just backup your stuff). Safer bet would be doing a fresh install though. Also get that ndiswrapper ready :)

---

### Post by PartisanEntity on 2007-04-20
Envy downloaded the drivers from the Nvidia website. So I guess those will definately need to be recompiled after the upgrade or install, now I have to find out if there is a version of Envy for Feisty.

Yeah I better get myself ndiswrapper since I am going to need it :)

---

### Post by forrestcupp on 2007-04-20
You don't need Envy in Feisty to install the nvidia drivers.  All you have to do is go to System->Administration->Restricted Drivers Manager and pretty much just check the box for nvidia proprietary drivers.  It does everything for you.  It's better this way because when your system updates, everything updates together.

---

### Post by PartisanEntity on 2007-04-20
> **forrestcupp said:**
> You don't need Envy in Feisty to install the nvidia drivers.  All you have to do is go to System->Administration->Restricted Drivers Manager and pretty much just check the box for nvidia proprietary drivers.  It does everything for you.  It's better this way because when your system updates, everything updates together.

Ah okay, yes I forgot about that! Thanks for the info.

So that leaves me with wifi issues only to worry about.

---

### Post by forrestcupp on 2007-04-20
It's very possible it might pick up your wifi, too.  The Restricted Drivers Manager works wonders.

---

### Post by PartisanEntity on 2007-04-20
As I said earlier in the thread, I tried the Feisty live CD and it mentioned some broadcom firmware error while it was loading, upon loading the desktop, it could not find any wifi networks. I did try loading the Restricted Drivers Manager but all it offered me where drivers for my graphics card which needed to be downloaded (but since wifi wasn't working that of course did not work :) ).

---

### Post by Zeroangel on 2007-04-20
I'm using the official NVIDIA drivers and beryl, and managed to update without any problems whatsoever.

In fact, I'm quite suprised that the update went so smoothly since the update installed a new kernel and the NVIDIA drivers typically do not mesh well with other kernels except for  the ones that they are installed on.

Another thing I noticed -- beryl uses MUCH less CPU, to the point where I can even play 3D games without beryl getting in the way too much (FPS wise)

My system config is:
Kubuntu Feisty
AMD Athlon 2800+ (using the latest generic kernel)
GeForce4 MX4000
512MB PC2700 RAM (With 512MB swap)
No Wireless

---

### Post by PartisanEntity on 2007-04-21
It worked! :)

The update worked it seems, I did have to blacklist the bcm43xx driver which came with Feisty though.

Very nice.

---

