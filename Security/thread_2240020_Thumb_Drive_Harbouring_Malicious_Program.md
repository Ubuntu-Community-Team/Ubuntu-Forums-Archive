---
title: "Thumb Drive Harbouring Malicious Program"
date: 2014-08-17
forum: Security
---

### Post by rob-rushworth on 2014-08-17
Evening, all.

I've a problem with a 32gb thumb drive that's driving me mad.
There's something living in there and I can't oust it.

I have a folder containing Gbs of work-related files that I can't delete.
No matter how I try or what I try, the files/folders simply replace themselves after "n" seconds... and the thumb drive restarts itself and reverts to its original contents.

I can't format the thumb drive by any means, and I can't delete the files / folders on it - but I can access, read them, and copy them off the drive.

I've tried disk managers, terminal commands, installing GParted, and nothing works... even using GParted as a Live CD won't format the drive or move / change the partitions on it.

Does anyone have any idea of how I can get my thumb drive back under my own control?

Whatever is in there, I need to kill it with fire.

Cheers

C

Ubuntu 14.04 - new installation.

---

### Post by tgalati4 on 2014-08-17
A good wack with a hammer will bring an unruly flash drive under control.

To reduce risk, boot from a Live USB stick and post the output of:

```
sudo fdisk -l
```

What is the origin of these files?  Are they utility programs that come with the flash drive?  Are they files that you put on there?  Have you changed the partitions on this flash drive from the original configuration?

---

