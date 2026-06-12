---
title: "Ubuntu 8.10 - can U install it on a ide&gt;sd card?"
date: 2008-11-27
forum: Server Platforms
---

### Post by slewis1972 on 2008-11-27
Hi All

Is it possible to install ubuntu server 8.10 on a sd card thats in a idea>sd card adaptor.

If so how as my current installation fails on partioning a 8gb HC SD card.

It finds it ok and I set the partioning, yet just fails on the partioning. And triple checked the lock was not on.

Any ideas?

Scott

---

### Post by Krupski on 2008-11-27
> **slewis1972 said:**
> Hi All

Is it possible to install ubuntu server 8.10 on a sd card thats in a idea>sd card adaptor.

If so how as my current installation fails on partioning a 8gb HC SD card.

It finds it ok and I set the partioning, yet just fails on the partioning. And triple checked the lock was not on.

Any ideas?

Scott

Partitioning of an SD card (or a CF card) will fail if the card is already formatted. Specifically, it will not allow you to "create a new blank space" on the card.

The solution is to zero out the device (or at least the partition table).

In Windows, you can use WinImage [([COLOR="Red"]**_LINK_**[/COLOR]]("http://www.winimage.com/download.htm")) and just write a NULL file to the card.

Or (easier), boot up Linux from a live CD, insert your SD card into a card reader, find out what it's name is:

```

sudo ls -laF /dev/sd*

```

Then, use "dd" to fill the SD card with zeros.

[COLOR="Red"]**ASSUMING**[/COLOR] that your card is "/dev/sdc", you would do this:

```

[COLOR="Red"][B]
# WARNING - EXAMPLE ONLY - DO NOT EXECUTE
# UNTIL YOU HAVE READ AND UNDERSTOOD THIS
# ENTIRE POST! A MISTAKE WILL ERASE DATA
# THAT CANNOT BE RECOVERED!
[/B][/COLOR]

sudo dd if=/dev/zero of=/dev/sdc bs=32K


```

Again, be 100% sure you know the drive name. In fact, do the "ls -laF /dev/sd*" command before you plug in the SD card, then do it again after you plug it in and see what NEW name pops up.

Once the "dd" command has filled the SD card with zeros, you will be able to go and install Linux onto it and the manual partitioner will give you no trouble.

Good luck!

-- Roger

---

### Post by slewis1972 on 2008-11-28
ok - tried that.

I did a basic setup

/boot
/
/swap

it failed to setup the swap. So I deleted it and did a basic install to see if I fails any further.

Is there a way to create the partition for swap once its up. I left 2gb spare just in case. I will be using webmin.

Thanks

Scott

---

### Post by slewis1972 on 2008-11-28
ok - looks like its failing even if I mix and match the partions, not just on the swap partition.

Any ideas if I pre-partion the sd card whether I can auto install it without going through the partition setup?

Any advice appreciated.

Scott

---

### Post by Philio on 2008-11-29
Yes you can, if the partitions are already there you can simply select manual partitioning and just set the mount points you want for the existing partitions :)

---

### Post by Krupski on 2008-11-29
> **slewis1972 said:**
> ok - tried that.

I did a basic setup

/boot
/
/swap

it failed to setup the swap. So I deleted it and did a basic install to see if I fails any further.

Is there a way to create the partition for swap once its up. I left 2gb spare just in case. I will be using webmin.

Thanks

Scott

OK, here's what I do (with a 4GB card).

* Boot the install CD
* Select MANUAL partitioning
* Select the flash card and hit enter. It will ask you if you want to "create a new blank partition table". Do it.
* Select "create partition". Set the mount point to "/", set it to "bootable" and select it's type as "EXT3" and select it's size (2000 MB).
* Then, create another partition (same size). Select it's type as "SWAP".
* Allow the install to write the changes to the flash card.
* Finish the install as normal.

Should work.

-- Roger

---

