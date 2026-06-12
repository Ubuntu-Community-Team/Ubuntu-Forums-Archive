---
title: "Ubuntu and Graphics Cards"
date: 2007-03-10
forum: The Cafe
---

### Post by curtisf14 on 2007-03-10
This question has probably already been asked, but why does Ubuntu not have better native support for graphics cards?  For example, if you have an nVidia video card (any of the common ones), why is it that Ubuntu doesn't automatically install (or at least easily give you the option to install) and automatically configure your graphics driver, without having to look up some guide online that involves editing text files?  It seems like this would make Ubuntu more welcoming to newcomers.

---

### Post by Tomosaur on 2007-03-10
Short answer: Legal issues.

There are free drivers available (which are right inside the linux kernel, meaning you don't have to do anything extra) to get your video working at a decent level. For things like 3D acceleration, which are required for games or for the eye candy effects of Beryl etc - you will need the propietary drivers which you download from the manufacturers website. The Ubuntu developers are not allowed, legally, to distribute these drivers with the operating system. There was some debate a while back on whether to include them with the next release - I think the current stance is 'not by default - but with a post-install option' - that is - the drivers won't be installed as soon as the system is, but getting them set up will be very easy: ie, by just clicking a few buttons. This will hopefully alleviate the problems many people face.

However - it's important to remember that Linux hardware support is very, very good natively. Windows requires YOU to install drivers for virtually everything. With Linux, most hardware works to exactly as it should with no extra setup. Things like graphics cards present problems because the manufacturers release very, very little information about how their hardware works - which means developers have a very hard time creating open-source drivers which do everything the closed-source drivers do.

---

### Post by Crooksey on 2007-03-10
Unless there are open source drivers for your chipset i.e Intel drivers

---

### Post by curtisf14 on 2007-03-10
I understand that the Ubuntu community wants to include only open source software.  I completely agree with that stance.  I'm glad to hear that it will hopefully be easy to install the non-open source drivers in the next release.  What I'm hoping is that there be a welcome screen that says something to the effect "We have detected that you have an nVidia graphics card.  We have already installed an open source driver for this card on your computer.  However, if you want to have improved graphics, click --here-- and an installation program can download and automatically install these drivers for you."  It should be just one click.

If this were the case, non-open source drivers wouldn't have to be included on the CD, but the user could have the option to quickly and easily install the non-open source drivers.  This would still be in the spirit of Ubuntu, but users wouldn't have to go through the trouble of searching how-tos on how to download and install the drivers, which involve scary things like editing text files (well, scary for the average user).

---

### Post by SishGupta on 2007-03-10
> **curtisf14 said:**
> I understand that the Ubuntu community wants to include only open source software.  I completely agree with that stance.  I'm glad to hear that it will hopefully be easy to install the non-open source drivers in the next release.  What I'm hoping is that there be a welcome screen that says something to the effect "We have detected that you have an nVidia graphics card.  We have already installed an open source driver for this card on your computer.  However, if you want to have improved graphics, click --here-- and an installation program can download and automatically install these drivers for you."  It should be just one click.

If this were the case, non-open source drivers wouldn't have to be included on the CD, but the user could have the option to quickly and easily install the non-open source drivers.  This would still be in the spirit of Ubuntu, but users wouldn't have to go through the trouble of searching how-tos on how to download and install the drivers, which involve scary things like editing text files (well, scary for the average user).

It is seriously going to be that easy in the next Ubuntu release, if not the one after.
There is a new system  preferences applet in feisty called "Restricted Drivers Manager". This applet detects restricted drivers that you may need, like wifi drivers and 3d card drivers, and shows you if they are enabled and or in use. To install you just click the enable check box next to the driver and hit OK. The rest is done automagically.
The applet isn't done and it will still let you install things if they don't work. For example, it will list the ati fglrx driver for unsupported ati cards and install it, which results in X crashing when you restart X. Since the applet isn't done it isn't installed by default and may or may not be installed by default by the time feisty is released.

---

### Post by Toadmund on 2007-03-22
I want to use beryl, it just convulses and blinks and does nothing.
I am stuck on Mesa.
Please, I am searching, I found somewhere on this forum how to switch drivers through a GUI.

[COLOR="Red"]How do I make my ATI x200 the default video card?[/COLOR]
Everything else I believe is ready to go.

---

### Post by WalmartSniperLX on 2007-03-22
> **Toadmund said:**
> I want to use beryl, it just convulses and blinks and does nothing.
I am stuck on Mesa.
Please, I am searching, I found somewhere on this forum how to switch drivers through a GUI.

[COLOR="Red"]How do I make my ATI x200 the default video card?[/COLOR]
Everything else I believe is ready to go.

Well I am going to assume you installed the proprietary drivers right? To make your card the default card you can try

```

sudo aticonfig --initial
sudo aticontig --overlay-type=Xv

```

or run 

```

sudo dpkg-reconfigure xserver-xorg 

```

And select 'fglrx' as your driver and accept the defaults after that.


Make sure you have this at the bottom of your xorg.conf file too:

```

gksudo gedit /etc/X11/xorg.conf

```

Section "Extensions"
        Option      "Composite" "Disable"
EndSection


If that doesnt help, check the Multimedia and Video forum please. I believe I made many posts regarding ati cards and setting them up, even for beryl (AIGLX and XGL but with your card AIGLX may not be possible). Also you should find more than you need if you just search.

---

### Post by prizrak on 2007-03-22
Why would you have to look at a guide and edit any kind of files? In Feisty it's all GUI including setting up for compiz/beryl. In Edgy it's as simple as going to Synaptic and installing nvidia-glx package and then running 
```
nvidia-xconfig
``` 
to get it running. If you want Compiz/Beryl then you just type in.
```
nvidia-xconfig --add-AddARGBGLXVisuals
```
and you are good to go.

---

