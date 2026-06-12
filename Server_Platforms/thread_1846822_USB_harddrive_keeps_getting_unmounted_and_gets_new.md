---
title: "USB harddrive keeps getting unmounted and gets new device ID"
date: 2011-09-19
forum: Server Platforms
---

### Post by DavidBeijer on 2011-09-19
Hi all,

I recently installed ubuntu server on a spare computer, which is to be used as mediaserver and for experimenting. Thusfar I have encountered no problems, got samba, ftp, www-host etcetera configured in no time, but one problem remains. I connected a 2TB USB harddrive to the computer. This gets recognised properly and shows up in /dev as sdb (and its first and only partition as sdb1). I mounted it to /home/media, and shared that folder through samba, which worked like a charm. Now however, every once and a while the HD gets disconnected somehow, and then shows up again in /dev, but with the device letter increased by 1. 

This is annoying, and it would be no problem, but it screws up the mount to /home/media, and it does not get restored automatically. Does anyone know the cause of this problem and a solution?

I have tried to add this disk to fstab, my fstab listing for this device:
```

UUID=02704CA7704CA371   /home/media     ntfs    user,auto,umask=000     0       0

```

This however did not work, it still gets assigned increasing drive letters, and the drive is not mounted to /home/media. (I've tried to emulate the interruptions by switching the drive off and on again, to no avail)

I have also read [this thread]("http://ubuntuforums.org/showthread.php?t=1786458&highlight=external+disk+fstab&page=2"), which seemed not to provide the solution.

Output of blkid:
```

david@awesome:/dev$ sudo blkid
/dev/sda1: UUID="2b30c5a9-f104-4bec-89c1-5d0ab9a0f37f" TYPE="ext4"
/dev/mapper/cryptswap1: UUID="7edabdd5-3c89-4c47-b4f9-ac3a81a9e55a" TYPE="swap"
/dev/sdf1: LABEL="Verbatim HDD" UUID="02704CA7704CA371" TYPE="ntfs"

```

The result from dmesg is quite long, one excerpt I think is relevant:
```

[91158.767259] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[91158.768002] sd 3:0:0:0: [sdc] Write Protect is off
[91158.768059] sd 3:0:0:0: [sdc] Mode Sense: 28 00 00 00
[91158.769749] sd 3:0:0:0: [sdc] Incomplete mode parameter data
[91158.774537] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[91158.787373] sd 3:0:0:0: [sdc] Incomplete mode parameter data
[91158.792116] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[91158.813069]  sdc: sdc1
[91158.816368] sd 3:0:0:0: [sdc] Incomplete mode parameter data
[91158.821100] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[91158.825681] sd 3:0:0:0: [sdc] Attached SCSI disk
[91305.601397] usb 1-1: USB disconnect, address 3
[91330.768167] usb 1-1: new high speed USB device using ehci_hcd and address 4
[91330.912469] scsi4 : usb-storage 1-1:1.0
[91331.917100] scsi 4:0:0:0: Direct-Access     SAMSUNG  HD204UI               PQ: 0 ANSI: 2 CCS
[91331.926899] sd 4:0:0:0: Attached scsi generic sg2 type 0
[91331.927171] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[91331.928593] sd 4:0:0:0: [sdb] Write Protect is off
[91331.928600] sd 4:0:0:0: [sdb] Mode Sense: 28 00 00 00
[91331.930415] sd 4:0:0:0: [sdb] Incomplete mode parameter data
[91331.932858] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[91331.938772] sd 4:0:0:0: [sdb] Incomplete mode parameter data
[91331.940982] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[91331.954865]  sdb: sdb1
[91331.957781] sd 4:0:0:0: [sdb] Incomplete mode parameter data
[91331.961211] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[91331.964577] sd 4:0:0:0: [sdb] Attached SCSI disk
[351195.116168] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[351195.256172] usb 1-1: device firmware changed

```

Does anyone have a solution for this? I don't care for the small interruptions, they are less than a couple of seconds, but the mount point getting lost (and the drive letter increasing) make it difficult to think of a workaround.

---

### Post by zackwasa on 2011-09-20
You can create labels for partitions and do the mounts in fstab using the labels

---

### Post by DavidBeijer on 2011-09-27
Tnx for the help, but the problem seems to have solved itself! I'm not entirely sure how though. 

Does fstab require a reboot before changes in the file become active? Or is this a little bit to much thinking with my old windows habits? 

As far as I understood the sources I checked on fstab a "sudo mount -a" should have all changes applied? Or am I wrong in this case?

---

