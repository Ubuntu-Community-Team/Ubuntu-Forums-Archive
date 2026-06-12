---
title: "Ubuntu Studio DVD non bootable"
date: 2012-12-14
forum: Ubuntu Studio
---

### Post by djftl on 2012-12-14
Hi guys,

I downloaded the Ubuntu Studio 12.10 iso torrent and burnt it on DVD. My bios is setup to boot from Cd/DVD drive first. When PC is attempting to boot it reads the Ubuntu Studio dvd and then the screen just remains blank with a blinking cursor on the upper left corner. It remains there indefinitely until I switch off the pc. 
I tried to boot from different pc systems nothing happens. I tried the wubi.exe in windows wubi doesn't execute.

I attempted a usb install using a bootable usb drive with unetbootin that is not success as well. Instead it brings me to a command prompt initramfs.

I tried on every pc and laptop both dvd and usb they do the same thing as above.

Now I'm testing the usb from a pc with an ECS G31T-M7 REV 1.0 motherboard.


Someone please help, I couldn't have downloaded 2 gig of Ubuntu Studio data for nothing.

Thanks for helpinh in advance.


DJFTL

---

### Post by jejeman on 2012-12-14
Well, since you downloaded ISO via torrent it should be ok. You can check again its md5 sum, but that should be ok since it's downloaded via torrent.

If you have active linux check md5 sum on burned DVD, to eleminate burning issues.

---

### Post by djftl on 2012-12-14
> **jejeman said:**
> Well, since you downloaded ISO via torrent it should be ok. You can check again its md5 sum, but that should be ok since it's downloaded via torrent.

If you have active linux check md5 sum on burned DVD, to eleminate burning issues.

Thanks for the reply, I have an active Linux but how do I check md5 sum? What are the necessary steps?

---

### Post by jejeman on 2012-12-14
Mount DVD
Open terminal
Go to DVD folder
Issue check command
```
md5sum -c md5sum.txt
```Check if I had written the name of the file correctly.

---

### Post by djftl on 2012-12-15
Thanks Jejeman,

I ran that command and terminal returned md5sum: md5sum.txt: no properly formatted MD5 checksum lines found. This is a real struggle.

Kind regards,

---

### Post by jejeman on 2012-12-15
I don't have 12.10 ISO at the moment, but in all this years of using Ubuntu Studio never had that message about md5sum.txt.
I guess, burn it again, but since USB is also not working, then maybe its corrupted ISO. Check the sum for ISO.

---

### Post by terrox on 2012-12-19
I have a similar problem, unable to boot Ubtuntu Sutdio on an old BIOS.

The DVD wont boot at all, just looks for boot record and eventually gives up and goes to next boot device.

Tried making bootable USB with UNetbootin but that wont load either.

DVD does boot on other computers.
Other Bootable CDs do work, so it might just be the DVD player on this machine is a bit faulty but that doesn't explain why I can't make a bootable USB with UnetBootIn.

I have other USB bootable sticks which work on my problematic machine, just not sure how to make a Bootable Ubuntu Studio disk. It just gets stuck after selecting an option from the list. No language selector pops up either because UnetBootin ignores that stuff, so maybe Ubuntu Studio expects some parameters and just wont work.

---

### Post by djftl on 2012-12-23
> **terrox said:**
> I have a similar problem, unable to boot Ubtuntu Sutdio on an old BIOS.

The DVD wont boot at all, just looks for boot record and eventually gives up and goes to next boot device.

Tried making bootable USB with UNetbootin but that wont load either.

DVD does boot on other computers.
Other Bootable CDs do work, so it might just be the DVD player on this machine is a bit faulty but that doesn't explain why I can't make a bootable USB with UnetBootIn.

I have other USB bootable sticks which work on my problematic machine, just not sure how to make a Bootable Ubuntu Studio disk. It just gets stuck after selecting an option from the list. No language selector pops up either because UnetBootin ignores that stuff, so maybe Ubuntu Studio expects some parameters and just wont work.

Terrox, I think Jejeman is correct to say this ISO might be corrupt. I tested even the wubi.exe on all different windows OS, it does not execute anything. This is an ISO I downloaded via torrent. How did you download yours Terrox?

---

### Post by Open and Sourced on 2012-12-23
Mount the CD to the terminal.

---

### Post by terrox on 2012-12-26
I downloaded mine from Torrent, I was going to say I've booted it from a laptop but I'm not sure that I have - I did boot 12.04.1 from laptop.

I've created at least two coasters from rewritable DVDs trying to get this working. Yes - re-writable coasters!! I dunno how that happened but those discs will not read at all so I can't seem to format them on two different DVD burners.

I think I just created my third rewritable coaster. Trying to format the disc after making a failed burn, "Failed to Erase Disc! - Reason: Session Fixation Error"

I just want a CD-ROM sized version of Ubuntu Studio so I can install it. Don't need all the Browser/Email stuff.

OR I'd like to burn the .iso to a USB and have it boot without any errors, I can't seem to do it in UNetBootIn

---

### Post by terrox on 2012-12-26
Try this.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Then install 12.10 to a USB.

Mine did not boot, but I was able to boot off a CD with PLOP bootmanager installed on it and then select USB boot from there.

My BIOS does support USB boot, but whatever is used in Bootable USB for 12.10 wont boot on my BIOS.

---

### Post by terrox on 2012-12-27
After all that I installed 12.04.1 and found it was slow (GUI and keyboard input feels laggy), so I thought it might be Graphics drivers and 11.04+ wasn't compatible with Geforce 4 MX 440. I stopped X server, disabled Nouveu, rebooted and installed NVidia 96 drivers (after Nvidia site gave me version 101 drivers which even aren't compatible).
Got the drivers installed, no difference, still slow.

Trying 10.04 now to see if it is responsive.

edit: was too hard to make a USB install for 10.04, 12.0.4.1 seems responsive now - not sure why, maybe it was USB WIFI that I have removed now.

---

### Post by djftl on 2012-12-28
> **terrox said:**
> Try this.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Then install 12.10 to a USB.

Mine did not boot, but I was able to boot off a CD with PLOP bootmanager installed on it and then select USB boot from there.

My BIOS does support USB boot, but whatever is used in Bootable USB for 12.10 wont boot on my BIOS.

Ok cool Terrox, I'll try that link and see what happens.

---

