---
title: "Windows can't detect partitioned HDD"
date: 2008-11-19
forum: Windows
---

### Post by Karilex on 2008-11-19
Hello I've been trying to dual boot windows xp with ubuntu (ubuntu installed first so i proceeded to partitioning my hard drive from the live cd unfortunately when i try installing windows i get a message telling me that i don't have any hard drives any explanations?

Thanks a lot :)

---

### Post by mentallaxative on 2008-11-19
Usually, people will install Windows first, then Ubuntu. Installing Windows after Ubuntu causes it to replace the master boot record with its own and possibly not recognise Ubuntu. The Ubuntu installer was specifically designed to accomodate for the existence of other operating systems, while Windows was not....

I'm sure someone will reply you soon with some *actual* advice, though.

---

### Post by Karilex on 2008-11-19
hmmm yes I should probably have installed windows first silly me so confusing ^^' well thanks for that anyway anyone know how i can correct my mistake?

---

### Post by Karilex on 2008-11-19
If not does anyone know of an open source OS that is a clone of windows but will still be able to easily dual boot?

Edit: I don't mean a clone just something that will be able to run all windows applications and drivers

---

### Post by kaldor on 2008-11-19
ReactOS is a Windows clone built ground up.. but it is not yet stable. Looks fun to fool around with though. :)

---

### Post by dptxp on 2008-11-19
install ubuntu again.

---

### Post by Karilex on 2008-11-19
> **dptxp said:**
> install ubuntu again.

Yes i have actually done that having messed up my hdd trying to dual boot i made my formated my hdd to ms dos but it still doesn't detect so i guess it's either my hdd which is damaged or my disk the second option probably being true since it is a bit scratched i'll try with another disk i'll keep you posted

---

### Post by psusi on 2008-11-20
Windows doesn't see the drive because you didn't give it the driver it needs.  You need to get the driver from your motherboard manufacturer and put it on a floppy and give it to the Windows installer.

---

### Post by Karilex on 2008-11-20
> **psusi said:**
> Windows doesn't see the drive because you didn't give it the driver it needs.  You need to get the driver from your motherboard manufacturer and put it on a floppy and give it to the Windows installer.

Ouch that hurts guess I'll do that thanks guys you were much more help on what turned out to be a windows issue than any microsoft staff could have been

---

### Post by Izek on 2008-11-20
> **psusi said:**
> Windows doesn't see the drive because you didn't give it the driver it needs.  You need to get the driver from your motherboard manufacturer and put it on a floppy and give it to the Windows installer.

Sometimes that isn't the case though, I've had issues where the windows CD wouldn't even say at the beginning of the HDD boot process "Press any key to boot from CD..." this was even with the CD being the first to boot. I found out the problem was the MBR that Ubuntu sets up on the harddrive. Not sure about now though. I know Vista usually handles the drives better in its CD than XP did.

---

### Post by the yawner on 2008-11-20
If you're only using 1 HDD then please note the nature of you partitions. Windows cannot detect logical partitions.

---

### Post by psusi on 2008-11-20
> **the yawner said:**
> If you're only using 1 HDD then please note the nature of you partitions. Windows cannot detect logical partitions.

It most certainly can.  And the issue is that it isn't seeing the drive at all, not with understanding what's on it.

---

### Post by tsali on 2008-11-20
You try fixmbr from the Windows disk recovery console:

```
fixmbr \Device\HardDisk0
```

You can also use a Live Linux CD (I prefer Knoppix) to use the dd tool to erase the MBR. Once the MBR is clear, the Windows installer should recognize the drive.

here is an example (EXAMPLE! You have to enter drive specific info)

```
dd if=/dev/zero of=/dev/sda bs=512 count=1

```

After you have cleared the disk, install Windows. Then defrag. Then install Ubuntu.

---

### Post by Karilex on 2008-11-21
> **tsali said:**
> You try fixmbr from the Windows disk recovery console:

```
fixmbr \Device\HardDisk0
```

You can also use a Live Linux CD (I prefer Knoppix) to use the dd tool to erase the MBR. Once the MBR is clear, the Windows installer should recognize the drive.

here is an example (EXAMPLE! You have to enter drive specific info)

```
dd if=/dev/zero of=/dev/sda bs=512 count=1

```

After you have cleared the disk, install Windows. Then defrag. Then install Ubuntu.

I already did this but it still doesn't detect i'll try with vista

---

### Post by ChrisRVComputers on 2008-11-21
hey it seems like no one know the answer to you question here , what exactly is the problem maybey i can help

---

### Post by K.Mandla on 2008-11-22
Moved to Windows Discussions.

---

### Post by Karilex on 2008-11-23
yes it was getting more of a windows issue than a ubuntu one

---

