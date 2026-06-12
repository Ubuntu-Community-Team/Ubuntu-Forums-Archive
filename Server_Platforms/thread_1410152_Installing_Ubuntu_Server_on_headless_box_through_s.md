---
title: "Installing Ubuntu Server on headless box through serial terminal"
date: 2010-02-18
forum: Server Platforms
---

### Post by samalex on 2010-02-18
Hi,

Back in the day we used to install most to all of our Unix/Linux systems on hardware with no monitor, keyboard, etc... we'd just connect a serial terminal to it, boot from the media, and run from there.  Using Ubuntu Server is this still possible?   Last time I did this was installing Red Hat 7.1 on a DEC Alpha, but that was years ago.

I have an 8 year old home-built server without a video card, and I'd like to use the serial port on an older laptop using a terminal program on the laptop to install 32-bit Ubuntu Server 9.10.  Is it possible to do a text-based installation of Ubuntu Server from CD where it sends everything through the serial port (/dev/ttyS1 or whatever)?  

Maybe this is thinking too old school, so just curious.

Thanks and take care,

Sam

Update: I found [this link]("https://help.ubuntu.com/community/SerialConsoleHowto") on the Ubuntu site showing how to set it up post installation, but is it possible to do this for installation?  Thanks..

---

### Post by tlsarles on 2010-02-18
Ninja Props if you get that to work. GL

---

### Post by Swathe on 2011-01-10
We are trying to get this going right now. The machine boots but serial display out put stops me seeing the little xserver stuff before the ncurses display

---

