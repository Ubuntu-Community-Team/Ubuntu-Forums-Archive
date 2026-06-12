---
title: "how can i tell if i properly installed my graphics card"
date: 2007-11-08
forum: The Cafe
---

### Post by dare2soar on 2007-11-08
the blue screen of death shows up every now and then, it says to check and see if (something) is properly installed, the only thing i can think of that could not be installed properly is my graphics card, since i installed it myself and i haven't really done it before.
since i'm still a newbie at this, i want to know, how can i tell if i properly installed my graphics card?   :confused:

---

### Post by RussianVodka on 2007-11-08
Is this happening in Windows or Ubuntu?

---

### Post by dare2soar on 2007-11-08
windows.   please tell me you have an answer

---

### Post by Bannor on 2007-11-08
make sure without over doing it that the card is all the way into board tighten the screw.  if the sreen shows the bios when you start you have done it right.  

for ubuntu if you can't get it to work.  look around for the right driver and install it in recovery mode (command line).  Windows usually works if the card is installed right although you may need to install the windows driver to get the most out of it.

---

### Post by dare2soar on 2007-11-08
i'm sorry...bios?                       again, i'm a newbie

---

### Post by svtfmook on 2007-11-08
did you go from ati to nvidia or vise-versa?

either way, uninstall the video drivers and install the drivers from the disk that came with the card or download them from the mfg'er's website.

also, right click on my computer, go to manage.  then expand event viewer.  click on "system".  look for an error in the log there, should be notated with a little red or yellow sign.

post what it says there.

then, right click on my computer again, go to  properties, click the hardware tab and then click the device manager button.  click view > show hidden devices.  look through the hardware sections for devices that are not installed properly.  they will be notated with a yellow sign.  if you find one, right click on it and try to reinstall the driver.

but the system log will give you a good idea where the error is coming from.

---

### Post by svtfmook on 2007-11-08
> **dare2soar said:**
> i'm sorry...bios?                       again, i'm a newbie
BIOS contains your CMOS settings for your hardware.  these settings are flashed onto an EPROM chip on your motherboard.  BIOS is a user interface to change the basic input/output settings for your hardware.

you can get into BIOS by pressing either the del key, or possibly one of the function keys during POST (first screen that comes up when you turn your computer on), it should say what key to press to enter settings during POST.  if not, try del, F1 or F2, they seem to be the common keys.

one thing to look for, is if you had onboard video, and you installed a card, then you would need to go into BIOS and disable the onboard video.  or else your system will be confused.

---

### Post by dare2soar on 2007-11-08
yes...it was ATI..now its NVIDIA

---

### Post by dare2soar on 2007-11-08
i see a bunch of little red and yellow signs  =/

---

### Post by svtfmook on 2007-11-08
ok
#1, go into control panel, install/uninstall programs
uninstall catalyst control center

#2, go into device manager, expand display and see what it says is installed for your display adapter and video card.  uninstall anything that says ATI by right clicking the ATI device and selecting "uninstall"

#3, reboot.  go back into device manager and see what it says is installed for your display adapter and video card.  the found new hardware may pop up, if it does, install the nvidia drivers from the disk provided or downloaded.

#4, reboot.

then go back into the system log and see if there are anymore errors.

oh, and was the ATI video card onboard or PCI?  if it was onboard, don't forget to go into BIOS and disable the onboard video under the "onboard chipsets section"

---

### Post by dare2soar on 2007-11-08
catalyst control center?
i don't see it

---

### Post by dare2soar on 2007-11-08
the ATI is uninstalled, and nvidia is installed... =/
what els could be wrong with it,,,blue screen of death showed up about 4 times since my first post....
by the way does anyone know anything about:
BAD_POOL_CALLER      or     DRIVER_IRQL_NOT_LESS_OR_EQUAL
   thats what it said on the blue screen....

---

### Post by svtfmook on 2007-11-08
bad pool caller is a device driver trying to access a part of memory that is normally blocked/used by windows xp.  and the irq error means a driver is trying to reach a device on an irq but it's not the right irq.

i would uninstall the nvidia driver and reinstall it.

also, look in the event viewer under system, look for a time right before the bsod and post what is written in the events right before the bsod.

---

### Post by dare2soar on 2007-11-08
i reinstalled nvidia. i think i did it right this time.
    
(also, look in the event viewer under system, look for a time right before the bsod and post what is written in the events right before the bsod.)
<-----  how would i know which one is the bsod?...will it say BSoD?
 
by the way thank you,,thank you very much for helping me...

---

### Post by svtfmook on 2007-11-08
easy way to tell is by seeing a large time gap between log lines, that means there was an event, there should be an error event, but the error event doesn't always show up, then there will start up items from the reboot.

---

### Post by dare2soar on 2007-11-08
i found this under error...
Application popup: SMSTray.exe-Application Error: The instruction at "0x7c2bdca2" reference memory at "0x00000200". The memory could not be "read".
Click OK to terminate the program 
Click CANCEL to debug the program
 
 is that it?

---

### Post by dare2soar on 2007-11-08
i found that after double clicking the information sign under error

---

### Post by svtfmook on 2007-11-08
do you have a samsung dvd drive?

go to start > run
type "msconfig" and click run
click the startup tab
uncheck smstray

---

### Post by dare2soar on 2007-11-08
yes, i installed the samsung mp3 player program.
i did what u said to do, i unchecked it, it said i had to restart my computer,after i clicked ok ,=/ the BSoD showd up again...this time it said...
IRQL_NOT_LESS_OR_EQUAL

---

### Post by svtfmook on 2007-11-08
ok, boot into safe mode (press F8 while the computer boots, select safe mode).  when you get into safe mode, go into device manager and uninstall the nvidia drivers.  reboot under normal mode.  go to the video card's manufacturer's website and download the latest drivers for your video card and install them.  restart.

if you still get BSOD's, download memtest86 (or use a ubuntu live cd) and run memtest.  if it fails on the first pass, then you have a bad ram module.

honestly thought, the irq error can be related to a lot of things.  have you also installed a joystick?  or anything else for that matter?  i would tryin uninstalling them and reinstalling again to get them to install to a different irq.

---

### Post by dare2soar on 2007-11-12
hey, thanks a lot for your help, but my computer broke and i had t take it to be fixed,,,..for some reason it wouldn't start windows.
so, its fixed,,,finally!!   thank you again     =)           :)

---

