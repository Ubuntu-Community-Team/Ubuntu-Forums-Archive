---
title: "old dell notebook issue..."
date: 2009-10-19
forum: The Cafe
---

### Post by hardyn on 2009-10-19
I have this older dell PM based notebook my GF's father gave me to try to fix.

notebook will not boot windows on the hard disk (i know he has done something strange with the install)

notebook will boot a 9.10 live disk just fine

notebook will not boot an XP install disk

im not worried about the hard disk, as that will just get figured out; but why will the machine do fine with a linux boot disk, but not the factory screened XP disk.  

"press any key to boot from CD..." ... then optical spins down and just sits.  This is the identical condition that is present with the non-booting primary hard disk.  after POST the machine hangs at a black screen.

Thanks for any help.

---

### Post by hal10000 on 2009-10-19
i suppose the XP disc is damaged.
Can you try to boot it on another pc?

---

### Post by hardyn on 2009-10-19
disk is good, fer sure fer sure.

---

### Post by xyphur on 2009-10-19
Try making a copy of the XP disc in another machine, burn at slowest speed, and boot from the resulting disc. It's rare, but media-drive incompatibility does happen.

---

### Post by hardyn on 2009-10-19
does that happen with factory pressed disks?  I would totally agree with you on burned disks.

---

### Post by xyphur on 2009-10-19
It can happen. Although, like I said, it's pretty rare. I've witnessed it twice myself, one of them was on a slim CD drive in a notebook, and the other was a regular old CDROM drive in some Pentium I worked on back in the day. Both were factory pressed CDs, and both CDs worked fine in other drives. I ended up having to swap out the drive for the duration of using said discs.

Who knows why it happens either. Perhaps firmware bug, or the media is just scratched in the right places to make the jitter correction go haywire and have the drive refuse any data being fed to it.

It's worth a shot... boot it up in another machine, and if it boots fine, use that drive to make an image, then burn that as slowly as you can to a quality CDR (I like inkjet printable ones with the thick coating, they're tough)

Best of luck, and let me know if it worked. :)

---

### Post by clonne4crw on 2009-10-19
I don't think the CD is the problem here. Now, with some laptops, the Windows XP CD doesn't have all the right drivers for the HDD controller, graphics, etc. This has been a problem for me in the past. Make sure that you don't need any special drivers before loading the Windows installer. If you can, use the CDs that are meant for the laptop model.

---

### Post by xyphur on 2009-10-19
I agree with your point about some laptop models (goes for newer desktops and mainboards too) having hard drive controllers that are simply too new to be supported by any drivers originally included on the Windows disc, but in this case, he says it doesn't even begin to load the windows installation wizard. It just sits there after he presses a key to boot from CD and does nothing after spinning the disc down. To me, that sounds like a disc the drive can't read (only reason to spin a disc down when attempting to read data from it is when jitter is too high, so the drive spins down in an attempt to correct the CRC failure and get good data.)

I still think that trying to rip & burn the original in a drive that can boot the disc in question is a potentially easy-fix to an otherwise more costly issue (replace drive, or replace disc)

---

