---
title: "Can &quot;nomodeset&quot; be automated?"
date: 2016-02-04
forum: Ubuntu, Linux and OS Chat
---

### Post by john_ladasky on 2016-02-04
I've been installing Ubuntu on computers since 2006.  Most of these computers have NVidia GPUs.  While I'm strongly biased towards open-source software, I want to use the NVidia proprietary drivers to ensure access to CUDA -- and to stop compiz from using so much CPU power.

I casually click through System Settings > Software & Updates > Additional Drivers and install the NVidia driver.  On reboot, I almost always get problems -- kernel panics, CPU soft failures, black screens, etc.  

After doing some frantic reading on the net, I inevitably return to an issue I've forgotten about for 18 months or so: that adding "nomodeset" to the boot command is (always?) required for NVidia drivers to get them to start correctly.

Would it be hard to arrange to update the boot command automatically when a user switches the video driver?  This has been a gotcha for me for years, and it's something that I always thought would eventually get fixed.  There may be good reasons NOT to automate the nomodeset decision, but I can't say that I know what they are.  Maybe a dialog box could be provided, if the user needs to think about the nomodeset decision before it gets made.

Discussion is appreciated, thanks.

---

### Post by mc4man on 2016-02-04
Can't say that nomodeset is required to use Nvidia drivers,  never  have had any issues when using the appropriate driver for the gpu .  Actually would think that nomodeset would prevent the driver from being loaded

---

### Post by buzzingrobot on 2016-02-05
A number of Nvidia cards are rather poorly supported by Nouveau.  I have one, a GTX 750ti. 

The issue with "Additional Drivers" and other similar tools is that they require the Nvidia card to be active.  Unfortunately, here, switching to Nvidia in the BIOS and rebooting will result in a black screen in sleep mode and an unresponsive keyboard.  You need to manually interrupt the boot and edit the grub config to add "nomodeset".  This typically enables a visible but degraded display so the Nvidia proprietary driver can be installed.

Interrupting the boot process and editing grub configuration files is risky and in no way should be forced on Linux users. If Nouveau cannot support the active card well enough to deliver a visible dispaly, Nouveau should not be used.

So, yes, it would be very useful to alter the boot process *in an installer*  to check for an active Nvidia card and offer the option to install a proprietary driver at that point.

A related issue that needs attention is that you cannot switch back to Intel onboard video without correctly purging the proprietary driver, which is also unreasonable to ask of users.

---

### Post by grahammechanical on 2016-02-05
What does nomodeset do?

Does it stop Linux from accessing the monitor's EDID chip to determine the optimum screen resolution? A temporary measure surely? I have a Nvidia card but I have never needed to use nomodeset. I do not have hybrid graphics. Why force on me something I do not need?

Regards.

---

### Post by buzzingrobot on 2016-02-05
> **grahammechanical said:**
> What does nomodeset do?



Nomodeset tells the kernel to avoid loading video drivers and use BIOS modes until X is loaded. Without it, the kernel sets the video mode and we get the nice boot screens and the transitions to the login screen.  When everything works.

My last two Nvidia cards, the current 750ti and the previous 550ti, always required the use of nomodeset on any distribution to avoid a black screen at the point X loads. Get the proprietary driver installed and that goes away, of course. (I don't have hybrid graphics, either.)

Nomodeset should be a one-time thing, but I suspect some users keep it around.

What I suggested wouldn't be mandatory. But, if a card that is known not to work is detected, it doesn't make sense to continue the boot knowing the system will be unusable when it completes. Better at that point to interrupt the boot, explain things to the user, and offer some options.  One option would be to insert 'nomodeset' for the user and continue the boot. Another would be to offer proprietary drivers for installation at that point.

---

### Post by kevdog on 2016-02-06
Can't you just add nomodeset to the grub kernel command line?  I thought that was how you set it permanently.

For example in /etc/default/grub, you could set the following like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"

You then have to regenerate the grub.cfg file after editing this file to make the change active. Run the following as root to do this:
grub-mkconfig -o /boot/grub/grub.cfg

---

### Post by buzzingrobot on 2016-02-07
> **kevdog said:**
> Can't you just add nomodeset to the grub kernel command line?  I thought that was how you set it permanently.



Yes, you can. I just think it's unreasonable to expect users, especially new users accustomed to having Nvidia "just work", to do that.  And also unreasonable to expect them to know how. 

Nomodeset, at least in my experience, delivers a very poor display that looks to be 640x480 and is often accompanied by distortions and screen affects. There's no way I could use it permanently. No 3D capability, as well, which makes it inappropriate for most modern window managers.

Cards that do not work correctly or at all with Nouveau (the usual problem seems to be that X crashes on launch) are known. Nvidia's Maxwell series is especially problematic. I'd like to see installers detect these cards and offer users a choice of the best availalbe options so they can avoid breaking their system.

---

### Post by mastablasta on 2016-02-09
i couldn't get it to work with or without nomodeset... :P

---

### Post by buzzingrobot on 2016-02-09
> **mastablasta said:**
> i couldn't get it to work with or without nomodeset... :P


Not surprised.  I had a 550ti card that wouldn't work with any kernel in the 3.2 series, not matter what I did.

---

