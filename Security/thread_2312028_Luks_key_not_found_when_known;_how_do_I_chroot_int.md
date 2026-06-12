---
title: "Luks key not found when known; how do I chroot into a LUKS system?"
date: 2016-02-01
forum: Security
---

### Post by joshua67 on 2016-02-01
My laptop was running both windows 8.1 and Ubuntu 14.04 with the ubuntu luks installation on an msata drive. One day in a bit of an emergency I decided to wipe the stock harddrive containing the windows installation I rarely used and created a luks volume for the entire drive. I then moved my home directory to this newly formatted harddrive. In doing so, while not thinking in the least, I deleted the grub for the ubuntu install on the other drive.

Now, after restarting the computer I was unable to boot ubuntu of course. However, the odd thing is that despite knowing the passphrase for the harddrive which I created in a rush and deleted grub off of I constantly receive the error "no key available with this passphrase" when trying to unlock from a live distro.

I backed up the masterkeys to a drive that was lost, and I am 99% certain I am using the right passphrase with this drive.

I do believe that the ubuntu installation missing grub may have this key stored in it still as I checked the option to remember forever. With 1% doubt, I would like to chroot into the broken system and try to see if it stored.

Outside of me possibly using the wrong passphrase (some time has passed since the drive was created and the blunder happened) I would greatly appreciate the assitance in verifying there are no issues with the luks drive with my home directory.

---

### Post by TheFu on 2016-02-03
I've never been able to re-boot a whole system encrypted Linux. I looked and looked for guides on how to manually setup all the different parts to do this. They were all out of data. None worked.

However, there is good news.  You should be able to mount the LUKs encrypted volume and see what it contains, then mount those items and get the data off.
For example, I bricked a chromebook with an encrypted SSD inside it.  Pulled that SSD out, then put it into a USB3 enclosure.  Then I use something like these commands to gain access to that data:

```
# How-to mount old C720 Luks encrypted storage
# Assume: sdf5 is the partition to be opened (usually logical partition)
# Assume: LVM is used
# $ sudo lsblk
# NAME                           MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
# sdf                               8:80   0 119.2G  0 disk  
# &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
# &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
# &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
#   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
#     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
#     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
#     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
# 
# sudo cryptsetup luksOpen /dev/sdf5 c720
# sudo mkdir /mnt/root /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-root /mnt/root
```

Obviously, you'll need to modify all the commands for your situation, but this should provide an idea of how to proceed.  Oh - and I think I had to do some LVM commands to get the VGs recognized the first time. Thereafter, it wasn't needed.
Hope this helps.

---

