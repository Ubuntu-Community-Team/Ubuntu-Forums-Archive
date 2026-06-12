---
title: "Screen power saving mode not activating in X11"
date: 2021-11-21
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2021-11-21
I set it to tuns the screen off after 6 minutes, 10 min later still on, this works on wayland, though as soon as it does the screen comes back on (black screen w/ cursor) and i can't even get to a TTY

kernel is 5.15.3-051503-generic

Ryzen 5 5600G w/ B550 board HDMI out -> DVI Monitor
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 166a
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 166b
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 166c
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 166d
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 166e
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 166f
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1670
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1671
16:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43ee
16:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43eb
16:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43e9
20:08.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea
20:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea
29:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
2a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller (rev 04)
30:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne (rev c9)
30:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller
30:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
30:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
30:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
30:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
```

---

### Post by TheFu on 2021-11-21
In X11, using kernel ...  5.11.20-0511, I know that these commands work on my Ryzen 5600g:
```
xset s off
xset -dpms &
xscreensaver-command -exit
```
I can't use Wayland. It breaks make workflows.

And do the reverse when I want to allow screen blanking again:
```
xset +dpms &
xset s on &
xscreensaver &
xscreensaver-command -activate

```

I use a little script to toggle those settings, though the name is almost a double-negative so I have to always think about what it actually does before using it. I generally just call the script from another script.
I'm not using Gnome-anything as a DE, so if that needs special settings, I haven't any clue.

---

### Post by pqwoerituytrueiwoq on 2021-11-21
With xset +dpms && xset s on the X11 the screen goes blank and come back on right way just like with wayland, however the system is usable

note that xscreensaver is not installed

i have been able to reproduce this on the daily kubuntu iso from today (sunday)

when the system locks up with wayland i can't login via ssh ,switch to TTY, use REISUB, but numlock/capslock leds respond

note that screen does not lock with X11

---

### Post by TheFu on 2021-11-21
> note that screen does not lock with X11 
Is there a screen-lock/saver program installed?  Which DE are you using, if any?

**inxi -bz** would be helpful for some basic info.  There's also a "capture everything" script that some of the moderators and most experienced folks have created over the summer.  It is on the ubuntuforums github [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info). It grabs some interesting things.

---

### Post by pqwoerituytrueiwoq on 2021-11-21
KDE, i thought i used the kubuntu tag.. oh i did...

testing the Kubuntu daily build as i plan to daily it for a few years

[https://paste.ubuntu.com/p/KN6ddVvrMJ/](https://paste.ubuntu.com/p/KN6ddVvrMJ/)

---

### Post by pqwoerituytrueiwoq on 2021-11-21
I was unable to get this problem using my Ryzen 5 3600 w/ RX 580 using display ports (dual monitors)
tried both X11 and wayland, note that i did set it to use 5 minutes to save time

---

### Post by TheFu on 2021-11-22
> **pqwoerituytrueiwoq said:**
> KDE, i thought i used the kubuntu tag.. oh i did...

testing the Kubuntu daily build as i plan to daily it for a few years

[https://paste.ubuntu.com/p/KN6ddVvrMJ/](https://paste.ubuntu.com/p/KN6ddVvrMJ/)

In the sidebar, is says 2009/Xubuntu. Imagine how confusing someone easily confused like me can get with different data?
I don't see any tags. Sorry. I block most google domains.

---

### Post by pqwoerituytrueiwoq on 2021-11-22
Xubuntu i still my daily system (Ryzen 5 3600 / RX 580 / X470) for now anyway, testing on a second-dairy system (Ryzen 5 5600G / B550)
How do you even block the tag? and why would you and what would google have to do with that? if there is some other tag thing i do not know about it probably cause i have it blocked

[ATTACH=CONFIG]289528[/ATTACH]

---

### Post by TheFu on 2021-11-23
> Thread: Screen power saving mode not activating in X11
is what I see. Perhaps I'm not looking in the right way/place?  I seldom visit a subforum list. Email includes direct links to my subscribed threads.
And in the side bar, I see
> Distro
    Xubuntu for every post from you.
I see "Ubuntu" for my posts, which isn't really true ... except that I run ubuntu, but without any DE.  None of this matters really. Lacking any other information - or conflicting information, I usually ask which DE - and we know it is KDE.  2 days ago, there was a list ... oh and I see now the titlebar of my window says > [kubuntu] Screen power saving mode not activating in X11   When someone says **X11**, I'll probably take a look at that thread. I usually skip KDE posts, since I'm clueless.  I'm interested in seeing how X11 vs Wayland is working for the crowd, since I've had broken workflows with Wayland.  Anyway, it appears this was all my fault. Mea culpa.

I block google stuff at the network layer because I believe that company is not-so-nice and is taking data without permission.  GoogleTagManager.com is one  blocked domain, there are hundreds more, but I do allow a few 'g' domains.  I assumed that the Kubuntu tag was stored by GoogleTagManager.com, somehow, but I don't know, since I don't see stuff from there.  I block hundreds of thousands of domains using a variety of techniques.  Firewalls, subnets, domainname patterns, regex patterns, and by content.  Since I cannot convince the entire world that I'm right about this, I can only block it from entering our network and slurping our data. My network is hostile towards many specific companies and their attempts to take without permission.  There are many worse companies than google in this aspect.

---

### Post by pqwoerituytrueiwoq on 2021-12-14
On X11 kscreen2 detects the monitor looking for a new sources and thinks a monitor was just plugged in as a result thus activating the new monitor it found, this only seems to affect AMD GPUs as far as i can tell

disabling a monitors auto source detection on the monitor works around this issue and on wayland solves the black screen lockup issue

---

