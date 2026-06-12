---
title: "[SOLVED] external drive spining"
date: 2007-12-25
forum: System76 Support
---

### Post by ncappel1 on 2007-12-25
Hello, I just got a Western Digital passport 250 GB portable hard drive, and I have some questions:

1. The drive came out of the box with formatted with vfat. I know that ubuntu uses ext3 by default, does this make any functional difference in the drive, or should I reformat it?

2. On the right-click properties of the device it says that the total capacity of the drive is 238.8 GB, why the discrepancy?

3. when I unmount via right-click the icon goes away on the desktop, but if I remove the cable there is an awful spinning down sound, the same as if you remove it without unmounting first, and I know that's not good! any suggestions as to what I should do?

System76 gazelle performance. gazp3, running ubuntu 7.10

---

### Post by palintheus on 2007-12-26
If you plan to use the drive on any windows boxes you should use a file system that can be read by default for both Linux and windows.

the discrepancy in the advertised space and the actual space comes from the difference in how they determine a GB, 1000MB vs 1024MB ( [http://www.diskview.com/disk-size-discrepancy.htm](http://www.diskview.com/disk-size-discrepancy.htm) )

no clue on #3

---

### Post by Salpiche on 2007-12-26
just remember that with Vfat you can transfer files that are 4 GB or less, using ext3 or NTFS allows for larger file size transfer.

#3 no clue either

---

### Post by thomasaaron on 2007-12-26
I'm not sure about #3 either. Since it spins up AFTER unplugging it, I'm guessing it is not a behavior related to Ubuntu.

---

### Post by ncappel1 on 2007-12-26
I should clarify, the drive continues to spin after it has been unmounted, and not unplugged. After unplugging it, it stops spinning, but it sounds like it hasn't synced and powered down. there is no whirring when it isn't connected to the computer.

---

### Post by thomasaaron on 2007-12-26
I see.

How long does it spin? I know that if you just transferred a large amount of data, it will spin a bit while writing the data to the disk before unmounting. But that should stop after a little bit.

---

### Post by Salpiche on 2007-12-26
Have you tried waiting for a few minutes after unmount to unplug it? I usually wait for a minute or so before unplugging it from both the usb and power down.

---

### Post by ncappel1 on 2007-12-26
Ok, so after doing a little experimenting, I found out that it takes exactly 10 minutes for the drive to stop spinning, regardless of whether or not data was written to the device, and whether or not the device was unmounted.

---

### Post by asmiller-ke6seh on 2007-12-27
> **ncappel1 said:**
> Ok, so after doing a little experimenting, I found out that it takes exactly 10 minutes for the drive to stop spinning, regardless of whether or not data was written to the device, and whether or not the device was unmounted.

So, sounds like that's the way it's supposed to work, eh?

SO, just remember to UNMOUNT before unplugging, and everything should be okay.

---

### Post by thomasaaron on 2007-12-27
Check out the second and third posts on this thread:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3932241](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3932241)

It sounds like the problem might be fixable. Let me know us know if you need any help pursuing it further. There is another post here that *might* be related. I'm not sure yet.

[http://ubuntuforums.org/showthread.php?t=594796&highlight=hard+drive](http://ubuntuforums.org/showthread.php?t=594796&highlight=hard+drive)

---

### Post by 50words on 2007-12-27
I have a 160GB WD Passport (just a bit older is all), and I have the same problem, if it is a problem. This drive just seems to want to spin and spin.

I reformatted to NTFS, by the way. Then back to FAT, just to see if it made a difference, but it did not.

It makes it a rather inconvenient portable drive if you have to plan 10 minutes ahead to unplug it. Kind of defeats the purpose, especially if you are working on a laptop, as I am. I love the drive otherwise, but I wish there was a way around the endless spinning.

---

### Post by asmiller-ke6seh on 2007-12-28
Umm...

Thomas, those posts seem to refer to a different situation - where the HDD spins down frequently and parks the head (like, once every minute), causing excessive wear and likley decreased MTBF.

I lbelieve **ncappel1 **was asking if there was a way to make sure that his external HDD was properly synced and parked before disconnecting the USB (and powering down the external drive) to make sure there was no loss of data or damage to the drive.

So, **ncappel1**, inquiring minds want to know: do you hear the drive park and shut down when you disconnect the external HDD in Windows? If not, wouldn't you expect it to behave the same way in Ubuntu/Linux?

---

### Post by ncappel1 on 2007-12-29
After unmounting on Ubuntu, the drive continues to spin for 10 minutes.

on a macbook (no windows box to test) after unmounting the drive spins down immediately.

On both mac and Ubuntu the drive powerlight stays on after unmounting (I don't think this is a problem though)

edit: it seems that [this thread ]("http://ubuntuforums.org/showthread.php?t=451344") has some similar discussion, but for some reason I feel hesitant to try the scripts, the whole conversation is a bit over my head...

---

### Post by asmiller-ke6seh on 2007-12-29
ncappel1,

You might want to make this a bug report in LaunchPad - which will bring it to developers' attention so that maybe this spindown function can be built into Ubuntu in a future release. Include the reference to the other thread you found (and includ the BASH script - it looks like it will work) because if Ubuntu is REALLY gonna be "Linux for Human Beings" then this function for WD external USB drives should be built in.

---

### Post by ncappel1 on 2007-12-29
Ok, I tried the script in post 15, by clem-vangelis [(thread)]("http://ubuntuforums.org/showthread.php?t=451344"), put it in my nautilus scripts folder, and it works perfectly. I'll also file the bug report in launchpad, if it hasn't already been done.

edit: heres the bug report
[https://bugs.launchpad.net/ubuntu/+bug/179255](https://bugs.launchpad.net/ubuntu/+bug/179255)

---

