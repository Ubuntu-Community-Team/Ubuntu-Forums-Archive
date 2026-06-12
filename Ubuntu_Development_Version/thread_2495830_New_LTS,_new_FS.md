---
title: "New LTS, new FS?"
date: 2024-03-03
forum: Ubuntu Development Version
---

### Post by laserburn2 on 2024-03-03
Considering that Ubuntu 24.04 is coming with kernel that supports bcachefs, are we going to see in the installer an option to use the new filesystem? I am generally adventurous enough to try new filesystems, as long as there is reasonable expectations that it won't break on my simple home configuration (one nvme stick). I was one of the early btrfs users on Ubuntu, which wrecked the system.

Currently, I'm on zfs, which is working great, except for the fact that Ubuntu installer is making bpool way too small and there is no option to change that. We tried to kick up some fuss and raise awareness of the problem, but it all fell on silent ears and I doubt it got addressed in the 24.04. Maybe someone could check.
[https://ubuntuforums.org/showthread.php?t=2491291](https://ubuntuforums.org/showthread.php?t=2491291)

---

### Post by jbicha on 2024-03-03
Ubuntu developers have higher priorities right now than making it easier for people to wreck their system with experimental filesystems. :wink:

I mean you're basically asking for additional features in the installer, but the people working on the installer are very busy with getting it to work for official Ubuntu flavors and support OEM configuration. There just isn't time for anything extra.

---

### Post by ian-weisser on 2024-03-03
Experimentation of this sort is rare during an LTS release.

It is more common during the non-LTS releases.

And is most likely to happen when community members pitch in. Lot of work to be done.

If you wish to check on a reported bug, please check the bug tracker.

---

### Post by MAFoElffen on 2024-03-04
> **jbicha said:**
> Ubuntu developers have higher priorities right now than making it easier for people to wreck their system with experimental filesystems. :wink:

I mean you're basically asking for additional features in the installer, but the people working on the installer are very busy with getting it to work for official Ubuntu flavors and support OEM configuration. There just isn't time for anything extra.
I'm still waiting for resolution of filesystem and volume manger features "we lost" with the new partitioner of the new installer = recognizing existing LVM and LUKS containers. That has been in bug reports, issues, and enhancement requests. No one (yet) has been willing to tell me what the new partitioner actually "is" so I can look into it on my own. Those have been in issues and launchpad questions.

*** I agree on the timing. Very well said. An LTS cycle is not the time for that.

---

### Post by laserburn2 on 2024-04-18
I'm reading on Phoronix that new installer can install zfs on root, even encryption is supported. I believe there is no longer a separate volume for /boot and zsys is out. I have no idea how they implemented zfs on Ubuntu 24.04, do they now use zfsbootmenu or what? If anyone tried new Ubuntu beta or knows more on the subject, I'd appreciate some feedback.

---

### Post by #&amp;thj^% on 2024-04-19
> **laserburn2 said:**
> I'm reading on Phoronix that new installer can install zfs on root, 
Yes
> **laserburn2 said:**
> even encryption is supported.
Todays .iso 4-19-2024  encryption is still broken, at least on my end.
> **laserburn2 said:**
>  I believe there is no longer a separate volume for /boot and zsys is out. I have no idea how they implemented zfs on Ubuntu 24.04, do they now use zfsbootmenu or what? If anyone tried new Ubuntu beta or knows more on the subject, I'd appreciate some feedback.
Not Quite:
```
inxi -p | grep bpool
    logical: bpool/BOOT/ubuntu_ntiqi9

```
And zsys is still in the repos:
```
 apt policy zsys
zsys:
  Installed: (none)
  Candidate: 0.5.11.3build1
  Version table:
     0.5.11.3build1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages

```
Mine in total is laid out like this:
```
ID-1: / size: 440.28 GiB used: 4.59 GiB (1.0%) fs: zfs
  ID-2: /boot size: 1.75 GiB used: 95.4 MiB (5.3%) fs: zfs
  ID-3: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat
  ID-4: /home size: 436.11 GiB used: 427 MiB (0.1%) fs: zfs
  ID-5: /root size: 435.69 GiB used: 1.1 MiB (0.0%) fs: zfs
  ID-6: /srv size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-7: /usr/local size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-8: /var/games size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-9: /var/lib size: 436.76 GiB used: 1.07 GiB (0.2%) fs: zfs
    fs: zfs logical: rpool/ROOT/ubuntu_ntiqi9/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_ntiqi9/var/lib/NetworkManager
  ID-12: /var/lib/apt size: 435.76 GiB used: 70.1 MiB (0.0%) fs: zfs
  ID-13: /var/lib/dpkg size: 435.72 GiB used: 37.4 MiB (0.0%) fs: zfs
  ID-14: /var/log size: 435.69 GiB used: 4.4 MiB (0.0%) fs: zfs
  ID-15: /var/mail size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-16: /var/spool size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-17: /var/www size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-18: swap-1 size: 4 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda3

```
Others will vary according to how they install it.

---

### Post by MAFoElffen on 2024-04-21
> **jbicha said:**
> Ubuntu developers have higher priorities right now than making it easier for people to wreck their system with experimental filesystems. :wink:

I mean you're basically asking for additional features in the installer, but the people working on the installer are very busy with getting it to work for official Ubuntu flavors and support OEM configuration. There just isn't time for anything extra.
@jbicha --- 

Sorry that this has hit the sensitivity underpinnings of my frustration. Nothing meant as personal at all...

I have asked for over a year on info on the newer partitioner, and scripts to be able to flip over to a console to change manually the size bpool and the EFI partitions during the canned ZFS install... Since no one would answer... I have done traces and debugging on my own to see what it does and how it works. Trying different things to get it to do what I can underneath it.

I filed issues at the ubuntu-desktop-installer github, questions at Launchpad. It did fall on "deaf ears". It used to be easy with subuiquity. With Flutter, another experience.

Alongside of that, there is an old bug report on the newer partitioner, as it relates to LVM2, and that it doesn't recognise things that are there, besides basic partitions. With the older partitioner, you could do LVM, and LUKS containers in console, start up the partitoner, and it would see what was there, and then fire up the installer, point the partitioner to the mounts you wanted to use for the filesystem, and have it continue the install using those mounts. 

That is not there anymore with the current partitioner. No one above us seems to care about that, nor the possibilities it ave us, that are not there anymore.  

The only other option to do that with the newer installer is using the Live Installer and it's scripts.

Or to do as I do, with using the Installer's LiveUSB's Live Image Environment (L.I.E.) as just that, create the environment and layouts, and either rsync or debootstrap the system into the created framework. That is how I usually do things, "manually"... But others, using the subiquity installer worked that way, so they noticed that doesn't work any longer and they have lost the ability to do many things. I said I would try to help...

I can see where the DEV's are too busy for any of us, or to hear what we have to ask or say... Heck, after visiting the Issue Section of the ubuntu-desktop-installer GitHub, after seeing that issues were not being addressed (and me helping others there), I filed an issue on "that" as a Specific Issue. But changing priorities are a continual cycle. Life happens. 

I started asking these questions during the Lunar Dev Cycle, when we went to the newer installer. Then we went to DEV Mantic, then DEV Noble... After Noble releases, then we just start another DEV Cycle for 24.10, and the priority is on that right? While those things are still unanswered, and not addressed. It's like they get ignored and pushed to the side.

It's not just ZFS or BTRFS, or some other exotic filesystem. It's the underlying toolset, and how it does not recognize what is there. It's LVM2, and LUKS, and many other things that have been around in Linux for many, many years. Canonical said it was working on the partitioner. They can't even tell people what it is, nor has anything been done to improve it (nor add the promised features) in the past year and a half. Just what is the schedule on that?

Yes, sorry. A bit of frustration with that. It spilled out in a gush. I'll just go back to my corner and lick my wounds in silence.

---

### Post by laserburn2 on 2024-04-21
> **1fallen said:**
> 
Mine in total is laid out like this:
```
ID-1: / size: 440.28 GiB used: 4.59 GiB (1.0%) fs: zfs
  ID-2: /boot size: 1.75 GiB used: 95.4 MiB (5.3%) fs: zfs
  ID-3: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat
  ID-4: /home size: 436.11 GiB used: 427 MiB (0.1%) fs: zfs
  ID-5: /root size: 435.69 GiB used: 1.1 MiB (0.0%) fs: zfs
  ID-6: /srv size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-7: /usr/local size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-8: /var/games size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-9: /var/lib size: 436.76 GiB used: 1.07 GiB (0.2%) fs: zfs
    fs: zfs logical: rpool/ROOT/ubuntu_ntiqi9/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_ntiqi9/var/lib/NetworkManager
  ID-12: /var/lib/apt size: 435.76 GiB used: 70.1 MiB (0.0%) fs: zfs
  ID-13: /var/lib/dpkg size: 435.72 GiB used: 37.4 MiB (0.0%) fs: zfs
  ID-14: /var/log size: 435.69 GiB used: 4.4 MiB (0.0%) fs: zfs
  ID-15: /var/mail size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-16: /var/spool size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-17: /var/www size: 435.69 GiB used: 128 KiB (0.0%) fs: zfs
  ID-18: swap-1 size: 4 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda3

```
Others will vary according to how they install it.

I got an important question. Did the installer allow you to change any of those sizes or could you just let it do everything automatically as it sees fit? Could you change the size of bpool or /boot?

---

### Post by #&amp;thj^% on 2024-04-21
I let the installer size it, manual partitioning did not work for me yet.

---

### Post by jbicha on 2024-04-21
I mean I personally don't have time to help with implementing new filesystem details as I'm quite busy with other desktop responsibilities. The Ubuntu Desktop Installer team is small and have been working on more important issues this release cycle. For instance, the new desktop installer framework is now used by all the desktop flavors except for Kubuntu, Lubuntu, and Ubuntu Unity. That wasn't really possible with 23.10.

There are quite a few other bugs in the desktop installer beyond your bugs. Sorry.

The new installer now makes it very visible that you can use a file to automate your install. Maybe that supports complex file system organization?

---

### Post by MAFoElffen on 2024-04-22
@jbicha ---
Yes the autoinstall does work. I had to file a bug where there was an issue with late commands not working, but they are working now. Me and another tested that, and the patch from proposed, before it got pushed through. 

Not in the docs, but the various sample desktop autoinstall scripts are located inside of the ubuntu-desktop-installer snap image... Found them while digging around.

@laserburn -- 
zsys was only included with 20.04, and was not included since then. It wasn't a default for 22.04. It's still in the repo's, but not needed.

/boot <> bpool is still there... This laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo zpool list
NAME      SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
backups  1.46T   224G  1.24T        -         -     0%    14%  1.00x    ONLINE  -
bpool    1.88G   766M  1.13G        -         -     2%    39%  1.00x    ONLINE  -
dpool     856G  2.55M   856G        -         -     0%     0%  1.00x    ONLINE  -
hpool     396G  64.1G   332G        -         -    13%    16%  1.00x    ONLINE  -
kpool     992G   495G   497G        -         -     1%    49%  1.00x    ONLINE  -
rpool     496G  27.7G   468G        -         -     2%     5%  1.00x    ONLINE  -
mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME   LABEL              SIZE FSTYPE     MOUNTPOINT MODEL
sda                       1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1 {SYSTEM}           550M vfat       /boot/efi  
&#9500;&#9472;sda2 Windows RE tools   500M ntfs                  
&#9500;&#9472;sda3 {Windows}        888.6G ntfs                  
&#9500;&#9472;sda4                     32G                       
&#9500;&#9472;sda5 bpool                2G zfs_member            
&#9500;&#9472;sda6 rpool              500G zfs_member            
&#9500;&#9472;sda7 hpool            397.4G zfs_member            
&#9500;&#9472;sda8                    983M                       
&#9492;&#9472;sda9                     30G                       
sdb                       1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1 kpool             1000G zfs_member            
&#9492;&#9472;sdb2 dpool              863G zfs_member            
sdc                       1.8T                       Dogfish SSD 2TB
&#9492;&#9472;sdc1 backups            1.5T zfs_member            

```
Not from the canned ZFS-On-Root install scripts... It was installed using the Server Edition LiveUSB as a boot medium, and it's console prompt environment.

It you need a bigger bpool, which you need to recreate it anyways if you plan to ever snapshot bpool, to get around a Grub bug that comes about after you do a ZFS bpool snapshot... snapshot bpool/BOOT. Send/Receive it somewhere for a backup... Destroy bpool. Grow the partition, and recreate bpool with these options:
[https://ubuntuforums.org/showthread.php?t=2494397&p=14175250#post14175250](https://ubuntuforums.org/showthread.php?t=2494397&p=14175250#post14175250)
Send/Receive the dataset back into the new pool to restore it.
Those creation options will get around this bug:
[https://savannah.gnu.org/bugs/index.php?64297](https://savannah.gnu.org/bugs/index.php?64297)

---

### Post by laserburn2 on 2024-04-22
> **jbicha said:**
> 
The new installer now makes it very visible that you can use a file to automate your install. Maybe that supports complex file system organization?

Does the new installer allow the user to change the size of bpool or /boot? That sounds like elementary stuff, not something that we should jump through hoops to get.

---

### Post by laserburn2 on 2024-05-06
There indeed was no way to manually choose anything for zfs installation, so I just went with what installer offered me.

NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G  97.6M  1.78G        -         -     0%     5%  1.00x    ONLINE  -
rpool   944G  22.9G   921G        -         -     0%     2%  1.00x    ONLINE  -

It's once again a small bpool, but it won't cause a problem until Ubuntu is upgraded. This is a six year old PC, slowly going towards replacement in a year or two, so that's not really a big concern.

---

### Post by MAFoElffen on 2024-05-07
The ZFS autoinstall scripts found inside the ubuntu-desktop-installer image, found at /snap/ubuntu-desktop-installer/<version_number>/bin/subiquity/examples/ do work. Such as 'ai-zfs-efi-simple.yaml':
```

#cloud-config
autoinstall:
  version: 1
  identity:
    realname: ''
    hostname: ubuntu
    username: ubuntu
    password: '$6$wdAcoXrU039hKYPd$508Qvbe7ObUnxoj15DRCkzC3qO7edjH0VV7BPNRDYK4QR8ofJaEEF2heacn0QgD.f8pO8SNp83XNdWG6tocBM1'
  source:
    id: ubuntu-server-minimal
  early-commands:
    - apt-get install -y zfsutils-linux
  late-commands:
    # Let's avoid recreating LP: #1993318
    - zpool set cachefile= rpool
    - cp /etc/zfs/zpool.cache "/target/etc/zfs/"
    - mkdir -p "/etc/zfs/zfs-list.cache" "/target/etc/zfs/zfs-list.cache"
/snap/ubuntu-desktop-installer/1245/bin/subiquity/examples/ai-zfs-efi-simple.yaml:    - truncate -s 0 /etc/zfs/zfs-list.cache/rpool
    - >-
      env -i
      ZEVENT_POOL=rpool
      ZED_ZEDLET_DIR=/etc/zfs/zed.d
      ZEVENT_SUBCLASS=history_event
      ZFS=zfs
      ZEVENT_HISTORY_INTERNAL_NAME=create
      /etc/zfs/zed.d/history_event-zfs-list-cacher.sh
    - >-
      sh -c
      'sed -E "s|\t/target/?|\t/|g" "/etc/zfs/zfs-list.cache/rpool" > "/target/etc/zfs/zfs-list.cache/rpool"'
    - rm -f "/etc/zfs/zfs-list.cache/rpool"
  storage:
    version: 2
    swap:
      size: 0
    config:
      - {type: disk, id: d1, ptable: gpt, match: {size: largest},
         wipe: superblock, grub_device: true}
      - {type: partition, id: d1p1, number: 1, size: 1G, device: d1,
         flag: boot, wipe: superblock, grub_device: true}
      - {type: format, id: d1p1_format, label: efi, fstype: fat32,
         volume: d1p1}
      - {type: mount, id: d1p1_mount, device: d1p1_format, path: /boot/efi}
      - {type: partition, id: d1p2, number: 2, size: -1, device: d1}
      - {type: zpool, id: d1_rpool, pool: rpool, vdevs: [d1p2], mountpoint: /,
         pool_properties: {ashift: 12},
         fs_properties: {acltype: posixacl, relatime: on, canmount: on,
                         compression: gzip, devices: off, xattr: sa}}

```
How familiar are you with Ubuntu Desktop? Because ZFS-On-Root has been a part of the installer on Ubuntu since 20.04...

I tend to do my own manual installs. If you search my username in the Support Sections, you can find some of my recipes for that... All the commands needed, from the live environment of an Installer LiveUSB.

---

### Post by laserburn2 on 2024-05-07
As I said, the computer is slowly heading towards retirement, then it's going to brother's kids and I expect kids will be wrecking it regularly, so not many reasons to worry about problems years down the road. 

I did notice that the new Ubuntu no longer makes automatic snapshots when updating software. How are we supposed to make and organize zfs snapshots now?

---

