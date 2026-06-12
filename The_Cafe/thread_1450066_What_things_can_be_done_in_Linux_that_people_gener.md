---
title: "What things can be done in Linux that people generally don't think they can be?"
date: 2010-04-08
forum: The Cafe
---

### Post by Macfunky on 2010-04-08
I would like to say not trivial stuff but I suppose that's as relevant so with the intentions of being broad, what things do people generally think that Linux can't do but actually can do (or even better)? Please be broad. I would like to hear technical stuff and user end stuff equally. Thanks :D

---

### Post by Psumi on 2010-04-08
startx - starts x-session from terminal (People think they need a *DM to do this. :|)

xcalc - Because people think they need gcalc. (xcalc comes with x11-utils)

Openbox Vs. DE - Because people think they need a DE to be pretty.

murrine gtk engine - Because people think GTK looks ugly without metacity prettying it up. (See also, Openbox Vs. DE)

no Panel - You don't need a panel to have good functionality. (Pair with notify-osd, conky and pcmanfm's desktop manager.)

recordmydesktop - Why do we need gtk-recordmydesktop? Oh right, because people like GUIs. Btw, without a panel, you need to killall gtk-recordmydesktop to stop it.)

---

### Post by eriktheblu on 2010-04-08
A lot of people I've talked to don't seem to think Linux can run a graphic interface (including our organizations IT guy, who hasn't tried the Karmic disk I gave him because it didn't have an activation code).

---

### Post by sisco311 on 2010-04-08
*Linux is used to create practically every blockbuster movie in theaters today, movies produced by Disney/Pixar, DreamWorks Animation, Sony, ILM, and other studios.*

[http://www.linuxmovies.org/](http://www.linuxmovies.org/)
[http://www.linux-netbook.com/10-blockbusters-made-with-the-help-of-linux](http://www.linux-netbook.com/10-blockbusters-made-with-the-help-of-linux)

---

### Post by Ceiber Boy on 2010-04-08
> **eriktheblu said:**
> A lot of people I've talked to don't seem to think Linux can run a graphic interface (including our organizations IT guy, who hasn't tried the Karmic disk I gave him** because it didn't have an activation code**).

when will people realize the free world

---

### Post by themarker0 on 2010-04-08
Gaming

---

### Post by Psumi on 2010-04-08
Have a systray without a taskbar/panel/dock.

[http://coldreactive.deviantart.com/art/Debian-Apr082010-160049239](http://coldreactive.deviantart.com/art/Debian-Apr082010-160049239)

---

### Post by Paqman on 2010-04-08
One guy I know doesn't think Linux mounts disks automatically, based on some nasty old version of RHEL he had to use years ago.

---

### Post by Psumi on 2010-04-08
> **Paqman said:**
> One guy I know doesn't think Linux mounts disks automatically, based on some nasty old version of RHEL he had to use years ago.

Linux doesn't mount USB Drives automatically, unless you have usbmount installed, or something similar.

---

### Post by Paqman on 2010-04-08
> **Psumi said:**
> Linux doesn't mount USB Drives automatically, unless you have usbmount installed, or something similar.

Yes, and I would imagine other OSes would have a similar problem, if you deliberately removed the equivalent subsystem.

:rolleyes:

---

### Post by Psumi on 2010-04-08
> **Paqman said:**
> Yes, and I would imagine other OSes would have a similar problem, if you deliberately removed the equivalent subsystem.

:rolleyes:

Which is a problem for people installing via mini.iso and want XFCE, LXDE or Openbox.

None of these DEs, nor their file managers (Including PCManFM) can mount USB Drives automatically alone... nautilus somehow does, and I do not know why.

---

### Post by johnb820 on 2010-04-08
Play DVDs, music editing, video editing, television and yes gaming.

EDIT: And also replacing/adding hardware without reinstalling the OS.

---

### Post by Psumi on 2010-04-08
> **johnb820 said:**
> EDIT: And also replacing/adding hardware without reinstalling the OS.

Windows XP and above can do that. Internal hardware such as RAM causes the system to need reactivation.

---

### Post by Dawei87 on 2010-04-08
> **Psumi said:**
> Which is a problem for people installing via mini.iso and want XFCE, LXDE or Openbox.

None of these DEs, nor their file managers (Including PCManFM) can mount USB Drives automatically alone... nautilus somehow does, and I do not know why.

you can automount usb and other external media with thunar in xfce or lxde

---

### Post by Warpnow on 2010-04-08
People are surprised the word linux has a meaning, as most of them seem to think its jibberish, and any computer without the windows task bar must be a mac.

---

### Post by Warpnow on 2010-04-08
Thunar automatically finds USB drives pretty well, but it does not automatically find other partitions on mounted drives, like XFCE never by default mounts my other distros, whereas gnome does.

---

### Post by aklo on 2010-04-08
Mounting of usb disk should be done automatically and not only if a user requires it and he got to find the program which will do it for him...i think mounting of usb is one of the basic stuff a good os should have.

Well at least ubuntu does it automatically for me...i don't care how it does it but as long as i don't have to go search for how to mount a usb drive it is good for me.

---

### Post by chucky chuckaluck on 2010-04-08
I don't think people who have heard of linux think of it in such a way.

---

### Post by red_Marvin on 2010-04-08
- run an interface that communicates with the operator with nothing but monospaced text ...and still be/run state of the art software.

---

### Post by swoll1980 on 2010-04-08
> **Psumi said:**
> Windows XP and above can do that. Internal hardware such as RAM causes the system to need reactivation.

RAM won't trigger a reactivation. A new processor wont either. The only thing I have found that will trigger a reactivation is a system board replacement.

Add: I never had to do a windows re-installation because I changed hardware.

---

### Post by swoll1980 on 2010-04-08
Most people think you have to know CLI-Fu to use Linux.

---

### Post by Paqman on 2010-04-08
> **swoll1980 said:**
> RAM won't trigger a reactivation. A new processor wont either. The only thing I have found that will trigger a reactivation is a system board replacement.


No single component will. The way the system works is that it only triggers reactivation if several devices are all changed at once. The reason you'll get it for mobos is that a mobo is several devices on one board.

---

### Post by kenweill on 2010-04-08
> **swoll1980 said:**
> Most people think you have to know CLI-Fu to use Linux.

Exactly.

Some people also think it's just another windows application.

---

### Post by Khakilang on 2010-04-08
Burn DVD movie, rip DVD, good window navigation and play Warcraft 3.

---

### Post by Irihapeti on 2010-04-08
OCR scanning. I was surprised to discover I could do this in Ubuntu. True, I needed to compile the package (tesseract) with a special setting before it would work properly, but once I'd done that, I was impressed with the accuracy of it.

---

### Post by Artemis3 on 2010-04-09
> **swoll1980 said:**
> Most people think you have to know CLI-Fu to use Linux.

Or be a programmer ^_^!

---

### Post by trig on 2010-04-09
my wifes window seven just got a nasty little virus. mine is still free.

---

### Post by Spike-X on 2010-04-11
> **Psumi said:**
> Have a systray without a taskbar/panel/dock.

[http://coldreactive.deviantart.com/art/Debian-Apr082010-160049239](http://coldreactive.deviantart.com/art/Debian-Apr082010-160049239)
How does one go about doing this?

---

