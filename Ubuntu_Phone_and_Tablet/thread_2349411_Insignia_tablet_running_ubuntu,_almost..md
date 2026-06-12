---
title: "Insignia tablet running ubuntu, almost."
date: 2017-01-14
forum: Ubuntu Phone and Tablet
---

### Post by joefunsch on 2017-01-14
I got my Insignia Windows10 tablet finally to boot and install Ubuntu  16.04LTS but it won't boot without the modified Ubuntu 16.04 Live USB  stick where I have added bootai32.efi to /boot/efi folder.

I'm on  it now with this post, but of course running from the Live USB stick.   My question is how do I move the bootai32.efi file to the internal drive  of the Insignia tablet?

I'm so close, but still not quite there.  Any help someone may have would be great.  

Thank you in advanced,

JoeF

---

### Post by krusty8 on 2017-01-16
What does the partitioning of the disk look like? What does mount say, what does parted print say?  

NB I'm just guessing in the dark here. If someone with some actual knowledge about this tablet shows up I'm gonna shut up :)

---

### Post by joefunsch on 2017-01-16
Well, woo hoo comes to mind.  not exactly sure what I did, but it seems to be working...

So to go on:   during the install from a Ubuntu Live 16.04LTS USB stick; I installed using the entire disk space (which this tablet sees as an SD Card of 32GB in size.
It totally erased the "sdd" and repartitioned the disk to 537 Part.1 FAT,29Gb Ext4 /,and 2.1Gb swap.
On the USB stick, I did copy bootai32.efi to the efi/boot folder to start with as that is the only way I could get the tablet to boot at all.  Part of that UEFI boot thingy....

Anyways, I also had to buy a USB to Ethernet adapter as Ubuntu wouldn't see the tablets WiFi adapter (yet).  Normal issue there; probably have to update 3rd part drivers and that hopefully will come around.

it took "forever" to install and seemed to be locked up. I started the install process at 8pm and by 8:30 it was 80% done with the "installing files" portion.  At 2AM it was still at the same exact point!! I left it alone this time.  Other times when it "lockedup" at this time, I would power off the unit and complain a bit. Ok a lot...  This time I just let it burn "quietly hoping it would actually burn".  When I got up at 6:30AM, it was still at the same exact point.  Now I shut it off and left it.

Tonight, I powered it up to see if I could make any new progress expecting to boot from the USB stick again.  This time, it asked me to login???   Live USB's/CD's don't ask to login.  Something new!!  I logged in and it is or seems to be running Ubuntu just fine.  I am still running on USB/Ethernet and I went in and enabled 3rd party vendors.  I am in process of downloading all the new updates now that 3rd party is on. Hopefully that will take care of the wifi.

If this continues to work, I will continue this post and give more details as to what system settings are and how it is working.  This is surprising to me as I was having a problem getting it to boot on the internal drive itself.  no problems running from USB, but internal was an issue.  Maybe letting it "stew" with the internet plugged in, got it.

Thanks krusty8 for the reply and I do understand that if someone doesn't know about a specific device, they won't post. At least you tried; so thank you.

Regards,

---

### Post by joefunsch on 2017-01-16
;(  short lived!!  the updates I ran I was just talking about broke it.  Now it boots "grub rescue>" only.  "error: file '/boot/grub/i386-efi/normal.mod"

arrrrrg.   Ok, so there has got to be a way to now fix this issue.  

I go in to cmos and at least now ubuntu comes up as a bootable option (however it don't work) as well as the USB stick.  So I believe I should be able to move the bootai32.efi file to the boot internal and hopefully that fixes that.  I'll be back......

---

### Post by Jon_Thomas on 2017-01-18
Wow, this is a great thread.  I picked up the same tablet just after Christmas.  I have 16.10 Ubuntu Unity installed and running from a USB drive.  Currently it will boot, update, and even run _Unity 8 _from the USB drive!  It saw the WiFi card from the start when I booted from the Live USB.  It took a LONG time for it to install running through the keyboard USB 2 ports.

The weird part is the three things that don't work presently.  The touch and screen rotation I didn't expect to work to begin with,  but what is strange is it will NOT see the battery at all.  Tried installing acpi, tried a few hardware info programs, won't show up at all.

The interesting portion is one of the hardware info programs was showing the system structure, and showed 2! memory DIMM slots on the mother board, one of which was in use with the current 2Gb of system RAM.  Makes me tempted to open it up and see exactly where that socket is and if a person could add another chip of the same make to boost it to 4Gb...hmmmm?

Either way, keep posting on your progress.  It took me a couple tries to get my Linux system on the USB stick.  Went that route as I am using the Windows install for work.  I also have Phoenix OS installed on the main hard drive, so you could say I have a $200 triple-boot system.  Looking to upgrade my USB stick to a USB 3 or even a USB-C stick for better read/writes.  Still pretty slow even plugging the current stick into the USB-C port via OTG dongle.

Now just need to look into touch screens and the battery issue.

---

### Post by Jon_Thomas on 2017-01-19
Quick update.  Just to see that is wasn't a one-off instance, I was able to install Ubuntu Mate 16.10 to another USB drive. It is updating and running good right now. 

So I would recommend trying the 16.10 Ubuntu releases, as the 16.04 versions have issues with the EFI bootloader installation.  I think it comes down to the 16.10 having the grub-efi32 package available in the image where the 16.04 releases do not.

---

### Post by joefunsch on 2017-02-12
Ok.  thought I would post.... gave up.  Insignia tablet has too many issues trying to do this.  I reinstalled Windows.  done.

---

