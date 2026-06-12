---
title: "Resize Partition NTSF"
date: 2007-06-10
forum: Windows
---

### Post by lsutiger on 2007-06-10
I have a windoze Media Center that I run, well, my media center with. The problem si that I accidentally sized my music partition to large and I would like to reclaim that space and add it to my video partition. I made it 160 gb vs the 60 I wanted.
I have a linux boot cd that will mount ntfs drives ( It is used to do registry hacks and password resets, etc). Can I use this cd and use a linux program to resize this partition w/o loosing the data on either drive?
If so, how please.
Thanx in advance!

---

### Post by FuturePilot on 2007-06-10
Easiest way.
Download the Gparted live CD
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php") 
Burn it to a CD and boot it.
Once in Gparted all you have to do is click Move/Resize and resize the 160GB partition to 60GB. Then go over to the other partition click Move/Resize again and make it take up the rest of the space. Then click apply and let it do it's thing. After it's done reboot and you should be good. 
If you get a thing about CHkDSK DO NOT cancel it. If by any chance there were any errors during the resize it will fix them.

---

### Post by lsutiger on 2007-07-08
Thanx, but I hit a wall. I resized down my 160gb partition to 60. So now I have one partition of 300GB, on partition of 60gb and 107gb of unallocated space. But gparted will not allow me to merge the unallocated space with the 300GB partition. When I choose Resize/Move it gives me a maximum of 300 gb. What could be the problem here (or solution)
(The live cd freezes up me mouse, so I am usin keyboard only)

---

### Post by smoker on 2007-07-08
hi, are you using the 'gparted live-cd' or a ubuntu live-cd, also is your unallocated space and the partition you want to resize next to eachother?

---

### Post by lsutiger on 2007-07-08
AH! See your point! No the partitions were not 'next' to each other. Thanx for the input! resize the 'middle' partition with leading space....
And using gparted-live

---

### Post by smoker on 2007-07-08
yes, sometimes you have to shift partitions about to get the free space next to the one you want to expand!

best of luck

---

