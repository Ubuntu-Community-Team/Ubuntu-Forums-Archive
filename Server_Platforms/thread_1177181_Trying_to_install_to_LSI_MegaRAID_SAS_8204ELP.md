---
title: "Trying to install to LSI MegaRAID SAS 8204ELP"
date: 2009-06-03
forum: Server Platforms
---

### Post by squeezebox_huf on 2009-06-03
Hi helpful folks! I have an Acer Altos G330Mk2 server and I want to put Ubuntu onto it, but am having trouble. The disk drive discovery is failing, telling me "No disk drive was detected", but in actual fact I have 2 Seagate 250GB drives in a mirror arrangement via the LSI MegaRAID SAS8204ELP controller and hot-plug backplane.

I have hunted through these forums (and googled generally) for several hours now, to no avail. It appears from the LSI website that they have rpm-packaged drivers for Redhat and SLES distros, and I have those same packages available from the resource driver CDrom, but I don't know enough about installation to get any further. (not sure if they'd be any use to me anyway!)

Does anybody know of a way to install onto these RAID cards? 

During my trials I have discovered that removing the raid card (and hot-plug backplane) and relying on the on-board raid also gives confusing results. Basically, the Ubuntu install process still sees 2 independent disks even if I use the motherboard RAID to mirror them! (still LSI RAID controller)

Thanks very much.
Hamish

---

### Post by bullgr on 2009-06-03
hi...
i has the same problem in a HP Proliant server...
the problem is that the raid controllers are not recognized from ubuntu.

and of course the drivers are in rpm format...

there are two solutions:
-use alias command to make deb packages from the rpm drives packages they comes with the cd. but i not suggest this!!! it's really unstable to do such thing in a production maschine.
-install red hat (like i do in HP Proliant)... sorry about this, please don't beat me...

i don't like these situation and we must complain to the companies to support deb packages for theyr products.

but until then, the best choise is to buy a dell maschine that supports ubuntu out of the box!!!

---

### Post by cainwong on 2010-08-08
Sounds similar to my previous case, this might help:
[http://ubuntuforums.org/showpost.php?p=9690768&postcount=7](http://ubuntuforums.org/showpost.php?p=9690768&postcount=7)

---

