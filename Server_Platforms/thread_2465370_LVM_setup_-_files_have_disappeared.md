---
title: "LVM setup - files have disappeared"
date: 2021-07-31
forum: Server Platforms
---

### Post by martinjh99 on 2021-07-31
Not sure how this happened but I have a LVM setup which seems to be ok from what I can gather but all the files have disappeared on it.

```


vgdisplay:

  --- Volume group ---
  VG Name               datavg
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               <1.82 TiB
  PE Size               4.00 MiB
  Total PE              476934
  Alloc PE / Size       476934 / <1.82 TiB
  Free  PE / Size       0 / 0
  VG UUID               detds1-pfeV-2Jjj-65oJ-J9oA-pI2g-zYHDEe


pvdisplay:

  --- Physical volume ---
  PV Name               /dev/sdb
  VG Name               datavg
  PV Size               931.51 GiB / not usable 1.71 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238467
  Free PE               0
  Allocated PE          238467
  PV UUID               ohtweF-CVp9-WT0G-0gfq-FLF6-RWDq-fmraXw

  --- Physical volume ---
  PV Name               /dev/sdc
  VG Name               datavg
  PV Size               931.51 GiB / not usable 1.71 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238467
  Free PE               0
  Allocated PE          238467
  PV UUID               DiC5yX-q1QN-ckk8-CFwP-2Fms-bfGe-CSZyke


mount:

/dev/mapper/datavg-lv--0 on /home type ext4 (rw,relatime)

fstab:

UUID=67d38d79-36cf-425d-9473-0e6d0a1464fa /home ext4 defaults 0 0

lsblk:

sda                         8:0    0 931.5G  0 disk
&#9500;&#9472;sda1                      8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0   930G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:1    0   930G  0 lvm  /
sdb                         8:16   0 931.5G  0 disk
&#9492;&#9472;datavg-lv--0            253:0    0   1.8T  0 lvm  /home
sdc                         8:32   0 931.5G  0 disk
&#9492;&#9472;datavg-lv--0            253:0    0   1.8T  0 lvm  /home


du -h: 

/dev/mapper/datavg-lv--0           1.8T  3.4G  1.7T   1% /home



```

Is there a way to get files to show back up?

---

### Post by TheFu on 2021-07-31
Please show the exact command AND the output for everything.

What does **more /etc/fstab** show?
What does **df -Th** show?

Appears LVM was used with out any partitions on sdb and sdc.  That is NOT a best practice.  Always lay down partitions.

Just to make it easier and more compact to see, please post
```
sudo pvs
sudo vgs
sudo lvs 

```too.

What is missing, exactly?  
 One file in /home?   
 One file in /usr/local/etc/xyz/abc/deep/deep/deep/.buried/deep/deep/xyz.conf?

If I'm guessing, it appears the fstab doesn't have a line for the ubuntu--vg-ubuntu--lv mount, but that could be due to not posting complete data. There are other inconsistencies in what was posted, so I'm not really comfortable trusting the data.

---

