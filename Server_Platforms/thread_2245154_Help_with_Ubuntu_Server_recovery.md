---
title: "Help with Ubuntu Server recovery"
date: 2014-09-21
forum: Server Platforms
---

### Post by Marc-NJ on 2014-09-21
Not sure if anyone can help with this (or even if there is any recovery possible), but I had an Ubuntu server installed across several hard drives (I believe via LVM - is that correct?) on an old workstation and it experienced some sort of issue that fried the PSU.  I replaced the PSU with a new one, but it still won't start and is throwing up BIOS errors (and worse, the BIOS isn't even recognizing the hard drives attached).  Perhaps it's just an issue with the actual workstation hardware and not the HD's themselves - but how would I move those hard drives elsewhere in order to get the Ubuntu server booted again and get access to it?

Any help is greatly appreciated!  Thanks!

---

### Post by Michael_McKenney on 2014-09-22
You can download and install memtest86+ in Ubuntu and run it.  

Power supply fried.  I have seen them pass AC to the components and fry everything.  What BIOS errors?  I would try clearing the CMOS.  Unplug the computer.  Some boards have a jumper to clear the CMOS.  Take everything off the board and check for leaking capacitors or burnt connections.

---

### Post by Marc-NJ on 2014-09-23
Will definitely give this a shot, but is there any way I can pop out the hard drives and move to another system?  If so, how would I do this?  Thanks!

---

### Post by sandyd on 2014-09-24
> **Marc_Bressman said:**
> Will definitely give this a shot, but is there any way I can pop out the hard drives and move to another system?  If so, how would I do this?  Thanks!

Since Ubuntu uses UUIDs to detect partitions, moving the set of disks to a new system should be fine provided that ubuntu supports the hardware of the new system. You may have to configure some system-specific things such as network cards/etc

---

### Post by Michael_McKenney on 2014-09-24
You might be able to move them to another computer to test.  They should boot up same way unless fried.  Check the connections to them for burn marks.  Looks at the PCB board on the bottom for damage.

---

### Post by tgalati4 on 2014-09-25
True, some power supply failures can send damaging voltage and current to the motherboard.  Check the motherboard for bulging and leaking capacitors.  It's possible that a bad capacitor on the motherboard caused the PSU to fail and the new PSU can't supply enough current to overcome that.  So it's a round-and-round failure pattern that is not easy to diagnose without pulling everything apart and having working spare parts.  Some motherboards can be fixed if it is a simple capacitor problem.  Some can't.

I would build a new server (with 14.04 LTS) with newish hardware and then connect the drives and try to recover data that you can migrate over.  Just plug them in and do:

```
sudo fdisk -l
```

---

### Post by Marc-NJ on 2014-10-03
So for some reason I didn't get notifications about other replies on here and went ahead and did the following:

1) Purchased a Dell Dimension 2400 (previous system was a Dell Dimension 8100)
2) Attempted to connect the drives from the 8100 to the 2400

One of the drives was showing up as Unknown Device in the BIOS, but the other two seemed to be detected OK - unfortunately, as I think I previously mentioned, Ubuntu Server was installed using some sort of LVM spanning, so I need all the drives working in order to access my server and data I believe.

Because one drive wasn't being detected, but wasn't making any sort of "clicking" noises, I thought it might be the PCB and ordered a new one online.  New one arrived today, and I swapped them out.  Unfortunately, after swapping them out and plugging in power to the drive, I get nothing.  The drive doesn't even seem to spin up.  I swapped back the old PCB and plugged in power and it spins up and is definitely on.  I then used an IDE to USB cable to connect it to another computer (Win7) and while it obviously didn't show me any data, it did show up as healthy in disk management.  Plugging it back into the Dell Dimension 2400 still shows it as Unknown Device though.

Not sure what the next step would be to try and move forward on this?  I have another (extra) 500 GB IDE drive, and was thinking of using Clonezilla (if it will see the "bad" drive) and making an image, and then using that image to overwrite the extra 500 GB drive I have (which I believe would make it an exact replica) and then trying that extra 500 GB drive in my Dimension 2400 to see if it works - and if so then trying all 3 drives in there to see if I can get it started that way.  Does that make sense?  Should I try something else?

Any advice or help is greatly appreciated.  Thanks!

---

### Post by Marc-NJ on 2014-10-03
Spectacular - I upgraded the BIOS to the Dimension 2400 to the latest, plugged in the two good drives via IDE and the one "bad" drive via USB to IDE, and booted up and it works!  I had to update eth0 to eth1 to get networking working, but this is amazing.  I'm immediately going to back everything up, but I love Ubuntu!

Thanks everyone for your help - looks like I'm out of the woods here.

---

### Post by tgalati4 on 2014-10-03
When setting up a server, one needs to know exactly how the disk drives are laid out.  Servers require some expertise to set up, run, and recover.  Without knowing how you set up [LVM]("https://help.ubuntu.com/community/UbuntuDesktopLVM"), it would be difficult to offer any advice on how to recover.  Normally, you would take notes on what commands you used to set up the server, so that you would have a record to recreate the process during a disaster recovery.  Without those notes, recreating your previous environment would be non trivial.

As far as the unrecognized drive, it might just need formating (either low-level using the manufacturer's utility) or *gparted* to format it and recreate the partition table.  This of course, wipes any data on the disk and any chance of recovery.

If you think there are valid partitions on the drive, then try *testdisk*.  If *testdisk* can't recover the partitions, then try *photorec* to recover individual files.

(Disregard everything that I said.)

---

