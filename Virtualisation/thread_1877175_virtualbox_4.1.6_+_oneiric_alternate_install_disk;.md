---
title: "virtualbox 4.1.6 + oneiric alternate install disk; hangs on first boot"
date: 2011-11-07
forum: Virtualisation
---

### Post by robotcontrolledbiodomes on 2011-11-07
Hi everyone,

I'm trying to install Oneiric 32bit "alternate install" CD on Vbox 4.1.6. I initiate this install by pressing F4 (mode selection) on the CD boot screen, selecting command line install, and then selecting "Install Ubuntu" from the main menu.

Installation finishes without any problems. Upon the first boot into the newly installed system, the process hangs with a blinking "_" after 10 seconds or so. 

The "command line only" install option I'm talking about is briefly mentioned [**here**]("https://help.ubuntu.com/community/Installation/LowMemorySystems#Execute_installation"). It's basically a really trimmed down version of Ubuntu, without X. ISO I used is [**here**]("http://www.ubuntu.com/download/ubuntu/alternative-download").

Anyone experience similar problems? I've put the vbox log here:
[**http://pastebin.com/skEHnLyH**]("http://pastebin.com/skEHnLyH")

Edit: I've successfully installed and used the regular 32bit Oneiric on this same Virtual Box install.

Edit 2: I figured it out. Apparently there is a bug with Ubuntu where it boots to TTY7 which apparently doesn't do anything without a graphical login manager installed. The trick is to switch to a different TTY. I used Alt + F1 for Vbox. Also try Ctrl + Alt + F1 I'll file a bug report.

---

