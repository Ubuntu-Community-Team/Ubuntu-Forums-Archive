---
title: "Cryptsetup - can not access device"
date: 2009-04-13
forum: Security
---

### Post by ushills on 2009-04-13
For some reason I cannot access my encryted usb key anymore, this was working fine up to last week but now I get the following error when mounting manually. Gnome will no longer mount, I enter the passphrase but no mapping occurs.

```
sudo cryptsetup -v luksOpen /dev/sdf sdf
Command failed: Can not access device

```

luksDump

```
 sudo cryptsetup luksDump /dev/sdf 
LUKS header information for /dev/sdf

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
Payload offset:	1032
MK bits:       	128
MK digest:     	07 24 c4 81 c4 89 4f 85 3d d4 27 98 fc 36 79 ad d8 18 9b 81 
MK salt:       	a8 49 21 c1 5e d2 56 f4 98 b5 cb 36 6c 10 1a 84 
               	10 ea ea cf fd 0f bf b2 de 65 2e f7 ab a0 1b 7b 
MK iterations: 	10
UUID:          	00ec49c7-cd73-48da-b2e4-fe4ac1442d7e

Key Slot 0: ENABLED
	Iterations:         	167199
	Salt:               	a1 12 a9 78 1c 5b e0 59 1c 98 07 49 68 66 05 d4 
	                      	93 83 62 9e a9 c1 7f 21 99 8e ff 73 8d f3 60 2e 
	Key material offset:	8
	AF stripes:            	4000
Key Slot 1: ENABLED
	Iterations:         	139990
	Salt:               	44 5e 4e 1e c7 4a 33 f3 66 f1 25 80 37 df 6a 73 
	                      	9b 74 a6 03 56 d0 72 fd f1 ca ec d5 06 55 f8 6f 
	Key material offset:	136
	AF stripes:            	4000
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

```

Fdisk of drive, think it has always said this as raw drive is unformatted.

```
sudo fdisk -l /dev/sdf

Disk /dev/sdf: 8029 MB, 8029470208 bytes
248 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 15376 * 512 = 7872512 bytes
Disk identifier: 0x08020000

Disk /dev/sdf doesn't contain a valid partition table


```

---

### Post by hyper_ch on 2009-04-13
please provide the following info:

```

sudo fdisk -l

```

---

### Post by ushills on 2009-04-13
the drive mounts as /dev/sdf and the fdisk -l is given in post #1.  Only other drive is sda which has my ubuntu partition.

---

### Post by ushills on 2009-04-14
Output of fdisk for information

```
 sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4ef0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546   83  Linux
/dev/sda2           30270       30401     1060290    5  Extended
/dev/sda3            3188       30269   217536165   83  Linux
/dev/sda5           30270       30401     1060258+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 8029 MB, 8029470208 bytes
248 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 15376 * 512 = 7872512 bytes
Disk identifier: 0x08020000

Disk /dev/sdf doesn't contain a valid partition table

```

---

### Post by ushills on 2009-04-14
it appears that this is a long standing bug with gnome-mount.  It appears that gnome unlocks the encrypted usb partition as i end up with a device in /dev/mapper/ called luks_crypto and a series of numbers.  However, gnome will not mount this device.

---

### Post by ushills on 2009-04-15
Though I would help if anyone else had this issue, solved by reformatting usb drive to create a primary partition in my case sdf1 then creating luksformat on this primary partition.  Now it auto-mounts.

---

