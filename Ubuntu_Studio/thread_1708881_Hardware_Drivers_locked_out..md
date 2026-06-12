---
title: "Hardware Drivers locked out."
date: 2011-03-17
forum: Ubuntu Studio
---

### Post by madrabbi on 2011-03-17
Hi,

First time user of Ubuntu studio 10.04, first time poster here on this lovely forum (though I've lurked and searched for a few solutions already!), first question and it'll doubtless be a n00b moment, but I can take it so here we go...


Trying to make the wireless card state Active (currently showing inactive in Network Tools).
The obvious solution is to find the device in System/Administration/Hardware Drivers, but this is where my problem begins.
The icon for Hardware Drivers has a padlock on it and, I'm sure you've already guessed, when I click it there's a very brief window pops up before disappearing again without letting me in to change the settings.

Q: how do I unlock Hardware Drivers, please?

Running on Dell Latitude D520, 53Gb disk partition (WinXP on 2 pre-existing installs taking up a further 27Gb). Any more info you need please do ask :)
Thanks for any help you can give!

---

### Post by ailo.at on 2011-03-17
Usually you won't find drivers to hardware in: System -> Administration -> (Additional Drivers?). This is because most of them are included in the kernel and you never need to know they exist.
Most probably your network card is working, and you just need to connect to a network using the network icon on your panel. Left click it and see if there any networks available. Also make sure "Enable Wireless" is checked.

If you are unable to enable wireless, then we should look into what type of network card you have, and if you need additional drivers for it.

---

### Post by madrabbi on 2011-03-17
Thanks for the advice ailo

When you say *" connect to a network using the network icon on your panel"*, exactly what panel do you mean, please?

Cheers!

---

### Post by ailo.at on 2011-03-17
Oops. Need to check how this works on Ubuntu Studio. I of course haven't used wireless on a Ubuntu Studio install, so I need to check it out..

---

### Post by madrabbi on 2011-03-18
Cheers ailo.
If it's turning into a faff and a hassle, I reckon I'm going to clean the machine and install it with Ubuntu instead. I can always add Ubuntustudio's extras at a later date, anyway!

---

### Post by ailo.at on 2011-03-18
> **madrabbi said:**
> Cheers ailo.
If it's turning into a faff and a hassle, I reckon I'm going to clean the machine and install it with Ubuntu instead. I can always add Ubuntustudio's extras at a later date, anyway!

Sorry for talking out of my a** before. All you need should be right here:

[https://help.ubuntu.com/community/UbuntuStudioNetworkSetup](https://help.ubuntu.com/community/UbuntuStudioNetworkSetup)

I think the explanation there sums it up quite well. 

Using regular Ubuntu as a base won't be too much of a problem for most people, depending on your hardware. I usually use regular Ubuntu for my home / testing OS. But, for a production machine I'd go with something more tuned towards audio use.

Anyway, hope it works out for you, either way.

---

### Post by madrabbi on 2011-03-18
Ooh, now you're talking!
That's exactly what I was looking for, thank you :D

---

