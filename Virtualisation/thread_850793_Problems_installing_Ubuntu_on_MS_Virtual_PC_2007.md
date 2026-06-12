---
title: "Problems installing Ubuntu on MS Virtual PC 2007"
date: 2008-07-06
forum: Virtualisation
---

### Post by Crul on 2008-07-06
Hi,

I'm trying to install Ubuntu on MS Virtual PC 2007. I started the installation and everything went through OK until the reboot.

At this point I removed the installation CD from the disk player and clicked the reboot button.

So the system started to reboot and I pressed the escape button when the GRUB prompt appeared so that I could boot in safe mode to change the video settings for Ubuntu as it doesn't work well with Virtual PC.

So I chose the safe mode option and pressed enter. Then various text appeared but in the end it always ended up hanging and it never reached the command line. 

The link below shows what kind of text appeared on the screen after I tried to load Ubuntu in safe mode

[[IMG]http://img74.imageshack.us/img74/8594/ubuntuscreenfe7.th.jpg[/IMG]](http://img74.imageshack.us/my.php?image=ubuntuscreenfe7.jpg)

If someone could help me out and give me some direction into how I can solve this problem I would be grateful.

Thanks

---

### Post by phaid on 2008-07-06
You may run into some installation quirks just trying to run the install from the cd  

Have a look here, which has a guide to get it running
[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)

that looks like it should take care of most of it and may get it working for you.  If that doesn't work and you still have issues,  Post them here so that we can see what they are and if we can help, or see if you can find the issues via goolge, then come back and let us know what worked and what didn't

---

### Post by p_quarles on 2008-07-06
Moved to Virtualization. 

There are more than likely a few people around here with experience using that application, but you're probably likely to get more support using VMWare or VirtualBox, since those are more favored in Linux circles.

---

### Post by Crul on 2008-07-07
I had a look at the link posted above by phaid.

Basically I'm stuck in between steps 1.1.4 and 1.1.5

I interrupt the reboot at the Grub prompt but I never reach the command line, various booting text appears (look at the image in the OP) but no command line.

Anybody have any suggestions/ideas as to why this might be happening?

Thanks

---

### Post by alloydog on 2008-07-10
I'm trying to install **8.04 Server** with VirtualPC 2007.

I get the initial boot screen, but when I hit F4 to get the other boot options, only "**Normal**" is given, that is no other options such as "**Safe graphics mode**".

I have read in several places that you need to drop the colour depth to 16, which I have tried to do.

I have tried desktop **Ubuntu 8.04** and also another small distribution called [**_Debris_**](http://debrislinux.org) by editing the grub boot line with vga=0x317 (1024x768 16bit colours), but only get a blank screen after the boot starts.

In fact I have not had luck with any Linux distribution...

---

### Post by phaid on 2008-07-10
This site has step by step instructions:
[http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/](http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/)

I'd recommend reading through the comments sections before trying it as it details some issues  people have encountered and fixes for them

---

### Post by alloydog on 2008-07-11
I had a retry this morning, and it seems the main problem was between the chair & keyboard...  I put the vga=0x317 after the -- of the boot line in GRUB.

After putting it in the right place, the installation ran OK, until it just after it asked for the username & password and HTTP proxy.  After that it froze at 42% looking for mirror...

---

