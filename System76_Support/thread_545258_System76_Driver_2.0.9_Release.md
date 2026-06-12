---
title: "System76 Driver 2.0.9 Release"
date: 2007-09-07
forum: System76 Support
---

### Post by crichell on 2007-09-07
System76 Driver 2.0.9 has been released.  This update only includes bug fixes for the new black and silver Darter (daru2).

Changelog:

Version 2.0.9

   1. Fix Darter (daru2) Headphone Sensing Bug #130669
   2. Improve Darter (daru2) battery monitor Bug #130739 - Fixes buggy DSDT table in BIOS - installs via initrd.img

If you have a new Darter I recommend running the driver.  Go to System > Administration > System76 Driver

Click the "Install Drivers" tab > Click "Install"

---

### Post by saxamo on 2007-09-07
'It just tells me "all drivers for this system are provided by ubuntu" when I click install from the drivers tab. I don't think I get an update.

Edit: However, when I go directly to the update manager it installs successfully from there.

Thanks!

---

### Post by ackey on 2007-09-07
I believe it installed successfully and I restarted, however, I'm not seeing any improvement in the battery monitor.  I had already fixed the headphone issue by hand.  So is this not a full fix of the power manager issue, or did I not successfully install??

---

### Post by thomasaaron on 2007-09-07
Well you said you installed it and rebooted. 
You didn't say that you actually ran it: System > Administration > System76 Driver. (Restore Tab, Restore Button).

---

### Post by palintheus on 2007-09-07
I installed it ran update and saw lots of HDD activity, and it took several minutes like it was installing things, but then finished with all the drivers are provided by ubuntu, which I know isn't the case, due to the headphone issue.

The power management applet now does not have any randomness while plugged in, but as soon as I unplugged it it showed 0% on mouse over and the battery icon was almost empty and red, but when clicked it shows 100%. Once plugged in the randomness returned.  ](*,)
::EDIT::
I don't know if this helps, but when plugged in the battery LED is not lit either...

At first plugging in my headphones muted the front, but there was still no sound in the headphones. I had to go to Edit > Preferences and check-mark the Headphones box, then under the switches tab in the main applet check-mark the headphones box. It worked, I got blasted in my ears, beware, the headphone and main volume is the same and if PCM is all the way up your headphones will be dramatically louder (at least in rythmbox).

---

### Post by poetbeware on 2007-09-08
Hi, unfortunately I'm not seeing any improvement in the battery monitor either. It will say crazy things like "64 hours until charged". The effect seems to be random.

---

### Post by imhavoc on 2007-09-09
> **thomasaaron said:**
> Well you said you installed it and rebooted. 
You didn't say that you actually ran it: System > Administration > System76 Driver. (Restore Tab, Restore Button).

Tom,

What's going to happen when I click "Restore?"

"Restore" has very draconian overtones for me. I'm always hesitant to have all of my personal config files overwritten, and have to start over with all of my customization stuff. Some of my customization includes additions to the /etc/apt/sources.list and things like that.

---

### Post by tvnz on 2007-09-09
when will serval series drivers release? thks

---

### Post by voidmage on 2007-09-09
These things work with gazp3 as of a tribe 5 dist-upgrade from feisty:
Sound
Battery monitor
Cpu scaling
Camera

Having a few issues with:
Wireless: knetworkmanager sometimes needs a restart to connect to networks. Sometimes I have to "sudo /etc/dbus-1/event.d/25NetworkManager restart". Other times I have to reboot entirely. Might be my network infrastructure, but no way to confirm that here.

Unsure about gnome's nm-applet, since I use KDE.

Haven't gotten working yet:
Suspend
Hibernate (wasn't working in feisty either)

Haven't tested:
Card reader, but I expect it to work.

---

### Post by palintheus on 2007-09-09
> **imhavoc said:**
> 

What's going to happen when I click "Restore?"

.

Everything that is listed on the restore tab will happen.

1. Setup System76 software repository list (Replaces Existing)
2. Installs System76 xorg.conf file (Replaces Existing)
3. Installs necessary drivers for your machine
4. Installs included applications

---

### Post by Aug Leopold on 2007-09-09
Just restarted, tried, to install new drivers on daru2, and i got the supported by ubuntu message. So, i did the restore and rebooted. Result: The battery monitor is still messed up(but possibly less than before) and now the sound _always_ goes through the speakers because the system doesn't detect my headphones.
Did this just make it worse?

---

### Post by palintheus on 2007-09-09
You might try this, from my previous post:

> At first plugging in my headphones muted the front, but there was still no sound in the headphones. I had to go to Edit > Preferences and check-mark the Headphones box, then under the switches tab in the main applet check-mark the headphones box. It worked, I got blasted in my ears, beware, the headphone and main volume is the same and if PCM is all the way up your headphones will be dramatically louder (at least in rythmbox).

---

### Post by Aug Leopold on 2007-09-09
Sorry, must have skipped that, i did what you said and now it goes back to the old way where it plays though both. (Not that i mind, because if you turn it down you can barely )hear the speakers.) Now I'm off to test the battery monitor.

---

### Post by palintheus on 2007-09-09
Hmmm, mine mutes the speakers now, here is a few screenshots of my Volume Control for comparison.

---

### Post by Aug Leopold on 2007-09-09
ah-ha! It appears that if 'front' is not muted sound will still play through the speakers when headphones are in. Muting the 'front' volume fixes the problem.

So to recap for anyone else viewing this.
1. goto switches tab, check off headphones
2.goto playback tab, mute 'front' or alternatively hit (fn+f9)

UPDATE: It turns out that the fn+f7/f8 hotkeys adjust the 'front' volume, so if you adjust the volume with those and then want to use headphones again you have to re-mute it. (fn+f9)

---