### Post by martinjh99 on 2021-07-31
```

martin@sienna ~ % sudo pvs
[sudo] password for martin:
  PV         VG        Fmt  Attr PSize    PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <930.01g 8.00m
  /dev/sdb   datavg    lvm2 a--   931.51g    0
  /dev/sdc   datavg    lvm2 a--   931.51g    0

martin@sienna ~ % sudo vgs
  VG        #PV #LV #SN Attr   VSize    VFree
  datavg      2   1   0 wz--n-   <1.82t    0
  ubuntu-vg   1   1   0 wz--n- <930.01g 8.00m

martin@sienna ~ % sudo lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0      datavg    -wi-ao----  <1.82t
  ubuntu-lv ubuntu-vg -wi-ao---- 930.00g

martin@sienna ~ % more /etc/fstab
UUID=578d5d15-68b4-437b-be3d-4cb86f3565e1 / ext4 defaults 0 0
UUID=e9143bef-163d-4188-90d0-f7a4d1591375 /boot ext4 defaults 0 0
UUID=67d38d79-36cf-425d-9473-0e6d0a1464fa /home ext4 defaults 0 0
UUID=F275-8BD9 /boot/efi vfat defaults 0 0
/swap.img       none    swap    sw      0       0

martin@sienna ~ % df -Th
Filesystem                        Type      Size  Used Avail Use% Mounted on
udev                              devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs                             tmpfs     1.6G  3.4M  1.6G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      915G   15G  854G   2% /
tmpfs                             tmpfs     7.8G     0  7.8G   0% /dev/shm
tmpfs                             tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                             tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda2                         ext4      976M  204M  706M  23% /boot
/dev/mapper/datavg-lv--0          ext4      1.8T  3.4G  1.7T   1% /home
/dev/sda1                         vfat      511M  7.9M  504M   2% /boot/efi
/dev/loop0                        squashfs  100M  100M     0 100% /snap/core/11316
/dev/loop1                        squashfs  100M  100M     0 100% /snap/core/11420
overlay                           overlay   915G   15G  854G   2% /var/lib/docker/overlay2/8f9d4c010677c8ede5ac43c3bc3904f78ca68bb2f95e8bb0c1563c9182a41ad5/merged
overlay                           overlay   915G   15G  854G   2% /var/lib/docker/overlay2/02d1ae1377b6d97058212b6b3fad3efbb9cb08fc0f9ada46985122fe1ce5075b/merged
overlay                           overlay   915G   15G  854G   2% /var/lib/docker/overlay2/f110e1deb6cc2468fee99e52e265d391a8c23d4d79a78935d97dfefa75a11000/merged
overlay                           overlay   915G   15G  854G   2% /var/lib/docker/overlay2/f6eadb6e06e2bd56672a814118a6bd142d50e60de5d935fe132fec3fc57be975/merged
overlay                           overlay   915G   15G  854G   2% /var/lib/docker/overlay2/0020bdc0e2078d4b3498665bd193c26990566731c03bc212e049bf63dc262e12/merged
overlay                           overlay   915G   15G  854G   2% /var/lib/docker/overlay2/9b427833df960d12076ec6b6be453defdfbe389f522b19d57b29a61cc3d10e16/merged
shm                               tmpfs      64M     0   64M   0% /var/lib/docker/containers/a748ccbc92bb5b0a5a5706695146fc9101ada4e8a7e29cc8a6f91884db4e636a/mounts/shm
shm                               tmpfs      64M     0   64M   0% /var/lib/docker/containers/8cfdc2e5500848d635dae23b0bd939917f334d68319eb97e5285626dedc7e7f1/mounts/shm
shm                               tmpfs      64M     0   64M   0% /var/lib/docker/containers/06571c88d4dbcbede88ef15188cf6d13d79f4ab00d492a46707d7d1e71c5893a/mounts/shm
shm                               tmpfs      64M     0   64M   0% /var/lib/docker/containers/aa719bcc60c9bbc726e9cd05ad2959263244c5fc78ce89812e6354cf2ece7085/mounts/shm
shm                               tmpfs      64M     0   64M   0% /var/lib/docker/containers/79b51baec9f23aa063d9e0190020fcba39d5b3fd05284b1b72e58c618113e7c4/mounts/shm
shm                               tmpfs      64M     0   64M   0% /var/lib/docker/containers/f51006008fcb8b223322d0366294211134018cc81300e8e52928899e71ce36f0/mounts/shm
tmpfs                             tmpfs     1.6G     0  1.6G   0% /run/user/1000


```

Running Docker here hence the /var/lib/docker mounts...

All my media ripped from CD's/movies, movies downloaded from Youtube, other data stored on the server...

Although df seems to think that the data is still there... probably can't rebuild without losing data can I without actual partitions...?

---

