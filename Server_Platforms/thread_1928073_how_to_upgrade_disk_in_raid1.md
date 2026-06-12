---
title: "how to upgrade disk in raid1?"
date: 2012-02-19
forum: Server Platforms
---

### Post by davidmaxwaterman on 2012-02-19
My computer boots from a RAID1 setup, which is over two 80GB disks. I would like to upgrade this to two 200GB disks.

I'm not 100% sure of the procedure... :

1) mdadm -f one of the drives
2) shutdown and replace it with a 200GB drive
3) boot up in degraded mode
4) add the new drive and let it repair the array
5) repeat for other drive

I guess this will waste 120GB of space - ie just use 80GB as before. How to make it use the rest of the space?

I see from below that I have swap on there too.

Thought I'd ask some experts. Any advice?

Max.
Ubuntu 11.10.
Not sure what info to give, but here's something :
```
/dev/sda1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" UUID_SUB="b623acaa-b427-50a4-faf2-ae62954b89b9" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdb1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" UUID_SUB="9c4beba4-3fa7-fe6d-16a4-493dcb2ba376" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/md1: UUID="2Zxdfy-pQOv-tuFl-beGD-3QqZ-NyJW-NPWGQW" TYPE="LVM2_member" 
/dev/mapper/server-root: UUID="8deb8591-2ffb-4fbc-9953-692ae284d34a" TYPE="ext4" 
/dev/mapper/server-swap: UUID="90e8572f-07f5-4163-9beb-18b945932ebc" TYPE="swap"
```

---

### Post by rubylaser on 2012-02-19
Since it's RAID1, you could fail one device at a time and add bigger devices, and then grow the filesystem, or you could just throw the new disk in the system and from the live cd, dd one of the exiting drives onto the new 200GB drives, then just expand your filesystem after you boot from the new bigger disks.

This second route should be faster to do, and you'll always have your original disks as a backup during the process.

---

### Post by jailbait on 2012-02-19
> **davidmaxwaterman said:**
> My computer boots from a RAID1 setup, which is over two 80GB disks. I would like to upgrade this to two 200GB disks.

I'm not 100% sure of the procedure... :

1) mdadm -f one of the drives
2) shutdown and replace it with a 200GB drive
3) boot up in degraded mode
4) add the new drive and let it repair the array
5) repeat for other drive

I guess this will waste 120GB of space - ie just use 80GB as before. How to make it use the rest of the space?

I see from below that I have swap on there too.

Thought I'd ask some experts. Any advice?

Max.
Ubuntu 11.10.
Not sure what info to give, but here's something :
```
/dev/sda1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" UUID_SUB="b623acaa-b427-50a4-faf2-ae62954b89b9" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdb1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" UUID_SUB="9c4beba4-3fa7-fe6d-16a4-493dcb2ba376" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/md1: UUID="2Zxdfy-pQOv-tuFl-beGD-3QqZ-NyJW-NPWGQW" TYPE="LVM2_member" 
/dev/mapper/server-root: UUID="8deb8591-2ffb-4fbc-9953-692ae284d34a" TYPE="ext4" 
/dev/mapper/server-swap: UUID="90e8572f-07f5-4163-9beb-18b945932ebc" TYPE="swap"
```
Do this.

Attach the new RAID array to the computer, and mount the RAID with a livecd.
Mount the original RAID to somewhere like /target/original, along with the other partitions (i.e. /boot, /home, whatever)

Partition the new RAID array. 
Mount the new RAID array to somewhere like /target/new. Mount all the partitions on the new RAID (i.e. /boot, /home, whatever) to their respective mountpoints in /target/new as well.

Run something like 
```

cp -R -p /target/original /target/new

```

Mount --bind the /sys, /proc, /dev to the respective folders in /target/new

