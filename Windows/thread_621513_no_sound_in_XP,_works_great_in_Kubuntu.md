---
title: "no sound in XP, works great in Kubuntu"
date: 2007-11-23
forum: Windows
---

### Post by thermophile on 2007-11-23
first off, I hate Windows too and if all programs worked in Ubuntu I'd never run XP.  But my husband wants to play some flight simulator games and he says that the only decent ones are for windows, so I'm trying to get the computer set up for him.  

the problem: no sound in Windows, but the sound works in Linux so it must be a driver problem right?  I have a Shuttle XPC that I bought used last year that has a VT8237 bridge,  I've downloaded and tried to install the following drivers: Via Vinyl driver, Via vt1617a, and the "audio" driver from shuttle for my particular motherboard.  the via drivers acted like they were installing but then would stop and I'd get a "device not responding (code 10)" error.  the install wizard wouldn't recognize the shuttle audio driver.  I'm using the wizard because I don't know any other way to update/add a driver in windows.

please help

---

### Post by rickyjones on 2007-11-25
I recommend calling the PC manufacturer. They should be able to provide the correct drivers. A lot of times the manufacturer of the PC will require their own custom driver. Sounds like that is the situation.

-Richard

---

### Post by kodak on 2007-11-25
Installing sound drivers in windows.

go to Start and right click on "computer" and select manage to open a new window

look for and click Device Manager

right click on Multimedia Audio Controller in the list and select properties

hit Reinstall driver to launch a new window

select "no not this time" then enter (or next)

select "install from specific location"

the "select do not search"

in new list look for and select "Sound Video Game Controller"



now you need to locate your driver, i found it works best if the driver is on a cd (removable media)

---

### Post by inversekinetix on 2007-11-26
is onboard sound enabled on your motherboard?

---

### Post by thermophile on 2007-11-27
> **kodak said:**
> Installing sound drivers in windows.

go to Start and right click on "computer" and select manage to open a new window

look for and click Device Manager

right click on Multimedia Audio Controller in the list and select properties



I don't have any type of multimedia or audio controller listed in device manager, just audio and video codecs.  it doesn't give me an option to reinstall or remove any of those codecs.

I don't know if onboard sound is enabled-how would I figure that out?

---

### Post by gspx on 2007-11-27
It should be in the sound options in your control panel, something like controlpanel >> sound options >> advanced :)

---

