---
title: "Problem with drive assign in Windows XP"
date: 2008-12-28
forum: Windows
---

### Post by andy_blah on 2008-12-28
I've been having some problems with NTFS's "smart" way of assigning drive letters dynamically. I have two HDD: one of 40GB, where I have three partitions, on the first one is Windows, on the second is Ubuntu's drive, and on the third, a 1GB swap partitions, and the second HDD is of 80GB where I keep my general data. I want the first partition on the first HDD to be set as C: and the second HDD partion to be set as D:, but when I reinstall windows, the second HDD partition always jumps to C:, so when Windows is installed, the partition jumps to D:. Is there any way to work around this issue?

---

### Post by tsali on 2008-12-28
> **andy_blah said:**
> I've been having some problems with NTFS's "smart" way of assigning drive letters dynamically. I have two HDD: one of 40GB, where I have three partitions, on the first one is Windows, on the second is Ubuntu's drive, and on the third, a 1GB swap partitions, and the second HDD is of 80GB where I keep my general data. I want the first partition on the first HDD to be set as C: and the second HDD partion to be set as D:, but when I reinstall windows, the second HDD partition always jumps to C:, so when Windows is installed, the partition jumps to D:. Is there any way to work around this issue?

Having trouble understanding your problem.

Why is it an issue WHAT drive it assigns?

If you install Windows on hd0,0 - that becomes C: no matter what you do, It's the Windows startup disk. 

Ubuntu is installed in hd0,1 with swap on hd0,2 . How are you getting Windows to mount an Ubuntu install or swap partition at all? I didn't think Windows could read ext3 reliably and certainly not detect and mount them without help.

I would think the ONLY thing on hd0 that it would be reading would be the Windows partition - C:

Assuming this is the case, I think you can use Windows admin tools to format your second drive (hd1) and assign drive letters to it as you want. Try that. It won't let you fool with the Windows C: drive though.

---

### Post by andy_blah on 2008-12-28
> **tsali said:**
> 
Why is it an issue WHAT drive it assigns?

It is an issues because all the paths in the programs I use are messed up, and everything stops working properly

> **tsali said:**
> If you install Windows on hd 0,0 - that becomes C: no matter what you do, It's the Windows startup disk. 

In my case, it doesn't, that's why I'm asking for help here

> **tsali said:**
> Ubuntu is installed in hd 0,1 . How are you getting Windows to mount an Ubuntu install partition at all? I didn't think Windows could read ext3 reliably. 

At the moment:
C: = hd 1,0 -> My general data HDD/partition
D: = hd 0,1 -> Windows's partition

And I want them to be:
C: = hd 0,1 -> Windows's partition
D: = hd 1,0 -> My general data HDD/partition

I didn't said that I wanted to mount Ubuntu, or that I have it mounted

> **tsali said:**
> In any case, I think you can use Windows admin tools to format partitions and assign drive letters to them. Try that. It won't let you fool with the Windows C: drive though.

It doesn't let me "fool" with neither the current C: or D: drive

---

### Post by tsali on 2008-12-28
Strange.

Do you have data on you second hard disk that you can do without? Which drive has the Windows bootloader? Did yu have Windows previously installed on the other drive?

My next suggestion would be to wipe the second drive completely (delete the partition in Windows), then reboot and see if you have the same issue.

---

### Post by tsali on 2008-12-28
For some reason, Windows considers your second hard disk to be the first primary partition it encounters on boot.

Which drive has the Windows bootloader? Which drive is set to boot first in BIOS?

---

### Post by andy_blah on 2008-12-28
The data on the 2nd HDD is quite important, so an partition format/delete is out of the question. Both drives seem to have the boot.ini file in the root if that's what you mean. Other drive as in hd 1,0?

I think this happened while re-installed Windows, had to delete the Windows partition and create it again, in that time, the partition from the second HDD (hd 1,1) got up in front of the Windows partition, thus becoming letter C:. Tried to hide hd 1,1 in Partition Magic, but without sucess (the option for partition hide was grayed out)

---

### Post by andy_blah on 2008-12-28
Seems that I've made a mistake. The partition table is as follows:

hd 0,1: My general data partition
hd 0,2: Ubuntu partition
hd 0,3: Swap partition
hd 1,0: Windows partition

Could it be this the cause of the problem? If so then how do I fix it?

---

### Post by tsali on 2008-12-28
> **andy_blah said:**
> Seems that I've made a mistake. The partition table is as follows:

hd 0,1: My general data partition
hd 0,2: Ubuntu partition
hd 0,3: Swap partition
hd 1,0: Windows partition

Could it be this the cause of the problem? If so then how do I fix it?

