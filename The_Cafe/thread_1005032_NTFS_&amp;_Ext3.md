---
title: "NTFS &amp; Ext3"
date: 2008-12-07
forum: The Cafe
---

### Post by Grant A. on 2008-12-07
I was thinking, why aren't NTFS and/or ext3 used on thumb drives? Wouldn't this stop that whole "safely unmount or your drive will be destroyed" thing?

---

### Post by KiwiNZ on 2008-12-07
ntfs is for windows only so unless you are prepared to pay royalties its not going to be widespread

---

### Post by bufsabre666 on 2008-12-07
theres nothing stopping you from formatting them like that (fire up gparted, it does work) but fat is prefered cause its got a small footprint ((more effective space)) and it is basically universal, as in every os reads it

---

### Post by snova on 2008-12-07
> **Grant A. said:**
> I was thinking, why aren't NTFS and/or ext3 used on thumb drives? Wouldn't this stop that whole "safely unmount or your drive will be destroyed" thing?

No. Choice of filesystem has little to do with it, it's always a bad idea to do that.

Besides, flash drives have a limited lifespan, and some filesystems will lower this more than others. I would suspect these two of that, though I'm no filesystem geek.

Not only that, but space economy- there's a reason you can't put NTFS on small devices.

And again, FAT is supported everywhere. I can't think of any other filesystem that has that kind of universality.

---

### Post by Polygon on 2008-12-07
the reason fat16/32 is used on usb keys:

1: its universal. Even though microsoft has the patents for it (i think they got to keep them, right?) fat16 can be read and written two by mac, linux and windows.

2: it mostly has to do with block size (or cluster size, i forget), since on drives, only one file can occupy a block/cluster/whatever....so if its too big,then small files that usually get put on usb keys would take an entire block/cluster, and waste that entire block, therefore wasting space.  

At least thats what one of my teachers told me, but its been 3 years =P

---

### Post by snova on 2008-12-07
> **Polygon said:**
> 1: its universal. Even though microsoft has the patents for it (i think they got to keep them, right?) fat16 can be read and written two by mac, linux and windows.

2: it mostly has to do with block size (or cluster size, i forget), since on drives, only one file can occupy a block/cluster/whatever....so if its too big,then small files that usually get put on usb keys would take an entire block/cluster, and waste that entire block, therefore wasting space.

1. I think they only apply to certain pieces, like FAT32 or whatever.

2. There's also the overhead of the filesystem itself, the way it is designed in the first place. FAT is very simple, lacks more advanced features, but in a way, is also free from them.

Ext3 keeps a journal in addition, which can't exactly help.

And you can change the block size, depending on the FS.

(I await the arrival of somebody knowledgable of the subject to prove me wrong. :p)

---

### Post by andamaru on 2008-12-07
Short Answer: 
Support by the most operating Systems (aka support by Windows)

Long Answer: 
it's the way fat stores files, it produces the least amount of writes. Most file systems move around files so they can be accessed faster (reduce fragmentation), Fat does not do this. Fragmentation isn't a problem on flash memory, so wasting write cycles moving around files is just a waste.

---

### Post by az on 2008-12-07
The limited number of write cycles to NAND devices is mostly irrelevant.  The cells are suppose to be cycled by the controller on the device to prevent the same cell from being written to to until all the other cells have had their turn.  When this is properly implemented, it would take years of continuous writing to use them up.

NTFS and Ext3 are not that much more protected from unsafe unmounts, but the recovery and cleanup following such an occurrence is a lot faster when you use a journal as do ext3 and NTFS.

The main reason why FAt 16 is prevalent in a lot of digital appliances is because it is easy to find a fat filesystem driver-on-a-chip.  You don't want to use CPU power which consumes more time and wattage than a separate component which will take care of the filesystem for you.  So the FAT filesystem driver is hardware-built-in.  This does not explain USB thumb drives, though.  As mentioned, the fat filesystem is the only filesystem that is ubiquitous on all modern operating systems.

---

