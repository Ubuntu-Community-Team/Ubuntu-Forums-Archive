---
title: "Experiance with SiI3114CTU (RC-209-EX) cards?"
date: 2008-11-25
forum: Server Platforms
---

### Post by McLogic on 2008-11-25
[LIST]
[*]Has anyone used this card?
[*]Does the driver support multiple cards?
[/LIST]


I have an old P4 that I'm trying to bring back into service as a network attached storage box. To add more drives, I have been looking at the PCI 4-port SATA Rosewill card that uses a Silicon Image chip (SiI3114CTU).

It appears that the chip works in Ubuntu. What I want to know is if I can use 2 cards to get a total of 8 ports. I'm not worried about speed, only about having it work. The PCI bus will slow the system down, but not as much as the 100/T network.

[http://www.rosewill.com/products/985/productDetail.htm](http://www.rosewill.com/products/985/productDetail.htm)

Newegg is selling it for $25:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816132013](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132013)

---

### Post by qx48 on 2011-01-11
It has been a while since the opening post, but I am looking for information on/ help with this card as well.

I have been using Ubuntu on and off for several years now and am looking to make the switch from Windows to Ubuntu permanently. 

The lack of support or drivers for this card in Ubuntu (or my knowledge thereof) is my primary setback at this point in time. I am not at the point where I'm ready to risk botching up a "mdadm" configuration for software RAID while all my data is on the drive, and I would like to keep the data intact if at all possible. 

I have a RAID 5 volume across 3x 500 GB Western Digital 5400rpm SATA drives that is formatted with NTFS. The card I'm using is also the Rosewill RC-209-EX with the SiI3114 chip just as in the original post. Since it's a PCI card, I can't perform any "hardware" RAID configuration from a pre-OS environment like the BIOS that I'm aware of. 

I attempted to install the SATARAID5 manager software (32-bit version, via Wine) from the CD that came with the card, but that just launches a white box in the middle of my screen that I can't get rid of without logging out and back in. 

I originally set up the array by installing the aforementioned software on my Windows 7 partition (which, like my Ubuntu 10.10 installation, is on a completely separate drive) and then using Windows Disk Management utility to create the RAID5 volume. 

Is there any way to mount this array in Ubuntu 10.10 without formatting or breaking the array? If not, would the software RAID option (with mdadm or similar utility) really be that much better than the pseudo-hardware-RAID offered by this card?

The system I'm working with has the following specs:

Intel DP45SG desktop board
Q6600 @ stock 2.4GHz
4GB DDR3 1333 MHz
500GB WD 7200rpm SATA (separate from array, dual booting Win7 x64 and Ubuntu 10.10 x64)
Additional 1.5TB Seagate 5200rpm SATA drive (also separate and on mobo controller)

Let me know if you need any more information from me.
Thank you in advance for any information that can be provided.

---

### Post by disabledaccount on 2011-01-11
Ubuntu (or rather linux kernel) has support for this chip.
SIL3114 is SATA controller equipped with fake-raid software. Array format AFAIN is supported by dmraid, at least you can try it. Nevertheless You should consider this solution as workaround, not for long-term usage.
Raid5 is a joke on this HW - mdadm is way better than every known bios-based piece of ***it
NTFS is not well supported under linux (low performance, lack of support for compressed folders, sometimes problems with permissions) - this is another reason for moving data to native linux FS - or to stay with windows.

How can you think that it would be possible to use windows version of array manager in wine? It is supposed to work with windows drivers, not kernel modules right? :)

---

### Post by qx48 on 2011-01-11
As far as the array manager with wine, I pretty much knew it wouldn't work. I'm not completely versed in the methods that the Linux kernel has in facilitating and communicating with the hardware layer, and the card said it supported Linux so I wanted to try everything I could think of before posting just to be safe. (even though it was the .exe version and hope for a miracle :))

Thanks for your information. I'll just have to decide between the two long term options you mentioned (mdadm with Ubuntu, or Windows). 

As far as a Linux FS, is there a better option than ext3 or ext4? I've been thinking of trying xfs but I'm not an expert in the differences between these types of file systems. 

Thanks

---

### Post by disabledaccount on 2011-01-11
> **qx48 said:**
> As far as a Linux FS, is there a better option than ext3 or ext4?Every FS behaves differently under different load conditions - so if You are looking for best solution then look for some performance tests. Generally Ext4 is optimal choice for most load profiles, although I expect that in near future BTRFS will "take the lead" :)

---

