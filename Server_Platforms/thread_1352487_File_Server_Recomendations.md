---
title: "File Server Recomendations"
date: 2009-12-11
forum: Server Platforms
---

### Post by ricochet on 2009-12-11
I need to setup a large file server for video editing.  Needs to connect to 2-5 windows machines, 30TB+ in raid, simple web interface, and easy for novice to replace a HDD after failure.

What problems can you foresee?  What raid level would you recommend? Any hardware you recommend for this task?

Thanks
Richie

---

### Post by JonRohan on 2009-12-11
That is a lot of storage and probably won't be able to go on one server. The RAID level will depend on what kind of performance you require. A big RAID5 array will be quite a bit slower than an equivalent RAID10 array. The RAID10 array will require many more disks to get to 30TB.

A HP MSA60 is capable of 12 TB but its going to set you back over 10k. That's with SATA drives too. :o 12x1TB SATA drives, that's considered a fairly cheap base spec storage array.

Either way to do 30TB correctly you'll be looking for some form of storage array or SAN. Its going to cost.

---

### Post by munky99999 on 2009-12-11
3ware is one of the bigger names in raid cards.

[http://www.3ware.com/products/serial_ata2-9650.asp](http://www.3ware.com/products/serial_ata2-9650.asp)

9650SE-16ML

2 of those. So you have 32 ports worth. You want sata as sas is usually high performance and not volume.

Raid 6: That means you lose 2 drives worth of space.

But it's best if you split those apart on computers. You dont want all your eggs in one computer case ready for them to be crushed.

Get 2 computers which are identical.

Raid 5 lets 1 drive die.
Raid 6 lets 2 drives die. Before loss of data.

Well basically for the computer itself. You basically need 1x Pci-e 1x slot. The rest is more or less your choice. Or 2 of those slots if you want to make it 1 shared folder.


And on top of all that.


[http://kingwin.com/products/cate/mobile/racks/kf_4000_bk.asp](http://kingwin.com/products/cate/mobile/racks/kf_4000_bk.asp)

So 8 of those.


The hard drives you use. You should aim for 

Western Digital Caviar Green 2TB SATA 32MB Cache 3.5IN Hard Drive

So yes. You could survive 30 tb of space using 16 drives. That second computer is fault tolerance. Yes you could scale it back to only 1 computer with 16 drives. 1 raid card. Etc Etc. However there's loads of just 1 thing involved here. Which means lots of single points of failure can make your day a bad one.


Finally you want probably a 2U or 3U rack case. Also depending on the case you buy. You could altogether eliminate the need for the above mobile hard drive racks.

---

### Post by Vegan on 2009-12-12
I have seen some 24 port adapters for PCI express. 2 such cards could supply a 50 disk 8U chassis with 100TB of storage.

---

### Post by Cheesemill on 2009-12-12
I'm not sure what the maximum capacity or hardware requirements of [FreeNAS ]("http://www.freenas.org/")are but it has a good WebUI.

---

