---
title: "Virus removal failed"
date: 2011-01-15
forum: Security
---

### Post by gpdas on 2011-01-15
Hi all, I have a serious problem. My pen drive is infected with Desktop_1.ini virus, that has come along with some video(.dat) files from Windows system. I am unable to delete this file or its parent folder with 'sudo rm -rf foldername'.
**It shows the error**
[COLOR=Red][B]root@gpdas-laptop:/media/AKSHAY4GB# rm -rf vengaboys
rm: cannot remove `vengaboys/AVSEQ01.DAT': Read-only file system
rm: cannot remove `vengaboys/Desktop_1.ini': Read-only file system[/B][/COLOR]

But the folder as well as file shows '[U]execute permission'
[/U]
     [COLOR=Red][B]4 drwx------  2 gpdas gpdas      4096 2011-01-14 14:21 Semi's
     4 drwx------  2 gpdas gpdas      4096 2010-08-19 00:54 Songs
     4 drwx------  2 gpdas gpdas      4096 2011-01-14 14:21 vengaboys[/B][/COLOR]

Any help is highly appreciated.

---

### Post by nitrogensixteen on 2011-01-15
i recommend you fix whatever vector introduced the malware before worrying about your flash drive.

unmount the drive and remount with rw options.

for example:
sudo umount /dev/sdbX
sudo mount -t vfat -o rw /dev/sdbX /media/virus

---

### Post by I'mGeorge on 2011-01-15
> **gpdas said:**
> Hi all, I have a serious problem. My pen drive is infected with Desktop_1.ini virus, that has come along with some video(.dat) files from Windows system. I am unable to delete this file or its parent folder with 'sudo rm -rf foldername'.
**It shows the error**
[COLOR=Red][B]root@gpdas-laptop:/media/AKSHAY4GB# rm -rf vengaboys
rm: cannot remove `vengaboys/AVSEQ01.DAT': Read-only file system
rm: cannot remove `vengaboys/Desktop_1.ini': Read-only file system[/B][/COLOR]

But the folder as well as file shows '[U]execute permission'
[/U]
     [COLOR=Red][B]4 drwx------  2 gpdas gpdas      4096 2011-01-14 14:21 Semi's
     4 drwx------  2 gpdas gpdas      4096 2010-08-19 00:54 Songs
     4 drwx------  2 gpdas gpdas      4096 2011-01-14 14:21 vengaboys[/B][/COLOR]

Any help is highly appreciated.

Download avast for linux from here [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4) You will need a register key, just register to their site and you will get one for free. Update your avast database after installation and scan your usb drive with it.

---

### Post by gpdas on 2011-01-15
Sincerely speaking, I am not much worried about the virus. But I am worried that Linux rm -rf command is unable to remove a file. In any tutorial it is written that be careful to use this command. Second point is whether this virus will affect/enter into my Ubuntu system?
waiting for a reply.

---

### Post by StaticIp on 2011-01-15
This interests me as well.

---

### Post by gradinaruvasile on 2011-01-15
> **gpdas said:**
> Sincerely speaking, I am not much worried about the virus. But I am worried that Linux rm -rf command is unable to remove a file. In any tutorial it is written that be careful to use this command. Second point is whether this virus will affect/enter into my Ubuntu system?
waiting for a reply.

The drive is mounted as read only for some reason and the kernel forbids modifications in this state. Remount it as rw (read-write). 
Post the output of "dmesg" command in a terminal 5 seconds after you inserted the drive.

Or just unmount and delete the partitions on it with fdisk and reformat it.

---

### Post by I'mGeorge on 2011-01-15
you could play with the permissions of the file using chmod

---

### Post by gpdas on 2011-01-15
After inserting USB drive, the 'dmesg' command shows the following
[11964.633298] usb 2-1: new high speed USB device using ehci_hcd and address 6
[11964.766442] usb 2-1: configuration #1 chosen from 1 choice
[11964.767514] scsi7 : SCSI emulation for USB Mass Storage devices
[11964.767748] usb-storage: device found at 6
[11964.767754] usb-storage: waiting for device to settle before scanning
[11969.764647] usb-storage: device scan complete
[11969.765544] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer Micro     8.01 PQ: 0 ANSI: 0 CCS
[11969.766808] sd 7:0:0:0: Attached scsi generic sg2 type 0
[11969.774428] sd 7:0:0:0: [sdb] 7862911 512-byte logical blocks: (4.02 GB/3.74 GiB)
[11969.775084] sd 7:0:0:0: [sdb] Write Protect is off
[11969.775093] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08
[11969.775099] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11969.779859] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11969.779873]  sdb: sdb1
[11969.785092] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11969.785105] sd 7:0:0:0: [sdb] Attached SCSI removable disk

Pl tell me there is any problem.

---

### Post by DodgeV83 on 2011-01-15
Is it one of those flash drives with a hardware "read-only" switch?  If so, switch it off

:)

---

### Post by gpdas on 2011-01-15
No, There is no Hardware switch for Read-Only mode.

---

### Post by OpSecShellshock on 2011-01-15
The best approach is probably to copy the files you want to save over to another drive and then reformat the USB drive. If the USB drive is NTFS formatted then it probably will not be affected by Linux permissions.

---