### Post by MAFoElffen on 2021-07-31
What do you mean? If you use the du command in human readable format, it returns the results of estimated space of files in a filesystem... It did exactly what you asked for the "target"... You mistakenly pointed the command to the LV, instead of where is was mounted... I think what you meant was more along the lines of 
```

du -h /dev/sda3/home

```
...where the filesystem within that Logical Volume actually exists... Right?

Basically, think of it like Russian Dolls. Think of the LV as a partition within the Volume Group, which is within the Physical Volume group... But it doesn't mean anything until the LV is mounted somewhere, where you can find it and follow a path to it... It your case, the PV and root LV volume (starts at /dev/sda3)... and the LV that contains your home gets mounted as home, and mounted to the root. So the path of your home would be /dev/sda3/home.

Your path in the command was just pointing to the wrong target where your filesystem and files "are."

EDIT: You could have even shortened the path to /home or ~/ and it will still work... They are most likely still there (high probability)... You just need to follow the bread crumbs to them.

---

### Post by martinjh99 on 2021-07-31
/home is working fine and mounted fine it seems that all the data under /home/martin/data is missing.

---

### Post by MAFoElffen on 2021-07-31
What is the results of 
```

du -h /home/martin/data

df --output=source,used,avail /home/martin/data

```

---

### Post by martinjh99 on 2021-07-31
```

du -h /home/martin/data
4.0K    /home/martin/data/media
8.0K    /home/martin/data

```

Should be a whole load of files and folders under /home/martin/media...  In fact there also should be a whole load of files and folders in /home/martin/data as well...


```

martin@sienna ~ % df --output=source,used,avail /home/martin/data
Filesystem                Used Avail
/dev/mapper/datavg-lv--0  3.4G  1.7T

```

---

### Post by MAFoElffen on 2021-07-31
> **martinjh99 said:**
> ```

[code]
martin@sienna ~ % df --output=source,used,avail /home/martin/data
Filesystem                Used Avail
/dev/mapper/datavg-lv--0  3.4G  1.7T

```
I agree, but there is something really wrong with this... Instead of files, it's showing the LVM LV "again"(???) I do not understand that at all... Almost like there somehow is some kind of loop.

---

### Post by MAFoElffen on 2021-07-31
And if you list the directories they are empty? Or do they loop back and show they LVM LV again?

---

### Post by martinjh99 on 2021-07-31
```

martin@sienna ~/data % pwd
/home/martin/data
martin@sienna ~/data % ls -lR
.:
total 4
drwxr-xr-x 2 root root 4096 Jul 31 04:25 media

./media:
total 0

```

---

### Post by MAFoElffen on 2021-07-31
And is the 1.7TB used the files in there? or other? Or toher files in your home directory?

---

### Post by martinjh99 on 2021-07-31
The missing files should be in /home/martin/data yes

---

### Post by martinjh99 on 2021-07-31
```

 sudo vgcfgrestore --list datavg

  File:         /etc/lvm/archive/datavg_00000-331230425.vg
  VG name:      datavg
  Description:  Created *before* executing 'pvscan --cache --activate ay 8:16'
  Backup Time:  Mon Jun 17 15:13:48 2019


  File:         /etc/lvm/archive/datavg_00001-592638837.vg
  VG name:      datavg
  Description:  Created *before* executing 'pvscan --cache --activate ay 8:32'
  Backup Time:  Mon Jun 17 15:13:48 2019


  File:         /etc/lvm/backup/datavg
  VG name:      datavg
  Description:  Created *after* executing 'vgcfgbackup datavg'
  Backup Time:  Sat Jul 31 04:41:31 2021




```

Think I can rebuild it from these backups/archives without losing data?  Is it worth trying...?

If I do I'm going to follow this page: [https://www.thegeekdiary.com/corruption-or-accidental-deletion-in-lvm-how-to-rebuild-lvm-from-archive-metadata-backups-in-rhel-centos/](https://www.thegeekdiary.com/corruption-or-accidental-deletion-in-lvm-how-to-rebuild-lvm-from-archive-metadata-backups-in-rhel-centos/)  I know its Centos but LVM commands used will be the same yes?

