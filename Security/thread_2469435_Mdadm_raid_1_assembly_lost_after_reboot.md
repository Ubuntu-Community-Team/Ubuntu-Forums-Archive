---
title: "Mdadm raid 1 assembly lost after reboot"
date: 2021-11-29
forum: Security
---

### Post by ilmazzo on 2021-11-29
Hi there,

I was upgrading my raid 1 2x2TB with 2x8TB so I made these steps:

- Connected on sata the new disks
- Created a new raid 1 software on these disks (md1)
- Created a new filesystem on the new raid 1 and copied data from old raid (md0) to new one (md1).
- shutdown pc
- removed physically old disks
- started the machine again

and there it comes the problems:
- got stuck into recovery mode because md1 was not ready (!)
- went into disks info and saw that the system remapped my new drives on the old letters because the old disks where disconnected!
- Ok so I recreated the raid again on the new disks: the data were still present on the raid filesystem (ext4) and after other 10 hours of syncronizing the raid I got the data accessible.
- No matter what I do: after every restart md device disappers and I have to syncronize again the array , I get the data on the raid again and I can mount it to the /mnt/md127 or whatever I want ... the only thing that is changed is that I don't get ubuntu to get into recovery mode again , I get a normal boot but still no array available...

I'm using the same guide I used years ago to setup it the first time with the 2x2TB drives:

[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)

Any hint would be appreciated.

Thanks!

---

### Post by TheFu on 2021-11-30
Some facts please?

Contents of /etc/fstab? - at least related to the mount of RAID devices.
**sudo mdadm  --detail --scan**

---

### Post by ilmazzo on 2021-12-01
yep you are right sorry

[I]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/brancaleone--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=56b207a7-5dad-49ba-ba0e-6e42a6b9e0c5 /boot           ext2    defaults        0       2
/dev/mapper/brancaleone--vg-swap_1 none            swap    sw              0       0

#auto mount soft raid
/dev/md127 /mnt/md127 ext4 defaults,nofail,discard 0 0[/I]

--------------------------------------------------------------------------------------------------------------

 blkid
[I]/dev/sda1: UUID="56b207a7-5dad-49ba-ba0e-6e42a6b9e0c5" TYPE="ext2" PARTUUID="2e501cb8-01"
/dev/sda5: UUID="MYhRna-gNbE-9u4o-6LkA-oo53-terv-pVfd20" TYPE="LVM2_member" PARTUUID="2e501cb8-05"
/dev/sdb1: LABEL="raiddisk1" UUID="3BC6D6B072A9F5CD" TYPE="ntfs" PARTUUID="8bdd9571-aae5-4d3c-985c-85db3bcd07b1"
/dev/sdc1: LABEL="raiddisk2" UUID="07EF1F5036335BF6" TYPE="ntfs" PARTUUID="1f0ba522-088f-4931-89f8-3bb4168d352c"
/dev/mapper/brancaleone--vg-root: UUID="ad6dd84b-a549-4f5a-ba26-15507903e316" TYPE="ext4"
/dev/mapper/brancaleone--vg-swap_1: UUID="b06d1561-10c4-4d8b-96fe-870cfb2b76b3" TYPE="swap"
[/I]
md127 is gone...because I rebooted it.

**"sudo mdadm  --detail --scan" **it doesdo nothing....no outputs, no activity in /proc/mdstat......

thanks!

---

### Post by TheFu on 2021-12-01
If 
```
sudo mdadm --detail --scan
```
shows nothing, the there isn't any array connected. Cannot mount something that isn't connected.

Is there a reason you use mdadm and LVM?  LVM can do a few different RAID types. Why not take advantage of using 1 tool?  If you use LVM, then you have the lvchange and lvconvert and pvmove and whole lvm snapshot capabilities too without the same overhead that running both mdadm AND lvm on the storage would bring.
```
$ sudo lvconvert --type raid1 .... 
```
Lots of good information in the different LVM manpages.
Or jump to using ZFS for data (not ready for the boot-OS storage) like all the new kids are doing.

Plenty of options.  mdadm is so 2005. ;)

Of course, if you prefer mdadm, go for it.  Get the array recognized. That would be the first step.

---

