---
title: "Server project with RAID10"
date: 2009-10-23
forum: Server Platforms
---

### Post by Naerymdan on 2009-10-23
Hi,

I just got myself a beast of a machine and am looking to build it up with RAID10.

Since there is no real hardware RAID on the motherboard, I opted for software RAID 10 (or 1+0).

The new Ubuntu 9.10 Server Edition gives the option of setting up RAID 10, which I choose.

From there, options are abundant:

I have 4 identical hard drives setup in RAID 10, which gives me 1 logical hard drive.

I then put a LVM on that logical disk, in which I then put a Ext4 main partition and a swap partition.

Since I heard about grub having problems with RAIDs, I setup my /boot on a micro usbkey conveniently plugged right in the motherboard.

My question are:

1 - Should I put the /boot in the main RAID LVM Ext4 partition, foregoing the need for the usb key?
2 - Should I fiddle around and remove the swap space from the RAID/LVM and have a swap partition on each of my disk outside the RAID? (and if so, how can I do that, the automatic partitionner didn't want to)
3 - Anything I should do differently? Filesystem? Something?

Here is the hardware:
1 x SUPERMICRO MBD-X8DTL-iF-O Dual LGA 1366 Intel 5500
2 x Intel Xeon E5504 Nehalem 2.0GHz LGA 1366 80W Quad-Core Server Processor
2 x Kingston 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 ECC Unbuffered Server Memory
4 x SAMSUNG EcoGreen F2 HD154UI 1.5TB SATA 3.0Gb/s 3.5"

---

### Post by ivicks on 2009-10-23
I would put the boot partition on the the main RAID. I have never used a micro usbkey to boot with.

Also I have heard there are issues with Ext4 filesystem that is why i still use Ext3 filesystem.

---

### Post by Naerymdan on 2009-10-23
Ah... but both Grub and LILO fail to install on the RAID array whe I tried after your reply.

Not much more luck with GRUB2 either. Maybe if I tried to not install it in the MRB?

---