### Post by rob-rushworth on 2014-08-17
Hammer sounds good right now, tgalati4.[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=241895")

The origin of the files is a shared "library" of sorts - teaching resources - mostly .pdf files, .doc, .odt, etc  - no idea of the premiere source.

> sudo fdisk -l

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a75b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   300654591   150326272   83  Linux
/dev/sda2       300656638   312580095     5961729    5  Extended
/dev/sda5       300656640   312580095     5961728   82  Linux swap / Solaris

Disk /dev/sdb: 32.5 GB, 32463912960 bytes
256 heads, 13 sectors/track, 19052 cylinders, total 63406080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    63406079    31703024    c  W95 FAT32 (LBA)



---

### Post by bashiergui on 2014-08-17
> A good wack with a hammer will bring an unruly flash drive under control.<-- This. If you're trying to delete them then just smash the thing and be done with it.

---

### Post by rob-rushworth on 2014-08-17
But then I'm down XBucks and will never know whodunnit.

And I need to know who that was.

Flame throwers at dawn - I love the smell of napalm in the morning.

---

### Post by bashiergui on 2014-08-17
Whodunnit is probably way less interesting than you want it to be. Change permissions (as root) on the files in the thumb drive to 777 then see if you can delete them. If that doesn't work it sorta sounds like it's mounted as a write-protected drive. Or the drive is in the process of failing.

edit: Eliminate the simple sys admin type of issues. 90% of my problems in Linux are due to permissions issues. The other 42% is usually due to math errors.

---

### Post by fugu2 on 2014-08-18
USB drives all have individual firmwares that they run, and it is possible that this firmware has become corrupted. idk if you'd be able to extract the firmware from that USB stick or not, but if you willing to get your hands dirty, i'd give a Bus Pirate a try.
Edit: Backup your important data on it first, and there is a good chance you'll probably toast the stick anyway

---

### Post by tgalati4 on 2014-08-18
So we have established that the drive is FAT32 with only one partition and no hidden partitions.  Your partition is defined from block 32 to block 63406079, one block short of total reported to the operating system.  So there is no room for another partition or any other data.

Post the output of the top level directory of the flash disk:

```
ls -la
```

We need to determine the owner, group and permissions of the files on the disk.

It will look something like:

> 
tgalati4@Mint14-Extensa /media/tgalati4/3239-3530 $ ls -la
total 68
drwx------   3 tgalati4 tgalati4 32768 Dec 31  1969 .
drwxr-x---+  4 root     root      4096 Aug 18 12:14 ..
drwx------  49 tgalati4 tgalati4 32768 Oct  8  2013 tgalati4_13Oct13_Backup


Use the quote tags to preserve formatting.

---

### Post by rob-rushworth on 2014-08-18
```
 ls -la 
```

...gives, in total...

> 
/media/rob/DDD$ ls -la
total 3405300
drwx------   3 rob  rob       16384 Jan  1  1970 .
drwxr-x---+  3 root root       4096 Aug 19 09:00 ..
-rw-r--r--   1 rob  rob  3486979566 Aug  9 13:41 asstd.zip
drwx------  28 rob  rob       16384 Aug  9 13:49 School


This was very difficult to get as the flash drive keeps cycling off / on / off and seems to be refreshing itself. I had to practice getting the path pasted into the terminal and the ls -la command in there before the drive cycled... not much time.

---

### Post by rob-rushworth on 2014-08-18
> i'd give a Bus Pirate a try.

Took a look at that, and to be honest - I'm not up for it. Way beyond my skillset. But thanks for the suggestion.

> Change permissions (as root) on the files in the thumb drive to 777 then  see if you can delete them. If that doesn't work it sorta sounds like  it's mounted as a write-protected drive. Or the drive is in the process  of failing.

Can't delete the files anywhichway. 
The drive is/was brand new. The day I bought it, my wife used it once where she works (hospital) to transfer files between computers. Then, after that, I placed a back-up collection of files on it - it's been a problem since then. There's a collection of weirdly named text files buried in there and a folder that tries to copy itself out first. The folder is called 

> @.Ç

I think this is the problem.

If I try to open this folder, I get the message:

> This location could not be displayed
Sorry, could not display all the contents of &#8220;@.Ç&#8221;: Error when getting information for file '/media/rob/DDD/School/New Headway/@.Ç/&#8804;&#9575;¬8&#9552;&#9558;?'.p': Input/output error

By this time, the drive has cycled off - but it doesn't come back on again and I see a blank screen, as in the picture below, instead of the drive contents.

[IMG]http://i.imgur.com/sf7LXCf.png[/IMG]

---

### Post by vasa1 on 2014-08-18
> **rob-rushworth said:**
> ...
This was very difficult to get as **the flash drive keeps cycling off / on / off and seems to be refreshing itself**. I had to practice getting the path pasted into the terminal and the ls -la command in there before the drive cycled... not much time.

> **rob-rushworth said:**
> ... **a folder that tries to copy itself out first**. ...
Is your OS a straight-forward Ubuntu 14.04 or is it a Wubi thing or a live USB?

I'm asking because the USB in question seems to have a mind of its own. I've **bolded** what I can't understand. Was the origin of all the files from a Linux system or from some other OS? Are you still using the file manager that comes with 14.04 by default?

Can you mount/unmount the USB from the file manager?

---

### Post by rob-rushworth on 2014-08-18
My current installation is a straight-forward 14.04 installed from a CD maybe 10 days ago. I updated from 12.04, which was installed as a dual-boot system alongside a wheezy distro called Archeos, with Archeos being installed first. The back-up on the USB drive was made from said 12.04 installation.

**Yes, my USB has a mind of its own** - like I said at the start, something's living in there.

Just from my own observations (and I'm certainly no expert) it looks like something is projecting from the USB and living in system memory - and whatever that thing is, it is protecting the USB drive's contents and can operate in system memory even when the USB is used with a Live CD. To clarify - i can't remove or change the contents of the USB even with GParted run as a Live CD.

---

### Post by vasa1 on 2014-08-19
Can you just insert the USB without mounting it? And what file manager are you using?

---

### Post by lisati on 2014-08-19
> **tgalati4 said:**
> 
Use the quote tags to preserve formatting.
[NOPARSE]```
 and 
```[/NOPARSE] are often preferred as they provide scroll bars for long quotes.

---

### Post by rob-rushworth on 2014-08-19
vasa1 , when plugged in, the drive automounts, then soon after dismounts itself, then remounts itself, etc, etc. I'm using the default file manager that came with 14.04.

If I try to copy out large folders from the drive, the dismount/remount causes a failure in the transfer... meaning I have to go farther into the folder tree and transfer out smaller folders or individual files. 
The @.Ç folder seems to be first in line to be copied from the flash drive if I try to copy folders that contain its folder within their tree, but the transfer of @.Ç seems to fail as it's flagged as such very early on during transfers which later fail themselves due to the repetetive "time-out".


lisati , duly noted, thanks.

---

### Post by tgalati4 on 2014-08-19
Was this flash drive used on a keychain?  It seems that you have an intermittent connection inside the USB connector.  This would cause the flash drive to appear and disappear and cause the files to go immediately to RO (read-only).  Immediately after plugging in the flash drive:

```
dmesg | tail -50
```

Now put a little pressure on it--up and down and do it again:

```
dmesg | tail -50
```

If this is the case, then you can carefully cut open the flash drive and resolder the 4 pins of the USB jack.  This is to recover the data, not a permanent fix.  Once you recover the data, take a hammer and end its misery.

---

### Post by rob-rushworth on 2014-08-19
Not been on a keychain - didn't even come with a strap.  Handling before I got it... no idea.
It's a...

[https://www.google.com/search?client=ubuntu&channel=fs&q=adata+c008+32gb&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=adata+c008+32gb&ie=utf-8&oe=utf-8)

bought at an accessories shop in my local mall.


```
dmesg | tail -50
```

...first time gives...

```
dmesg | tail -50
[14606.280050] sd 8:0:0:0: [sdb] CDB: 
[14606.280052] Write(10): 2a 00 00 00 00 21 00 00 01 00
[14606.280061] end_request: I/O error, dev sdb, sector 33
[14606.280066] Buffer I/O error on device sdb1, logical block 1
[14606.280068] lost page write due to I/O error on sdb1
[14606.616041] usb 2-6: new high-speed USB device number 6 using ehci-pci
[14606.793963] usb 2-6: New USB device found, idVendor=125f, idProduct=a000
[14606.793968] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[14606.793971] usb 2-6: Product: USB Flash Drive
[14606.793973] usb 2-6: Manufacturer: USB 2.0
[14606.793976] usb 2-6: SerialNumber: AA00000000000932
[14606.794258] usb-storage 2-6:1.0: USB Mass Storage device detected
[14606.794339] scsi9 : usb-storage 2-6:1.0
[14608.962130] scsi 9:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  1100 PQ: 0 ANSI: 4
[14608.962360] sd 9:0:0:0: Attached scsi generic sg2 type 0
[14608.966630] sd 9:0:0:0: [sdb] 63406080 512-byte logical blocks: (32.4 GB/30.2 GiB)
[14608.967367] sd 9:0:0:0: [sdb] Write Protect is off
[14608.967370] sd 9:0:0:0: [sdb] Mode Sense: 43 00 00 00
[14608.968124] sd 9:0:0:0: [sdb] No Caching mode page found
[14608.968127] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[14608.971471] sd 9:0:0:0: [sdb] No Caching mode page found
[14608.971475] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[14608.972361]  sdb: sdb1
[14608.975347] sd 9:0:0:0: [sdb] No Caching mode page found
[14608.975351] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[14608.975354] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[15954.858172] usb 2-6: USB disconnect, device number 6
[18129.896043] usb 2-6: new high-speed USB device number 7 using ehci-pci
[18130.073821] usb 2-6: New USB device found, idVendor=125f, idProduct=a000
[18130.073825] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[18130.073828] usb 2-6: Product: USB Flash Drive
[18130.073831] usb 2-6: Manufacturer: USB 2.0
[18130.073833] usb 2-6: SerialNumber: AA00000000000932
[18130.074106] usb-storage 2-6:1.0: USB Mass Storage device detected
[18130.074818] scsi10 : usb-storage 2-6:1.0
[18132.242609] scsi 10:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  1100 PQ: 0 ANSI: 4
[18132.242831] sd 10:0:0:0: Attached scsi generic sg2 type 0
[18132.245578] sd 10:0:0:0: [sdb] 63406080 512-byte logical blocks: (32.4 GB/30.2 GiB)
[18132.246759] sd 10:0:0:0: [sdb] Write Protect is off
[18132.246762] sd 10:0:0:0: [sdb] Mode Sense: 43 00 00 00
[18132.247696] sd 10:0:0:0: [sdb] No Caching mode page found
[18132.247699] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[18132.251306] sd 10:0:0:0: [sdb] No Caching mode page found
[18132.251309] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[18132.252211]  sdb: sdb1
[18132.255201] sd 10:0:0:0: [sdb] No Caching mode page found
[18132.255204] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[18132.255208] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[18132.457100] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[18132.540264] systemd-hostnamed[7861]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

...second time -  wiggled, moved, gently twisted, etc, then left alone while tested...

```
dmesg | tail -50
[18130.073828] usb 2-6: Product: USB Flash Drive
[18130.073831] usb 2-6: Manufacturer: USB 2.0
[18130.073833] usb 2-6: SerialNumber: AA00000000000932
[18130.074106] usb-storage 2-6:1.0: USB Mass Storage device detected
[18130.074818] scsi10 : usb-storage 2-6:1.0
[18132.242609] scsi 10:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  1100 PQ: 0 ANSI: 4
[18132.242831] sd 10:0:0:0: Attached scsi generic sg2 type 0
[18132.245578] sd 10:0:0:0: [sdb] 63406080 512-byte logical blocks: (32.4 GB/30.2 GiB)
[18132.246759] sd 10:0:0:0: [sdb] Write Protect is off
[18132.246762] sd 10:0:0:0: [sdb] Mode Sense: 43 00 00 00
[18132.247696] sd 10:0:0:0: [sdb] No Caching mode page found
[18132.247699] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[18132.251306] sd 10:0:0:0: [sdb] No Caching mode page found
[18132.251309] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[18132.252211]  sdb: sdb1
[18132.255201] sd 10:0:0:0: [sdb] No Caching mode page found
[18132.255204] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[18132.255208] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[18132.457100] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[18132.540264] systemd-hostnamed[7861]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[18197.549895] usb 2-6: USB disconnect, device number 7
[18197.560033] sd 10:0:0:0: [sdb] Unhandled error code
[18197.560038] sd 10:0:0:0: [sdb]  
[18197.560040] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[18197.560043] sd 10:0:0:0: [sdb] CDB: 
[18197.560044] Write(10): 2a 00 00 00 00 21 00 00 01 00
[18197.560053] end_request: I/O error, dev sdb, sector 33
[18197.560057] Buffer I/O error on device sdb1, logical block 1
[18197.560059] lost page write due to I/O error on sdb1
[18197.900040] usb 2-6: new high-speed USB device number 8 using ehci-pci
[18198.077835] usb 2-6: New USB device found, idVendor=125f, idProduct=a000
[18198.077839] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[18198.077842] usb 2-6: Product: USB Flash Drive
[18198.077844] usb 2-6: Manufacturer: USB 2.0
[18198.077847] usb 2-6: SerialNumber: AA00000000000932
[18198.078126] usb-storage 2-6:1.0: USB Mass Storage device detected
[18198.078191] scsi11 : usb-storage 2-6:1.0
[18200.246371] scsi 11:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  1100 PQ: 0 ANSI: 4
[18200.246606] sd 11:0:0:0: Attached scsi generic sg2 type 0
[18200.247328] sd 11:0:0:0: [sdb] 63406080 512-byte logical blocks: (32.4 GB/30.2 GiB)
[18200.249428] sd 11:0:0:0: [sdb] Write Protect is off
[18200.249430] sd 11:0:0:0: [sdb] Mode Sense: 43 00 00 00
[18200.252025] sd 11:0:0:0: [sdb] No Caching mode page found
[18200.252029] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[18200.255468] sd 11:0:0:0: [sdb] No Caching mode page found
[18200.255471] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[18200.256359]  sdb: sdb1
[18200.259342] sd 11:0:0:0: [sdb] No Caching mode page found
[18200.259345] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[18200.259348] sd 11:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by rob-rushworth on 2014-08-19
Mjolnir's twitching...  Hammer Time?

---

### Post by fugu2 on 2014-08-19
You **might** be able to diagnose the problem using a usbmon 
```
http://wiki.wireshark.org/CaptureSetup/USB
```
FYI, i have found that the USB protocol is hard to understand, even using a tool like wireshark. You might be able to find out what is going on with this, you might not.

---

