---
title: "Bootable ISO Backups: Best backup solution for encrypted, bootable ISO Disk Images"
date: 2024-08-12
forum: Server Platforms
---

### Post by filtereduser on 2024-08-12
[COLOR=#0C0D0E][FONT=-apple-system][FONT=inherit][FONT=inherit][FONT=inherit]I am running Ubuntu Server 22.04 (amd64) on an intel machine with Full Disk Encryption. It is a server, and therefore I can't risk it not surviving any corruption, data loss, or cyberattacks. Therefore I am looking for a backup solution that can create daily bootable disk images of the running server, and save them to an external hard drive. In case of corruption, I ideally would be able unplug the external hard drive with .img or .iso backups, plug it into another computer, and flash the corrupted drive with the bootable image backup. Then I could just plug in the flashed drive back into my PC, and run a completely intact OS.
[/FONT][/FONT][/FONT][/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system][FONT=var(--theme-post-body-font-family][FONT=inherit]On top of that, I would like for it to be compatible with Full Disk Encryption with LVM, and be able to encrypt the .img backups with FDE as well. Lastly, I want it to also shrink the partitions of the .img files the smallest size so that there is no unused free space in each partition. That way, each backup bootable .img file will only be say, 10GB, instead of 128GB. When the .img file is then reflashed to another drive (using say, balena etcher), the newly flashed drive will automatically expand its shrunken partitions to the full size of the drive when Ubuntu gets booted.[/FONT]
[FONT=inherit]There is a series of scripts that a guy on the Raspberry Pi forums, that do exactly what I am looking for. The backup solution I require is almost identical to [these image file utilities scripts]("https://forums.raspberrypi.com/viewtopic.php?t=332000#p1511694") for the Raspberry Pi. The only exception is that the Raspberry Pi utils don't support fully encrypted disks, and dont offer encryption for the final .img files it produces. Feel free to take a look at the [pi scripts here]("https://forums.raspberrypi.com/download/file.php?id=65508") if you need a better Idea of what I want.
[/FONT]
[FONT=inherit]In summary, I need a backup solution for Ubuntu Server 22.04 (amd64) that can do the following things:[/FONT]

[LIST=1]
[*]Make bootable disk images in .img or .iso format of a Running Live Ubuntu Server, and save them to an external drive.
[*]Can run on an Ubuntu System that has full disk encryption enabled
[*]Can encrypt or password protect the resulting backup .img or .iso files
[*]Can shrink partitions (or at least the root partition) to smallest size possible in each backup .iso or .img file, so that each backup file is much smaller than the running system.
[*]Can automatically expand shrunken partitions (or at least the root partition) upon booting a newly flashed Hard drive.
[/LIST]
[/FONT]
[/FONT][/COLOR]

If there is anyone out there who has suggestions for tools or OS Software that can accomplish my needs, I would be very appreciative.

Thanks you!

---

### Post by TheFu on 2024-08-12
Images/clones are a terrible backup solution and nearly impossible to automate.  Every backup requires a full copy of everything which makes a backup that should take 2 mintues require 90 minutes or longer. Additionally, backing up a running OS is a good way to have corrupt backups.  

You are right to ensure that you have excellent backups when encryption is used.  FDE is only useful when the system is powered off (or the storage container is closed).  When it is open/active, it doesn't provide any special security.

The solution for that is to use LVM snapshots to freeze blocks, then backup the read-only snapshot as you normally would. However, with LUKS and FDE, there are usually 2 partitions that aren't managed by LVM.  I just setup a new laptop with FDE. The disk layout looks like this:
```
$ lsblk 
NAME                TYPE  FSTYPE        SIZE FSAVAIL FSUSE% LABEL MOUNTPOIN
nvme0n1             disk              476.9G                      
&#9500;&#9472;nvme0n1p1         part  vfat          512M  504.8M     1%       /boot/efi
&#9500;&#9472;nvme0n1p2         part  ext4          1.7G    1.3G    12%       /boot
&#9492;&#9472;nvme0n1p3         part  crypto_LUKS 474.8G                      
  &#9492;&#9472;nvme0n1p3_crypt crypt LVM2_member 474.8G                      
    &#9500;&#9472;vgmint-root   lvm   ext4           35G   24.1G    22%       /
    &#9500;&#9472;vgmint-swap_1 lvm   swap          4.1G                      [SWAP]
    &#9492;&#9472;vgmint-home00 lvm   ext4           20G   18.5G     0%       /home

```

The LVs weren't installed like that.  The root LV was over 460GB, which is just crazy to me. There was no home00 LV at all.  Immediately after the installation, I quickly resized the root LV and created a home00 LV of sufficient size for my needs.  I'll probably create a "stuff" LV, since it is a laptop and some different files from other systems will be handy to have on it when away from home and disconnected from all networks.

/boot and /boot/efi aren't encrypted.  BTW, this is a Linux Mind 22 install (based on 24.04) on a laptop, so I didn't really setup the storage the way I would for a server.  I haven't setup backups because the laptop is only a few days old, but I'll get automatic, daily, versioned, pulled backups working in a few days.  My backup server will "pull" all the data, like it does for my other systems.  I need to find my USB3-to-GigE adapter. Using wifi for backups is a challenge due to terrible throughput of all wifi when compared to almost any other wired connection.

I don't use encryption on my Pi computers.  My Pi computers don't have any data on them. They pull data over the LAN when they need it.  I use FDE on laptops.  But I back those up using the same method I use for all my systems. I've posted at least 50 times on backups and recovery here.

You can look up how to use LVM snapshots for your backups here: [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)  In my example disk layout above, only the root and home00 LVs will be capable of having LVM snapshots.  As you can see, I've barely allocated the available storage.  The free storage will be used later and I'll try to have at least 20% unused for snapshot use with backups.  Ignore that LVM is inside a LUKS container.  When I'm done, the daily backups will take less than 3 minutes and the complete system restore will take less than 30 minutes (probably).  It is only when a system has huges amounts of storage on a failed disk that restores take longer, IME.  I've had a 4TB HDD with both data and the OS fail.  The restore took about 26 hours because that's how long it took to get the 4tb of data onto the new HDD.

---

