---
title: "Ubuntu 10.10 Server with Intel Raid cannot boot."
date: 2011-04-14
forum: Server Platforms
---

### Post by Robinmontreal on 2011-04-14
Hello all... i just went through a standard install of Ubuntu server 10.10 via CD. I installed it on a Supermicro dual quad Xeon core , with **Intel Matrix Storage** RAID1 Only two disks each on a Seagate 2 TB 7200RPM  SATA II.


I went through the whole install without issues at all, but only after its time for the reboot at the end of the install it did not come back up. It drops to Busy Box and shows the following message.

Gave up waiting for root device. Common Problems:

- Boot args (cat /proc/cmdline)
- Check rootdelay=(did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/c7f05983-e7dc-4c2d-b0c1-b82da2b1cefe does not exist.
Dropping to shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Booting into recovery mode does not do anything i get the same error. I cannot mount the device either when booting from live CD or from recovery mode...

Doing a ls -la /dev/mapper/* gives me this
/dev/mapper/isw_bfbihcid_Volume0 -> ../dm-0

doing a blkid gives me
/dev/sda: UUID="^P^[Z^PM-^F&#9830;M-^B&^P^[Z^PM-()X^PM-^H6Z^PM-^?M-^?M^-?M-^?" TYPE="ddf_raid_member"

Same for sdb, its too long to write  :)

Here is a partial dmegs 

GPT:Alternate GPT header not found at end of the disk.
GPT:3907022847 != 390729167
GPT: Use GNU Parted to correct GPT errors.
GPT:Primary header thinks Alt. header is not at end of the disk.
GPT:Alternate GPT header not at the end of the disk
GPT:3907022847 != 390729167
device-mapper: dmraid45: initialized v0.2594b

doing a cat /proc/cmdline gives me
BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-server root=UUID=c7f05983-e7dc-4c2d-b0c1-b82da2b1cefe ro quiet

Doing a cat /proc/modules ( i left out s few things i think are not related)

dm_raid45 75026 0 - live 0xffffffffa0039000
xor 4709 1 dm_raid45, live 0xffffffffa0000000

Keep in mind i had to copy these errors message from the screen, so there might be a typo, but i do not think so....

So what should i do next?
I tried re-installing at least 5 times, i even thought the partition was to big for / so i shrunk it to 500 gigs, still a no go...

Any help appreciated..

Thanks in advance and to all a good day!

Rob Morin 
Montreal, Canada

---

