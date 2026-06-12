---
title: "ecryptfs swapfile-pagefile"
date: 2011-09-05
forum: Security
---

### Post by linis_australis on 2011-09-05
Greetings chaps, :D

I'm keen to use a swapfile for a USB install I'm doing. My problem is that my project requires encryption. It seems that ecryptfs recommends that I use a swap partition and dm-crypt - however dm-crypt doesn't pass TRIM information to the blockdevice (at least not by default as it's insecure to do so).

This means the USB won't be able to apply wear-level tech I think.

So I'm wondering firstly if it is possible to use ecryptfs on a swapfile/pagefile instead and secondly if it is possible what are the drawbacks?

tags:  ecryptfs,swapfile,wear leveling,usb,dm-crypt

---

### Post by DZ* on 2011-09-07
I don't know of a good way of making an ecryptfs swap file, but disabling trim doesn't disable wear leveling. With dm-crypt encrypted swap partition, the flash controller won't be notified how much within the swap is used, but that doesn't mean the content of the partition will be constantly stored in one (or continuous) place. I think that simply means for the controller that you've got a big chunk of data the size of the swap partition.

---

