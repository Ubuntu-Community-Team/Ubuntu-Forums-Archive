---
title: "bare metal backup of mdadm"
date: 2011-03-03
forum: Server Platforms
---

### Post by garethsimpsonuk on 2011-03-03
I'm looking for a way to do a bare metal backup of our server using a tool such as ghost or clonezilla. The limitation is that / is on an mdadm raid 5.

The only relevant info I could find on clonezilla's site was:

# Software RAID/fake RAID is not supported by default. It's can be done manually only. 

Not quite sure what this means though.

Does anyone have any suggestions?

Many thanks

---

### Post by garethsimpsonuk on 2011-03-08
bump

---

### Post by disabledaccount on 2011-03-08
"Bare metal" image of /root can be done only from live cd / another installed system. It is not sufficient to remount filesystem as read-only, because md still can write to drives. If this is not a problem (powering off the system), then such image can be made very easily with dd.
The most reliable and fastest way is to make separate images of array members.
Reliable, because you can restore array even if one of image files becomes broken (in fact number of needed files reflects raid level fault tollerance)
Fastest, because you can run several dd processes for several HDDs at the same time (that makes sense only if you have fast enough destination storage)

Speed of dd: none of presently manufactured HDDs is using 512 byte blocks - its just virtual mapping for LBA compatibility. You should use bs values that are multiply of 4096 (or 4K) and something like 1MB or 8MB would be fine.

...and if You need real bare metal backup, then use "read sector" function from hdparm :)

---

### Post by garethsimpsonuk on 2011-03-09
Thanks for the reply Tomazzi. Sounds good but I'm really looking for an out of the box solution such as Clonezilla, Ghost or Acronis true image.

Powering down the system is not a problem (although it would be nice to be automated) I am just unsure of whether these image based backup systems support mdadm.

Also what I would like to do is create directory exclusions e.g. do not include /srv/* as these shares are backed up using file based backup. I just need a backup of the core system.

Any recomendations on a tool to do this?

Thanks

---

### Post by disabledaccount on 2011-03-10
> **garethsimpsonuk said:**
> Also what I would like to do is create directory exclusions e.g. do not include /srv/* as these shares are backed up using file based backup. I just need a backup of the core system.So You can't create "bare metal" backup. This is generally bad idea to put user/client data files on /root partition. Directory exlusion(s) need support for filesystem structure in backup software, and this is exactly what prevents making block-layer backup. In fact, safe exlusions would need full filesystem core to be implemented (f.e. due to journal data presence).

You can copy or rsync directories preserving permissions and (re)install bootloader on new drive - however any mistake can result in broken system. Other solution is to make backups of all config files and data, repartition the drive then reinstall the system. It's also worth to consider making two separate arrays for /root and data instead of partitioning single md array.

---

### Post by garethsimpsonuk on 2011-03-10
Thanks Tomazzi that makes perfect sense. If exclusions aren't possible we will just have to backup the whole array (3TB).

In hindsight, placing the /srv directory on its own array would have been beneficial but we are stuck with it now. Any idea how much disk space a 3TB array (50% full) will take?

So if I copied (using live cd) "/" excluding "/srv" what would I be missing? in order to restore and how would I go about restoring this?

Thanks

---

### Post by disabledaccount on 2011-03-11
Disk image compression ratio depends on contents - f.e. mp3, jpg pictures and movies wont compress at all.

You must preserve permissions and ensure proper symlinks replication - thats all. 
Restoring means copying everything back to new partition and reinstalling bootloader (grub or whatever you have). You will also need to correct /etc/fstab entries to match new filesystem UUID or different device mapping (/dev/sd<x>)

---

