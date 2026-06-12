---
title: "Troubles with fglrx"
date: 2012-10-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Sworddragon on 2012-10-10
Today I switched from a GeForce 8600 GT (nvidia-current 304.51.really.304.43-0ubuntu1) to an AMD Radeon HD 7750 (fglrx 2:9.000-0ubuntu3). After a reboot I noticed some graphic errors if I'm opening and maximizing a terminal. For example a part of the terminal is drawn into the panel and games have graphical issues too.

fglrxinfo returns:

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series 
OpenGL version string: 4.2.11903 Compatibility Profile Context


```

I get on glxgears ~7940 FPS so all seems to working fine here. Has somebody an idea how to get fglrx to work on Quantal?

---

### Post by QIII on 2012-10-10
The way to get it to work with Quantal is to wait until Catalyst 12.10 appears in the repo and use the open source Radeon driver until then.  You could do some patching, but it's hardly worth it at this stage.

Even the 12.9 "Ubuntu 12.10 Preview Beta" Catalyst driver in the repo does not work fully.

For several years the xx.4 and xx.10 drivers have been made available to Canonical ahead of release to the rest of the Linux community.  I am sure it will happen again this time.  This usually occurs at about the time of the RC.

---

### Post by jfernyhough on 2012-10-10
> **Sworddragon said:**
> Has somebody an idea how to get fglrx to work on Quantal?You mean apart from it appearing to be working already? Most graphical glitches will be fixed by the time the 12.10 driver is released; fglrx 9.00 is based on the 12.9 beta. The "issues" the games are having are impossible to attribute to the driver, X, the game, or the libraries the game is using, unless you give a little more information.

---

### Post by Sworddragon on 2012-10-10
> **QIII said:**
> The way to get it to work with Quantal is to wait until Catalyst 12.10 appears in the repo

The problem is here in germany I have 14 days to send the graphic card back if I don't want to keep it.


> **QIII said:**
> and use the open source Radeon driver until then.

I have installed and activated them in the xorg.conf. The problem is after the X-Server switches to the console 7 it freezes the complete system. I had to boot with Knoppix and delete the xorg.conf to get my system working again.


> **QIII said:**
> You could do some patching, but it's hardly worth it at this stage.

If the patches will solve my problem it could be worth it.


I have downgraded the linux kernel, X-Server and fglrx to the Precise version but the problem still exists. I'm getting even in the right bottom corner of my screen an error message that my hardware is unsupported. aticonfig says the same.


> **jfernyhough said:**
> You mean apart from it appearing to be working already? Most graphical glitches will be fixed by the time the 12.10 driver is released; fglrx 9.00 is based on the 12.9 beta. The "issues" the games are having are impossible to attribute to the driver, X, the game, or the libraries the game is using, unless you give a little more information.

What information do you want to have? At least all is working fine if I'm switching back to my GeForce 8600 GT and nvidia-current. I'm getting graphical issues with lxpanel if lxterminal is maximized, winecfg doubles the half of the window in iteself and shows other graphical glitches (even with a virtual desktop enabled) and games with wine are starting but showing a blue background or other graphical issues. Only native linux games are starting and seems to be working fine.


Summary:

- NVIDIA is working fine on my system.
- 2D graphic mode does not work correctly with my desktop and winecfg.
- 3D games with Wine does not work but native 3D games seems to work.
- The open source driver will freeze my system.
- I'm limited on time to solve this problem.

---

### Post by sonnet on 2012-10-11
> **Sworddragon said:**
> Today I switched from a GeForce 8600 GT (nvidia-current 304.51.really.304.43-0ubuntu1) to an AMD Radeon HD 7750 (fglrx 2:9.000-0ubuntu3). After a reboot I noticed some graphic errors if I'm opening and maximizing a terminal. For example a part of the terminal is drawn into the panel and games have graphical issues too.

fglrxinfo returns:

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series 
OpenGL version string: 4.2.11903 Compatibility Profile Context


```

I get on glxgears ~7940 FPS so all seems to working fine here. Has somebody an idea how to get fglrx to work on Quantal?
I have a 7850 installed on Kubuntu 12:10 and didn't experience your problem.
In any case, there's no guarantee your problems would get solved, with the new drivers (assuming the problems are truly related to the drivers)

---

### Post by QIII on 2012-10-11
Sworddragon -- I see your plight.  However, you must consider the fact that you started out using a yet-to-be released OS that is still in development and will use a yet-to-be released driver that is still in development.  The fact that sonnett is OK is no guarantee that you will be.

Patching instructions can be found in the Quantal subforum.  Remember that even that is an "unnatural" state and might not even work any more at this point in development and with your modifications.

Have you considered using straight Precise for the time being rather than a sullied version of Quantal?

---

### Post by Sworddragon on 2012-10-12
> **QIII said:**
> Have you considered using straight Precise for the time being rather than a sullied version of Quantal?

