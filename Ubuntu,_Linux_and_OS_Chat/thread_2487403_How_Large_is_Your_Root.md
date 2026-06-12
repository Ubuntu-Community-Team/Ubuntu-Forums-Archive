---
title: "How Large is Your Root?"
date: 2023-06-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-06-03
Periodically I suffer from **/** being full.  I feel mine is too large, however, I would be interested to see what size people 'generally' have in normal use.  I would say I'm a typical 'ordinary' Desktop user - mainly email and web surfing although I occasionally do some video editing.  I have always had a separate partition for** /** - at the moment I have a LVM environment with a specific LV for **/**.  Additionally I have deleted snap from my system.  Currently my **/** size is 22G which to me seems large compared to previous ubuntu installs.

```
dad@dadubuntu:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
tmpfs                        1.6G  2.0M  1.6G   1% /run
/dev/mapper/vg01-root         40G   22G   16G  60% /
tmpfs                        7.7G     0  7.7G   0% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1               197M   11M  187M   6% /boot/efi
tmpfs                        7.7G     0  7.7G   0% /run/qemu
/dev/mapper/vg01-ub2204base   49G   17G   31G  35% /media/dad/ub2204base
/dev/mapper/vg01-home         49G   17G   31G  35% /home
tmpfs                        1.6G  3.2M  1.6G   1% /run/user/1000
```

Be interested to see what **/** size people have on their machines.

---

### Post by ajgreeny on 2023-06-03
For reasons which I have never fully understood my root partition on any of my Xubuntu machines has never needed to be more than 20G and I've never used more than 13G of that.

Like you I have removed all the snap infrastructure so that saves a lot of space and I do not game at all.  I also keep the filesystem as clean as possible by removing the caches, though as I use apt, not apt-get in terminal only for updates etc, the potentially large cache is never created.

I am sometimes baffled by the large size that some users root partitions require but no doubt they use their machines very differently to me!

---

### Post by guiverc on 2023-06-03
I usually divide my drive space in two & that dictates the size.

My *old* primary box had a 160GB disk, and I wanted two OSes (LTS & *development*) on it, so created a shared *swap partition* then split the size between the two OSes (*with separated /home & / for each*). My usual way of helping me remember which is which, is to keep sizes unique, so it's not an equal split, but each partition will be a unique GB size... on that box I had 27GB for one / & 28GB for the other /

Whilst using that box (*from mid-2017 until its PSU died late 2022*) I would run into space issues & inability to update the system (*or login thus $HOME partition*) at least 8 times per year.  My hope was to create the partitions 31 & 32GB when I initially formatted; but I didn't want to have the hit on my $HOME partitions when I planned it in 2017.

Normally I use a box for a week+ with a different OS before I clean install the OSes I plan on keeping.. I didn't do it with this replacement box; instead of was used for QA-test installs during my test period (*my boxes are all refurbished; thus second hand*) & my installs where mostly *install alongside* followed by *replace partition* which meant I didn't end up with separate /home & / partitions as I usually use. Anyway my current sizes are 

```

/dev/sda6   92796928 297035775 204238848 97.4G Linux filesystem
/dev/sda7  298084352 498835455 200751104 95.7G Linux filesystem

```

Space used/available currently is 

```

/dev/sda6             96G   72G   20G  79% /

```

on this my *development* (thus *mantic*) install. I'd expect similar (*maybe more free on LTS as I use it a lot less!*)

With how I use a desktop system, I always plan on having 32GB as my preferred minimum / which is why I was *regularly fighting* for space when I had only 27GB & 28GB. But I also *bloat* my systems too, eg. my *older* primary box started life as a Ubuntu Desktop (GNOME), on which I added Lubuntu (LXDE), Xubuntu (Xfce) & Ubuntu-MATE (MATE) onto it..  

Unlike in 2017 when I built my *older* primary system, I'm now *heavily* involved with the Lubuntu team, thus this new install was a Lubuntu (LXQt) Desktop install, on which I did my usual thing of adding  `ubuntu-desktop` (GNOME), `xubuntu-desktop` (Xfce) ...   ie. *bloating* it up how I like it...  *Hey's its nice to login using a different session (desktop) on the same system & have it operate differently.. or if I read about some new feature in GNOME, I can logout, change my DE & login with GNOME & give it a try  (then logout & return to my preferred LXQt/Xfce environment when I start pulling out my hair too much due to GNOME's behavior that's not my cup-of-tea)*

