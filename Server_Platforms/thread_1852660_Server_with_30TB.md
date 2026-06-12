---
title: "Server with 30TB?"
date: 2011-09-30
forum: Server Platforms
---

### Post by huyt on 2011-09-30
Hi Everyone,
I would like to use Ubuntu to set up a small server on a desktop computer. Can you suggest what the smartest way would be to set up about 30TB of hd storage? It can be either external or internal harddrives...

Thanks!!!

---

### Post by judoka9999 on 2011-09-30
Are you sure you mean 30TB and not 30GB?

If you want 30TB of usable storage you should look into a SAN, it will be pricy though.

---

### Post by huyt on 2011-09-30
yes, i need TB. there are some external harddrives around in the 12TB range, but i am not sure if ubuntu supports the use of them

---

### Post by LinuxFan999 on 2011-09-30
> **huyt said:**
> yes, i need TB. there are some external harddrives around in the 12TB range, but i am not sure if ubuntu supports the use of them
Ubuntu should support them. If you want to use internal hard drives, you would need 10 3TB hard drives, or 15 2TB hard drives. Keep in mind that you can't boot from a 3TB hard drive without a 64bit OS and UEFI.

---

### Post by huyt on 2011-09-30
i was thinking of something like this:

[http://www.amazon.com/Buffalo-Technology-DriveStation-External-HD-QL12TU3R5/dp/B004Z9Y008/ref=sr_1_1?ie=UTF8&qid=1317415745&sr=8-1](http://www.amazon.com/Buffalo-Technology-DriveStation-External-HD-QL12TU3R5/dp/B004Z9Y008/ref=sr_1_1?ie=UTF8&qid=1317415745&sr=8-1)

---

### Post by cariboo on 2011-09-30
My server has 8 hard drives in it, I just added them as I needed them, there is one PATA connector with 2 drives connected, 4 SATA with another 4 drives connected, and I purchased an inexpensive raid card from ebay with an additional 4 SATA connectors, I'm using the addon raid card in [jbod]("http://en.wikipedia.org/wiki/Non-RAID_drive_architectures") mode.

Currently I have a total of 4TiB of storage from all the hard drives, but my plans are to upgrade to 8 2TiB drives in the near future.

---

### Post by rubylaser on 2011-10-01
Those are way overpriced for what you're getting IMO.  You'd want to get at least 13 3TB internal drives and mount them in case with a couple of HBAs (like the IBM m1015 with IT firmware).   These would let you do software RAID like mdadm or ZFS, but would be portable and much cheaper than a hardware RAID card.  13 disks would allow you RAID6 or RAIDZ2 (on ZFS) with 1 spare device.  And 13 Hitachi 3TB drives would be much cheaper than 3 of those Buffalo stations (and many times faster too)

(13) [Hitachi 3TB 5k3000]("http://www.bhphotovideo.com/c/product/764167-REG/Hitachi_0S03228_3TB_5K3000_Deskstar_3_5.html") $120/each $1,560
(2) [IBM m1015]("http://www.ebay.com/itm/IBM-ServerRAID-M1015-LSI-SAS9220-8i-8-Port-46M0861-/290615243408?pt=COMP_EN_Networking_Components&hash=item43aa04b290#ht_1556wt_914") $100/each $200
(1) [Supermicro X9SCM-F-O motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182253") $199
(1) [Xeon E3-1230 processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115083&cm_sp=Pers_InterAlsoBought-_-19-115-083_1_PM-_-13-182-253") $239
(2) [Kingston 8GB of RAM kits]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139262&Tpk=KVR1333D3E9S%2f8G") $79.99/each  $159.98
(1) [NORCO RPC-4020]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811219021") $299.99
(1) [Seasonic X650 PSU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817151088&Tpk=Seasonic%20X650") $179.99

TOTAL $2,838

Add a couple small disks for RAID1 for the OS, and you'll have one PC capable of a lot of storage for less than 3 of those Buffalo Drivestations. And, you're getting a VERY capable server to boot that can be used for other things like ESXi (you can use PCI passthrough to pass the IBM m1015's through to your file storage virtual machine).

You'd need to figure out what filesystem to use as EXT4 is limited to 16TB and I've had nothing but problems with XFS on bigger volumes.  I've switched our array at work over to Solaris 11 and I'm using ZFS+napp-it for my storage needs.

---

### Post by z61P on 2011-10-03
> **huyt said:**
> i was thinking of something like this:

[http://www.amazon.com/Buffalo-Technology-DriveStation-External-HD-QL12TU3R5/dp/B004Z9Y008/ref=sr_1_1?ie=UTF8&qid=1317415745&sr=8-1](http://www.amazon.com/Buffalo-Technology-DriveStation-External-HD-QL12TU3R5/dp/B004Z9Y008/ref=sr_1_1?ie=UTF8&qid=1317415745&sr=8-1)

Have you considered using something similar to the Buffalo unit that has an iSCSI interface?

---

### Post by rubylaser on 2011-10-03
> **z61P said:**
> Have you considered using something similar to the Buffalo unit that has an iSCSI interface?

Do you mean an ethernet port? ;)  Or are you thinking of fibrechannel?

---

### Post by Vegan on 2011-10-03
If you are looking for big storage, consider rack mounted servers

the old 4U chassis route with 16 drive bays can hold lots of hard disks but I suggest using enterprise grade disks

then there is the SSD chassis with their smaller form factor. Generally those are very expensive and not very generous in capacity.

30TB is not going to be cheap no matter how you slice and dice it.

---

