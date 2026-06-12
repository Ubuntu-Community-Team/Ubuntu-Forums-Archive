---
title: "Install windows XP without a CD Drive"
date: 2008-07-22
forum: Windows
---

### Post by abhiroopb on 2008-07-22
So I bought a VERY low end PC for the family. Its a desktop and I decided not to buy a CD Drive to save money. Stupidly I forgot that a CD drive is required to install XP. Still even now I don't really want to spend money on a CD drive as it will go completely unused. No matter what it costs (even if it is 10-20 USD) I don't want to waste the money unless it is absolutely necessary.

I have a desktop with a AMD Semprom processor, shared graphics memory, 1gb ram, and a hitachi 320gb hd. Originally we used to use the hitachi as an external hard drive with an enclosure but now we've put it into the desktop. So I still have the enclosure.

I also have a brand new XP Home CD.

My question is how can I install XP onto the hitachi hard drive?

I thought I'd be able to install it by using my laptop. So I connected the hitachi externally and I ran the XP install CD. I got an error: something along the lines of Windows cannot install because the drive cannot be read, you may need to install SCSI drivers, etc. It was a VERY long message (filling the entire screen).

Any ideas? I don't care how I do it I just need XP installed on the hard drive which I can then use in the desktop.

Thanks a lot!

---

### Post by Joeb454 on 2008-07-23
Moved to Windows Discussions :)

---

### Post by insane_alien on 2008-07-23
swap one out from your own computer for a couple of hours.

---

### Post by rickyjones on 2008-07-23
Take the CD ROM from a different computer and use that. When you're finished put it back.

Another option is to copy the i386 folder onto the hard drive. Insert the hard drive into the new computer. Boot the system with a basic DOS floppy. Run C:\i386\winnt.exe.

Perform a network install (similar to above but the floppy needs to load a networkable version of DOS with the NIC drivers loaded)...

Best bet? Spare CD ROM drive...

-Richard

---

### Post by dca on 2008-07-23
If the 320gb HDD was a 3.5" IDE drive than you can pull a CD drive out and plug it into those connectors and edit BIOS to boot from USB.  If the 320gb HDD was a 2.5" SATA (like a laptops) than you're pretty much out of luck.  You would need to temp install a CD drive in your box.
 
You can PXE network install boot from Norton Ghost (images drives or install OS's over network) but that also is on CD media.
 
You can take what I told you above...  Go to the store and purchase an ext CD burner, install the OS and return the drive saying you don't like it???  Just make sure your BIOS allows to boot from USB...
 
Or you can take some of the advice in previous posts.  Find a USB thumbdrive that can fit (+1 GB) the entire OS and make sure if the HDD is SATA you have the necessary drivers because XP doesn't include, create a DOS boot floppy and point it to the thumbdrive as suggested provided the boot disk you made includes the drivers for USB & NIC, etc...

---