I have only downgraded the related parts as I have said above. But the problem still exists.


I have contacted the AMD support and they have given me [this](http://wiki.cchtml.com/index.php/Main_Page) link to install the driver. I could successfully build the package and install it (it is fglrx 9.000 like the one in the Ubuntu repository). But starting the desktop environment has given me this error: (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension

I have searched about this message on Google and found hints that the driver doesn't maybe support the X-Server 1.13.0. I have written this to the AMD support and I got answer that drivers for Linux doesn't exist. Curiously both support answers had a lot of typos.

I'm out of ideas. It seems I have to send my graphic card back and look for one from NVIDIA which is the counterpart for the AMD Radeon HD 7750. At least in the 2 last years I'm using Linux I had never such big troubles with nvidia-current. But thanks for all which tried to help me :)

---

### Post by QIII on 2012-10-12
The point that your less-than-knowledgeable contact at AMD failed to note is that the 12.9 driver does not support X Server 1.13, which the 12.10 driver will.

Hence my suggestion to wait for the driver to be in the repo or use a straight up install of Precise.

Quantal is a development version and has not been released yet and the 12.10 driver has not been released yet.

Lest you leave believing that nobody has run in to issues with NVIDIA, search the forums.  Neither ATI nor NVIDIA is perfect, neither is either horrible.

---

### Post by Sworddragon on 2012-10-12
> **QIII said:**
> Hence my suggestion to wait for the driver to be in the repo or use a straight up install of Precise.

As already said Precise packages have the same problem for me. Maybe the bug is related to the AMD Radeon HD 7750 or another special component on my system.


> **QIII said:**
> Lest you leave believing that nobody has run in to issues with NVIDIA, search the forums.  Neither ATI nor NVIDIA is perfect, neither is either horrible.

I know the problems too with nvidia-current but I could ever found a solution in a short time.

---

### Post by novafluxx on 2012-10-14
Unity won't start for me when I use the AMD drivers from the repo's, I tried both that were listed in sources and after logging in, I get no unity, just a desktop background. I had to right click to change background to open up the settings in order to get to the software sources and change it back.

I hope it gets resolved soon because the systems seems so slow using llvmpipe. I really want to see Unity 3D in all its glory!

---

### Post by jfernyhough on 2012-10-15
> **novafluxx said:**
> Unity won't start for me when I use the AMD drivers from the repo's, I tried both that were listed in sources and after logging in, I get no unity, just a desktop background. I had to right click to change background to open up the settings in order to get to the software sources and change it back.This sounds more like an issue with the Unity settings; for example, Compiz under fglrx can go a bit weird with Blur enabled (mipmap or gaussian). 

You could try a:

$ dconf reset -f /org/compiz/

and see if that sorts it out.

---

### Post by Peter09 on 2012-10-15
I have exactly the same problem, no Unity. Compiz crashes with a no fglrx error. No way to get it up and running :(

Below is what I get doing a compiz --replace in a terminal.

> compiz --replace&
[2] 8418
peter@Pavilion:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: decor

etc
etc
etc


---

### Post by jfernyhough on 2012-10-15
Oh. Those errors would indicate that fglrx isn't loaded properly.

I'd guess that running glxinfo will show an error.

What cards do you two have?

---

### Post by novafluxx on 2012-10-15
> **jfernyhough said:**
> Oh. Those errors would indicate that fglrx isn't loaded properly.

I'd guess that running glxinfo will show an error.

What cards do you two have?

I have a Radeon HD 7850

---

### Post by novafluxx on 2012-10-15
> **jfernyhough said:**
> This sounds more like an issue with the Unity settings; for example, Compiz under fglrx can go a bit weird with Blur enabled (mipmap or gaussian). 

You could try a:

$ dconf reset -f /org/compiz/

and see if that sorts it out.

Pretend I'm an end user please. Explain what that command does so I can have a better understanding of all of this, please.

---

### Post by novafluxx on 2012-10-16
Peter09 and I seem to have the same issue.

---

### Post by Peter09 on 2012-10-16
Yes - I've had this issue since I upgraded about 3 weeks ago - graphics card is (I think -I'm at work at the moment) a Radeon 4500/5100.

Everything else seems to work - I can open a terminal (Cntrl-Alt-T) and run individual stuff, but no unity and compiz. Only other quirk for me is that I have a screen connected to the back of the laptop - not using the laptop screen, but I don't think that is the issue.

There seems to be a bug drifting about that talks about the Radeon driver not being ready for this release, but it seems to have a very low profile for the impact it will have if this version is released.

---

### Post by novafluxx on 2012-10-17
Well I hope things get sorted out soon. If we got a couple weeks post-release with no fix, I'll reinstall 12.04 or go with Mint Debian Edition.

---