To me, your 40GB is a **GREAT** and ideal size.. This box would probably have had about that size if I'd not used it for QA-test installs which caused me to end up with single-partition installs (*not counting the ESP*)..

---

### Post by makitso on 2023-06-03
I run ubuntu budgie 22.04.  Have you looked at your journal size?  
I run the command to reduce it's size.

journalctl --vacuum-size=20M



```

rob@rob-T510:~$ df -hFilesystem                 Size  Used Avail Use% Mounted on
tmpfs                      373M  3.4M  369M   1% /run
/dev/sda6                   20G  9.0G  9.2G  50% /
tmpfs                      1.9G   46M  1.8G   3% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
/dev/sda5                  511M   12M  500M   3% /boot/efi
/dev/mapper/home            24G  1.5G   21G   7% /home
tmpfs                      373M  164K  372M   1% /run/user/1000

```

---

### Post by Quarkrad on 2023-06-03
I'm also on 22.04 - my current journal size is 24mb - hardly big.  Thanks for the info - didn't know about that.

---

### Post by kc1di on 2023-06-03
Kubuntu 22.04 - 39 Gigs / partition. More than needed. Only using 34% of that at present.

---

### Post by makitso on 2023-06-03
Couple of points:

*  You probably have a swap file vs a swap partition.
*  df -h statistics are not realtime, at least for me.  I needed to reboot to see new numbers.
*  Are you using any databases?  They are in the root partition.

---

### Post by Quarkrad on 2023-06-03
Interestingly I have:

```
dad@dadubuntu:~$ swapon -s
Filename				Type		Size		Used	Priority
/dev/dm-3                               partition	8388604		0	-2
dad@dadubuntu:~$ sudo blkid | grep swap
/dev/mapper/vg01-swap: UUID="609a1ec4-3e3e-4cce-b832-4aa0f5b7c5e0" TYPE="swap"
```

I have certainly created a logical volume for swap which is dev/vg01/swap (8GB).  swapon says dev/dm-3 and is about the same size, not sure what /dev/dm-3 is though.  I'm new to LVM, the logical units I have set up are all on the only Volume Group I have, /dev/vg01, so I'm a little confused about /dev/dm-3.

---

### Post by Quarkrad on 2023-06-03
There are no databases on this machine - or any Gaming environments.

---

### Post by TheFu on 2023-06-03
A freshly installed 20.04 Server with a light Window Manager, no DE:
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01           ext4   35G  6.6G   26G  21% /
/dev/nvme0n1p3                    ext4  672M  280M  343M  45% /boot
/dev/nvme0n1p2                    vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-home01           ext4  9.8G  5.0G  4.3G  54% /home
/dev/mapper/vg01-var01            ext4   20G  1.8G   17G  10% /var
/dev/mapper/vg01-tmp01            ext4  3.9G   15M  3.7G   1% /tmp
/dev/mapper/vg01-libvirt--01      ext4  134G  131G  2.8G  98% /var/lib/libvirt
/dev/mapper/vg--hadar-lv--backups ext4  459G  686M  458G   1% /Backups
```

I cheat a bit by having separate LVs for /var, /home, virtual machines, swap and /tmp (its a security thing).  My /var is larger than I'd normally have as a precaution for **lxd** needs. I actually have a 50GB LV that is setup for ZFS use for LXD needs.

Here's the layout/use for another 20.04 system that has some time (installed last August) on it:
```
$ dft
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   27G  5.7G  83% /
/dev/nvme0n1p2                              ext4  574M  280M  252M  53% /boot
/dev/nvme0n1p1                              vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg00-home                       ext4   26G  9.2G   15G  38% /home
/dev/mapper/vg00-var                        ext4   54G   14G   39G  26% /var
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  7.1G   12G  39% /var/lib/jellyfin

