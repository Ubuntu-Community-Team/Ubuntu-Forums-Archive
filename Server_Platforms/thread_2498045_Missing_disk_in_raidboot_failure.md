---
title: "Missing disk in raid/boot failure"
date: 2024-05-27
forum: Server Platforms
---

### Post by daves00 on 2024-05-27
Hi,

My ubuntu 22 system has the following disk configuration (from lsblk):

NAME   FSTYPE   FSVER LABEL       UUID                                 FSAVAIL FSUSE% MOUNTPOINTS

sda                                                                                   
&#9500;&#9472;sda1                                                                                
&#9500;&#9472;sda2 btrfs                      141fcdc4-1cfc-4b4f-b4f1-d3a5201aa1ad  219.4G    24% /var/snap/firefox/common/host-hunspell[INDENT=12]/
[/INDENT]
 &#9500;&#9472;sda3 ext4     1.0               72c362c4-dd47-4df9-aa97-428030bae5e0   89.7G     4% /home
&#9492;&#9472;sda4 swap     1                 3a32f713-1da3-4ccb-9a80-078a7e452853                

sdb    btrfs          mediastore1 7dccef16-3ef6-474b-9107-be30f0c65d1b                
sdc    btrfs          mediastore1 7dccef16-3ef6-474b-9107-be30f0c65d1b    1.4T    66% /srv/nfs4/Music[INDENT=13] /mnt/mediastore
[/INDENT]
 sdd    btrfs          mediastore1 7dccef16-3ef6-474b-9107-be30f0c65d1b     

       
the btrfs mediastore1 is raid 1 with 3 disks. I know 3 aren't needed but  i knew one would fail soon due to age (from my previous pair or raid 1  disks)

a disk is failing so time to replace it, however when i swapped the disk  Ubuntu wouldn't boot which seems to be due to /etc/fstab options which i  have just realised are set to defaults for mediastore1.


# /etc/fstab: static file system information.
# <file system>                 <mount point>   <type>   <options>           <dump>      <pass>
# 
UUID=141fcdc4-1cfc-4b4f-b4f1-d3a5201aa1ad     /               btrfs   defaults,subvol=@     0           1
UUID=72c362c4-dd47-4df9-aa97-428030bae5e0     /home           ext4    defaults                0           2
UUID=359e40d2-d34f-419e-88e7-1b312c732aa6     none            swap    sw                  0           0

# New mediastore/btrfs raid drives
LABEL=mediastore1                 /mnt/mediastore btrfs defaults            0         0

# NFS shares 
/mnt/mediastore/music2                /srv/nfs4/Music    none    bind            0        0


