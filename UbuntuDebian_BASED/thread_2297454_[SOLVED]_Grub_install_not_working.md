---
title: "[SOLVED] Grub install not working"
date: 2015-10-03
forum: Ubuntu/Debian BASED
---

### Post by alex297 on 2015-10-03
I'm fairly new to Ubuntu, so I don't really know what I'm doing.  

I tried to dual boot elementary OS (basically Ubuntu with superficial changes) on an Asus F554L notepad with Windows 10.  When I restarted, I got a [GNU GRUB screen (Minimal BASH-like line editing is supported)]("http://ubuntuforums.org/showthread.php?t=2136856"). I still could boot into windows by holding the escape key and selecting windows.
 So I used live boot to run:
```
grub-install /dev/sda
```
which got me:
```
grub-install: error: cannot find efi directory
```
So then I used [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to try to fix my problems, but that didn't work either. [Please see this link for logs]("http://paste.ubuntu.com/12662643/").  They instructed me to run the following command in Windows:
```
bcdedit /set {bootmgr} path \EFI\grub\shimx64.efi
```
I still end up with the same screen on start up. The only difference was that the escape key menu had one more option (presumably the one I just added), but that new option still lead to the GNU GRUB screen.


Thanks for any help!

---

### Post by oldfred on 2015-10-03
Better/easier for us, if you just use the link that Boot-Repair gives to pastebin.

Moved to Elementary/Other OS sub forum. Not sure of differences with Elsementary.

Often better not to have a separate /boot partition for most Desktop installs, full drive encryption with LVM does have to have the separate /boot.

Your install looks normal. Does elementary just use /EFI/grub? Ubuntu uses /EFI/ubuntu as location of efi boot files.

Your sda1 is the ESP - efi system partition. Shows as FAT32 with boot flag. Actual setting is some very long GUID. Gparted uses boot flag to assign the GUID. The gdisk program uses a ef00 code to assign the GUID.
Sometimes the FAT32 need either chkdsk from Windows or dosfsck from Linux.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by howefield on 2015-10-04
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by alex297 on 2015-10-04
> **oldfred said:**
> Better/easier for us, if you just use the link that Boot-Repair gives to pastebin.
Thanks, I did that.

> **oldfred said:**
> 
Often better not to have a separate /boot partition for most Desktop  installs, full drive encryption with LVM does have to have the separate  /boot.

Again, I'm fairly new to Ubuntu, so I don't really know what I'm doing.  I encrypted my home folder, and I created swap, /home, /boot, and /  root partitions.  Are you saying that I should reinstall using a standard install?


> **oldfred said:**
> Your install looks normal. Does elementary just use /EFI/grub? Ubuntu uses /EFI/ubuntu as location of efi boot files.

Your sda1 is the ESP - efi system partition. Shows as FAT32 with boot  flag. Actual setting is some very long GUID. Gparted uses boot flag to  assign the GUID. The gdisk program uses a ef00 code to assign the GUID.
Sometimes the FAT32 need either chkdsk from Windows or dosfsck from Linux.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

You lost me here.  If you think that it would help, I'll try installing Ubuntu and see if that goes smoothly.

So what are you saying?  That I should liveboot elementary and run the following?
```
dosfstools - dosfsck utilities
sudo dosfsck -t -a -w /dev/[COLOR=#b22222]**sda**[/COLOR]

```

Thank you!

---

### Post by oldfred on 2015-10-04
You should be able to run those commands from the terminal in any Linux.

I do not like standard install as that is just / (root) and swap. But I use data partitions not /home as separate partition and that is a bit more advanced. For most the separate /home is good. 
And if you are using encryption of any type be sure to have really good backup procedures. Encryption makes file recovery difficult or impossible if you have any file system issues.

---

### Post by alex297 on 2015-10-09
> **oldfred said:**
> You should be able to run those commands from the terminal in any Linux.

I do not like standard install as that is just / (root) and swap. But I use data partitions not /home as separate partition and that is a bit more advanced. For most the separate /home is good. 
And if you are using encryption of any type be sure to have really good backup procedures. Encryption makes file recovery difficult or impossible if you have any file system issues.

I tried what you suggested, and I'm still getting the nasty boot screen.  Maybe I'm mounting/unmounting the wrong partitions?

I installed:
[LIST]
[*] boot loader in /dev/sda
[*]/boot in sda7 (Primary Ext2)
[*]Swap in sda8 (Logical)
[*]/ in sda9 (Logical Ext4)
[*]/home in sda10 (Logical Ext4)
[/LIST]



Thank you so much!



```
elementary@elementary:~$ umount /boot/efi
umount: /boot/efi is not mounted (according to mtab)
elementary@elementary:~$ umount /boot
umount: /boot is not mounted (according to mtab)
elementary@elementary:~$ sudo fsck.vfat -a /dev/sda1
fsck.fat 3.0.26 (2014-03-07)
/dev/sda1: 282 files, 33990/98304 clusters
elementary@elementary:~$ sudo fsck.vfat -a /dev/sda
fsck.fat 3.0.26 (2014-03-07)
Logical sector size is zero.
elementary@elementary:~$ sudo fsck.ext4 -a /dev/sda2
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


elementary@elementary:~$ sudo fsck.ext4 -a /dev/sda9
/dev/sda9: clean, 144688/7045120 files, 1246600/28155392 blocks
elementary@elementary:~$ sudo fsck.ext4 -a /dev/sda10
/dev/sda10: clean, 48/35381248 files, 2271424/141495808 blocks
elementary@elementary:~$ sudo fsck.vfat -a /dev/sda7
fsck.fat 3.0.26 (2014-03-07)
Logical sector size is zero.
elementary@elementary:~$ sudo fsck.ext2 -a /dev/sda7
/dev/sda7: clean, 321/122160 files, 22867/488192 blocks
elementary@elementary:~$ mount /dev/sda7 /boot
mount: only root can do that
elementary@elementary:~$ sudo mount /dev/sda7 /boot
elementary@elementary:~$ mount /dev/sda /boot/efi
mount: only root can do that
elementary@elementary:~$ sudo mount /dev/sda /boot/efi
mount: /dev/sda already mounted or /boot/efi busy
elementary@elementary:~$ sudo mount /dev/sda1 /boot/efi
elementary@elementary:~$ sudo mount /dev/sda7 /boot/efi
[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]



```

```
elementary@elementary:~$ unmount /boot/efi
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
unmount: command not found
elementary@elementary:~$ umount /boot/efi
umount: /boot/efi is not mounted (according to mtab)
elementary@elementary:~$ umount /boot
umount: /boot is not mounted (according to mtab)
elementary@elementary:~$ fsck.vfat /dev/sda1
fsck.fat 3.0.26 (2014-03-07)
open: Permission denied
elementary@elementary:~$ sudo fsck.vfat /dev/sda1
fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
Leaving filesystem unchanged.
/dev/sda1: 282 files, 33990/98304 clusters
elementary@elementary:~$ sudo -a fsck.vfat /dev/sda1
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
usage:  sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p  prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-u user] file ...
elementary@elementary:~$ sudo fsck.vfat -a /dev/sda1
fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
Performing changes.
/dev/sda1: 282 files, 33990/98304 clusters
elementary@elementary:~$ sudo fsck.vfat -a /dev/sda1
fsck.fat 3.0.26 (2014-03-07)
/dev/sda1: 282 files, 33990/98304 clusters
elementary@elementary:~$ dosfstools- dosfsck utilities
dosfstools-: command not found
elementary@elementary:~$ dosfstools - dosfsck utilities
dosfstools: command not found



```

---

### Post by oldfred on 2015-10-09
You cannot run fsck on mounted partitions, nor entire drive like sda. And you cannot run on swap or some of the unformatted partitions that UEFI may require.

The ESP - efi system partition is often sda1 or sdb1, but Windows may make it sda2 or sda3. The ESP is normally the only FAT32 partition. 

Better to use the parameters, as even when you say clear dirty bit, it does not seem to do it.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by alex297 on 2015-10-09
> **oldfred said:**
> You cannot run fsck on mounted partitions, nor entire drive like sda. And you cannot run on swap or some of the unformatted partitions that UEFI may require.

The ESP - efi system partition is often sda1 or sdb1, but Windows may make it sda2 or sda3. The ESP is normally the only FAT32 partition. 

Better to use the parameters, as even when you say clear dirty bit, it does not seem to do it.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)