### Post by ilmazzo on 2021-12-02
> **TheFu said:**
> If 
```
sudo mdadm --detail --scan
```
shows nothing, the there isn't any array connected. Cannot mount something that isn't connected.

Is there a reason you use mdadm and LVM?  LVM can do a few different RAID types. Why not take advantage of using 1 tool?  If you use LVM, then you have the lvchange and lvconvert and pvmove and whole lvm snapshot capabilities too without the same overhead that running both mdadm AND lvm on the storage would bring.
```
$ sudo lvconvert --type raid1 .... 
```
Lots of good information in the different LVM manpages.
Or jump to using ZFS for data (not ready for the boot-OS storage) like all the new kids are doing.

Plenty of options.  mdadm is so 2005. ;)

Of course, if you prefer mdadm, go for it.  Get the array recognized. That would be the first step.

I don't even know what LVM is and I'm not sure why are you saying that I'm using both, can't see any reference in the output I paste here......

I expected that configuring mdadm.conf would be the only thing to do to setup the array as you said....I forgot yesterday to put the cat of it

After the array is assembled I make the tee command to append on the mdadm.conf the new array details showed by mdadm --scan --detail as explained in the guide above..... 

So mdadm.conf should instruct mdadm that a array is there and through fstab I should have the md127 dev mounted automatically on the mnt/md127 folder, so I guess the issue is within mdadm :(

---

### Post by TheFu on 2021-12-02
> **ilmazzo said:**
> I don't even know what LVM is and I'm not sure why are you saying that I'm using both, can't see any reference in the output I paste here......

I expected that configuring mdadm.conf would be the only thing to do to setup the array as you said....I forgot yesterday to put the cat of it

After the array is assembled I make the tee command to append on the mdadm.conf the new array details showed by mdadm --scan --detail as explained in the guide above..... 

So mdadm.conf should instruct mdadm that a array is there and through fstab I should have the md127 dev mounted automatically on the mnt/md127 folder, so I guess the issue is within mdadm :(

The fstab file clearly shows that LVM is being used with a "root" LV and "swap_1" LV.  Run **sudo lvs** if you don't believe me.  Can also run **sudo vgs** and **sudo pvs** to get the full summary of LVM PVs, VGs, and LVs.  
If you'd like to see the total disk layout in a little clearer way, run
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
```

To setup an array using mdadm requires creating the array, laying down a file system on that array device, then modifying the fstab to mount the file system.  This would be the same as for any partition or LV after creation of the device.  15 yrs ago, it was common to use mdadm for RAID, then to create an LVM PV on that RAID array, then create a VG and how ever many LVs (think of LVs as really smart partitions that can be modified while the system is running).  The "killer app" for LVM is to take backups of 100% quiesced "snapshot" LVs. This prevents corrupted backups for things like running DBMSes, but it is for any files that are open and being modified.  The other "killer app" for LVM is the ability to add more space to existing LVs as it becomes needed, while the system keeps running.  In 25+ yrs, I've never been able to guess correctly where storage for any system needs to be made available. LVM solves that.  Only make an LV the size needed for the next 3 months, since resizing up (no down) is trivial and can be accomplished while the system is running.

LVM is a good thing and you are already using it, as you'll see with those commands above. The commands are purely data viewing, not modifying.  That lsblk command is worthy of creating an alias ... though I typically leave off the UUIDs, since I don't use UUIDs with LVM mounts. The fstab above doesn't either.

---

### Post by ilmazzo on 2021-12-02
Ooook I trust you :)

I don't need anything of that tbh, it's a fileserver for my things that share the raid folders thorough SMB on my LAN for other pcs, that's it :) anyway I'll note it in my book "things to read about linux"

I made exactly the steps you are mentioning in the first place (I think is the fifth time I recreate the array that i suddenly loose when restart the machine)

mdadm create blablabla on the drives , not the partitions
got the md127 showing up under /dev
created a ext4 partition on it of 8TB
mounted the new partition in /mnt/md127
copied data from old raid partition to new raid partition
updated mdadm.conf
updated fstab
run the init-fsram update

as explained in the guide.

In fact every mdadm --create I do after every reboot will provide me the data copied the first time from the old raid so i can at least skip the 9 hours of copying the data and access it

Question:
- the fstab does not list the sdb and sdc disks which are the raid "members", nor the md after it has been created. The only references about the md I can recall are in the mdadm.conf. Is this ok in your opinion?

Thanks again! :)

---

### Post by TheFu on 2021-12-02
Always create a partition, specifically sized, to hold the mdadm array.  Using the whole drive is NOT a best practice for a number of reasons. Replacement disks from other vendors can be sized exactly correct. There are other reasons when a RAID needs some help too.  Without a partition table, there are some tools that just don't work.

You must manually edit the fstab.  Nothing in that file is automatic. Use **sudoedit**.  It has probably been 10 yrs since I use mdadm to create a new array. I don't recall having to ever touch the mdadm.conf file manually.

Also, you probably don't want to leave storage mounted under /mnt/.  That area is for admin work ... like you've been doing. Perfect use.  But the forever mount location should be somewhere else.  If you use snap packages, the practical answer is to mount under /media/ (even if that is technically a wrong answer).  There's a point where being "right" is less important than having something that works.  If you don't know whether you use snaps, then it is almost 100% likely that you will in the future, even if you don't currently. I'm not a fan of snaps. About 80% of the ones I've tried fail to work for different reasons. Alas, I'm forced to use at least 1 snap - I like lxd containers and the code for that is only shipped as a snap.  Once in the last year, it got broke and I isn't letting me delete a test snap currently, so it is not perfect. I cannot tell if the problem is with the snap or the lxd code.  So many other snap packages just don't work that I don't trust them.  The people who designed the entire snap process seem to think that computers can be treated like smartphones and might have 2 storage devices at most.  That just isn't true in my situation or in corporate environments.  For a very long time snaps didn't work with NFS ... then they got them working, but only if the storage was located in the snap-approved subdirectories.  IF I'm an enterprise with 200 external storage mounts, I'm not going to put them all under /media/ and I'm certainly not going to put 50K user HOME directories under /home/ when we've had them split up under /u/ storage for the last 30 yrs.  snaps actually have hard coded /home/ inside when they should trust the LDAP returned passwd DB values for HOME directories.

After boot, you can look in /proc/mdstat to see the status for any mdadm arrays.

---

### Post by ilmazzo on 2021-12-02
Ok so let me translate

Since partitions of the two raid-disks are not shown up in the fstab I should erase them and create two new partitions, assemble the raid on the just-created partitions instead of whole hdd reference, adjust fstab accordingly and see what happens?

Thanks for the advices regarding mount points :)

---

### Post by TheFu on 2021-12-02
> **ilmazzo said:**
> Ok so let me translate

Since partitions of the two raid-disks are not shown up in the fstab I should erase them and create two new partitions, assemble the raid on the just-created partitions instead of whole hdd reference, adjust fstab accordingly and see what happens?

Thanks for the advices regarding mount points :)

The translation is off and a little scary.  All sorts of partitions won't show up in the fstab that still exist and have valuable data.
But you are using LVM, so all the fstab entries with /dev/mapper/ point to LVM LVs <---- those are "Logical Volumes".  If you delete the partition where they reside, it will be a very bad day.
What I wrote was:
> Always create a partition, specifically sized, to hold the mdadm array.
Since you are using RAID1, this means that at least 1 partition on each of the 2 HDDs needs to be identically sized.  
The fstab mount should point at a /dev/md{something} device.

---

### Post by ilmazzo on 2021-12-14
Finally i've solved!!!!!

I lost all the data but okay, I'll copy them again ...

The only things I did different this time were:

- created the mdadm array to partitions instead of whole disks
- activated the "raid" flag on the disks (but I was already seeing them as "raid member" in the disks utility but, ok...) maybe this was just a placebo, dunno
- created new filesystem ext4 on the md127 device created by mdadm
- mounted it through fstab to a mnt folder

at the first reboot I could not see the mounted raid automatically (except on the fstab I thought I put the right UUID and stuff) but I noticed the md127 device still present os manually mounting it I got again the raid partition! In X I used the disks utility and set to automount the partition from there and bum! I got it mounted every restart I did. GG!!!!

Thanks for your support TheFu ):P

---

