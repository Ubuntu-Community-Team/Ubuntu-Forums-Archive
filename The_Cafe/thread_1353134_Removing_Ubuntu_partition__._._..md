---
title: "Removing Ubuntu partition  . . ."
date: 2009-12-12
forum: The Cafe
---

### Post by orlandomike on 2009-12-12
We are getting a netbook for a friend (no cd drive) and i wanted to install Ubuntu on it along with the existing xp home. My question is, after it is partitioned with linux, if she decides she doesnt like it, can the linux partition be removed and ecover that partitioned space back to windowss since i know of no easy way to get windows back o there without a dvd drive.?

Any help on that?

---

### Post by kevCast on 2009-12-12
No.

---

### Post by NoaHall on 2009-12-12
> **kevCast said:**
> No.

Yes. If you boot using a USB drive, you can resize the partition, or there are some Windows applications which can do it.

---

### Post by orlandomike on 2009-12-12
the same usb boot used to install.... makes sense as long as your booted with the usb you should be able reconfigure the partitions .

---

### Post by Xbehave on 2009-12-12
Yes, livecd/liveusb will let you delete the ubuntu partition then resize the windows partition, the only thing that may be tricky is resizing the fat partition to fill the space while keeping the data, so look into that but im 90% sure it will be doable

---

### Post by koleoptero on 2009-12-12
Yes it can be done, I've done it a few times myself. If she decides she wants to remove it then you boot from the livecd or usb stick again, open partition manager and delete the linux partitions and resize the ntfs or fat32 partition to take up the whole drive.

There are risks in doing this so make sure you backup any files there might be in the hard drive.

Also you'll need a tool to delete grub2 from the master boot record (MBR). It can be done from the ubuntu livecd/usb stick but I don't recall exactly how, you'll have to google that. :)

---

### Post by Bölvaður on 2009-12-12
on the live cd you will find a program kalled gnome partition editor aka gparted.
you can delete the partitions from there and resize the windows partition over it (if it is vista I wouldnt do it though)
You can always replace the partitions with ntfs partition so instead of having 1 windows partitions you now have 2... that might be not too stupid if you are expecting hdd failure and dont want to risk loosing data from both partitions.


also in windows I remember there are programs you can buy to do this, I remember one from norton that was good, but it was also expensive.


if you have vista (that includes w7) then you are encouraged to resize the partitions from windows. It might take much more time or harder to get hold on applications to do it, but because of the filesystem they are using (with encryption) it can be hell.

---