Thanks for the feedback, I'll try it again.  In the mean time, [I found someone who is having the same problem as me]("http://elementaryos.stackexchange.com/questions/1776/how-can-i-fix-a-secure-boot-failing-to-grub-when-i-installed-0-3-1/1884#1884").  There is a solution, but it doesn't quite seem to work.  This is what I get when I try it:

```
configfile (hd0, gpt9)/boot/grub/grub.cfg
```  
Gets me: 
  ```
error: filename expected
```  
I tried all the other partitions (1 through 10) just to be sure, but they all get the same error.  
  [HR][/HR]  **Miscellaneous**
  When I enter 
  ```
configfile (hd
```
I get :
  ```
hd0 hd1error: failure reading sector 0xfc from 'hd1'. error: failure reading sector 0xe0 from 'hd1'. error: failure reading sector 0x0 from 'hd1'.   
```
When I enter: 
  ```
configfile (hd0,gpt 
```  
I get {I leave out the partition sizes after gpt2, but they are there.  I can retrieve them if necessary}:
  ```
Possible partitions are:
Partition hd0,gpt1:  Filesystem type fat - Label 'SYSTEM', UUID 14E4-FCC4 - Partition start at 1024KiB - Total size 102400KiB
Partition hd0,gpt2:  No known filesystem detected - Partition start at 103424KiB - Total size 921600KiB
Partition hd0,gpt3:  No known filesystem detected 
Partition hd0,gpt4:  No known filesystem detected 
Partition hd0,gpt5:  No known filesystem detected 
Partition hd0,gpt6:  No known filesystem detected 
Partition hd0,gpt7:  Filesystem type ext* - Last modification time 2015-10-09 20:11:06 Friday, UUID d9e87737-12df-4b32-98fb-c928101860a0
Partition hd0,gpt8:  No known filesystem detected 
Partition hd0,gpt9:  Filesystem type ext* - Last modification time 2015-10-09 20:05:04 Friday, UUID 6322aa7b-461e-493a-9d50-d03e83e1e543
Partition hd0,gpt10:  Filesystem type ext* - Last modification time 2015-10-09 20:05:09 Friday, UUID 4415c308-5b3f-47eb-b1f1-f69d8c39e00b
```

---

### Post by alex297 on 2015-10-09
UPDATE!!!  I fixed it!  Thanks for all your help!

Solution:

```
configfile /efi/grub/ 
``` and hit tab  (you may need to wait half a minute for it to load)
It should give you a list of possible files.  I chose cfg
```
configfile /efi/grub/grub.cfg 
``` 


Open terminal after boot and type:
```
cd /boot/efi/EFI/grub
sudo cp grubx64.efi grubx64.efi.backup 
sudo rm grubx64.efi
sudo cp /boot/grub/x86_64-efi/grub.efi /boot/efi/EFI/grub/grubx64.efi 
```

---

