---
title: "Serious Installation Problem"
date: 2009-09-30
forum: Ubuntu Moblin Remix
---

### Post by 1roxtar on 2009-09-30
I tried installing Ubuntu Moblin Remix Jaunty to my Acer Aspire One netbook and during the partition format stage, I got a "SERIOUS ERROR" message and my computer froze.  I unplugged my netbook and removed the battery to shut it off.  Now when I try to boot it back up, I get a solid black screen.  Only the power button comes on.  I read that the UMR tested well on the Aspire ONE.  Did I just murder my hard drive????

---

### Post by Mutt77 on 2009-10-02
Hopefully you were installing from an outside source (ISO, USB, etc..)
if not you may have corrupted all the MBR information. If GRUB was not installed properly then you won't get to any OS. 
Solution if you have a desktop or another machine, download and make a bootable USB partition. Then install from there.

---

### Post by 1roxtar on 2009-10-02
Yes, I was installing from a flash drive.  When I hit the power button, I can hear the fans spinning and the only light I have lit is the power button.  When I hit the power on, The battery light turns on then turns off and still a blank screen.  I will try your suggestion.  Thank you for your input.

---

### Post by DC^ on 2009-10-03
Try to install again ?

---

### Post by cimh on 2009-10-03
I had something similar trying to install moblin 2 to my eee a few days ago. both times I tried the program halted during the partition phase and kicked me out saying corrupted drives - The drives (ssds) were fine till moblin got hold of them - and of course no lasting damage done but I had to reinstall and format with ubuntu. 

I probably install a new distro twice a month and I have never seen anything like this. it just didnt seem to be able to handle a straight forward disk format. the usb was ok and ran fine in live mode. 

The only thought I had was perhaps it was upset by the ext4 disks - moblin install doesnt give you an ext4 option so perhaps it couldnt handle the exisiting drive?

I've seen one other person reporting the same thing.

cimh
901 karmic beta

---

### Post by linux_tech on 2009-10-04
You could also try the alternate install.

---

### Post by om26er on 2009-10-05
there is no problem i install live cd of UMR atleas once in two days and never got into this. try installing again and if it don't work download the beta again. fyi have been using ubuntu moblin remix for a month and have not got into this typo problem

---

### Post by 1roxtar on 2009-10-08
I figured it out!  Thank Goodness!!!  

I had to flash my BIOS using the (Macles) Acer Aspire One BIOS Recovery.

[http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html)

---

