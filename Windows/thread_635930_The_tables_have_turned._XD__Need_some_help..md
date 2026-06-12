---
title: "The tables have turned. XD  Need some help."
date: 2007-12-09
forum: Windows
---

### Post by Sarteck on 2007-12-09
A while back, I would have been coming to these forums on Windows asking how to get Linux working.... Now it's the other way around.  Heh heh.

My girlfriend, she uses Windows XP (mainly just to play her Sims 2), and suddenly last night it goes kaput.  It's trying and failing to load her game, so after about an hour of listening to that damned Sims music, she shuts it down (holds in the power button for a few seconds).

When she turns it back on, it has not sound whatsoever.  Being a Windows user, her next attempt to fix it is... you guessed it!  Reboot again!

Nothing.  Ah, well, she decides she'll go online and download some malware removal tools (while I'm laughing, sitting at my smoothly-running Ubuntu system, heh heh).

...No Internet, either?  Ouch, now I'm starting to feel sorry for her.

The strange thing is, she is connected to our Wireless network (both Windows and RaLink Config Utility say so), but she cannot ping to the router.  I can see her in our workgroup, but she doesn't appear to have an IP address in SMB4K.  Her IP is static, and it was working perfectly fine before the game crashed.

I've seriously been out of Windows for a while, so I don't even know where to -begin- tackling this problem.  Any advice/assitance would be appreciated.

---

### Post by Dr. C on 2007-12-09
My first suggestion is to boot the system from an Ubuntu live CD and check that the hardware (sound, internet etc) actually works.

If Ubuntu works then one can either try to fix Windows XP or back up the activation files (wpa.bak and wpa.dbl found in C:\WINDOWS\system32) and reinstall. If you re install make sure to back up all the data on the computer. Also if you reinstall make sure to back up or uninstall any licensed rights for other DRM software music etc on the system. This has to be done for each application  individually. 

After re- installation of XP, do not activate, shut the system down and reboot from the Ubuntu live CD. Then from Ubuntu replace the the activation flies with the back up copies and reboot Windows XP. This avoids unnecessary activations since Windows XP is re-installed on the same hardware.

**By the way this does not work to pirate Windows XP, only to back up and re-install a legitimate (genuine) copy of Windows XP on the same hardware. **

---

