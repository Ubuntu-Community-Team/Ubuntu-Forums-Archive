---
title: "Mounting zfs array at boot and /etc/fstab?"
date: 2023-08-06
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2023-08-06
This is my 1st time using zfs

I switched from md to zfs for my HDD array, want to be sure i have everything good and will work when i reboot

I made my zfs disk array like this
```
sudo zpool create -m /mn[COLOR=#000000]t/HDD mypool mirror sdf sdg mirror sdh sde[/COLOR]
```[COLOR=#000000]
this is my fstab file
```
$ cat /etc/fstab
```[/COLOR]```

# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/md0p1 during curtin installation 
/dev/disk/by-id/md-uuid-ede07d21:4114781a:b6762645:db22bf0e-part1 /         ext4 defaults,noatime 0 1 
# /mnt/Data was on /dev/md1p1 during curtin installation 
/dev/disk/by-id/md-uuid-28843301:920a306f:47f8cd80:d4d35fcd-part1 /mnt/Data ext4 defaults,noatime 0 1 
/mnt/Data/kvm-images    /home/chad/kvm/images    bind x-systemd.requires=/mnt/Data,defaults,bind  0 0 
/mnt/HDD/www            /var/www                 bind **x-systemd.requires=/mnt/HDD**,defaults,bind   0 0 
/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind **x-systemd.requires=/mnt/HDD**,defaults,bind   0 0 
/swap.img               none                     swap sw 

```

Will the zfs array mount to [FONT=monospace]/mnt/HDD and fstab not hang on boot?

This not working would be a pain as logging in will suck as i will need to get a monitor and keyboard out, i need the VM to get up and running and give the server it's IP address
[/FONT]

---

### Post by TheFu on 2023-08-06
I don't believe that ZFS uses the fstab file at all.

On my ZFS system, it was a check-box install, here's the entire fstab (comments removed):
```
UUID=0930-9C6D  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub  /boot/grub      none    defaults,bind   0       0
UUID=ae4bb4de-325f-4133-bd37-4d4273c9b260       none    swap    sw      0

```

```
$ sudo zfs list rpool
NAME    USED  AVAIL     REFER  MOUNTPOINT
rpool  18.0G  16.4G       96K  /
```

I can only guess that grub or efi are handing over the mounting to the ZFS sub-system inside the kernel:

```
$ lsmod |grep zfs
zfs                  4112384  24
zunicode              348160  1 zfs
zzstd                 491520  1 zfs
zlua                  163840  1 zfs
zavl                   16384  1 zfs
icp                   311296  1 zfs
zcommon               106496  2 zfs,icp
znvpair                98304  2 zfs,zcommon
spl                   118784  6 zfs,icp,zzstd,znvpair,zcommon,zavl
```

Unfortunately, I'm the blind leading the blind here.  [https://askubuntu.com/questions/1186283/how-can-i-make-zfs-datasets-mount-automatically-on-boot](https://askubuntu.com/questions/1186283/how-can-i-make-zfs-datasets-mount-automatically-on-boot) might help.  I did create a new dataset under rpool called "mydataset" and it is being mounted automatically to the mount point I specified: 
```
$ df -Th 
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/mydataset                                  zfs   2.0M  128K  1.9M   7% /media/mdata

```

While this is on a desktop, it is religiously backed up and I expect it to fail any OS upgrade attempts.  If that happens in a few years, I'll do a fresh install.

---

### Post by MAFoElffen on 2023-08-06
I explained that in my previous post, that there is a lot more options in the create statements, especially about ZFS mountpoints in that statement. Fortunately, ZFS is very adaptable and flexible.

Do this:
```

sudo su
zfs get mountpoint mypool

```
That will return the current mountpoint of the pool... Note that the 'zpool' command does not return a mountpoint property on a pool. That property is get and set with the 'zfs' command.

I set up a hierarchy for my filesystem. I create my datasets on top of my pool, starting with a base dataset, then sub-datasets and mount them like this (while still as root):
```

mkdir /data
UUID=2204  ## This can be anything, but I usually set to the version I am running.

zfs set mountpoint=/data mypool
zfs create -o canmount=off -o mountpoint=none mypool/DATA
zfs create -o mountpoint=/data mypool/DATA/ubuntu_$UUID
# Then check your work to see where the mounts are...
zfs list

```
If you have a type, you can use zfs rename to correct it. If you need to change the mountpoint again, the syntaxt is
```

zfs set -o mountpoint=/mountpoint

```
During creation, You can temporarily set a temp mountpoint with the "-R flag" in your create point like this
```

sudo zpool create \
    -o ashift=13 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off \
    -O mountpoint=/data -R /mnt \
    datapool raidz2 \
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1 \
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1 \
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1 \
    ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1 \
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1

```
If you create it that way with a temp mountpoint, on creation, it mounts to that temp mount point, where you could rysync data from wherever to populate it, or whatever... Then export it / import it... and it come back up in the mountpoint declared in the create statement.


Note that all of these properties can be reset after creation, **EXCEPT FOR "ashift**", which affects your underlying blocksize. If you need to change that for your tuning, you need to destroy your pool, re-create the pool with the new ashift setting, and restore your data. Note that after you make a change on something that affects data, that if affects what is written after that change, not for what is already written in the pool. (Example: adding a 'new disk' to the pool...) So if you want it to apply for all, or if you want to re-distribute and load-balance your data across the pool, then you back your data off, and rewrite it fresh...

Like I explained with mdadm, LVM, ZFS, BTRFS, have a good backup strategy that works. Backing off data and rewriting it is a common practice to work things out, or to migrate things to something better.

If you search the Forum on my username, there are a couple threads here on pool diagnostics, performance and tuning.

I would setup a pool with a spare drive (or do it in a VM) and play with it to learn the ZFS commands, what you can do, and practice with it. You can practice making snapshot, exporting pools and importing them to another location, etc. That is where your knowledge is going to build and how you can see how things can be flexible and adaptable. Like LVM2... Most people probably use about 10% of what it can really do... Because they don't understand what it can do, or how to use it.

EDIT: 
On ZFS-On-Root, there is a cron job that runs a trim and a scrub once a month. "scrub" is ZFS'es comparison to ext4'es fsck... For production, scrub is recommended once a week. For home type user's, once a month.

EDIT2:
ZFS caches: I create ZFS caches within /etc/zfs/zfs-list-cache and add that property for the cache in my root and boot pools... This cache helps with mounts on bootup... But that is more geared for just those two types of pools. I have created that cache for other pools, and it works and keeps track of things, but I don't see that it really affects anything expect for root/boot pools, for mounting within the initramfs ram image... Yes, I do play with things to see for myself, and to understand how things work underneath the covers.

---

### Post by pqwoerituytrueiwoq on 2023-08-06
[FONT=monospace][COLOR=#000000]assuming the pool mounts automatically will the bind's work in my fstab
[/COLOR][/FONT]```
/mnt/HDD/www            /var/www                 bind **x-systemd.requires=/mnt/HDD**,defaults,bind   0 0
/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind **x-systemd.requires=/mnt/HDD**,defaults,bind   0 0
```[FONT=monospace][COLOR=#000000]

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]$ zfs list [/COLOR]
NAME     USED  AVAIL     REFER  MOUNTPOINT 
mypool  26.8G  7.10T     26.8G  /mnt/HDD
[/FONT]
[FONT=monospace][COLOR=#000000]$zpool get mounpoint mypool [/COLOR]
bad property list: invalid property 'mounpoint'
[/FONT]
[FONT=monospace][COLOR=#000000]$zpool get mountpoint mypool [/COLOR]
bad property list: invalid property 'mountpoint'
[/FONT][FONT=monospace][COLOR=#000000]
$zpool get all [/COLOR]
NAME    PROPERTY                       VALUE                          SOURCE 
mypool  size                           7.25T                          - 
mypool  capacity                       0%                             - 
mypool  altroot                        -                              default 
mypool  health                         ONLINE                         - 
mypool  guid                           12479053363165969774           - 
mypool  version                        -                              default 
mypool  bootfs                         -                              default 
mypool  delegation                     on                             default 
mypool  autoreplace                    off                            default 
mypool  cachefile                      -                              default 
mypool  failmode                       wait                           default 
mypool  listsnapshots                  off                            default 
mypool  autoexpand                     off                            default 
mypool  dedupratio                     1.00x                          - 
mypool  free                           7.22T                          - 
mypool  allocated                      26.8G                          - 
mypool  readonly                       off                            - 
mypool  ashift                         0                              default 
mypool  comment                        -                              default 
mypool  expandsize                     -                              - 
mypool  freeing                        0                              - 
mypool  fragmentation                  0%                             - 
mypool  leaked                         0                              - 
mypool  multihost                      off                            default 
mypool  checkpoint                     -                              - 
mypool  load_guid                      15725222613977429801           - 
mypool  autotrim                       off                            default 
mypool  compatibility                  off                            default 
mypool  feature@async_destroy          enabled                        local 
mypool  feature@empty_bpobj            enabled                        local 
mypool  feature@lz4_compress           active                         local 
mypool  feature@multi_vdev_crash_dump  enabled                        local 
mypool  feature@spacemap_histogram     active                         local 
mypool  feature@enabled_txg            active                         local 
mypool  feature@hole_birth             active                         local 
mypool  feature@extensible_dataset     active                         local 
mypool  feature@embedded_data          active                         local 
mypool  feature@bookmarks              enabled                        local 
mypool  feature@filesystem_limits      enabled                        local 
mypool  feature@large_blocks           enabled                        local 
mypool  feature@large_dnode            enabled                        local 
mypool  feature@sha512                 enabled                        local 
mypool  feature@skein                  enabled                        local 
mypool  feature@edonr                  enabled                        local 
mypool  feature@userobj_accounting     active                         local 
mypool  feature@encryption             enabled                        local 
mypool  feature@project_quota          active                         local 
mypool  feature@device_removal         enabled                        local 
mypool  feature@obsolete_counts        enabled                        local 
mypool  feature@zpool_checkpoint       enabled                        local 
mypool  feature@spacemap_v2            active                         local 
mypool  feature@allocation_classes     enabled                        local 
mypool  feature@resilver_defer         enabled                        local 
mypool  feature@bookmark_v2            enabled                        local 
mypool  feature@redaction_bookmarks    enabled                        local 
mypool  feature@redacted_datasets      enabled                        local 
mypool  feature@bookmark_written       enabled                        local 
mypool  feature@log_spacemap           active                         local 
mypool  feature@livelist               enabled                        local 
mypool  feature@device_rebuild         enabled                        local 
mypool  feature@zstd_compress          enabled                        local 
mypool  feature@draid                  enabled                        local
[/FONT]

```[FONT=monospace]
[/FONT]

---

### Post by TheFu on 2023-08-06
Most of the time, rather than using a bind mount, a symlink can be used.  The main time it doesn't work is with snap package constraints, to my knowledge.  There are a few odd programs that don't follow symlinks but those are the exception, by far.  Less than 1% of all programs seem to care.  For decades, I've used symlinks to change versions of custom software in use, for example.

---

### Post by MAFoElffen on 2023-08-06
See my attachment... That is one of my recipe's for one of my servers/workstations. LOL.

This is what it looks like i it's fstab:
```

root@msi-ubuntu:~# grep . /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / is rpool on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part3 during migration
# 
# /home is hpool on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part5
##UUID=a5c5987f-82ab-4e16-a39f-aa5564a0a2ef /home           ext4  defaults,rw   0   0
UUID=0A24D9F224D9E0AD             /home/mafoelffen/WIN_G  ntfs  defaults,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
UUID=828C01738C016351             /Media_H                ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
# EFI at /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part1
/dev/disk/by-uuid/CBE6-0806 /boot/efi vfat defaults 0 0
/boot/efi/grub /boot/grub none defaults,bind 0 0
# swap is on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part4
/dev/disk/by-uuid/943f90ef-079f-4a38-840f-f786d19127ab none swap discard 0 0

```
This is what it looks like in the ZFS mounts of the filesystem:
```

root@msi-ubuntu:~# sudo zfs list
NAME                                             USED  AVAIL     REFER  MOUNTPOINT
bpool                                            613M  2.03G      192K  /boot
bpool/BOOT                                       612M  2.03G      192K  none
bpool/BOOT/ubuntu_2204                           612M  2.03G      612M  /boot
dpool                                           3.25M   450G       96K  /dpool
dpool/DATA                                       192K   450G       96K  none
dpool/DATA/ubuntu_2204                            96K   450G       96K  /dpool
hpool                                            499M   346G      192K  /home
hpool/USERDATA                                   493M   346G      192K  none
hpool/USERDATA/ubuntu_2204                       493M   346G      493M  /home
kpool                                            399G   500G       96K  /kpool
kpool/QEMU-KVM                                   399G   500G       96K  none
kpool/QEMU-KVM/ubuntu_2204                       399G   500G      104K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                   399G   500G      399G  /kpool/ISO
kpool/QEMU-KVM/ubuntu_2204/KVM-VM                 96K   500G       96K  /kpool/KVM-VM
kpool/QEMU-KVM/ubuntu_2204/images                112K   500G      112K  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt               596K   500G      596K  /etc/libvirt/
rpool                                           17.7G   707G      192K  /
rpool/ROOT                                      17.6G   707G      192K  none
rpool/ROOT/ubuntu_2204                          17.6G   707G     7.34G  /
rpool/ROOT/ubuntu_2204/srv                       192K   707G      192K  /srv
rpool/ROOT/ubuntu_2204/usr                       488K   707G      192K  /usr
rpool/ROOT/ubuntu_2204/usr/local                 296K   707G      296K  /usr/local
rpool/ROOT/ubuntu_2204/var                      10.3G   707G      192K  /var
rpool/ROOT/ubuntu_2204/var/cache                1.20G   707G     1.20G  /var/cache
rpool/ROOT/ubuntu_2204/var/games                 192K   707G      192K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                  8.05G   707G     7.89G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService   240K   707G      240K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager    296K   707G      296K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt              80.5M   707G     80.5M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker            192K   707G      192K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg             78.6M   707G     78.6M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs               192K   707G      192K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                  1.04G   707G     1.04G  /var/log
rpool/ROOT/ubuntu_2204/var/mail                  192K   707G      192K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                 1008K   707G     1008K  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                 256K   707G      256K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                  12.2M   707G     12.2M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                   192K   707G      192K  /var/www
rpool/USERDATA                                  4.05M   707G      192K  none
rpool/USERDATA/root_2204                        3.87M   707G     3.87M  /root

```
Putting all 3 sources together, you can see where I created datasets for those mounts...

In partitcle, for instance, look at the mounts for pool "kpool". It is one pool, but the datasets are mounted within 4-5 completely different places within the filesystem (with the same pool, but different datasets). ZFS exists as an overlay above the filesystem, then you work your mounpoints to place it into your filesystem... So it exists integrate into it. I can take one snapshot of that kpool pool, and backup everything I need for everything related to my KVM installation on that machine. I can send/receive it to another machine to duplicate it, or export it / import it to a new system to migrate it.

Does that give your a different perspective on how that works?

---

### Post by TheFu on 2023-08-06
Curious.

Why:
```
/dev/disk/by-uuid/943f90ef-079f-4a38-840f-f786d19127ab
```
when
```
UUID=943f90ef-079f-4a38-840f-f786d19127ab
```
is more concise and contains the same level of information.

Or is it a case of it is working, too lazy to change it?

---

### Post by MAFoElffen on 2023-08-06
In Linux, there are hundreds of ways to do the same thing. As you have told other people in posts, to use Unique ID's from the /dev/disk/ tree:
```

root@msi-ubuntu:~# ls /dev/disk/
by-id  by-label  by-partlabel  by-partuuid  by-path  by-uuid

```
I'm getting old. I don't trust my eyes to transfer over UUID's... So in my recipe's I create algorithms to do that for me...

For getting unique id's... Honestly, I usually use /dev/disk/by-id, which includes the disk model and serial number. That is more 'visual' to be in going int the case and knowing this drive is this one. 
```

root@msi-ubuntu:~# ls -l /dev/disk/by-id/ | awk '/nvme0n1p4/ {print $9}'
nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part4

```
But that does not always work, because it does not always add a symlink to each drive under there, at all times. I don't know why. At other times, it will add mulitple entries for the same drive. 

It always has an entries for each partition  in /dev/disk/by-uuid/
```

root@msi-ubuntu:~# ls -l /dev/disk/by-uuid/ | awk '/nvme0n1p4/ {print $9}'
943f90ef-079f-4a38-840f-f786d19127ab

```
Of course I could get the same by using blkid...
```

root@msi-ubuntu:~# blkid -s UUID -o value /dev/disk/by-id/$(ls -l /dev/disk/by-id/ | awk '/nvme0n1p4/ {print $9}' | head -n1)
943f90ef-079f-4a38-840f-f786d19127ab
#or simply
blkid -s UUID -o value /dev/nvme0n1p4
943f90ef-079f-4a38-840f-f786d19127ab

```
So I retrieve the unique identifier and load it into a variable, then I use that variable in an echo statement to the /etc/fstab file...

Lazy? LOL. More intelligent. More work for the first time to figure out the algorythm, but from then on, can be re-used again and again.

Now the echo the line as the fstab statement... Could have been whatever of various methods, but is still the same amount of work, and is just a different perspective of the same thing. (is saying the same thing...)
```

echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part4) \
    none swap discard 0 0 >> /etc/fstab
## Is the same as:
echo UUID=$(blkid -s UUID -o value ${DISK}-part4) \
    none swap discard 0 0 >> /etc/fstab

```
...and is the same effort expended in saying it... Agreed to disagree? LOL

If you are talking about typing? Yes. I maybe end up typing more the first time, to create a new recipe. But as a programmer and sys admin for so many years, I know if I crete something generic, it will save me lots of time down the road. That and I can use it as a journal for how things are put together on a system. That way, I can copy code from one script to another, for another system, and it will just work. 

That saves me time and effort, so i can take it easy. I put in the extra effort for that luxury, later on.

---

### Post by MAFoElffen on 2023-08-06
In Linux, there are hundreds of ways to do the same thing. As you have told other people in posts, to use Unique ID's from the /dev/disk/ tree:
```

root@msi-ubuntu:~# ls /dev/disk/
by-id  by-label  by-partlabel  by-partuuid  by-path  by-uuid

```
I'm getting old. I don't trust my eyes to transfer over UUID's... So in my recipe's I create algorithms to do that for me...

For getting unique id's... Honestly, I usually use /dev/disk/by-id, which includes the disk model and serial number. That is more 'visual' to me in opening and going into the case (or a hot-swap bay) and knowing this drive is the one. Sort of like blinking a drive light in a drive bay, so you know you have the right drive. right? (When you have 70 SSD's in a rack mount... you want to be sure. LOL)
```

root@msi-ubuntu:~# ls -l /dev/disk/by-id/ | awk '/nvme0n1p4/ {print $9; exit}'
nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part4943f90ef-079f-4a38-840f-f786d19127ab

```
But that does not always work, because it does not always add a symlink to each drive under there, at all times. I don't know why. At other times, it will add mulitple entries for the same drive. 

It always has just one entry for a filesystem within each partition  in /dev/disk/by-uuid/
```

root@msi-ubuntu:~# ls -l /dev/disk/by-uuid/ | awk '/nvme0n1p4/ {print $9}'
943f90ef-079f-4a38-840f-f786d19127ab

```
Of course I could get the same by using blkid...
```

root@msi-ubuntu:~# blkid -s UUID -o value /dev/disk/by-id/$(ls -l /dev/disk/by-id/ | awk '/nvme0n1p4/ {print $9; exit}' )
943f90ef-079f-4a38-840f-f786d19127ab

```
So I retrieve the unique identifier and load it into a variable, then I use that variable in an echo statement to the /etc/fstab file...

Lazy? LOL. No. Maybe just more intelligent. More work for the first time to figure out the algorythm, but from then on, can be re-used again and again.

Now the echo the line as the fstab statement... Could have been whatever of various methods, but is still the same amount of work, and is just a different perspective of the same thing. (is saying the same thing...)
```

echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part4) \
    none swap discard 0 0 >> /etc/fstab
## Is the same as:
echo UUID=$(blkid -s UUID -o value ${DISK}-part4) \
    none swap discard 0 0 >> /etc/fstab

```
...and is the same effort expended in saying it... Agreed to disagree? LOL Like me, you are another sys admin. You know that the symlinks all point to the same place. If you do not use a unique id, then those things can change with a reboot. Right? That is what both of us have preached for years.

That gets a bit "creative" when I start mixing different filesystem types within the same partition, because of file managers and file system mounts... Remember, my niche was making a system's infrastructure appear like it is just one-single-system.

---

### Post by pqwoerituytrueiwoq on 2023-08-07
> **TheFu said:**
> Most of the time, rather than using a bind mount, a symlink can be used.  The main time it doesn't work is with snap package constraints, to my knowledge.  There are a few odd programs that don't follow symlinks but those are the exception, by far.  Less than 1% of all programs seem to care.  For decades, I've used symlinks to change versions of custom software in use, for example.
i mainly use this cause i have had permission issues with apache2 (placing a server folder in /tmp or /home for example) and bind was a easier way around it and i find fstab to be a easy way for me to keep track of this stuff later

---

### Post by TheFu on 2023-08-07
Apache has the public_html module to allow websites under users' HOME directories.
Doing anything in /tmp/ besides storing temporary files is a bad choice.  There are many reasons this is true, mainly security reasons.  For example, my /tmp has this fstab entry:
```
/dev/vg01/tmp01      /tmp             ext4 defaults,noexec,nodev,nosuid 0 1
```

If you've ever been cracked, you'd know that they often will try to setup programs in /tmp/ to gain deeper access to the system.  While noexec won't completely stop them, it will slow them down and might be just enough to confuse a bot attacker.  Plus, they can't trick any user into running a program in /tmp/ that provides different or elevated access.

Anyway, this probably doesn't impact your intended goals, just something more to consider.

---

### Post by pqwoerituytrueiwoq on 2023-08-07
sometimes i use /tmp for files that get written to alot where i do not want to put wear a flash storage that i need to access over http

---

### Post by MAFoElffen on 2023-08-08
As a programmer/dev, I use /tmp for things I don't care about keeping around... but need to store at times, for things that don't like to be just in RAM. I think of that as being a hard, more durable variable, by storing what I need to temporarily in a file. I try to avoid that, but some things just work better that way:

Quoted from the Linux Handbook:
> 
What is the /tmp directory in Linux? As the name suggests, the tmp (temporary) directory under root is used to store the data used by the system and user applications to store the data that are needed for a short period of time. Most Linux distributions are preconfigured to empty the tmp directory after each reboot.

I still do cleanup for the just in cases... Because as best-practices go, that is just the right thing to do. Ubuntu, by default, is one of those Distro's that cleanup the /tmp directory immediately on a reboot. Though, the files written to /var/tmp are kept.

---