1. Is the solution given in this old question still the best solution? [https://ubuntuforums.org/showthread.php?t=2387008](https://ubuntuforums.org/showthread.php?t=2387008)

2. If I implement the old solution presumably the NFS shares moves to the same place

3. Is there a better solution or specific options i can use in the fstab so I can keep everything in the fstab.

Thanks in advance
Dave

---

### Post by MAFoElffen on 2024-05-28
I read that solution, asked my self how that was the same(???)

That person had 3 drives, with the system divided up between those 3 drives, with no RAID present. Which is different than your, your had 3 drives with a partition on each that is a 3-way RAID1.

In a RAID1 as root (/), unless you also create and sync an EFI partition on each of those mirrored drives, then whichever drive the EFI partition is on, then if that drive fails, it will fail until some kind of EFI partition is found...

What I see in your output, is that only one EFI partition exists, which I assume is /dev/sda1. If /dev/sda fails... Well.

If it did have 3 EFI partitions, then you just set the Boot order to which one you want to use. 

Of course you, what that requires is installing Grub 3 times, to populate all EFO partitions for it to get the right UID's worked out for that.

Another thing I learned (first) with doing ZFS-On-Root, with mirrors, it this:
> 
Disable grub-initrd-fallback.service
 For a mirror or raidz topology:```

sudo systemctl disable grub-initrd-fallback.service
sudo systemctl mask-grub-initrd-fallback.service

```
This is the service for /boot/grub/grubenv which does not work on mirrored or raidz topologies. Disabling this keeps it from blocking subsequent mounts of /boot/grub if that mount ever fails.

 Another option would be to set RequiresMountsFor=/boot/grub via a drop-in unit, but that is more work to do here for no reason. Hopefully [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1881442") will be fixed upstream
Next is the fstab file entries. To have an EFI partion to mount into /boot/efi, I use UUIDs of all 3 partions, with having the primary uncommented, so it is the primary, then the other 2 lines (with the other two UUIDs) commented, until I point it to that partition. That way I don't have to fumble around looking those up after a drive failure. 

For mount options in those fstab entries, for mirrored drives, I use
```

UUID=<UUID_1>  /boot/efi  vfat defaults,nofail,errors=continue,umask=0077 0 0
#UUID=<UUID_2>  /boot/efi  vfat defaults,nofail,errors=continue,umask=0077 0 0
#UUID=<UUID_3>  /boot/efi  vfat defaults,nofail,errors=continue,umask=0077 0 0

```
Another tip I learned with mdadm, LVM2, ZFS & BTRFS... Use either UUID, label or a unique disk id (such as /dev/disk/by-id, /dev/disk/by-uuid, /dev/disk/by-label), instead of using /dev/sdxy. When "x" in that can change over a boot or reboot. 

Also, even though mdadm, LVM2, and ZFS can be created 'whole disks' in a create, I always put those (storage containers) into a partition I created. That way I have total control of the boundaries, and size of a bound storage container, that it will exist within. Over the years, I have had, and had to help people recover there systems, when they used the whole disks, and installed those within an unbound disk, as a storage container. Trust me. It is simpler, and safer.

---

### Post by daves00 on 2024-05-29
Thank you for the above -  I should have specified that my setup that  root is not on mediastore and you have highlighted it is on sda, as you  have correctly determined.
I will look into the aspects you have highlighted above, and am sure there are learnings for me.

If  sda dies, well i reinstall Ubuntu which is pretty straight forward for  me. My server doesn'ty have many application on it outside of the basic  setup. It is Ubuntu + Jellyfin (config backed up onto the Raid) + 1  print driver

The purpose behind my config is that the media library won't be lost, hence the raid.


The  issue I am trying to resolve is when the Mediastore1 volume is degraded  that the system will still boot without having to edit fstab; i.e. make  any mediastore1 failure graceful.


Hopefully thats a bit  clearer - and not written at stupid o'clock at night having spent a  couple of hours fidlling with Ubuntu :D

---

### Post by TheFu on 2024-05-29
I don't see any NFS mounts.  Labeling something as NFS in the comments doesn't make it NFS, nor does using a directory name /srv/nfs4.

I know nothing about BTRFS.  Early data loss issues and problems with certain workloads drove me away.

I consider /mnt/ to be for temporary administrative mounts while storage is setup, before end users make any use of it.  That's what the standard says it is to be used for.  Why not just mount storage where you want it to be directly?  If you plan to share it via NFS, then each client system gets to decide where every share will be mounted.

Because I'm stupid, I mount NFS storage exactly the same places on the NFS-servers as I mount them on each client.  Prevents confusion for me.

The NFS server:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-lv_media              ext4  3.5T  3.5T   23G 100% /d/D1
/dev/mapper/istar--vg2-lv_media2            ext4  3.6T  3.6T  2.4G 100% /d/D2
/dev/mapper/istar--vg3--back-lv_media3_back ext4  3.6T  3.6T   31G 100% /d/D3
/dev/mapper/WDBLK_8T-lv_d6                  ext4  3.6T  3.3T  176G  95% /d/D6
/dev/mapper/WDBLK_8T-lv_d7                  ext4  3.6T  1.4T  2.1T  41% /d/D7
```

NFS Clients:
```
Filesystem                                       Type  Size  Used Avail Use% Mounted on
istar:/d/D1                                      nfs4  3.5T  3.5T   23G 100% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.6T  2.4G 100% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   31G 100% /d/D3
istar:/d/D6                                      nfs4  3.6T  3.3T  176G  95% /d/D6
istar:/d/D7                                      nfs4  3.6T  1.4T  2.1T  41% /d/D7
```

My LVM names could be more consistent.  I have backups, not RAID.  I keep those simple too. The client computers don't have access to the backup areas.
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB-istar--back3--a      ext4  3.6T  3.5T  132G  97% /d/b-D1
/dev/mapper/istar--8TB-istar--back3--b      ext4  3.6T  3.6T  6.4G 100% /d/b-D2
/dev/mapper/istar--vg2--back-lv_media2_back ext4  3.6T  3.6T   36G 100% /d/b-D3
/dev/mapper/istar--8TB--B-lv4_back          ext4  3.6T  3.3T  168G  96% /d/b-D6
/dev/mapper/istar--8TB--B-lv5_back          ext4  3.4T  1.4T  1.9T  43% /d/b-D7

```
These are backups for huge storage areas.  Think of it as delayed mirrors.  Daily, versioned, system backups are separate.  End users (and my normal account), don't have access:
```
$ ls /d/b-D7/backups/
ls: cannot open directory '/d/b-D7/backups/': Permission denied

```
Backups need to be secured from casual access.

Be careful using RAID with a failing disk.  Often times, RAID is a great way to have corrupted data written to multiple places concurrently.  You'll want backups to fix that.

---

### Post by darkod on 2024-05-29
I have never used btrfs but this is what I think...

First of all, please post terminal output inside CODE tags, that keeps certain order of text and makes it much more readable.

I think the boot error you get is from the following line in your fstab:
```
# NFS shares
/mnt/mediastore/music2 /srv/nfs4/Music none bind 0 0
```

If I understood correctly, the btrfs filesystem Mediastore1 is local on the same machine, and is mounted at /mnt/mediastore.

If that is so, what is the purpose of the above NFS line in fstab? It's like you are taking a filesystem that is already local and mounted, and try to mount it locally again.

Have you tried to comment out the NFS line and see if it can boot like that?

---

### Post by TheFu on 2024-05-29
I'd guess the goal is to have all NFS shared storage under  /srv/nfs4/ while having extra local storage mounted under /mnt/ for some reason, but I really don't know.  There are probably some different examples that do this, which has led to confusion for what is "standard" and what is "required" and what just happened to be a method selected by the example creators as a way to convey things that aren't necessarily actually stated.

OTOH, IDK.

---

### Post by darkod on 2024-05-29
Yeah, actually I just noticed the "none bind" part in the mount line.

But like it was previously said, if you want to export /mnt/mediastore/music2 then you just define it lke that in the nfs exports config. You don't need to create a "double" mount.

The boot error might also be from the btrfs mount line in fstab, I haven't worked with btrfs so I don't know how the system would react if one data disk goes down. But if it is in raid or any type of redundancy, and especially since we are talking about data disks and not OS disks, I would expect the system to be able to boot if you lose one disk. Otherwise it sort of beats the purpose...

---

### Post by MAFoElffen on 2024-05-30
> **daves00 said:**
> Thank you for the above -  I should have specified that my setup that  root is not on mediastore and you have highlighted it is on sda, as you  have correctly determined.
I will look into the aspects you have highlighted above, and am sure there are learnings for me.

If  sda dies, well i reinstall Ubuntu which is pretty straight forward for  me. My server doesn't have many application on it outside of the basic  setup. It is Ubuntu + Jellyfin (config backed up onto the Raid) + 1  print driver

The purpose behind my config is that the media library won't be lost, hence the raid.

The  issue I am trying to resolve is when the Mediastore1 volume is degraded  that the system will still boot without having to edit fstab; i.e. make  any mediastore1 failure graceful.

Hopefully that is a bit  clearer - and not written at stupid o'clock at night having spent a  couple of hours fiddling with Ubuntu :D

Then if the priority is your media files. I think other Members here will agree with me, especially TheFu, one of "my things" I have preached since the 90's, is to try to use the concept of a 3 tier distributed processing system... with your OS and applications in one tier, your "data" in the next tier, your presentation in the third tier. As is the best choice, of course your data should and is your priority.

If you just set up your OS in one partition, on one disk... So what if it fails. Easy to install or restore in no time at all. Listen to TheFu on what config files to backup. He uses Jellyfin himself. He can install a new system (OS), and restore his configs in 20 minutes. (My configs are more complicated so take a bit longer...) If that were on RAID, it would take much longer to build the array... To even be able, to then install or restore... Some times, planned obsolescence tat can be switched out easily and quickly, is better than an armored sloth.

Your two other drives? Mirrored, but Look into a ZFS mirrored vdev. for your data... If one drive fails, it will still be up and running. If you do not have a hot-swap, as long as your spare was seen by BIOS before the failure, you can even change out the drive, and resilver the mirror, live, without even rebooting.

Or your original idea of an mdadm mirror, which would reassemble with the data offline.

Lots of options available. That is the thing with Linux. 100's of ways to do the same thing.

Remember: RAID does not take the place of backups, but it will add another layer of protection. In mdadm, it is faster to create new and restore, than to try to repair. That comes from years of being a Systems Admin. I've had a lot of dirty hands on-practice at this, did some research beyond to see what would be best for me, and chose what will got me back up the fastest. That is where server priorities lie--- Uptime, providing those services.

---

### Post by daves00 on 2024-05-30
Thanks for all of the above, and i may have used some incorrect terminology. I am far more used to windows than linux.

You have given me plenty to look into - many thanks.

NFS  - I added an NFS share (or Bind), to music2, and this is the line the  gui tool placed in fstab autoamtically. A convoluted reason - my server  is running SMB 2 & 3; I have some Sonos speakers that only support  SMB1. I wanted to have access via SMB 1, read only to just the music2  folder. I have a raspberry Pi, running raspian that - this connects to  the NFS share, and also runs SMB 1 to then share this with the Sonos  speakers. All of this is locked down by IP. My intent is that this is  mroe secure than running SMB 1 on the server. The mediastore 'volume'  does have sensitive data elsewhere on the disk. Hence this is a work  around to reduce risk regards the SMB1. I'llr eview the config of this  in line with above comments.

Backups - yes, all in place

I  had a bad experience with mdadm and lost a raid array. Sufficiently  long ago I don't recall the details, but scarred enough to not like/use  it.

Re darkod's comment 'But if it is in raid or any type of redundancy, and especially since we  are talking about data disks and not OS disks, I would expect the system  to be able to boot if you lose one disk. Otherwise it sort of beats the  purpose...' - and that is exactly the issue i am trying to resovle.

Due  to limitations on this old HP Microserver when a disk starts failing, I  have to shutdown and swap the disk over. No hot swap, and no spare sata  connections.


One of the comments above mentioned the  standard way to set up things - a couple of links where i can find this  info would be very helpful.

Thanks All

---

