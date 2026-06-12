---
title: "PopOS Unable to boot (Volume group not found)"
date: 2021-08-11
forum: Ubuntu/Debian BASED
---

### Post by robo731 on 2021-08-11
I just upgraded my system and when I restarted I get an error 
```

Volume group "OSs" not found
Cannot process volume group OSs

```

After a few of these, I get:

```

mdadm: No devices listed in conf file were found.
cryptsetup: Waiting for encrypted source device /dev/mapper/OSs-Swap...

```

Ultimately I'm dumped to an initramfs shell.

I am able to boot to the backed up kernel on my system though.

I understand that it might have something to do with an encrypted swap partition, but not too much beyond that. I tried the steps outline here: [https://askubuntu.com/questions/1253428/cryptsetup-waiting-for-encrypted-source-device-swapfile/1253836#1253836](https://askubuntu.com/questions/1253428/cryptsetup-waiting-for-encrypted-source-device-swapfile/1253836#1253836), but unfortunately they did not work.

Any advice on where I can go from here?

---

### Post by TheFu on 2021-08-11
Boot from a Try Ubuntu installer ISO/flash drive. Install **boot-repair**, and use the gather information button, then post the URL it creates.  DO NOT allow it to attempt any repairs. This can be bad in many situations. Just get the bootinfo stuff.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by robo731 on 2021-08-11
Ok, sure here's the output I got: [https://paste.ubuntu.com/p/WyjwqsBrwX/](https://paste.ubuntu.com/p/WyjwqsBrwX/)

---

### Post by TheFu on 2021-08-11
Nothing is jumping out to me. Sorry.

You have LVM, but there isn't any RAID/mdadm involved, so ignore that message.
The bootInfo script didn't have issues activating the VG and definitely saw both LVs, so I don't think those are the issue. It is somewhere upstream. I do BIOS boot with LVM on multiple systems, but those each have a separate boot partition. No UEFI.

So someone else will need to respond.

---

### Post by robo731 on 2021-08-12
Got it, well thank you for looking anyways.

Here's some other resources I found when I was trying to investigate the problem:
- [https://www.reddit.com/r/pop_os/comments/n7qsqb/how_to_fix_cryptsetup_waiting_for_encrypted/](https://www.reddit.com/r/pop_os/comments/n7qsqb/how_to_fix_cryptsetup_waiting_for_encrypted/)
- [https://askubuntu.com/questions/1254772/cryptsetup-waiting-for-encrypted-source-device-swapfile-fstab-empty](https://askubuntu.com/questions/1254772/cryptsetup-waiting-for-encrypted-source-device-swapfile-fstab-empty)
- [https://askubuntu.com/questions/286284/system-no-longer-boots-gave-up-waiting-for-root-device-initramfs-dev-mappe#286383](https://askubuntu.com/questions/286284/system-no-longer-boots-gave-up-waiting-for-root-device-initramfs-dev-mappe#286383)

---

### Post by TheFu on 2021-08-12
So - LVM+LUKS encryption has very different mandates on Ubuntu. If you ARE using encrypt (which I don't see in the data), **always** tell people that.  

My only UEFI laptop uses LVM+LUKS encryption. The fix for any disk issues with encrypted storage that won't open is to reinstall and restore from backups.

---

### Post by oldfred on 2021-08-12
Moved to Other OS since PopOS.

Boot-Repair report did not show all the info that normally is in /. Or / was not mounted.
It seems you have to mount & decrypt install before running report, although it should ask to decrypt? It does seem to ask if LVM or RAID as difficult to parse and tell apart.
Then it will show grub & fstab and some other settings from inside /.

---

### Post by robo731 on 2021-08-12
Yes, I believe my system is LVM+LUKS. I'm able to boot by choosing the old kernel though, so it feels like some process in the update just failed. Would like to use restoring from backup as a last resort.

Hmm, it did not ask me to decrypt, should I try mounting and decrypting manually and running boot-info again? If so, could you point me towards any resources on how I might do so?

Here's some additional info:

**fstab**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>  <mount point>  <type>  <options>  <dump>  <pass>
PARTUUID=0e084b33-98a9-4961-8649-0d80ffb2d137 /boot/efi vfat umask=0077 0 0
UUID=d0551677-7218-49cf-896c-95ae3a2b9ffa / ext4 noatime,errors=remount-ro 0 0
/dev/mapper/cryptswap none swap defaults 0 0

```

**lsblk**
```

NAME            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
nvme0n1         259:0    0 238.5G  0 disk  
&#9500;&#9472;nvme0n1p1     259:1    0   511M  0 part  /boot/efi
&#9492;&#9472;nvme0n1p3     259:2    0 235.7G  0 part  
  &#9500;&#9472;OSs-Swap    253:0    0    12G  0 lvm   
  &#9474; &#9492;&#9472;cryptswap 253:2    0    12G  0 crypt [SWAP]
  &#9492;&#9472;OSs-Pop     253:1    0   100G  0 lvm   /

```

**blkid**
```

/dev/mapper/OSs-Pop: UUID="d0551677-7218-49cf-896c-95ae3a2b9ffa" BLOCK_SIZE="4096" TYPE="ext4"

```

**crypttab**
```

cryptswap UUID=5cca5321-07de-4056-bce7-70ab736ef93d /dev/urandom swap,plain,offset=1024,cipher=aes-xts-plain64,size=512

```

It seems to me like only my swap is encrypted. I wonder if disabling the swap and rerunning some other part of the update can help resolve the issue.

---

### Post by TheFu on 2021-08-12
An encrypted swap without an encrypted OS is sorta useless, IMHO. I've never seen a system setup in this way.
I have no useful suggestion for a fix as it is currently. 

I'm happy to make wild suggestions tomorrow, if there is interest, but that would move the encryption device so nearly all storage is encrypted, except /boot/ which will need to be a new partition.

---

### Post by robo731 on 2021-08-12
Hmm, yeah, I'm not sure why I ended up doing that, but I agree.

I don't really care if it is encrypted at all in fact and would be fine with foregoing the encryption altogether.

Wild suggestions would be welcome, but take your time, I'll be offline over the weekend. I may take a crack at some of the other things in the resources I linked earlier as well.

---

### Post by TheFu on 2021-08-13
To remove the swap LV, just disable the swap (swapoff), delete that LV (lvremove), then recreate a new LV (lvcreate) and format it for as swap (mkswap) and get the new device pointer - something like /dev/{vgname}/{lvname} and put that into the fstab as swap.  
Remove the crypttab line with swap - or comment it out.

Finally, run **swapon -a**.

All this can happen while the system keeps running.  The swapoff command can take 15+ minutes.  Use free to see how much swap is being used.

Lastly, run **update-grub**.

If there are any errors about being out of storage, don't reboot. It isn't uncommon for too many kernels to be in /boot/ and eating too much storage.  I don't see how that can happen without a separate /boot partition, but we see odd things all the time here.

---

### Post by robo731 on 2021-08-16
Ok, that sounds like a good plan, thanks.

I disabled the swap, but when I try to delete the LV, it says the device is in use even though free seems to indicate otherwise:

```
Logical volume OSs/Swap is used by another device.
```

I tried this suggestion next: [https://askubuntu.com/a/109961/491784](https://askubuntu.com/a/109961/491784), but it gives a similar error:

```
Device /dev/mapper/OSs-Swap is still in use.
```

I was also confused by the output of sudo fdisk -l:

```
Disk /dev/nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectorsDisk model: SAMSUNG ************-******             
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: EB5E32A4-E0CE-49B9-9DBF-066016079B80


Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048   1048575   1046528   511M EFI System
/dev/nvme0n1p3 5769216 500117503 494348288 235.7G Linux LVM




Disk /dev/mapper/OSs-Swap: 12 GiB, 12884901888 bytes, 25165824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/OSs-Pop: 100 GiB, 107374182400 bytes, 209715200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/cryptswap: 12 GiB, 12884377600 bytes, 25164800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

I see /dev/mapper/OSs-Swap and also /dev/mapper/cryptswap.

PopOS uses systemd so I think I'll need to do bootctl update instead of update-grub when we can reach that step.

[B]
EDIT:

[/B]I tried the other suggestion here: [https://askubuntu.com/a/109961/491784](https://askubuntu.com/a/109961/491784) and commented out the swap in /etc/fstab and /etc/crypttab and then after rebooting, I was able to remove the volume and both entries are gone from fdisk's output.

I ran sudo update-initramfs -u and bootctl update which gave:

```

Skipping "/boot/efi/EFI/systemd/systemd-bootx64.efi", since a newer boot loader version exists already.
Skipping "/boot/efi/EFI/BOOT/BOOTX64.EFI", since a newer boot loader version exists already.

```

I still was not able to boot with the current kernel, but still can with the old one.

---

### Post by robo731 on 2021-08-18
I tried updating my system and rebooting, but no change.

When I boot and get dumped to BusyBox and try to exit, it was giving me an error similar to this:

[https://www.reddit.com/r/linuxquestions/comments/a0q02g/system_boots_into_busybox_shell_and_claims_uuid/](https://www.reddit.com/r/linuxquestions/comments/a0q02g/system_boots_into_busybox_shell_and_claims_uuid/)

One of the responses here says that maybe the kernel did not include the nvme module. Do you think something like that could be the case?

When I tried running blkid, there was no output.

Maybe this would help: [https://askubuntu.com/a/788802/491784](https://askubuntu.com/a/788802/491784)

---

### Post by TheFu on 2021-08-18
I don't have any NVMe installed in any of my systems currently. Sorry.  I have an NVMe drive, but that's for a new build, plus I was careful to get a well-regarded model.

You say that you disabled swap.  How?  Only the **swapoff** command will work. 
Then comment out the swap line in the fstab and the crypttab.
Then go do the partition work.  I'd delete everything including /dev/nvme0n1p3, then create a 4.1G partition and format it as Linux Swap. No need for LUKS or LVM at all.
There is little reason for swap to be larger than 4.1G on a desktop. In a server, the goal should be to avoid needing **any** swap, since RAM is cheap again.

Rather they saying what happened, SHOW IT!

---

### Post by robo731 on 2021-08-19
Yes, I disabled it with swapoff and commented it out in fstab and crypttab.

Here's the output of fdisk which shows the swap is gone:
```

Disk /dev/nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: SAMSUNG *********-*****              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: *****************


Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048   1048575   1046528   511M EFI System
/dev/nvme0n1p3 5769216 500117503 494348288 235.7G Linux LVM




Disk /dev/mapper/OSs-Pop: 100 GiB, 107374182400 bytes, 209715200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

And free:
```

              total        used        free      shared  buff/cache   available
Mem:        8005256     4547508      271284     2235296     3186464      956260
Swap:             0           0           0

```

If there's anything else you'd like to see, just let me know, I'll do my best to provide it.

I am thinking the issue is not related to the swap or encryption afterall.

I think we can also rule out the NVMe theory I had before as well, I ran update-initramfs in verbose mode and the output shows the nvme modules being included: [https://pastebin.ubuntu.com/p/myKCRRG962/](https://pastebin.ubuntu.com/p/myKCRRG962/)

I am thinking the issue is related to initramfs or to the update state of my machine maybe. I would like to disable the splash screen on boot and set the mode to verbose so I can see the messages when I am booting up. I sometimes see some text flash by, it might give a clue.

I wonder if trying to remove the kernel which is not working and trying to reinstall it would help.

The other thing I suspect is that the upgrade/update did not complete correctly. The "Pop Shop" shows some updates for my system:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289006&stc=1[/IMG]

But fails to install them with the following error:
```

The following packages have unmet dependencies:
  gnome-shell: Depends: gir1.2-mutter-7 (>= 3.38.4) but 3.38.3-2ubuntu0.20.10.1pop1~1614025450~20.10~5e5ece9 is to be installed
               Depends: libedataserver-1.2-26 (>= 3.33.1) but it is not installable
               Depends: libgdk-pixbuf-2.0-0 (>= 2.22.0) but it is not installable
               Depends: libmutter-7-0 (>= 3.38.4) but 3.38.3-2ubuntu0.20.10.1pop1~1614025450~20.10~5e5ece9 is to be installed

```

There was also some problems before I initiated the upgrade to this new kernel in Pop Shop, but I just used apt to update instead hoping to avoid the issue. Maybe this is the cause of the problem.

---

### Post by robo731 on 2021-08-23
I did some more research in the incomplete update vein. I think this is the problem. When I run apt upgrade, it gives the following output:

```

The following packages have been kept back:
  fwupd-signed gir1.2-gdm-1.0 gir1.2-mutter-7 gnome-control-center
  gnome-shell-common gnome-shell-extension-prefs libglapi-mesa
  libnss-systemd linux-generic linux-headers-generic
  linux-image-5.11.0-7620-generic linux-image-generic
  linux-modules-extra-5.11.0-7620-generic linux-system76
  nautilus-extension-gnome-terminal systemd-sysv virtualbox-dkms
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

```

I think I need to run apt full-upgrade if I want to continue updating. I did a dry run of it though and I got the following output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gnome-shell-extension-alt-tab-raise-first-window
  gnome-shell-extension-always-show-workspaces
  gnome-shell-extension-pop-shop-details
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic linux-system76 pop-desktop
The following packages have been kept back:
  fwupd-signed gir1.2-gdm-1.0 gir1.2-mutter-7 gnome-control-center
  gnome-shell-common gnome-shell-extension-prefs libglapi-mesa
  libnss-systemd linux-headers-generic nautilus-extension-gnome-terminal
  systemd-sysv
The following packages will be upgraded:
  linux-image-5.11.0-7620-generic linux-image-generic
  linux-modules-extra-5.11.0-7620-generic virtualbox-dkms
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  pop-desktop linux-system76 (due to pop-desktop)
4 upgraded, 0 newly installed, 3 to remove and 11 not upgraded.
Remv pop-desktop [1.6.0~1625267683~21.04~ac0465f]
Remv linux-system76 [5.11.0.7620.21~1624379747~20.10~3abeff8]
Remv linux-generic [5.11.0.7620.21~1624379747~20.10~3abeff8]
Inst linux-image-5.11.0-7620-generic [5.11.0-7620.21~1624379747~20.10~3abeff8] (5.11.0-7620.21~1626191760~21.04~55de9c3 Pop!_OS PPA:21.04/hirsute [amd64]) [linux-image-generic:amd64 ]
Conf linux-image-5.11.0-7620-generic (5.11.0-7620.21~1626191760~21.04~55de9c3 Pop!_OS PPA:21.04/hirsute [amd64]) [linux-image-generic:amd64 ]
Inst linux-modules-extra-5.11.0-7620-generic [5.11.0-7620.21~1624379747~20.10~3abeff8] (5.11.0-7620.21~1626191760~21.04~55de9c3 Pop!_OS PPA:21.04/hirsute [amd64]) [linux-image-generic:amd64 ]
Conf linux-modules-extra-5.11.0-7620-generic (5.11.0-7620.21~1626191760~21.04~55de9c3 Pop!_OS PPA:21.04/hirsute [amd64]) [linux-image-generic:amd64 ]
Inst linux-image-generic [5.11.0.7620.21~1624379747~20.10~3abeff8] (5.11.0.7620.21~1626191760~21.04~55de9c3 Pop!_OS PPA:21.04/hirsute [amd64])
Conf linux-image-generic (5.11.0.7620.21~1626191760~21.04~55de9c3 Pop!_OS PPA:21.04/hirsute [amd64])
Inst virtualbox-dkms [6.1.18-dfsg-5pop0~1624392638~20.10~b904788] (6.1.18-dfsg-5pop0~1624392638~21.04~b904788 Pop!_OS PPA:21.04/hirsute [amd64])
Conf virtualbox-dkms (6.1.18-dfsg-5pop0~1624392638~21.04~b904788 Pop!_OS PPA:21.04/hirsute [amd64])

```

I'm concerned that this combination of removals, withholding and upgrades, might result in a still incomplete state.

---

