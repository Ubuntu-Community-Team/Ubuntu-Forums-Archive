---
title: "Audacity Responsiveness"
date: 2013-03-16
forum: Ubuntu Studio
---

### Post by Hal58 on 2013-03-16
The release of 12.04 LTS seemed to include a couple of 'features' to Audacity which have completely destroyed its effectiveness in editing music files at a low level, such as removing scratches, pops and ticks from recorded vinyl.  The previous LTS release (10.04) contained a version of Audacity that had a fixed horizontal scroll bar which allowed scrollong by complete 'screen' or smooth scroll (by pressing the arrows on left/right end).  The system seemed to respond instantly even on a lightweight 1.2 GHz Athlon netbook.

The new version contains no fixed scrollbar, but a pop-up pointer which only seems to scroll a 'screen' at a time after a noticeable delay, then in three painfully slow segments.  Even a multi-core 2.6 GHz Athlon system is too slow to be usable.

A second feature is zooming in and out with the +/- 'buttons'.  Even on lightweight netbooks, the old 10.04 version of Audacity seemed to react instantly, but the Audacity in the 12.04 (and 12.10) release is so slow that I am always three to five button presses ahead and must wait a seeming eternity for the system to catch up.

I have tried to compile the old 10.04 Audacity source under 12.04 with no success as well as compiling several Beta and Release versions of Audacity from Sourceforge and WxWidgets, all with no success.

Does anyone have any fix for these two problems so that I do not need to retain a couple of systems with 10.04 installed?  TIA.
Hal

---

### Post by tgalati4 on 2013-03-16
What were the compilation errors?  Perhaps you need some older support libraries to be installed along side newer libraries in order to compile it successfully.  Just proceed carefully.  I would take the 10.4 audacity deb package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and use the command line *dpkg -i* command to install it and post the errors that show up.  Uninstall the current audacity first:

```
sudo apt-get purge audacity
```

---

### Post by jejeman on 2013-03-17
> The new version contains no fixed scrollbar, but a pop-up pointer which only seems to scroll a 'screen' at a time after a noticeable delay, then in three painfully slow segments.
Obviously you are using Ubuntu not Ubuntu Studio.
Install Ubuntu Studio and everything will be as before. Or install XFCE or just use something that is not Unity.

Everything you have mentioned are not "features" of Audacity, but of DE.
I don't know what PC you have, here on C2D 3GHz with US 12.10 everything is snappy in Audacity.

---

### Post by Hal58 on 2013-03-18
> **jejeman said:**
> Obviously you are using Ubuntu not Ubuntu Studio.
Install Ubuntu Studio and everything will be as before. Or install XFCE or just use something that is not Unity.

Correct.  I am using Gnome 2d (no effects).  I prefer not to change desktop environments if possible but did take your advice and 'purged' my system of compiz which also removed unity and gnome-desktop.  After rebooting the system to insure that no remnants remained, the system was a tad quicker until I 'zoomed' in to a spot in a file to the point where individual samples were displayed.  As I approached that point, the display lagged more and more when responding to 'button' presses, and in the end, the horizontal scrolling was as bad as previously reported.  No permanent scroll bars were displayed, just the 'popup' ones which won't allow smooth scrolling needed to spot some types of 'noise'.

> **jejeman said:**
> Everything you have mentioned are not "features" of Audacity, but of DE.
I don't know what PC you have, here on C2D 3GHz with US 12.10 everything is snappy in Audacity.

I am beginning to believe that the symptoms I am experiencing are due to some DE-related library that I cannot identify.  I did install the 10.04 version of audacity (including audacity-data and a needed libsoundtouch1c2) on an Acer Aspire One 722 (dual-core AMD C60) per the previous responder's reply and it displays the same scrollbar anomalies as the 12.04 version (2.0) as well as the slowdown when zoomed in (32-bit system).

The performance is still slow on a 64-bit installation on a Toshiba Satellite, Dual-core AMD E-300 processor at 1.3 GHz and a Samsung Series 840 SSD.  I have also upgraded a 1.6 GHz AMD E-350 dual-core system to 12.10 which is somewhat improved in responsiveness, but still has the scrollbar, scrolling and slowdown anomalies noted above.  Completely unusable for the vinyl cleanup tasks I perform.

BTW, the Toshiba Satellite system was perfectly acceptable speed and interface-wise with a slower SSD under Ubuntu/Gnome 8.04 and 12.04.

Hal

---

### Post by Hal58 on 2013-04-08
Well, it appears that the problems with audacity responsiveness and scrollbars in Ubuntu 12.04 and 12.10 are due to some factors in the environment associated with Gnome.  After an install of Ubuntu 12.04 server, then "sudo apt-get install xorg icewm audacity", audacity performed as it did in previous 10.04 installs.  I miss some of the features of the Gnome environment, but It is worth it to get Audacity working so I can restore more old LP music.

---

