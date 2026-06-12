---
title: "Installing 12.04 into VirtualBox 4.18 installation never finishes"
date: 2012-08-16
forum: Virtualisation
---

### Post by wvxvw on 2012-08-16
Hello, I'm trying to install Ubuntu 12.04 LTS into VirtualBox 4.18 running on a Debian machine. I've got so far as a screen with the timezone selection, but 3 hours passed since then, and all I see is a spinning cursor and no progress in copying files. No error messages (at least not through the GUI) have been given. The GUI is overall responsive (I can move the window having the installation, move the mouse pointer etc.) but the installation seems to make no progress. It shouldn't take this long, should it?

---

### Post by smartboyhw on 2012-08-16
> **wvxvw said:**
> Hello, I'm trying to install Ubuntu 12.04 LTS into VirtualBox 4.18 running on a Debian machine. I've got so far as a screen with the timezone selection, but 3 hours passed since then, and all I see is a spinning cursor and no progress in copying files. No error messages (at least not through the GUI) have been given. The GUI is overall responsive (I can move the window having the installation, move the mouse pointer etc.) but the installation seems to make no progress. It shouldn't take this long, should it?
 Maybe the hard disk has a problem. The installation option is next...

---

### Post by wvxvw on 2012-08-16
Sorry, I didn't make myself entirely clear, it's not the screen, where you choose the language of the installer, it's the screen with the world map, where you choose your location (that's a bit further into installation).

However, it appeared that VirtualBox blocked mount command or did something to that effect, which probably put the installer in some sort of an infinite loop. However, all subsequent attempts at installing Ubuntu into a freshly created VM have led to the computer crash. I.e. when the screen with the map loads, the computer goes to reboot w/o any messages... This looks like some sort of a hardware failure, but I've no idea what fails. Any hints?

---

### Post by Dedoimedo on 2012-08-16
I would assume it's bad virtual machine settings, not hw.
Can you change the disk controller type or enable/disable apic/acpi?
Dedoimedo

---

