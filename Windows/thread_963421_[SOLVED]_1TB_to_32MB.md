---
title: "[SOLVED] 1TB to 32MB"
date: 2008-10-30
forum: Windows
---

### Post by tadcan on 2008-10-30
I bought a new 1TB drive and put it in. I then went to computer disk management in XP to format it to NTFS. I let it do its thing and came back all seemed fine. Now when I check its telling me that the disk is 32MB. (Unformatted it was full seize) So what did I do wrong?

---

### Post by garyedwardjohnston on 2008-10-30
Are you running Ubuntu or Windows?

---

### Post by Golem XIV on 2008-10-30
Possibilities and solutions:

- Old BIOS without support for LBA (32 GB max).  Update your BIOS.
- Jumper on disk set to limit capacity to 32 GB (for compatibility with older BIOSes).  Remove or change jumper setting.
- Windows XP not updated to SP1.  Update XP with Service Pack 3.

Hopefully one of these will help you.

---

### Post by tadcan on 2008-10-30
Its XP and it has SP3 installed. Its a sata2 drive. 

Its a new machine basically. Does that affect the bios options?

---

### Post by Golem XIV on 2008-10-30
If the machine is new (<5 years old) the BIOS should recognize the entire drive.

Sorry if I couldn't be of more help...

---

### Post by tadcan on 2008-10-30
I can see the Hard Drive when I booted with the 8.10 live CD. I have a screenshot of it, but it wont let me upload the image. 

I tried booting into safe mode, same result.

---

### Post by Majorix on 2008-10-30
I don't suggest using external drives with Windows. It has serious problems with USB drives, and may cause data loss and/or the loss of the whole HD :(

---

### Post by tadcan on 2008-10-30
its an internal drive. 

when I checked properties the partition style is listed as a 'master boot record' (MBR) That could account for its small size. 

Here is a screen shot of what I see.

EDIT: In 8.10 the drive is listed under removable media. Could that be a clue.

---

### Post by smoker on 2008-10-30
windows computer disk management isn't that great, i wouldn't be surprised if the size of the drive is more than it can cope with,

use the gparted partitioner on the ubuntu live cd to format it, or download and make a bootable version of gparted to do so: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

you should also be able to download an application from the hard drive manufacturer's support site to format the drive if you prefer that.

best of luck

---

### Post by adaptr on 2008-10-30
> **tadcan said:**
> I bought a new 1TB drive and put it in. I then went to computer disk management in XP to format it to NTFS. I let it do its thing and came back all seemed fine. Now when I check its telling me that the disk is 32MB. (Unformatted it was full seize) So what did I do wrong?
Boot from an Ubuntu Live CD and go to a terminal.

Then type ```
sudo fdisk -l
``` and see what it says.

If it's partitioned badly then anything is possible, but the drive won't suddenly have become smaller.

@smoker: such nonsense. Windows (2000 and up) will happily deal with any size drive now in existence, as long as the BIOS recognises it, which it does because he says it used to work.

---

### Post by KiwiNZ on 2008-10-30
Have you tried the manufacturers disk tools to try to restore?

 the drive is probably defective you will need to replace it .

---

### Post by tadcan on 2008-10-30
I tried the manufacturers disk tool. It to only saw 32MB

I put ```
sudo fdisk -l
``` into terminal and got

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e7de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101       79539   597931267+   f  W95 Ext'd (LBA)
/dev/sda3           79540       91201    93675015   83  Linux
/dev/sda5            5101       79039   593914986    7  HPFS/NTFS
/dev/sda6           79040       79539     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x23f09580

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          64       32224+   7  HPFS/NTFS
```

I have also asked a friend for help. One of his suggestions was to unplug the two optical drives. When I rebooted there was still an optical drive listed. He suspects that the drive has been mislabled. 

The next option is to reformat the drive with the live CD. I plan to wipe 8.04 and install 8.10 anyway. After I see my options I'll come up with a plan.  

KiwiNZ, I should known soon if its a hardware failure or not. Fingers crossed.

---

### Post by fiddledd on 2008-10-30
> **Majorix said:**
> I don't suggest using external drives with Windows. It has serious problems with USB drives, and may cause data loss and/or the loss of the whole HD :(

Really, I bet there's many here who would like to see a link to back up your claim. Unless of course it's just more FUD.

BTW, I've used the same 7 hard drives connected to USB ports on my Windows machines for at least 6 years. Do you think these serious problems will manifest themselves soon?

---

### Post by Majorix on 2008-10-31
> **fiddledd said:**
> Really, I bet there's many here who would like to see a link to back up your claim. Unless of course it's just more FUD.
Sorry about before... I just wanted to sum it up, because I felt too lazy to write the whole story. Anyways...

My story with USB HDD's and Windows is like this. I had an old 500GB Western Digital USB drive, which I used on Linux and the old XP installation (latter of which could not "remove" the drive for some reason).

Recently I bought a new notebook which came pre-installed with Windows Vista. Without the USB drive plugged-in, everything ran fine. Then I wanted to play my mp3's on the USB drive, and as such I used it. Vista wanted to reboot after doing a few upgrades in the meantime, and I let it.

After the reboot, a black screen which said "One of your disks has to be checked for consistency" -or whatever that message was exactly- greeted me, and then it showed the drive label for the FAT32 partition of the HDD (It is rather large, like 400GB's or so). Again I let it check it, but it got stuck at 0%. I waited for a few minutes and it hit 1%. It was late through the night, so I left it on and went to sleep.

When I came back the next day to check on it, it said 40% and this time it wasn't even hitting 41%. So, in all sadness I was in, I force restarted the PC.

This time, I didn't get that "I have to check your disks" message, so I was happy. But for some reason the computer was acting very slow. I clicked "Computer" (the old "My Computer") and I saw that the drive (with all of its partitions) were not listed in there.

I tried playing around in Vista by plugging in and out, but none worked. I thought maybe it is a problem with Vista, so I launched Arch Linux. But Arch Linux didn't "see" the drive either.

I don't know what is wrong exactly, but the problem is that the drive is dead atm. It contained more than 400GB's worth of files.


If I say "don't use USB drives with Windows", then you know you should listen to me :p

---

### Post by tadcan on 2008-10-31
During the 8.10 install I had the option of putting in on the new fully recognised drive. This doesn't solve my problem, it was intended for extra space on XP. 

I tried partition magic, but it saw only 32MB. 

When I am finished with the install will try gparted.

Guys, while I appreciate your help, if you want to have a discussion about external devices can you move it to the community cafe?

---

### Post by tadcan on 2008-10-31
I have made progress. I installed 8.10 onto the 1TB drive. I also deleted the 8.04 on the main drive.

My plan is this to repartition the first drive to take up the free space that was the 8.04 partition with the C: and D: drives. Got an error with partition magic. When it booted up I got error 1529 while executing batch. 

Will try gparted once I get new blank CDs.     

Then to reduce the 8.10 partition to around 80GB. Then reformat the rest of it to NTFS. 

Anyway I'm tired now. Pick this up in the morning. 

Advice as always is welcome.

---

### Post by tadcan on 2008-11-01
I got 8.10 onto my main drive. Then reformatted the extra drive to NTFS. Not so hard in the end!

---