```
See how I cheat with jellyfin storage under /var by putting it somewhere else?  I knew the jellyfin's media DB would be 10G+ eventually from an earlier install.  Back when I was running Plex MS on the system, that DB was 100GB!
Most of /var on this system is being used by apt-cacher-ng to cache all the packages for all the systems on the LAN.  I really should move that into a dedicated LV, I suppose.
```
$ sudo du -sh --one-file-system /var/cache/*  2>/dev/null  |sort -h
...
4.6M    /var/cache/fwupd
5.4M    /var/cache/debconf
155M    /var/cache/jellyfin
232M    /var/cache/apt
**9.2G**    /var/cache/apt-cacher-ng
```


On both those systems, swap is 4.1GB in a separate LV. Again, neither have swap in the same storage as /.  I abhor swap files and consider them abominations.  In reality, it probably doesn't matter much where swap is.

I use LVM for storage of virtual machines.  Those aren't showing up in the dft output.  I also have 5 lxc containers running on each 20l.04 system. Those use different storage than shown here ... so far.

Moving onto a desktop ... I switched from Ubuntu to Mint 21.1 with a WM-only setup ... and chose ZFS.  **df** really doesn't show the truth with ZFS, 
```
$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_d0wbmk                         zfs    24G  7.3G   17G  31% /
rpool/mydataset                                  zfs   2.0M  128K  1.9M   7% /media/mdata
rpool/USERDATA/jp_5njgy6                         zfs    27G  9.6G   17G  37% /home/jp
rpool/USERDATA/root_5njgy6                       zfs    17G  384K   17G   1% /root
rpool/ROOT/ubuntu_d0wbmk/srv                     zfs    17G  128K   17G   1% /srv
rpool/ROOT/ubuntu_d0wbmk/usr/local               zfs    17G  256K   17G   1% /usr/local
rpool/ROOT/ubuntu_d0wbmk/var/log                 zfs    18G  658M   17G   4% /var/log
rpool/ROOT/ubuntu_d0wbmk/var/spool               zfs    17G  4.4M   17G   1% /var/spool
rpool/ROOT/ubuntu_d0wbmk/var/games               zfs    17G  128K   17G   1% /var/games
rpool/ROOT/ubuntu_d0wbmk/var/lib                 zfs    17G   27M   17G   1% /var/lib
rpool/ROOT/ubuntu_d0wbmk/var/mail                zfs    17G  128K   17G   1% /var/mail
rpool/ROOT/ubuntu_d0wbmk/var/snap                zfs    17G  128K   17G   1% /var/snap
rpool/ROOT/ubuntu_d0wbmk/var/www                 zfs    17G  128K   17G   1% /var/www
rpool/ROOT/ubuntu_d0wbmk/var/lib/AccountsService zfs    17G  128K   17G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_d0wbmk/var/lib/dpkg            zfs    17G   69M   17G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_d0wbmk/var/lib/NetworkManager  zfs    17G  256K   17G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_d0wbmk/var/lib/apt             zfs    17G   85M   17G   1% /var/lib/apt
bpool/BOOT/ubuntu_d0wbmk                         zfs   1.8G  535M  1.3G  30% /boot
/dev/vda2                                        vfat  512M   17M  496M   4% /boot/efi
```
so I'm using an alias for **lsblkt** to show the layout:
```
$ lsblkt
NAME    SIZE TYPE FSTYPE     MOUNTPOINT
sr0    1024M rom             
vda      **40G** disk            
&#9500;&#9472;vda1    1M part            
&#9500;&#9472;vda2  513M part vfat       /boot/efi
&#9500;&#9472;vda3  1.8G part swap       [SWAP]
&#9500;&#9472;vda4    2G part zfs_member 
&#9492;&#9472;vda5 35.7G part zfs_member 

```
I don't know how to read the ZFS df output. Maybe you can figure out what it is saying?

Don't be afraid to add specific storage LVs when and where they are needed.

---

### Post by Dennis N on 2023-06-03
A comparison to other users depends on several things, such as: is home a separate partition or LV? Mine isn't. Is there a separate partition or LV for file storage? I have one. Here's what I get:
root logical volume (including home folder) =  30G (25G used).
home folder alone shows = 4G used
separate LV for file storage = 86 G. (66G used)

I use quite a few Flatpak apps: they use 4.5G in /var - (and included in the 25G used for /). 
No snap support is installed.

---

### Post by TheFu on 2023-06-03
> **Quarkrad said:**
>   I'm new to LVM, the logical units I have set up are all on the only Volume Group I have, /dev/vg01, so I'm a little confused about /dev/dm-3.

DM is "disk mapper" ... which is the real device name for the LV.  

If you look under /dev/disks/ for all the symlinks pointing at dm-3, you'll see what the mapper service has decided are permanent names for that LV/file system.  /dev/{vgname}/{lvname} is what I use for the fstab mounts, but /dev/mapper/ is what df has decided to show.  

Any of the symlinks under /dev/disks/  that point at the correct /dev/DMx device are fine to use.  by-label/ an by-uuid/ are most commonly used.

I find the installer's choices, as put into the /etc/fstab file, to be offensive.  Who needs the /dev/disks/by-uuid/uuid-xxxxx-xxxx-xxxxxxxx-xxxxxx junk?  It provides ZERO useful information, unlike using /dev/{vgname}/{lvname} which is extremely useful.  Heck, if there is a LABEL used on the partition/LV, even the fstab LABEL= mount option would be nicer.  I can only guess there are plans to remove the UUID= and LABEL= options from the fstab at some point in the future.  Why else would someone create a hanky installer fstab that is actually worse?

---

### Post by mikodo on 2023-06-03
```
/dev/nvme0n1p3   40G   11G   27G  30% /  

```
Tis a Xfce thing, I think.

---

### Post by lammert-nijhof on 2023-06-03
I run VMs and my Host OS is a minimal install of Ubuntu 22.04 LTS, so my usage is:

Host OS; 15 GiB; free 17%; it has a snap for Firefox. All snaps 2.8 GB and 2 Gnome snap versions (1x 3.38 and 2x 42). 

VMs, note that I don't mention the standard OS snaps added by Canonical: 
- Xubuntu 22.04 LTS; 23 GiB; free 28%. it has snaps for Whatsie (WhatsApp); Caprine (Messenger); Skype and Firefox :)  All snaps together; 3.8 GB note that the Gnome snap stuff is much smaller than in Ubuntu. 
- Ubuntu 16.04 ESM; 18 GiB; free 18%, it has snaps for Firefox; LibreOffice; Cups and Thunderbird :) :)  All snaps together 5.2 GB while LibreOffice takes 2x 1.1 GB. It only has Gnome 3.38 and 42 snaps. 
- Ubuntu 22.04 LTS ; 32 GiB; free 26%. it has snaps for Firefox; Telegram; Cups and SuperTuxKart. All snaps together 6 GB. Firefox 2x 240 MB; Telegram 2x 390 MB; SuperTuxKart 2x 620 MB. All 2x 5 Gnome versions from 3.26 to 42 take 2x 1335 MB
- Ubuntu Studio 20.04 LTS; 19 GiB; free 11%; no snaps, except the few added by Canonical (2.8 GB). Many large multimedia apps (deb).

Ubuntu 22.04 LTS is used by me to try-out new and some old apps and I expect, that is why it has collected 5 Gnome snap versions from 3.26 to 42. 
Note, that I store my data and VMs on OpenZFs on the Host. The VMs have access through Virtualbox Shared Folders.  I have absolutely no problems with the performance of those snaps, only loading LibreOffice is slow (1.1GB). Once loaded it works fine from the ZFS memory cache.

---

### Post by aljames2 on 2023-06-04
Not sure now why I chose 60G, knowning I was using LVM.  I used to always set up around 25-35G.
```

Filesystem           Type   Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root ext4    59G  6.9G   49G  13% /
/dev/nvme0n1p2       ext4   672M  262M  361M  43% /boot
/dev/nvme0n1p1       vfat   511M  6.1M  505M   2% /boot/efi
/dev/mapper/LVG-home ext4    30G  5.1G   23G  19% /home
/dev/mapper/LVG-VMs  ext4   147G   46G   94G  33% /data

```

```

NAME         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda            8:0    0 465.8G  0 disk 
&#9492;&#9472;sda1         8:1    0 465.8G  0 part 
sdb            8:16   0   1.8T  0 disk 
nvme0n1      259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1  259:1    0   512M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2  259:2    0   700M  0 part /boot
&#9492;&#9472;nvme0n1p3  259:3    0 930.3G  0 part 
  &#9500;&#9472;LVG-swap 253:0    0     6G  0 lvm  [SWAP]
  &#9500;&#9472;LVG-root 253:1    0    60G  0 lvm  /
  &#9500;&#9472;LVG-home 253:2    0    30G  0 lvm  /home
  &#9492;&#9472;LVG-VMs  253:3    0   150G  0 lvm  /data

```

---

### Post by Quarkrad on 2023-06-05
@ aljames - wow, that's low 6.9G compared to my now 23G.  What sort of system are you running (version, Desktop type, etc)?

---

### Post by aljames2 on 2023-06-06
> **Quarkrad said:**
> @ aljames - wow, that's low 6.9G compared to my now 23G.  What sort of system are you running (version, Desktop type, etc)?

Xubuntu 22.04 stock with no extras except KVM, Libvirt, Virt-manager.  Its my VM host.
I did take Network Manager off of it and use networkd instead, perhaps that saved some space.
Oh, also removed Firefox snap because I don’t do browsing on my VM host.

---

### Post by ajgreeny on 2023-06-07
I would agree that your 6.9G is very small though I suspect that the system is used for nothing more than running KVM, (am I correct?), but I also think the 23G mentioned by Quarkrad is quite large.

My Xubuntu which is used for everything I do, no games but does run Emby-mediaserver and is used for some audio and video editing, is about 11 to 12G.  I remove all snaps and the complete snap infrastructure which saves a significant space in root but I do still wonder what is actually using Quarkrad's 23G of space.

---

### Post by aljames2 on 2023-06-07
> **ajgreeny said:**
> I would agree that your 6.9G is very small though I suspect that the system is used for nothing more than running KVM, (am I correct?)

Yes that is all at the moment.  All the other applications I like are running in VMs.

---

### Post by douglas.e.ryan on 2023-06-08
```
 df -hFilesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.3M  1.6G   1% /run
/dev/nvme0n1p2  468G   58G  386G  14% /
tmpfs           7.8G  705M  7.1G   9% /dev/shm
tmpfs           5.0M   12K  5.0M   1% /run/lock
/dev/nvme0n1p1  1.1G  6.1M  1.1G   1% /boot/efi
tmpfs           1.6G  188K  1.6G   1% /run/user/1000 
```

---

### Post by ajgreeny on 2023-06-09
> **douglas.e.ryan said:**
> ```
 df -hFilesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.3M  1.6G   1% /run
/dev/nvme0n1p2  468G   58G  386G  14% /
tmpfs           7.8G  705M  7.1G   9% /dev/shm
tmpfs           5.0M   12K  5.0M   1% /run/lock
/dev/nvme0n1p1  1.1G  6.1M  1.1G   1% /boot/efi
tmpfs           1.6G  188K  1.6G   1% /run/user/1000 
```

You seem to be using g the default single partition containing root and home all together; only the EFI  partition is separate in your system so that all looks normal.

What point were you trying to make?

---

### Post by Quarkrad on 2023-06-09
I have identified my problem but need help/clarification.  My virtual machines were mounted under **/media** - deleting these vm's my root logical volume is now 7.8G.  Now I need some help with my understanding of mount points.  If I were to create a new logical volume, for say Fedora, does it have to be mounted under **/**?  I believe it does, as is it not the case that 'everything is under **/**'?   So the more logical volumes I create (for virtual machines) the larger **/** will get as the default seems to be **/media** which is under **/**.  What I'm struggling with is **/** appears to fill up because I'm adding more *logical volumes/virtual machines*  even though these virtual machines are on different logical volumes to the one that contains **/**.  Am I getting confused with that part of my brain that is still in Windows Land where you have partitions that are like completely separate islands?  I thought logical volumes were somewhat like windows physical partitions - but they seem not to be.