Set BIOS to boot the drive with Windows FIRST.

---

### Post by andy_blah on 2008-12-28
It is set that way, otherwise GRUB wouldn't load.

---

### Post by tsali on 2008-12-28
> **andy_blah said:**
> It is set that way, otherwise GRUB wouldn't load.

Not necessarily. Do you know which drive has grub in the MBR?

I am running a clean Vista install on sda (SATA2 in BIOS). I installed Ubuntu on sdb (SATA3 in BIOS) and directed it to install grub to the MBR of sdb. This left sda untouched. I set BIOS to boot SATA3, which starts grub. Grub then boots Windows on sda if I select that option. The only thing I had to do was edit menu.lst in the Ubuntu install because grub got the drive assignments backward, ie it called hd0 = hd1 in all of the boot entries. I reversed them all and it boots quite nicely.

You could try simply swapping the drive connections in the box. Some modern mobos with multiple SATA connections sometimes treat them oddly.

Otherwise, you could try this:

1) Run FIXMBR on the disk with Windows. You should have FIXMBR on your Windows install disk. Hopefully, that will clear grub from that disk's MBR. After that, use your BIOS boot options to boot directly into that drive (not grub) to verify Windows will boot. YOU DON'T HAVE TO PUT GRUB ON THIS DISK.

2) Reinstall grub on the MBR of the drive with Ubuntu. 

3) Grub is notorious for not getting drive assignments right in menu.lst. You may have to boot the Ubuntu live CD and edit menu.lst in the boot folder of the Ubuntu install.

4) Once grub is setup correctly on the drive with Ubuntu, you should be able to set your computer to boot to that drive first, then select the Windows drive from that point.

---

### Post by andy_blah on 2008-12-28
> **tsali said:**
> Not necessarily. Do you know which drive has grub in the MBR?

> **tsali said:**
> YOU DON'T HAVE TO PUT GRUB ON THIS DISK.

As I said, it is on the Windows drive, I placed it on the Window's HDD MBR because I thought that I created the partition on the same HDD with Windows, but now I find out that I did the reverse, how silly I am...

> **tsali said:**
> You could try simply swapping the drive connections in the box. Some modern mobos with multiple SATA connections sometimes treat them oddly.

The two HDDs are only IDE, since that's only what my motherboard can support unfortunately

> **tsali said:**
> 1) Run FIXMBR on the disk with Windows. You should have FIXMBR on your Windows install disk. Hopefully, that will clear grub from that disk's MBR. After that, use your BIOS boot options to boot directly into that drive (not grub) to verify Windows will boot.

Strangely, I don't have such a utility on my Windows XP CD, maybe an alternative? I did delete Windows from it's partition and was going to re-install it, would that erase the MBR? I suppose not

> **tsali said:**
> 2) Reinstall grub on the MBR of the drive with Ubuntu. 

> **tsali said:**
> 4) Once grub is setup correctly on the drive with Ubuntu, you should be able to set your computer to boot to that drive first, then select the Windows drive from that point.

Certainly will try to do those things, tho I don't see how this will fix my problem with the wrong drive letter assignment.

---

### Post by tsali on 2008-12-29
> I don't see how this will fix my problem with the wrong drive letter assignment.


You said you have two boot.ini files - one on each drive. This reduces it to only one.

Are you sure that you have no way of backing up all of your data and starting clean? For example, copy everything important out of the 40GB drive to the 80GB, then reinitialize that entire drive with Ubuntu.

To zero the MBR to allow a clean Windows install, you can do this with a Knoppix live CD:

[http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query.-606489/](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query.-606489/)


I don't know what else to tell you. Good luck.

---

