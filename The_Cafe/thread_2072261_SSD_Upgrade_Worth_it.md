---
title: "SSD Upgrade Worth it?"
date: 2012-10-17
forum: The Cafe
---

### Post by mamamia88 on 2012-10-17
Using a netbook with ram already maxed out.  I'm using arch with xfce.   Do you think it's worth upgrading to an ssd?  I'm seeing a lot of cheap ones on sale lately.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
as long as you stick with a reliable manufacture intel/samsung/crutial are some good ones
though my corsair one is still working good, but i am using it in a very low write environment

a ssd will make booting and opening apps faster, it is NOT going to make adobe flash run better or get you more FPS in games (can make loading maps faster)
make sure your bios has AHCI support, you will need that for trim

---

### Post by rg4w on 2012-10-17
Personally, yes.  I put an SSD in my laptop, and now it's so quiet and fast I'm not sure I could ever go back to a spinning platter.

---

### Post by mamamia88 on 2012-10-17
> **rg4w said:**
> Personally, yes.  I put an SSD in my laptop, and now it's so quiet and fast I'm not sure I could ever go back to a spinning platter.

how about if i have to take the entire thing apart to change out the hd?   this is a netbook so it isn't as simple as unscrewing 1 screw and taking it out of a compartment on the back

---

### Post by szymon_g on 2012-10-17
I've upgraded to 256gb M4 fro Spinpoint F3 harddrive. to be honest- i haven't notice any difference in boot, maybe some programs run slightly faster.
from the other hand: things like changing a lot of small- to-medium size files (like mp3) is much faster than the HDD.

---

### Post by Mikeb85 on 2012-10-17
As a second hard drive, yes.  I don't think I'd want to sacrifice the reliability and size of my HDD...

---

### Post by pqwoerituytrueiwoq on 2012-10-17
well that is one of the fastest mechanical drives on the market
2.5" drives are slower than 3.5" drives
here is my laptop's hdd benchmarks
[[IMG]http://www.zimagez.com/miniature/screenshot-10172012-044026pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-10172012-044026pm.php")

---

### Post by rg4w on 2012-10-17
> **mamamia88 said:**
> how about if i have to take the entire thing apart to change out the hd?   this is a netbook so it isn't as simple as unscrewing 1 screw and taking it out of a compartment on the back
My Dell M101z has a lid on the bottom for easy access to the drive.  I've also completely taken other laptops apart, but I wouldn't recommend it unless you're comfortable doing so.

Also, I don't know exactly how much of a difference this has made for my speedup, but right after I swapped in the SSD I remapped /tmp to a RAM disk at /tmpfs.  If you have plenty of RAM (I rarely use more than half of mine) it can be a good option for a modest speed bump.  But as with hardware, if you're not comfortable modifying your fstab it may be better left alone; fstab is a key part of the system, and while I find it easy to work with, damaging it without a backup can make life complicated.

---

### Post by mamamia88 on 2012-10-19
> **rg4w said:**
> My Dell M101z has a lid on the bottom for easy access to the drive.  I've also completely taken other laptops apart, but I wouldn't recommend it unless you're comfortable doing so.

Also, I don't know exactly how much of a difference this has made for my speedup, but right after I swapped in the SSD I remapped /tmp to a RAM disk at /tmpfs.  If you have plenty of RAM (I rarely use more than half of mine) it can be a good option for a modest speed bump.  But as with hardware, if you're not comfortable modifying your fstab it may be better left alone; fstab is a key part of the system, and while I find it easy to work with, damaging it without a backup can make life complicated.
well i ordered one and then cancelled the order.  or at least tiger direct said they would atempt to stop shipment.  Honestly besides the bootup gains probably not worth it.   i have an extra laptop drive lying around in case this one ever breaks down on me.

---

