---
title: "unable to boot bare metal restore from RAID1 and LVM"
date: 2010-11-28
forum: Server Platforms
---

### Post by ReTheOff on 2010-11-28
I appreciate any assistance you may have. I have been struggling with this for days.  

Main problem, need to boot on new, but identical hardware. (secondary server)  I have used fsarchiver to backup /boot, rootfs, /usr, and /var.  After I created new md0 and md1 drives, and also new lvm volumes, I restored with fsarchiver.

Then, using either sysrescuecd or the original install cd in rescue mode, I mounted and chrooted into the newly recoverd system.  Then I run update-grub, but I get an error like so:
```
grub-probe: error: no mapping exists for `md0'
```
I am unable to run grub-install either.

I have tried mondorestore, too, before trying fsarchiver. Using other version of sysrescuecd, and not sure how, but I would only boot to busybox and the system wouldn't find any /dev/mapper devices.  But nevermind that for now, I just need to be able to install grub on the mbr at this point.

Little bit of system background:
Using Ubuntu x64 server 10.04.
Original system is working fine.
Have disk layout:
2 - 1tb drives (/dev/sda and /dev/sdb)
/dev/md0 is 1g, on sda1 and sdb1
/dev/md1 is about 900g, on sda5 and sdb5
/dev/md0 is ext3 mounted as /boot
LVM (on /dev/md1, and LV's formatted as ext4):
/dev/mapper/vg1-root - /root
/dev/mapper/vg1-usr - /usr
/dev/mapper/vg1-var - /var
(/tmp, /home, /swap on LVM as well)

I scripted the recovery from USB disk.(/dev/sdd1) From sysrescuecd, where I have fsarchiver available.  
The script starts by removing any vg1 VG's, then PV's. 
Then stops md0 and md1.
Then uses dd to write zeros on drive, in an effort to remove any existing metadata.
Then uses sfdisk to create partitions from saved file.
It then creates the md0 and md1.
Finally creates PV's, VG, and all the LV's.

After all that, I run another script to restore all the system data only using fsarchiver,which completes normally.

Then I a mount and chroot.
I update mdadm.conf:
```
mdadm --detail --verbose --scan > /etc/mdadm/mdadm.conf
```
Maybe I don't need to do that though. It was just something I tried while troubleshooting.

Lastly, I run update-grub and receive the error above.  I was able to run and install grub to the mbr before, however it only booted to busybox and couldn't find any LVM's. (but they existed)

Aside from the grub-install issue, my other question is this. What's the best way to do this? To restore to a new server when you have LVM over RAID?  Seems like all the docs I find cover LVM, but not RAID, or the other way around, they cover RAID, but no LVM.  Anyway, there must be a simple way to recover my server(s) using this configuration, which seems quite common. (without using some expensive 3rd party product)  Mondorestore is a perfect example though. It would be perfect if it only supported LVM over RAID. I couldn't get it work at all, even if I created all the RAID/LVM volumes manually first and using their current version.

My ultimate goal is A) for my personal/business use to configure multiple servers once and reload on secondary hardware. Also B) to do the same thing for my clients server installations, so I can quickly recover the system to new hardware in an emergency. (although this is rare, I'd still prefer to have that ability)  If I have to dump my script, do it all manually, or use something totally different, I am open to alternatives.  I am just getting tired of having to manually rebuild RAID/LVM and install a server and all the same services, it should be mostly script-able, I would think. Cloning doesn't seem to be a good option either, because of the LVM/RAID.

Thanks for any help and advice.

---