---

### Post by volkswagner on 2021-07-31
I see only 3.4Gig used under /home. I don't think your data is there.

What's the output of:
```
sudo du -h --max-depth=1 /home/yourUserName
```

I think should rebuild your setup. There are a couple of things
that aren't considered best practices. As others mentioned you should
create a partition for your PV.
The second issue I see is using multiple disks/volumes/partitions
for the VG. Although this is a feature it's not recommended. I think
it's like using RAID0 for your data.

Consider getting larger physical disks or break up your mount points
like /data/video and /data/otherMedia (one for each volume group).
The beauty of LVM is the flexibility to grow volumes. You can
create a volume for each media type, genre, etc. then grow
the volumes/directories as needed.

With three physical disks, you should have three VGs.

There is a way to change/fix the setup without reinstalling:
basic steps, we can offer a full plan if you go this route:
```
su root #login as root
mkdir /tmphome #create temporary home directory
rsync -av /home /tmphome #copy data to new location
umount /home #unmount the lvm mount point
mv /home /homeOld #rename original /home
mv /hometmp /home #make new home folder active
nano /etc/fstab (comment out the mount point for /home)

```

Testing > try logging in via ssh as your user and run other tests like
```
df -h
du -h --max-depth=1 /home/
du -h --max-depth=1 /home/yourUserName
```

---

### Post by martinjh99 on 2021-07-31
```

 sudo du -h --max-depth=1 /home
[sudo] password for martin:
3.4G    /home/martin
11M     /home/data
16K     /home/lost+found
3.4G    /home

 sudo du -h --max-depth=1 /home/martin
4.0K    /home/martin/.landscape
8.0K    /home/martin/.ssh
12K     /home/martin/.links2
8.0K    /home/martin/.ansible
6.5M    /home/martin/TTF
387M    /home/martin/.dotnet
4.0K    /home/martin/t4
8.0K    /home/martin/.vim
12K     /home/martin/.spotifydl
60K     /home/martin/.config
12K     /home/martin/.aspnet
4.0K    /home/martin/.emacs.d
16K     /home/martin/snap
16M     /home/martin/.templateengine
12K     /home/martin/.cddb
56M     /home/martin/code
8.0K    /home/martin/data
2.8M    /home/martin/.nuget
8.0K    /home/martin/.docker
13M     /home/martin/.cache
104K    /home/martin/vol
34M     /home/martin/.local
2.7G    /home/martin/docker
8.0K    /home/martin/.gnupg
5.7M    /home/martin/aspnet
4.0K    /home/martin/.caddy
4.0K    /home/martin/sdd
1.3M    /home/martin/.nano
4.0K    /home/martin/tmp
3.4G    /home/martin

```

If I was going to do the way you said with regards to moving the home directory I would have to do it from a rescue disc? At least though stop all the docker containers so I don't confuse anything by moving the data out from under the containers...


If I can get away without installing from scratch I would prefer that as I have a internal network DNS server going...

---

### Post by volkswagner on 2021-07-31
Doing it from a rescue disk would be the cleanest/safest.
Of course, the commands/paths would change but the
general scope would be the same. You could also do
it from recovery mode and make the file system writeable.

If Docker is the only service you are running from /home,
stopping it should be sufficient.

I'm wondering if your data was written while /home
wasn't mounted on the LVM. I would think the
df command would reflect the use in / though.
If you boot a live CD, you'll need to mount
the LVMs to fully diagnose.

---

### Post by martinjh99 on 2021-07-31
To be honest now thinking about it I might add those two other discs to the vg that has the operating system on it so I can still have the extra space and start with the ripping all over again... reconfiguring Samba etc...

Any best practices I should know about? Apart from using partitions instead of whole discs...

---

