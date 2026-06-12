---
title: "I have a problem with bootable usb flash"
date: 2019-10-09
forum: Windows
---

### Post by hiepvs on 2019-10-09
[COLOR=#141414][FONT=&amp]I wanted to create a bootable drive for win xp, [/FONT][/COLOR][COLOR=#141414][FONT=&amp]when convert FAT32 to NTFS with some commands:
[/FONT][/COLOR]```
[COLOR=#141414][FONT=inherit]sudo apt-get install gparted[/FONT][/COLOR]
sudo apt-get install ntfs-3g
df -h
umount /dev/sdb1 [COLOR=#141414][FONT=inherit]sudo mkntfs --fast --label myUsbDrive /dev/sdb1[/FONT][/COLOR]
```
[COLOR=#141414][FONT=&amp]I can't mount usb, i tried some ways but still failed:
[/FONT][/COLOR]```
[COLOR=#141414][FONT=inherit]mount /dev/sdb1[/FONT][/COLOR]
sudo mount /dev/sdb1
[COLOR=#141414][FONT=inherit]sudo mount /dev/sdb1 /mnt[/FONT][/COLOR]
```
[COLOR=#141414][FONT=&amp]Yesterday, I pluged in the usb again. I has error:
[/FONT][/COLOR]> [COLOR=#141414][FONT=&amp]Error mounting /dev/sdb at: command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" exited with non-zero exit status 13: $mftmirr does not match $mft (record 0).[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Failed to mount '/dev/sdb1': input/output error.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]NTFS is either inconsistent, or there is a hardware fault, or it's a softraid/fakeraid hardware.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]In the first case run chkdsk /f on windows then reboot into windows twice.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]The usage of the /f parameter is very important![/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]If the device is a softraid/fakeraid then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1).[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Please see the 'dmraid' documentation for more details.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Name of usb: /dev/sdb1[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Link of directory: /media/bodhi64/myUsbDrive[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Like this pic:
[/FONT][/COLOR][ATTACH=CONFIG]284167[/ATTACH][COLOR=#141414][FONT=&amp]
[/FONT][/COLOR][COLOR=#141414][FONT=&amp]Anyone can help me? Thanks in advance.




---------
**_EDIT:_**
It will be solve by: convert NTFS to FAT32
[/FONT][/COLOR]```
[COLOR=#141414][FONT=inherit]sudo mkfs -t vfat /dev/sdb1[/FONT][/COLOR]
```

---

### Post by uRock on 2019-10-09
Moved to Windows sub-forum.

---

