---
title: "Recovering deleted partion table w/LUKS drive"
date: 2017-06-05
forum: Ubuntu/Debian BASED
---

### Post by james_wood2 on 2017-06-05
Thought I'd try this forum first, seeing how another thread I read earlier today seemed beneficial...  The skinny... A week back something went wrong when I was using Clonezilla to clone a USB disk to another of the same model.  In the process, I lost the partition table to the original disk and now can no longer boot from it (the backup also failed to clone with this Clonezilla method).  Afterwards, I used dd to 'clone' the original damaged disk so that I ensure I now have a 'practice' disk to try and recover from.

Testdisk:
Data not handy, however I had once tried recovering the partitions, but could not unlock the LUKS partition afterwards.

Hexdump (so far; It's still running after 2hrs):
[root@localhost XXXXXX]# hexdump -C /dev/sdc | grep LUKS
00719e30  65 64 00 4c 55 4b 53 ba  be 00 25 73 20 21 3d 20  |ed.LUKS...%s != |
0f500000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
e5999990  0b 9e 5b 22 88 c9 74 70  db 09 4c 55 4b 53 b5 ef  |..["..tp..LUKS..|
1087928d0  2e 82 9c 27 72 ff 4c 55  4b 53 4c 5f 4d 17 85 4e  |...'r.LUKSL_M..N|
160984730  c1 a5 4e cd 49 21 4c 55  4b 53 30 35 9a 37 c7 e6  |..N.I!LUKS05.7..|
2386aa770  d0 40 85 7e 4c 55 4b 53  e1 7d e0 d8 3b 02 18 61  |.@.~LUKS.}..;..a|
2a6077a70  b5 4c 55 4b 53 63 9f 72  1d a3 28 c6 9e a2 b6 26  |.LUKSc.r..(....&|
341485d70  e6 89 4c 55 4b 53 90 ab  11 64 f8 f3 13 b1 71 65  |..LUKS...d....qe|

I understand from reading there may be a way to mount the disk at an offset, then try and open the drive. Now, I am still trying to work through the Linux+ certification, so I am not afraid to say this mistake is beyond my training and experience to date.

Optimally I would like to restore the partition table so the drive is again bootable w/o sign of damage, however, if that's not possible, I would like to uncover a way to recover the damaged LUKS partition (or is it 'drive' given I had opted to encrypt the drive at installation?).  Also, I believe the LUKS partition was sitting inside an LVM partition according to fdisk -l, and my own memory..

Ideas?  T.I.A..

---

### Post by LostFarmer on 2017-06-05
some info from a LUKS hdd I have on hand.

The outputs will only be snippets of the commands.

 ```
dad@debian:~$ sudo fdisk /dev/sdb
/dev/sdb1     2048  1050623  1048576  512M EFI System
/dev/sdb2  1050624  2050047   999424  488M Linux filesystem
/dev/sdb3  2050048 39100415 37050368 17.7G Linux filesystem
```  sdb1 is a EFI partition.  sdb2 is the BOOT partition.  sdb3 is the LVM with '/ and swap'

```
dad@debian:~$ sudo dd if=/dev/sdb3 count=1 bs=512 | xxd
0000000: 4c55 4b53 babe 0001 6165 7300 0000 0000  LUKS....aes.....
0000010: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000020: 0000 0000 0000 0000 7874 732d 706c 6169  ........xts-plai
0000030: 6e36 3400 0000 0000 0000 0000 0000 0000  n64.............
0000040: 0000 0000 0000 0000 7368 6132 3536 0000  ........sha256..
0000050: 0000 0000 0000 0000 0000 0000 0000 0000  ...............
```. IT shows that " LUKS  aes" is on the first line of the first sector of the LVM partiton.
With your output of 'hexdump'  the sector start offset of "0f500000" will meet the requirements. (  0f500000=256901120/512=501760)--sector #=501760

IF your comp is booting in EFI mode , before the LVM partition you must have a EFI and Boot partition.  IF booting in legacy/mbr , then only needs the Boot partition before LVM.

So question that needs answer, EFI or legacy booting ?

off to sleep.

---

### Post by james_wood2 on 2017-06-06
This centos 7 version fails to show an 'efi' folder in /sys/firmware/, therefore I am now confident that I am booting from a legacy/older BIOS (HP 2540p laptop).

I had previously tried to restore the partitions which TestDisk had listed, however had not tried any 'offset' at that time.  Drive is currently inserted into the CentOS system, and I will try restoring the partitions again via TestDisk, then mounting the LUKS partition with an offset of "0f500000" this afternoon.

This is all new ground for me, certainly outside the knowledge I have acquired to date.  Thank you for your guidance.  I'll report the outcome later in the day.

---

### Post by oldfred on 2017-06-06
If you booted Centos in BIOS mode then it would not show in /sys/firmware.

If flash drive is gpt partitioned and has ESP - efi system partition, I would expect  it was UEFI.
But did flash drive boot on its own or only when plugged into original system and was using ESP or MBR from internal drive?
Do you have /EFI/Boot/bootx64.efi in the ESP on flash drive? That is the only way flash drives directly boot, if not booting from internal drive.

I do not know LVM nor encryption.
While primarily about resizing, the first part is about mounting the LVM & encrypted partition.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup 

And then if you can mount you may need fsck on the LVM ext4 partition(s), not the physical partitions. Although /boot as ext2 partition may need fsck.

---

### Post by james_wood2 on 2017-06-20
Sorry for the late response here .. 

 The Kali Distribution I am using right now on this computer does not have /EFI ...  All I do is ESC and then select from BIOS which device to boot from during power up.  Gut says this is legacy, as I've never encountered EFI issues with this Laptop before.

root@kali:~# locate .efi
/usr/lib/systemd/boot/efi/linuxx64.efi.stub
/usr/lib/systemd/boot/efi/systemd-bootx64.efi

Will review the other threads you supplied this aft and see what they say.  Tks.

---

### Post by howefield on 2017-06-20
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by LostFarmer on 2017-06-20
You likely then will only have 2 partition in the MBR.  The first will be a small boot partition and the other will be the LVM.

---

### Post by james_wood2 on 2017-06-24
> **LostFarmer said:**
> You likely then will only have 2 partition in the MBR.  The first will be a small boot partition and the other will be the LVM.

Looks to be the case per **blkid**:

/dev/sdc1: UUID="6750d3ab-8034-4186-a90f-51edf43504b9" TYPE="ext2" PARTUUID="23c7dcb8-01"
/dev/sdc2: UUID="4396dbd3-d71c-4d9b-a477-3a8c882a1631" TYPE="crypto_LUKS" PARTUUID="23c7dcb8-02"

**fdisk -l**

Disk /dev/sdc: 119.2 GiB, 128035323904 bytes, 250068992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x23c7dcb8

Device     Boot  Start    End Sectors  Size Id Type
/dev/sdc1  *      2048 499711  497664  243M 83 Linux
/dev/sdc2       501760 505855    4096    2M 83 Linux 

**per mount:**
/dev/sdc1 on /media/root/6750d3ab-8034-4186-a90f-51edf43504b9 type ext2 (rw,nosuid,nodev,relatime,uhelper=udisks2)
* Which I can access and see that it's grub

**cryptsetup** luksUUID /dev/sdc2 showed 4396dbd3-d71c-4d9b-a477-3a8c882a1631

Goal now is to try mounting at an the offset suggested, and do some additional reading on the subject (and mount command).  Certainly feels like "An inch and Hour", however, I am getting a feel for the commands.  Thanks everybody for the support.

---

### Post by LostFarmer on 2017-06-24
[SIZE=3]the below is what I would do.  after running fdisk -l to verify hdd  ( will use hdd sdc)
run fdisk /dev/sdc and delete sdc2 - save and exit
run fdisk /dev/sdc and make a new partition  -select the start sector as  '501760' - set end sector as default -- set file system as linux-- save  and exit.
reboot comp. --(to be sure the new partition table is the one in use)

You can try to boot into sdc at this time. If it asks to correct file system say no.

The below commands is what I use to manually mount a mint luks  system  on my debian booted system.  You will have to make some modifications.   NOTE is what I added to post not part of command or displayed data. 
```

[SIZE=4]dad@debian:~$sudo mkdir /mnt/crypthome   (you should delete the crypthone directory when done)

dad@debian:~$ sudo cryptsetup luksOpen /dev/sdb3 mydata  *NOTE (mydata is just a name, must be the same for luksOpen and luksClose)*
Enter passphrase for /dev/sdb3:    [I] NOTE(the password will NOtE be displayed)
[/I]
dad@debian:~$ sudo vgscan
  Reading all physical volumes.  This may take a while... 
  Found volume group "mint-vg" using metadata type lvm2      [I]NOTE  (you will have a output with  'ubuntu-vg' or what ever== use it in below commands in place of mint-vg)
[/I]
dad@debian:~$ sudo vgchange -ay mint-vg     *  NOTE ( see above note)*
  2 logical volume(s) in volume group "mint-vg" now active

dad@debian:~$ sudo lvscan
  ACTIVE            '/dev/mint-vg/root' [13.77 GiB] inherit    * NOTE(use the /dev/***/*** in next mount command)*
  ACTIVE            '/dev/mint-vg/swap_1' [3.89 GiB] inherit

dad@debian:~$ sudo mount /dev/mint-vg/root /mnt/crypthome   

 You can now open your file manager and see the data at /mnt/crypthome.  to properly unmount the luks device do below.

dad@debian:~$ sudo umount /mnt/crypthome 

dad@debian:~$ sudo vgchange -an mint-vg  [I] Note above, replace mint-vg
[/I]  0 logical volume(s) in volume group "mint-vg" now active

dad@debian:~$ sudo cryptsetup luksClose mydata[/SIZE]
```

Had a hard time seeing what I wrote so messed with the FONT size , not sure if it will mess up the information.
[/SIZE]

---

### Post by james_wood2 on 2017-06-29
**Thank you...**

- Deleted /dev/sdc2
- Created new Linux partition at offset 501760 as suggested
- Saved
- Rebooted
* Note: System would not reboot with both USB's plugged in, even though I indicated the correct USB to boot from
- Powered-off
- Removed, repaired/re-partitioned USB
- Rebooted into Kali Linux
- Inserted repaired USB and was prompted for Crypto PWD
* No matter how many times I entered the PWD, or alternate PSWDs (just in-case), the system would not accept any.
** Is it possible that I have forgotten??  I suppose, however, I don't think so..
*** This is the trouble I recall encountering when inserting USB into CentOS
*** Now "Back-up" USB (from DD) only shows 1 x 128Mb DOS partition; tested in Kali, CentOS, and SUSE.  ????  No Linux; I could have sworn I had tested this image was a successful duplicate, afterwards.??


**From Kali:**
root@kali:~# blkid
/dev/sda1: LABEL="System Reserved" UUID="B2C4B440C4B4091D" TYPE="ntfs" PARTUUID="ffeb202e-01"
/dev/sda2: UUID="3EF2B7DCF2B7969D" TYPE="ntfs" PARTUUID="ffeb202e-02"
/dev/sda3: UUID="0E5E07085E06E7F3" TYPE="ntfs" PARTUUID="ffeb202e-03"
/dev/sda4: UUID="788E-3481" TYPE="vfat" PARTUUID="ffeb202e-04"
/dev/sdb1: UUID="aad865e3-1274-4aeb-be18-e0e63a54ddb3" TYPE="ext4" PARTUUID="8e24122d-01"
/dev/sdb3: UUID="EFEE-AD65" TYPE="vfat" PARTUUID="8e24122d-03"
/dev/sdb5: UUID="4944f8c3-01d4-4e9d-af43-f713971dfc4b" TYPE="swap" PARTUUID="8e24122d-05"
/dev/sdc1: UUID="6750d3ab-8034-4186-a90f-51edf43504b9" TYPE="ext2" PARTUUID="23c7dcb8-01"
/dev/sdc2: UUID="4396dbd3-d71c-4d9b-a477-3a8c882a1631" TYPE="crypto_LUKS" PARTUUID="23c7dcb8-02"
root@kali:~#

Wondering if I need to tie this into LVM now (/device/mapper ..)?  Will review the second phase of your post now, and try the command based decrypting and mounting next..

---

### Post by james_wood2 on 2017-06-29
No luck with any of below... So, either I have forgotten the PSW (I don't believe so), or other?  Unfortunately, it's 13 character, so would probably be a challenge to hack (if even possible?)..

root@kali:~# umount /dev/sdc1
root@kali:~# mkdir /mnt/crypthome
root@kali:~# sudo cryptsetup luksOpen /dev/sdc2 mydata
Enter passphrase for /dev/sdc2: 
No key available with this passphrase.
Enter passphrase for /dev/sdc2: 
No key available with this passphrase.
Enter passphrase for /dev/sdc2: 
No key available with this passphrase.


root@kali:~# vgscan
  Reading all physical volumes.  This may take a while...
root@kali:~# lvscan

---

### Post by LostFarmer on 2017-06-29
> *** Now "Back-up" USB (from DD) only shows 1 x 128Mb DOS partition;  tested in Kali, CentOS, and SUSE.  ????  No Linux; I could have sworn I  had tested this image was a successful duplicate, afterwards.?? Was not the backup made after the partition table was messed up ?  Like to see the raw partition table from your backup.
" hexdump -C /dev/sdc -n 512  " post only the last 4 lines.

---

### Post by LostFarmer on 2017-06-30
My lvm is on a GPT disk and type code 83. Reading [http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html) says on a MBR/legacy partitioned disk the lvm is on a logical volume.  Now what I do not know if the lvm is changed from a logical volume to a primary volume if it would cause problems unlocking it (?).  

Also the partition type code should be 8E not 83 ,  check with fdisk and if wrong (83) change it to 8E.  That might make it work.

Just ran some tests and the above likely will not matter.
use gdisk and converted GPT to MBR disk and change the type code for the lvm from 83 to 8e, had no problems to unlock.  May later change the lvm from a primary partition to a logical volume but will need to shrink the boot partition, need some space between the end of sdb2 (/boot) and sdb3(lvm/luks).

---

### Post by james_wood2 on 2017-07-02
Thank you for the** hexdump** suggestion on the 'original backup'..

Last few lines that appear relevant...  Looks like something is astray here, too..

root@kali:~# hexdump -C /dev/sdc -n 512
0000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  b8 dc c7 23 00 00 00 00  |...<.u.....#....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|


Note:

I had a 'fresh' Lexar 128Gb S45 on hand, so I used dd to image the drive that you are assisting me with (post partition recovery/re-build).
/dev/sdc1: UUID="6750d3ab-8034-4186-a90f-51edf43504b9" TYPE="ext2" PARTUUID="23c7dcb8-01"
/dev/sdc2: UUID="4396dbd3-d71c-4d9b-a477-3a8c882a1631" TYPE="crypto_LUKS" PARTUUID="23c7dcb8-02"

Post image (~10.5hrs to complete):
- I powered down, removed both S45's, powered up into Kali
- Inserted image, and was prompted for a Crypto PSW
- Ran blkid, and others, to confirm a mirror copy:
/dev/sdc1: UUID="6750d3ab-8034-4186-a90f-51edf43504b9" TYPE="ext2" PARTUUID="23c7dcb8-01"
/dev/sdc2: UUID="4396dbd3-d71c-4d9b-a477-3a8c882a1631" TYPE="crypto_LUKS" PARTUUID="23c7dcb8-02"

# At least I have another backup from post partition recovery, just in-case 'whatever'. ;-)

Power down again, so still using initial drive being repaired, via fdisk, I verified file type on both partitions was displaying 83/Linux.  Changed FS type on sdc2 to 8e; wrote, verified modification took, cycled laptop (didn't just use partprobe).

Post reboot into Kali, I inserted 'sdc', however, was not prompted for a crypto password this time (could still access sdc1 - verified it is GRUB; however, cannot boot from this USB).  I again verified partition type modification took on sdc2 (8e/Linux LVM), then tried 'cryptsetup luksOpen /dev/sdc2 mydata' (/mnt/cryphome was previously created).  Went through the series of password attempts (have all I wish to try/have tested written down in leafpad), however, still no dice so far.

Also ran vgscan; empty (seconds to complete)

Have only so far skimmed [http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html).  For info on changing partition types, I was using: [http://www.labtestproject.com/using_linux/step_by_step_change_linux_partition_system_id_on_fedora_system](http://www.labtestproject.com/using_linux/step_by_step_change_linux_partition_system_id_on_fedora_system)

Within this 'exercise', I certainly can see how Linux can be 'controlled', and thus, why it's important to keep track of all the 'minor' changes.

Will review more of the LVM guide this eve, and keep writing down 'psw possibilities' to test, in case..

---

### Post by LostFarmer on 2017-07-02
The hexdump you posted shows zero partitions.  (MBR partitioned hdd only, not GPT) The partition data is 16 bytes long and start at offset 01be and stops at offset 01fd.  There is only space for 4 partitions.  You have all zeros.  [http://thestarman.pcministry.com/asm/mbr/W7MBR.htm](http://thestarman.pcministry.com/asm/mbr/W7MBR.htm) half way down will show complete MBR for MS Windows 7 and up.  The Master Partition Table part of the Master Boot Record will be the same for MS Windows or Linux.
Found sub sites MBR for linux-grub (legacy ?) [http://thestarman.pcministry.com/asm/mbr/GRUB.htm](http://thestarman.pcministry.com/asm/mbr/GRUB.htm)

> why it's important to keep track of all the 'minor' changes Agree and I fail to do so.

---