### Post by martinjh99 on 2021-07-31
> **volkswagner said:**
> 
There is a way to change/fix the setup without reinstalling:
basic steps, we can offer a full plan if you go this route:
```
su root #login as root
mkdir /tmphome #create temporary home directory
rsync -av /home /tmphome #copy data to new location
umount /home #unmount the lvm mount point
mv /home /homeOld #rename original /home
mv /hometmp /home #make new home folder active
nano /etc/fstab (comment out the mount point for /home)

```


Would you mind elaborating the full plan? I want to copy the files across as herew then add the two other discs in the data vg into the one that ubuntu has been installed in if that will work...

---

### Post by TheFu on 2021-07-31
>  Any best practices I should know about? Apart from using partitions instead of whole discs... 

[LIST]
[*]Use /dev/<vg-name>/<lv-name> for mounts in the fstab or autofs.  UUIDs don't convey any useful information.
[*]Don't put media files under /home.  /home needs different sort of backups and media files do.
[*]Don't span LVs over different physical disks, unless you are running LVM in RAID1 mode.  This is a recipe for disaster.  I lost about 80% of my data doing that, before I had *backup religion*.
[*]Don't use samba if there isn't any MS-Windows involved. Use NFS for Unix-to-Unix.
[*]Don't allocate all the storage in a VG to LVs. Expanding an LV is 5 seconds on a running system. I try to allocate only what is needed for the next 3 months.  Empty VG space is useful for snapshots and adding storage where needed, when needed. If it is all pre-allocated out, there's no slack and little flexibility.  Sorta defeats the reason to use LVM at all.
[*]Setup tune2fs to run fsck on the file systems monthly. Probably worth running manually now for all LVs.
[/LIST]

IMHO.

All media servers understand that multiple storage devices need to be merged into a single library and support that without file system techniques.
With LVM, I setup separate VGs for separate physical disks and let the media center handle the merge.  I mount media files using autofs under /d/D1, /d/D2, /d/D3 and all the backups go under /d/b-D1, /d/b-D2, /d/b-D3.  No need to be obtuse.  KISS is good:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-lv_media              ext4  3.5T  3.5T  5.8G 100% /d/D1
/dev/mapper/istar--vg2-lv_media2            ext4  3.6T  3.5T   30G 100% /d/D2
/dev/mapper/istar--vg3--back-lv_media3_back ext4  3.6T  3.6T   74G  98% /d/D3
/dev/mapper/istar--8TB-istar--back3--a      ext4  3.6T  3.5T  115G  97% /d/b-D1
/dev/mapper/istar--8TB-istar--back3--b      ext4  3.6T  3.5T   77G  98% /d/b-D2
/dev/mapper/istar--vg2--back-lv_media2_back ext4  3.6T  3.6T   71G  99% /d/b-D3
/dev/mapper/istar--8TB--B-lv4_back          ext4  3.6T   69M  3.4T   1% /d/b-D6
/dev/mapper/istar--8TB--B-lv5_back          ext4  3.4T   70M  3.3T   1% /d/b-D7
```

Data loss forced me to change my setup.  My backup disks are 4TB, so I don't allow any LVs to be larger than that.

When files disappear, there are a few possible answers:
[LIST]
[*]They were never where you thought. Lack of sleep causes mistakes.
[*]A mount failed.  Check the logs.
[*]fstab/autofs settings were tweaked incorrectly.
[*]A new mount is "over" where the files are stored. They are there, just under a mounted file system.
[*]Accidental deletion.
[*]Nefarious visitor doing bad things.  This can be a remote cracker or house guest. If they have read-write access, all bets are off. Some media center software can be configured for file management. I disable that to prevent other people in the house from deleting stuff. I use read-only NFS mounts for media files, so only direct management on the system with the DAS connection can be used and don't give out accounts on that box.  For example, nextcloud, plex and kodi all have access - just read-only.
[/LIST]

I'd do your fstab this way:
```
$ more /etc/fstab
UUID=e9143bef-163d-4188-90d0-f7a4d1591375 /boot ext4 defaults 0 [COLOR="#FF0000"]1[/COLOR]
UUID=F275-8BD9 /boot/efi vfat defaults 0 0
/dev/ubuntu-vg/ubuntu-lv /     ext4 noatime,errors=remount-ro,defaults 0 [COLOR="#FF0000"]1[/COLOR]
/dev/datavg/lv-0         /home ext4 noatime,errors=remount-ro,defaults 0 [COLOR="#FF0000"]2[/COLOR]
/swap.img       none    swap    sw      0       0
```

and I'd change the swap file to a swap LV.  That probably isn't too important.
```

       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.
