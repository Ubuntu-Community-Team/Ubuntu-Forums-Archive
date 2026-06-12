---
title: "Ubuntu studio keeps locking up"
date: 2008-04-29
forum: Ubuntu Studio
---

### Post by DJYoshaBYD on 2008-04-29
Ok.. I downloaded ubuntu studio, and when I install it, everything seems to go fine.. Sometimes, during the software install at the initial installation, it will fail, but when I retry it works..

But I noticed that I will open up a program, and the whole system locks up.. The only thing I install is the nvidia drivers using envy.. But it locks up either way.. With or without the nvidia drivers, and on random programs.. It just does it randomly.. Anyone else see this?

this is what I have


cpu: Pentium 4 HT 3.2ghz 32-bit (obviously) OC'd to 4.0ghz
ram: Kingston ddr1 400mhz 512mb
graphics: nvidia fx 5500 AGPx8 128mb, OC'd by 100mhz
linux version: Ubuntu Studio, clean install

---

### Post by Stochastic on 2008-04-29
Hmm, I can't tell you where your problem lies as, but it may be a bug with your particular hardware and some portion of low-level software.  What I would try is eiter: 
  - Re-install UbuntuStudio (and hope for a clean install).
  - Install regular Ubuntu and then download and install all the UbuntuStudio meta packages ```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-lookubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers uspash-theme-ubuntustudio
``` (really you don't need to type all of that as I'm sure icon-theme is a dependency of look etc... but better safe than sorry) feel free to omit any you don't want too.
  - Look into your system log messages and see if any errors/messages might help you to troubleshoot your current system (people in General Help forum would be more likely to know where/what to look (for) in this case).

---

