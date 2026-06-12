---
title: "Hard drive issue"
date: 2012-03-05
forum: The Cafe
---

### Post by grautskaahl on 2012-03-05
Hey guys! If this thread is hopelessly misplaced, please tell me - I couldn't find any specific forum/subforum for this...

My laptop hard drive has recently started removing folders on its own. It started with one or two less important folders that I could easily retrieve from backup, but today my *entire* 55gb music folder vanished, save for two subfolders within it. Disk usage tells me that the folder is still there, because the amount of space used on the drive is still the same. Is this some sign telling me that my computer is getting really old? Because I've only had it for two and a half years. I'm using a Dell Inspiron 1545 with a Ubuntu 10.10/Vista dual-boot.

Appreciate any input! :)

---

### Post by MG&amp;TL on 2012-03-05
Old hard disks do, unfortunately, die-this is a possible reason for randomly missing folders. You can see if yours is on its last legs by going to the disk utility program and running the SMART tests.

---

### Post by grautskaahl on 2012-03-05
The SMART test currently tells me the drive has 1  bad sector, but otherwise it looks fine. Anything specific I should look for?

---

### Post by MG&amp;TL on 2012-03-05
Not a hard disk expert. I think if there is nothing "bad" showing up, your disk is probably fine and we can move on.

---

### Post by miegiel on 2012-03-05
Bad sectors are bad news :( you'll need to replace the disk. Bad sectors are a sign of a failing disk or a disk that's damaged (physically).

But [COLOR="Red"]**DON'T PANIC**[/COLOR]

With fsck (file system check) you can check your disk for errors and bad sectors. And you can block bad sectors from being used so you won't loose data till you get a new disk. With a bit of luck fsck can save the music.

See [http://manpages.ubuntu.com/manpages/maverick/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/fsck.8.html)

If you run fsck from a ubuntu liveCD it's easier to check partitions that would be mounted if you boot from your disk.

---

### Post by CharlesA on 2012-03-05
> **miegiel said:**
> Bad sectors are bad news :( you'll need to replace the disk. Bad sectors are a sign of a failing disk or a disk that's damaged (physically).

But [COLOR="Red"]**DON'T PANIC**[/COLOR]

With fsck (file system check) you can check your disk for errors and bad sectors. And you can block bad sectors from being used so you won't loose data till you get a new disk. With a bit of luck fsck can save the music.

See [http://manpages.ubuntu.com/manpages/maverick/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/fsck.8.html)

If you run fsck from a ubuntu liveCD it's easier to check partitions that would be mounted if you boot from your disk.
+1, Most, if not all drives have spare sectors on them. I've got a couple drives that have a few bad sectors but the count hasn't gone up in a long time (about a year or more) so I just leave them.

But as always, have a good backup of anything you deem important. :)

---

### Post by mips on 2012-03-06
> **miegiel said:**
> Bad sectors are bad news :( you'll need to replace the disk. Bad sectors are a sign of a failing disk or a disk that's damaged (physically).

A few bad sectors are not the end of the world as long as the bad sector count does not keep on increasing. Bad sectors will be reallocated to spare space on a drive and the bad ones marked so they don;t get used again.

If the bad sector count keeps on climbing then replace the drive!

---

### Post by grautskaahl on 2012-03-08
The number of bad sectors doesn't seem to increase, but I think I'll invest in a new hard drive soon. I've never done this before - is it in any way more complicated than Youtube makes it look like?

---

### Post by miegiel on 2012-03-08
> **grautskaahl said:**
> The number of bad sectors doesn't seem to increase, but I think I'll invest in a new hard drive soon. I've never done this before - is it in any way more complicated than Youtube makes it look like?

A piece of cake by the looks of it. Easier than my laptop.

Make sure the new drive isn't thicker than the current drive. Some models are thicker or thinner because they have more or less platters inside. And make sure you have the right size screwdrivers (PH1, PH0, PH00 and/or PH000).

---

### Post by grautskaahl on 2012-03-10
Thanks! Are there any compatibility issues I should be aware of with regards to hard drive brands and such?

---

### Post by miegiel on 2012-03-10
> **grautskaahl said:**
> Thanks! Are there any compatibility issues I should be aware of with regards to hard drive brands and such?

All disks are built according to standard specifications regarding width, length, mounting (screw) holes and power and data plugs. The only thing you need to consider is the thickness (height) of the drive. I don't know your laptop, but some thin laptops only have room for thinner 2-platter (the number of disks inside) drives.

On the disk manufacturer's site you should be able to find the exact dimensions if you want to verify before ordering.

---

### Post by MisterGaribaldi on 2012-03-10
You might want to invest in a SATA/IDE-to-USB adapter. Usually they're about $20-$30 and will let you hook up HDDs quickly without the need to buy an enclosure. I have one (got it through TigerDirect) and it has proved invaluable for both myself and friends who've gotten into tight scrapes.

This is the one I've got: [http://m.tigerdirect.com/aHR0cDovL3d3dy50aWdlcmRpcmVjdC5jb20vYXBwbGljYXRpb25zL1NlYXJjaFRvb2xzL2l0ZW0tZGV0YWlscy5hc3A/RWRwTm89MjMyOTMwMCZDYXRJZD0zNzcw](http://m.tigerdirect.com/aHR0cDovL3d3dy50aWdlcmRpcmVjdC5jb20vYXBwbGljYXRpb25zL1NlYXJjaFRvb2xzL2l0ZW0tZGV0YWlscy5hc3A/RWRwTm89MjMyOTMwMCZDYXRJZD0zNzcw)

---