```
The settings in your fstab don't allow fsck to be checked unless it got bad enough to fail. Spending 30 seconds every month to run an fsck is a worthwhile preventative step to avoid problems.

Additionally, / LV shouldn't be over 35-45G total. It should just have space for the OS and OS config.    Create other LVs for where lots of files need to go.  For example, docker stuff should be on an LV.  If /var gets huge, make that a separate LV.  I think /home over 50G per userid is storage abuse too.

Mount these LVs were they are needed, but avoid mounts for a single userid in /home.
/home == good
/home/thefu != good. Avoid mounts under home.  Use symlinks to the real storage location.  Consider that other users might need access to the locations as well.

IMHO.  There are different opinions about all this stuff.

---

### Post by martinjh99 on 2021-07-31
Thanks - There is windows involved and I'm the only user.

I did think that someone might have got in as I left open port 80/443 on the router as I was going to setup something that I didn't get round to actually doing and forgot to close the ports.  Closed now though.

I shall take your ideas into consideration.  How did you change the mounts as the mounts I was using were the default ones on original setup.

---

### Post by volkswagner on 2021-07-31
> **martinjh99 said:**
> Would you mind elaborating the full plan? I want to copy the files across as herew then add the two other discs in the data vg into the one that ubuntu has been installed in if that will work...

That's exactly what we are advising you NOT to do.
Don't put multiple physical volumes in a volume group.
If you have three disks, you should have a minimum
of three VGs.

---

### Post by martinjh99 on 2021-07-31
Thinking about it now I verging on using wipefs to nuke the LVM metadata on both those other disks and just mounting them somewhere and using them that way.  I'm thinking using LVM is more trouble than it's worth from what you've said.

Probably the best way I'm imagining.

---

### Post by TheFu on 2021-07-31
LVM is an enterprise-class volume management system. It is very much like the commercial Veritas VM available for almost every platform in the 1990s.  LVM is extremely flexible, but it does add complexity and expects an informed admin to setup and make decisions.  Those decisions should mainly be to avoid problems, not necessarily what is easiest.

You already have learned some LVM stuff, so I wouldn't throw that away.  If you do, perhaps ZFS which is a file system AND volume manager would be of interest?  ZFS is crazy different from what you've used already and I don't consider it ready for boot/OS storage yet under Linux. For data storage, ZFS is 100% ready for use.

>  How did you change the mounts as the mounts I was using were the default ones on original setup. 
Seems an odd question for anyone using LVM and Linux since 2005.  I must not understand. Please clarify.

As volkswagner says, make an any changes from a live-boot (*try ubuntu*) environment and don't forget to update the fstab for the installed/boot version.

---

### Post by martinjh99 on 2021-07-31
Reading up on ZFS and Ubuntu and seeing I have 2 identical disks which would be great for a mirrored pool I might go that way instead.  At least with a mirror I would be able to have one disc faiilure which I wouldn't get with LVM...

Might create a VM to test playing about with ZFS and see what happens.

---

### Post by TheFu on 2021-07-31
LVM supports mirroring/RAID1.  You can change forwards and backwards with LVM between mirrored and not mirrored.  **lvchange** manpage has lots of information about it.

Where ZFS shines is with RAIDz2 ... which is 6 HDDs and hard to add/remove disks into the configuration.

---

