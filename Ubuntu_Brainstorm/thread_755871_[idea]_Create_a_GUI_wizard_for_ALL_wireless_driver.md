---
title: "[idea] Create a GUI wizard for ALL wireless drivers which don't work out of the box."
date: 2008-04-15
forum: Ubuntu Brainstorm
---

### Post by Mazza558 on 2008-04-15
For 8.10, the main goal is to create universal connectivity. To make this happen, a GUI similar to Envy needs to be created. It should:

- Have a database of the most common driver names (probably about 5mb on disc) 

-Have a wizard run at first boot for setting up a wireless driver if it doesn't work out of the box. This would involve several steps:
[LIST=1]
[*]Run "lspci" and match the name of the correct wireless driver to the database
[*]This then tells the wizard what driver will run perfectly with that hardware (e.g ndiswrapper, fwcutter)
[*]The wizard has a GUI with progress bars and info to indicate what it's doing. It also asks at this point that the PC be connected by ethernet cable to a point of internet access
[*]The wizard then runs a wget to the fwcutter driver or correct binary driver for ndiswrapper (from the manufacturer's website)
[*]The wizard then runs a pre-designed script for whichever driver to install it. For ndiswrapper, this involves the usual steps like "ndiswrapper -i bcm43.inf" etc. If a reboot is required, the wizard continues on startup.
[*]When the driver is installed, the GUI then attempts to connect to a network (build nm-applet into the wizard?)
[*]Finally, the GUI would run a simple test to check for connection - e.g "ping www.ubuntu.com", then try and open a link to [www.ubuntu.com](www.ubuntu.com) in firefox.
[*]At the end, the GUI would then ask if the connection is working (e.g the page loads) - if it does, the wizard is complete (and it removes any setup files)
[*]If the driver doesn't work, a troubleshooter is run.
[/LIST]

---

### Post by smartboyathome on 2008-04-15
What should be taken out to accomidate this if it doesn't fit? I have a feeling doing this will lead to a lack of programs for the end user since space is finite. :(

---

### Post by Mazza558 on 2008-04-15
> **smartboyathome said:**
> What should be taken out to accomidate this if it doesn't fit? I have a feeling doing this will lead to a lack of programs for the end user since space is finite. :(

Tracker needs to go. This would probably be a 6mb package, max.

---

### Post by xelapond on 2008-04-16
They don't include Envy with Ubuntu, so this doesn't have to be included.  Some people don't need a Wireless driver wizard.  It would be great though, a lot of people leave because they can't figure out there wireless cards.

---

### Post by phidia on 2008-04-16
Yeah, I do think that this is a good idea-it will require work obviously but good none-the-less. 
Some cards, like my atheros 5007er need a lot of fussing with to get working I'm using x86-64 Gutsy, but I tried 32bit distros that do not support wifi on my laptop.
If a user can't get on the internet it probably does become a negative introductory experinace.

---

