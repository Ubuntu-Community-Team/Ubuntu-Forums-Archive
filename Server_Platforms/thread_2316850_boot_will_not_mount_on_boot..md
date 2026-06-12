---
title: "/boot will not mount on boot."
date: 2016-03-11
forum: Server Platforms
---

### Post by katja2 on 2016-03-11
hello. i am running ubuntu server 14.04.4 x64. i've litterally just installed it along with java to run a minecraft server. everything works except when i boot up the server after an apt-get update/upgrade/dist-upgrade/autoremove/autoclean and then an apt-get install default-jre... which was the only thing i did after install. it will not get past the "wait for /boot to mount" message. 

so, question, would it help to "recreate" the /boot partition? or something? 

someone sent me this [https://wiki.ubuntu.com/ppc64el/MultipathSupport](https://wiki.ubuntu.com/ppc64el/MultipathSupport) which assumes i have multipath support. i dont know if i do or not? but its LVM for sure.

the tutorial to fix this issue says to put break=pre-multipath in your boot config.. which i assume is hitting "e" on boot and putting that in somewhere (i put it on the second line, as the first line seems to be a title.) and then booting with that by hitting F10. i did so, but no initrdfs console came up. it just booted to the same error. am i putting this command in the wrong place? this looks like a quick, straight forward fix.. but i don't exactly know how to get to an initrdfs prompt. on boot. could i go into the recovery bash console and get into initrdfs somehow?

---

### Post by howefield on 2016-03-11
Thread moved to the "*Server Platforms*" forum.

---

### Post by katja2 on 2016-03-15
bump.

does anyone know how to get to an initrdfs console at all? nothing on google seems to work, else i wouldn't be here.

---

### Post by wellsilva-email on 2016-03-15
Hi katja2, 

Take a look [here]("http://ubuntuforums.org/showthread.php?t=2217829"). The user hakuna_matata found that after the upgrade, he had to change the grub boot menu for the /boot drive to rw. You can edit during boot in the grub screen, [here]("https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot") it's how you can do that.

In the end of the thread there's a tutorial on how to make it permanent.  

Check if it solves your issue.[URL="http://ubuntuforums.org/showthread.php?t=2217829"]
[/URL]

---

### Post by katja2 on 2016-03-18
right. edited /etc/grub.d/10_linux with the replacing the line with "ro" to "rw"... rebooting.

that did not work. it boots when i tell it to skip /boot but otherwise, it still hangs there. nothing changed. though on that page, there was mention of "reinstalling grub" with sudo install-grub /dev/sda ... that would reset my grub configs.. but other than changing ro to rw, i've done nothing else. like he said, and you said he said, it worked fine before the first apt-get upgrade but then its now causing /boot to not mount. i CAN get into the system but well, as previously implied, its a server. i need to not have to hit any keys on boot when i issue a reboot command or it automatically reboots on cronjobs to install updates every week or so.

so, new question. would reinstalling grub fix that or do anything to /boot? and, if you don't know the answer, i rephrase my question to "would there be any adverse effects to reinstalling grub to test this out?"

---

### Post by katja2 on 2016-03-18
ok, well. i looked up grub-install and saw it was safe.. did it. /boot does not mount on boot. HOWEVER... i'm still able to get into /boot from in the OS when i hit S to skip.. i ran an ls -la and here's the output

> echo@localhost:/boot$ ls -la
total 37872
drwxr-xr-x  3 root root     4096 Mar 15 13:36 .
drwxr-xr-x 23 root root     4096 Mar 15 13:36 ..
-rw-r--r--  1 root root  1312645 Mar 11 08:17 abi-4.2.0-34-generic
-rw-r--r--  1 root root   184896 Mar 11 08:17 config-4.2.0-34-generic
drwxr-xr-x  5 root root     4096 Mar 18 15:12 grub
-rw-r--r--  1 root root 26784121 Mar 15 06:43 initrd.img-4.2.0-34-generic
-rw-------  1 root root  3757656 Mar 11 08:17 System.map-4.2.0-34-generic
-rw-------  1 root root  6716080 Mar 11 08:17 vmlinuz-4.2.0-34-generic




does that look legit?

---

### Post by katja2 on 2016-03-18
after doing research, one option is [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) boot repair.. which is a GUI interface... i'm running a server, which means command line only. so, that's... not going to help. so that's out.

and two, [http://ubuntuforums.org/showthread.php?t=2217829&page=5](http://ubuntuforums.org/showthread.php?t=2217829&page=5) user says his /tmp isn't loading.. and suggested to chmod 777 it.... would that explode violently if i tried to do that on my /boot? i mean, if i can cd into it and ls it... its obviously there. maybe permissions are incorrect for some weird reason? (i swear i didn't change anything there.. and apparently this is a valid bug that hasn't been solved yet for x64bit server cd installs (though, apparently it doesn't effect network server installs)) either way.. dunno if chmod 777 would be reversable or if it would cause things not to work.


EDIT: just to humor myself, i tried sudo mount -o remount /boot just to see if it was actually mounted...since i can go into it. 
echo@localhost:/$ sudo mount -o remount /boot
[sudo] password for echo:
mount: /boot not mounted or bad option
echo@localhost:/$ sudo mount -o mount /boot
mount: special device UUID=4ba2d82d-13f8-46c8-9775-fb350663c659 does not exist

which apparently its not.. or i'm doing something wrong.

---

### Post by volkswagner on 2016-03-19
It appears when you are reading contents of /boot, that directory is likely mounted under /

Please post output of following commands:
```
sudo blkid
```
```
cat /etc/fstab
```
```
sudo fdisk -l
```
```
mount
```

---

### Post by katja2 on 2016-03-19
> echo@localhost:/$ sudo blkid
/dev/sda1: UUID="9fc6879f-8e66-4662-a3f7-59d040d7164f" TYPE="ext2"
/dev/sda5: UUID="b5240ffb-0dd2-4a4b-bc83-ce76ba30dc52" TYPE="crypto_LUKS"
/dev/sdb1: UUID="e5538df2-caef-4d90-9e23-c02db1e4ab65" TYPE="ext2"
/dev/sdb5: UUID="sGCGqI-ehSX-XDaA-lVCr-80mT-iRgT-e8xnNF" TYPE="LVM2_member"
/dev/mapper/localhost--vg-root: UUID="7e5ecc31-5a0a-4f41-9d7d-035c53358f56" TYPE="ext4"

NOTE: ignore sda. this server is running on sdb. this server and every last thing on it is sdb. sda is another HDD i have plugged in and boot from as a.. i guess. pseudo "live disk" to fix things if this doesn't boot. it also makes encrypted backups of configs and important stuff when booted. it's not part of the server. so, just ignore it.

> echo@localhost:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/localhost--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=4ba2d82d-13f8-46c8-9775-fb350663c659 /boot           ext2    defaults        0       2
#/dev/mapper/localhost--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


> echo@localhost:/$ sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004cca7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
/dev/sda5          501760   625141759   312320000   83  Linux


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000a72c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5          501760  1953523711   976510976   8e  Linux LVM


Disk /dev/mapper/localhost--vg-root: 991.3 GB, 991327944704 bytes
255 heads, 63 sectors/track, 120522 cylinders, total 1936187392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/localhost--vg-root doesn't contain a valid partition table


Disk /dev/mapper/localhost--vg-swap_1: 8568 MB, 8568963072 bytes
255 heads, 63 sectors/track, 1041 cylinders, total 16736256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/localhost--vg-swap_1 doesn't contain a valid partition table

NOTE: i am using sdb right now. this server has another HDD that it considers sda. there's nothing mounted from it its and fully encrypted and couldn't be mounted unless given a password. it's also, as you see, on a completely different drive. if you super need me to, i can reboot without that drive with issue the same command and post that output.


> echo@localhost:/$ mount
/dev/mapper/localhost--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/echo/.Private on /home/echo type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=b5cf77cac97274cf,ecryptfs_fnek_sig=420130b4767ca111)

there you go. all commands and outputs. that's some pretty sound wisdom there, if i may say so. i like that quote.

---

### Post by katja2 on 2016-03-19
oh ****. as i read my outputs... "/boot was on sda1 during installation." i might be able to explain this. during boot, i only had one HDD installed. this one. the SATA plugins on the motherboard are not labeled. i thought the upper right one was the first.. but apparently, looking at this, its the lower right, which i plugged the second HDD into.... hence it would make some sense for this to call itself sdb. though, i don't think that would matter that when i plugged the other HDD in they switched from sda to sdb? definitely interesting to note, though. and i could probably switch plugs on the motherboard and boot up just to see if that fixes anything. never had that be an issue on any other version of ubuntu linux or any linux. i had to also set the BIOS to boot to this one instead of the first one. which would definitely also be a side effect of that. but again, i don't see anything saying it HAS to be sda1 to boot.. if its sdb1, should work the same, right? worth asking at any rate.

---

### Post by darkod on 2016-03-19
This line in /etc/fstab says that /boot was on separate partition on install (called sda1 in that point of time):
```
[COLOR=#000000]*# /boot was on /dev/sda1 during installation*[/COLOR]
[COLOR=#000000]*UUID=4ba2d82d-13f8-46c8-9775-fb350663c659 /boot ext2 defaults 0 2*[/COLOR]
```

You also have a possible /boot on sdb1 especially if you used the guided LVM method when installing because that installs ubuntu server with separate /boot.

However, right now neither sda1 or sdb1 are mounted as /boot and the server is still booting normally (except the message about /boot), right? If the server boots, you don't need to mount any partition as /boot.

Were you doing any actions regarding /boot after the initial install? For example, maybe you integrated the files inside / and now you don't need separate /boot any more?

In any case the above quoted partition is not relevant any more because that UUID doesn't exist. The partition was probably reformatted or reinstalled over it. If the server boots OK I would first comment out (disable) that line in /etc/fstab which will make the error message go away on boot. And it will not try to mount that partition any more.

That should not affect the server at all because you are not mounting that partition now anyway...

---

### Post by darkod on 2016-03-19
> **katja2 said:**
> oh ****. as i read my outputs... "/boot was on sda1 during installation." i might be able to explain this. during boot, i only had one HDD installed. this one. the SATA plugins on the motherboard are not labeled. i thought the upper right one was the first.. but apparently, looking at this, its the lower right, which i plugged the second HDD into.... hence it would make some sense for this to call itself sdb. though, i don't think that would matter that when i plugged the other HDD in they switched from sda to sdb? definitely interesting to note, though. and i could probably switch plugs on the motherboard and boot up just to see if that fixes anything. never had that be an issue on any other version of ubuntu linux or any linux. i had to also set the BIOS to boot to this one instead of the first one. which would definitely also be a side effect of that. but again, i don't see anything saying it HAS to be sda1 to boot.. if its sdb1, should work the same, right? worth asking at any rate.

The naming of the disks sda, sdb, sdc, etc always goes in order of SATA ports on the board. And they are all labelled, you just have to look carefully on the board or the user manual.

But for booting the server, it doesn't matter. That's why /etc/fstab uses UUID and not /dev/sda1 in the relevant line. The sda1 is mentioned only in the comment which is for your information information.

That UUID mentioned in fstab is not present any mode in your system, the blkid command shows that. Switching the disks in the SATA ports makes no difference except if you prefer the main HDD to be sda.

---

### Post by volkswagner on 2016-03-19
> **darkod said:**
> The naming of the disks sda, sdb, sdc, etc always goes in order of SATA ports on the board. And they are all labelled, you just have to look carefully on the board or the user manual.

But for booting the server, it doesn't matter. That's why /etc/fstab uses UUID and not /dev/sda1 in the relevant line. The sda1 is mentioned only in the comment which is for your information information.

That UUID mentioned in fstab is not present any mode in your system, the blkid command shows that. Switching the disks in the SATA ports makes no difference except if you prefer the main HDD to be sda.

I believe the key reason for UUID is because MOST of the time devices are recognized in order of the SATA ports, but not ALWAYS. I have experienced
creating MDADM RAID installs where after first boot and even second boot, the UUID vs /dev/sdaX changed without moving SATA cables, meaning physical disks
were recognized in a different order after the initial install.

To make mounting more reliable, the UUID method is best.

excerpt from my install notes from a couple years ago:
```
&&&&&&&&&&& NOTE, on first boot new 1.5TB were /dev/sda/ and /dev/sdb &&&&&
	Now they show as /dev/sdc and /dev/sdd after reboot.
```

The above note referenced two drives in RAID 1. I had two other small drives in RAID 1 that also changed respectively.

---

### Post by katja2 on 2016-03-26
[COLOR=#000000]> Were you doing any actions regarding /boot after the initial install? For example, maybe you integrated the files inside / and now you don't need separate /boot any more?[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]

other than completely wiping the drive and installing it again (updating 32 bit to 64 bit because i grabbed the wrong disk) and then once it was installed, apt-get update and upgrade, etc... then installing web server stuff. nothing on the hardware-wise or filesystem-wise was edited personally by me. HOWEVER, its completely possible that the install script of the webserver software did something, as it created users and whatnot. i did run grub-install and whatnot as i said before. but nothing really changed boot-wise. it could've been booting from sda1... then grub-install made the boot partition on my hard drive. either way, i'll try removing that line from /etc/fstab.


done... aaaaaand rebooting. 


IT WORKS. WOO. SOLVED. 

thank you sooo very much. is there any way i can +1 you or thank you? i don't exactly know how this forum works.[/COLOR]

---

### Post by katja2 on 2016-03-26
[COLOR=#000000]thanks super a lot.[/COLOR]

---