Edit the fstab, install grub,update-grub, and edit /target/new/etc/mdadm/mdadm.conf to reflect the changes (you can find the changes in the livecd version of mdadm (/etc/mdadm/mdadm.conf).

---

### Post by davidmaxwaterman on 2012-02-20
> **rubylaser said:**
> Since it's RAID1, you could fail one device at a time and add bigger devices, and then grow the filesystem, or you could just throw the new disk in the system and from the live cd, dd one of the exiting drives onto the new 200GB drives, then just expand your filesystem after you boot from the new bigger disks.

This second route should be faster to do, and you'll always have your original disks as a backup during the process.

 Is there a variation of this where I can add the new bigger disks to the array, so I have a 4 disk RAID1, then fail and remove the two smaller disks?

Do I need to prepare the new disks in any way? NB, they used to be part of a different array, so I wonder if I need to erase them first.

---

### Post by 1clue on 2012-02-20
If you have LVM in there, you should be able to do it that way.  I've never done it but I can think of 2 things to try:
1:
Make a new array with the new disks.
Add the composite disk to the same volume group.
Retire the other array from the volume group.

2:
Make a new array with the new disks.
Make a new volume group with the new composite disk.
Change the existing partitions to the second volume group.

---

### Post by davidmaxwaterman on 2012-02-21
> **1clue said:**
> If you have LVM in there, you should be able to do it that way.  I've never done it but I can think of 2 things to try:
1:
Make a new array with the new disks.
Add the composite disk to the same volume group.
Retire the other array from the volume group.

2:
Make a new array with the new disks.
Make a new volume group with the new composite disk.
Change the existing partitions to the second volume group.

I'm curious why this depends on LVM. My idea was really to take advantage of the RAID and make it do all the hard work. After the disks have been switched (letting RAID do all the copying/etc), then I just need to grow the file system to fill the extra space.

---

### Post by rubylaser on 2012-02-21
You don't need LVM to grow the array.  mdadm supports growing and shrinking the number of disks and size just fine.  Your filesystem also needs to support growing, but ext4, xfs, or jfs all support growing the filesystem.  And, you would want to zero the superblocks on the disks that used to be in an array.  Something like this.

```
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdd1
```

But, it looks like you have LVM on top of your array based on this.
```

/dev/sda1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" UUID_SUB="b623acaa-b427-50a4-faf2-ae62954b89b9" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdb1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" UUID_SUB="9c4beba4-3fa7-fe6d-16a4-493dcb2ba376" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/md1: UUID="2Zxdfy-pQOv-tuFl-beGD-3QqZ-NyJW-NPWGQW" TYPE="**LVM2_member**" 
**/dev/mapper/server-root**: UUID="8deb8591-2ffb-4fbc-9953-692ae284d34a" TYPE="ext4" 
**/dev/mapper/server-swap**: UUID="90e8572f-07f5-4163-9beb-18b945932ebc" TYPE="swap"

```

Does this show a physical volume for LVM?
```
pvdisplay
```

It should look like this if you are just using mdadm without LVM
```

/dev/sda1: UUID="be0e3084-b6d1-245a-8930-01ba3dbfb1f1" UUID_SUB="eff1d4bf-7964-cdc7-aa7e-2306cbd99dcc" LABEL="mdadm-test:0" TYPE="linux_raid_member" 
/dev/sda5: UUID="a8780300-10c2-4a95-a309-aa5bb5e84769" UUID_SUB="c1be0eb7-42b7-e411-3cb2-3c168f937ba7" LABEL="mdadm-test:1" TYPE="linux_raid_member" 
/dev/sdb1: UUID="be0e3084-b6d1-245a-8930-01ba3dbfb1f1" UUID_SUB="d292fc9e-f0ae-84e6-95c0-b75592784938" LABEL="mdadm-test:0" TYPE="linux_raid_member" 
/dev/sdb5: UUID="a8780300-10c2-4a95-a309-aa5bb5e84769" UUID_SUB="a791feec-510b-d943-e0af-d0db8a54ea67" LABEL="mdadm-test:1" TYPE="linux_raid_member" 
/dev/md0: UUID="bcd086ca-346f-4fc2-8d98-a0fa763311a0" TYPE="ext4" 
/dev/md1: UUID="780b5897-9241-43cd-a43e-19a45b7cdb95" TYPE="swap"

```

---

### Post by rubylaser on 2012-02-21
I put together an [example]("http://zackreed.me/articles/64-increasing-the-size-of-mdadm-raid1-disks") of how to do this all via mdadm and not even have to boot from a LiveCD.  You "can" do this all from a running system if you want to.  Just add your two new drives to the existing computer and zero the superblocks before starting.

Again, you appear to be using LVM, so you'd also need to expand your volume group before you expanded the filesystem if you follow my example.  Please, backup your important data before trying this as well.

---

