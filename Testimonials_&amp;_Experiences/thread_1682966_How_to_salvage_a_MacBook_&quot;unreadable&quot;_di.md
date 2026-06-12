---
title: "How to salvage a MacBook &quot;unreadable&quot; disk...."
date: 2011-02-06
forum: Testimonials &amp; Experiences
---

### Post by knuthf on 2011-02-06
My son came home with a MacBook that was crashed, as usually, just days before he was to deliver his paper, it collapsed and Apple support told him that there was no hope - the disk was gone.
So, we made a swap - he came home for a long weekend and got a brand new MacBook and I was stuck with the old.

Its a long time since I worked with computers, but it seems like old things are still there. So, I burned a new image of the latest Ubuntu, and gradually I "saw" more and more of the lost disk.

I downloaded and installed MacOS "hfs" support. I then scan the SMART buffers to commit all outstanding writes - using "Disk Utility" - which is very similar to the "Disk Utility" on the MaxOS disk ("Snow leopard"). 

Then these is a flag in the "df" command, where you can dump all uncommitted buffers / copies of the superblock, and use an "old" copy of the superblock. "Old" is a few seconds before the last write - so not much is lost. 

Once this is in place, there is the "Disk Usage Analyzer" application. This will scan the disk and try to figure out where the different files should be in the hierarchy. This is very thourough, and just for the purpose of making a fancy chart, links in lost file fragments.

After this had done its reconstruction, I mounted a USB disk and made a complete backup "/User" - files, and recovered 20GB of music and my son's documents, including his paper - well it did not go that fast, but its all on the drive now.

I also found that there is a bug in MacOS, causing the users to loose disk space. Boot from OS disk, choose "Disk Utility" in the startup, and "Repair" the file system. 

SATA diagnostics of my son's disk revealed that it needed to be replaced. The same with the battery. 

With a Ubuntu CD, you have the best tool to repair a Mac that has lost its disk. 

Anyone with similar experience: describe the options you used to regenerate the file system (fsck and df).

---