---

### Post by donald187 on 2023-06-13
This is a fresh install with the stock snap apps plus chromium and just a few extra, minor applications from the repositories.

```

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           764M  2.6M  762M   1% /run
/dev/nvme0n1p7   37G   11G   24G  32% /
tmpfs           3.8G     0  3.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p9  279G  7.5G  257G   3% /home
/dev/nvme0n1p1  196M   75M  122M  38% /boot/efi
tmpfs           764M  128K  764M   1% /run/user/1000
/dev/sda1       932G   86G  846G  10% /media/donald/Seagate

```

EDIT:  Forgot that you had identified your problem.

---

### Post by aljames2 on 2023-06-14
> **Quarkrad said:**
> What I'm struggling with is **/** appears to fill up because I'm adding more *logical volumes/virtual machines*  even though these virtual machines are on different logical volumes to the one that contains **/**.  Am I getting confused with that part of my brain that is still in Windows Land where you have partitions that are like completely separate islands?  I thought logical volumes were somewhat like windows physical partitions - but they seem not to be.

In some uses, it is common practice to place root level directories within separate LVs.  For example, /var /opt and others.  I created one called /data and placed it in an LV which is where I mount my VMs.  You could do the same with /media and mount this directory in its own LV.  I leave /media in the same LV as / because I don’t persistently mount things there.  /media is where the system likes to temporarily mount attached storage.

I suggest you double check your pvs, vgs, lvs structures, and confirm which directories you have mounted in your LVs

---