### Post by andy_blah on 2008-12-29
Backed-up (but not by your method, the 80GB HDD has only 5GB free, the data wouldn't fit), deleted the partition and tried to re-install Windows, created from it's setup the partition for it, but it refuses to install because it says that the partition is not Windows XP compatibile :-?. I said okay, and booted from my Partition Magic disk and made the partition from there, boot up again in Windows setup, and guess what, it doesn't like that partition either :-?. I really don't know what's it's problem since I've done those steps before and worked.

---

### Post by andy_blah on 2008-12-29
Found out that I have to un-hide the partitions when I install Windows, even if that partition that I tried to hide wasn't on the same HDD (0,1 , the gemeral data one). Now I finished installing Windows, and fixed grub, so I booted from it. And after Windows install, the drives are still with the wrong letters. Now what should I do? There are no system files in the root of the Windows partition, only in the C: (hd 0,1) which baffles me even more.

---

### Post by lswest on 2008-12-29
You can right-click My Computer choose "manage", and then disk management (or words to that affect), and there you can assign drive letters to drives (permanently) by right-clicking and choosing "change drive letters and paths".

Make D: E: (temporarily), make C: be D: and then swap E: to C:

Also, you can't change these if there are system files on a partition.  You can, however, change one drive to a certain letter, and on next boot the drive will occupy the first open drive letter.

---

### Post by andy_blah on 2008-12-29
> **andy_blah said:**
> [QUOTE=tsali;6449060]In any case, I think you can use Windows admin tools to format partitions and assign drive letters to them. Try that. It won't let you fool with the Windows C: drive though.

It doesn't let me "fool" with neither the current C: or D: drive[/QUOTE]

Said it already ^_^

---

### Post by lswest on 2008-12-29
> **andy_blah said:**
> Said it already ^_^

Which is your system partition?  C: or D:?  If it's C: then it's as it should be, if it isn't, make C: E: and on next boot D: should become C:

---

### Post by andy_blah on 2008-12-29
> **lswest said:**
> Which is your system partition?  C: or D: ?  If it's C: then it's as it should be, if it isn't, make C: E: and on next boot D: should become C:

The system partition is D:. If you would have got through the rest of the thread, you would known that it does not let me do that with neither one. Says that both are system or boot volumes and cannot modify them

---

### Post by lswest on 2008-12-30
> **andy_blah said:**
> The system partition is D:. If you would have got through the rest of the thread, you would known that it does not let me do that with neither one. Says that both are system or boot volumes and cannot modify them

Option 1: Seeing as you re-installed, it was feasible that the boot volumes changed again.  The drive that's placed as C: is the first Data Partition, is it not?  Then manually disconnect it, boot to Windows and it will assign the system's drive to C: (at least, it should theoretically).  It's possible that it will swap drive letters again next time it boots with both hard drives though.

Option #2 When you're connecting the second drive, make sure the disks are in the proper order (read: system disk first, then data).  Then try setting the system drive as the Master, and the data drive as the slave in the BIOS

Option #3 [http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm](http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm)
The above is being run in safe mode, and I found it by googling "windows system disk wrong drive letter?".  It should work.

---

### Post by andy_blah on 2008-12-30
> **lswest said:**
> Option #3 [http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm](http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm)
The above is being run in safe mode, and I found it by googling "windows system disk wrong drive letter?".  It should work.

Thank-you for searching for that, finished doing it, restarted, and after that the Windows blue screen shows up, only displays the logo, with no text under (it usually appears showing what modules it loads) and freezes there. I was thinking that I might have to change the boot.ini(after I copied it into the D: drive, the one that was -not sure now- the Windows partition) to update it for the new configuration. But now Ubuntu doesn't let me mount it because I had to restart my computer by the hard way, so now the NTFS partitions are inaccessible, and I don't think that modifying boot.ini will do any good. Any suggestions of what I can do?

I didn't do step 1 and 2 because I really don't like to touch what's inside my computer, only if critical

EDIT: It looks EXACTLY like this when I try to boot Windows:

[IMG]http://i21.photobucket.com/albums/b256/surreal_assassin/Tmp/IMG_4567.jpg[/IMG]

---

### Post by andy_blah on 2008-12-30
I've got into BIOS a few moments ago, and it seems that the 40GB HDD is placed as a slave, while the other as the master on the first IDE channel. Can't change this from BIOS it seems...

---

### Post by lswest on 2008-12-31
about the windows thing, you can generate a new boot.ini file by booting to the XP cd, going to the recovery console and running "fixboot [drive]" (should generate a new boot.ini without installing the stupid bootloader again).  Make sure the [drive] bit is change to the system drive's drive letter.

---

### Post by andy_blah on 2008-12-31
It asks me for a floppy disk that I don't have. Can somebody give me the contents of it?(so I could place it on a floppy and use it in the recovery console)

EDIT: I wish you all a happy new year

---

### Post by andy_blah on 2009-01-02
Can somebody please help by sending me the Automated System Recovery Disk? I can't boot into Windows to do that T.T

---

### Post by andy_blah on 2009-01-02
After I see that no-body can, or want to help me making an Automated System Recovery Disk, I proceeded on removind the 2nd HDD, installing Windows, and it went well, after that, I plug in the 2nd HDD back, and try to start, and GRUB loads (from the 2nd HDD), and I choose to boot to Windows, but instead of booting onto Windows, it says that 'NTDLR is missing' error, tried to edit the partition line in GRUB, but regardless of the configuration, it would shown that either it is an executable error, inside GRUB, or it showed the 'NTDLR is missing' error. After that, I restarted, got into BIOS and choose to boot directly from the first HDD, but this time it shows an corrupt system error or something like that. Any advices of what I should do now?

---

