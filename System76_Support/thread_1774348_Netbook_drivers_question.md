---
title: "Netbook drivers question"
date: 2011-06-03
forum: System76 Support
---

### Post by flihi on 2011-06-03
Will Kubuntu 11.04 work with System76 drivers on my Starling netbook?

---

### Post by macaholic on 2011-06-04
I don't see why they wouldn't, drivers are almost always independent of the desktop environment (GNOME, KDE, XFCE, etc), so they should work as well on Kubuntu as they do on Ubuntu.

---

### Post by flihi on 2011-06-05
> **macaholic said:**
> I don't see why they wouldn't, drivers are almost always independent of the desktop environment (GNOME, KDE, XFCE, etc), so they should work as well on Kubuntu as they do on Ubuntu.
The only reason I wish to upgrade to Kubuntu 11.04 is because I am having trouble booting from a USB flash drive using Ubuntu 10.04 Remix on my Starling star1 model and I am curious if upgrading to Kubuntu 11.04 or Ubuntu 11.04 would solve this problem. Do you have any recommendations?

---

### Post by Dave_L on 2011-06-05
I'm running Ubuntu 10.04 netbook remix on a star3. I made a Live USB flash drive from ubuntu-11.04-desktop-i386.iso using Startup Disk Creator, and have no problem booting from the drive.

What kind of problem are you having?

---

### Post by Roush 427r on 2011-06-05
I am rocking Kubuntu 11.04 on my Star4, everything is hunky-dory. Looking into Arch right now actually. Just seems to be a problem with the Grub because I am getting Error Message 15: File not found. still looking into it. ](*,)

---

### Post by flihi on 2011-06-05
> **Dave_L said:**
> I'm running Ubuntu 10.04 netbook remix on a star3. I made a Live USB flash drive from ubuntu-11.04-desktop-i386.iso using Startup Disk Creator, and have no problem booting from the drive.

What kind of problem are you having?
At the Startup Disk Creator page, the bottom of the page is grayed out and will not let me create a startup disk when I click the Make Startup Disk tab. Maybe I am not saving the i386.iso image file to the correct file when I am asked before I download the file. The few times I did get the Startup Disk Creator to work I would have to go to the boot screen at startup and scroll down to my USB flash drive and then boot from there. What would happen then is I would just get a blank screen with the cursor flashing. I have a Starling star1 model.

---

### Post by Dave_L on 2011-06-05
Can you post a screen shot of the Startup Disk Creator window?

---

### Post by flihi on 2011-06-06
> **Dave_L said:**
> Can you post a screen shot of the Startup Disk Creator window?
I finally got it to work. When I would transfer the image file from my download folder to my USB flash drive using Create Startup Disk, there is a Finalizing popup that shows the progress with an indicator that goes back and forth. This would just lockup and freeze so I would try to remove my USB flash drive from the file page where it gives me the option to Safely Remove Disk but I would get a message that says Cannot Remove Disk- Disk Disk Still Running or something like that so then I would have to restart my Starling and then erase my USB flash drive and transfer the image file to my USB flash drive again but the Finalizing popup would just keep freezing up. I did this a few times so then I booted from the USB flash drive from the boot menu at startup just to see what would happen and it took me through the Kubuntu 11.04 install instructions and my Starling seems to be working just fine. With Ubuntu 10.04 Remix my Starling star1 seems to have some strange bugs so I will give Kubuntu a try and see what happens but I am curious if any non Debian based distributions of Linux will work with System76 drivers on my Starling.

---

### Post by isantop on 2011-06-07
Make sure you click "Erase Disk" before you write the image. I've found you need to select either the partition (/dev/sdb1) or the entire disk (/dev/sdb) in order to make it work, but this issue was fixed in Natty, so I can't remember which it is. 

The driver app will only run on Ubuntu is its variants, like Kubuntu, Lubuntu, Edubuntu, etc.

---

