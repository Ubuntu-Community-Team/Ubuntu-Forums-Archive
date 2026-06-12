---
title: "virtualbox: winxp sp 2 vdi does not boot in ubuntu"
date: 2008-06-17
forum: Virtualisation
---

### Post by joeboentoe on 2008-06-17
Situation:

I made a new virtual disk virtualbox in windows xp pro SP2. On that virtual disk I installed win xp pro SP2.

When I try to open that disk with virtualbox in Ubuntu then it doesn't boot. I double checked that the virtualbox application has the same settings in windows and ubuntu. It just shows the windows xp loading screen for less then a second and then a blue screen less then a second. Then it reboots and starts all over again. With the virtualbox in windows I can open the virtual disk fine.

How to solve this?

---

### Post by prshah on 2008-06-17
> **joeboentoe said:**
> 
I made a new virtual disk virtualbox in windows xp pro SP2. On that virtual disk I installed win xp pro SP2.
 It just shows the windows xp loading screen for less then a second and then a blue screen less then a second.


When the (virtualized) windows is booting up, keep tapping F8 (After the BIOS screen, _before_ the windows splash screen). On the boot menu that turns up, choose "Disable automatic restart on failure". This boot menu may turn up anyway since your last bootup failed.

Then continue starting windows. This time, when the blue screen comes, the system will not restart. Look in the blue screen for the error message: it will be ALL_IN_CAPS_WITH_UNDERSCORES. Post that error message here for further troubleshooting. Or simply grab a screenshot and post it here.

---

### Post by joeboentoe on 2008-06-17
The error screen is:

[errorscreen]("http://users.telenet.be/tranceminded/linux/problem.jpg")

---

### Post by prshah on 2008-06-18
> **joeboentoe said:**
> The error screen is:

[errorscreen]("http://users.telenet.be/tranceminded/linux/problem.jpg")

Looks to be in german, thank god for error numbers!

Your boot record _may_ be corrupted. Try rebooting and see if you can get into XP through GRUB dual boot. (Indeed, if grub starts at all!) 

IF that works, then use the F8 trick again in the virtual machine to land up in the Boot menu. This time, choose "use last known good configuration" option.


If that doesn't work then you've probably done something wrong in creating the VDI. I have not used vmware, so maybe someone else can advise you on that.

DISCLAIMER: This advise at your own risk, please.

---

### Post by joeboentoe on 2008-06-18
:)actually it's dutch.

I can boot this virtual disk with the virtualbox application installed in windows (both vista and xp SP2).

I cannot boot this virtual disk with the virtualbox application installed in Ubuntu.

So there is nothing wrong with the disk :). There must be something else

---

### Post by joeboentoe on 2008-06-18
SOLVED

I had a piix selected in the settings, everything works now

---

### Post by thefekete on 2008-08-11
Thanks, for posting your solution, I had a VERY important VDI backed up on a server that I couldn't access...

For those that are having similar problems, just go to General Settings for the guest machine and under the Advanced tab, select PIIX3 for the IDE Controller Type.

This was an issue for me when moving an existing and working XP SP2 VDI to another workstation with a newer version of VBox. The new machine had PIIX4 by default, and wouldn't boot. I changed it to PIIX3 and it worked fine.

---

### Post by trigoman05 on 2008-11-26
I coulndn't find the button to say thanks, but thanks!! This was really useful, I was driving myself nuts over this.

---

