---
title: "Moving Ubuntu server into BTRFS subvolumes"
date: 2023-07-10
forum: Server Platforms
---

### Post by allcoms on 2023-07-10
I remember getting excited about Ubuntu adopting ZFS a few years ago but now it looks like Canonical have backtracked and I'll have to make do with BTRFS.

I would like to use Timeshift or btrfs assistant to manage BTRFS snapshots under Ubuntu server. If you install a desktop spin of Ubuntu using BTRFS then it automatically installs into @ and a @home subvols so that you can use Timeshift but this is not the case for Ubuntu server since 20.04 I believe so I would like to know the exact procedure to modify a Ubuntu server 22.04 install so that it uses and successfully boots off a BTRFS subvolume (@) with a separate subvol for /home (@home).

This is how I tried to do it:

First I installed Ubuntu server 22.04. On my test machine I used mdraid RAID 1 mirrored array but I'm more likely to be using md RAID 10 in production.

I then booted off systemrescuecd. I had tried booting off Ubuntu MATE 22.04 first but for some reason that didn't see my mdraid partition.

To create to subvols and move the existing files:

mount /dev/md127p1 /mnt
btrfs sub create /mnt/@
btrfs sub create /mnt/@home
mv /mnt/home/* /mnt/@home
mv /mnt/* /mnt/@


Next I edited /mnt/@/etc/fstab and added mount options to mount the volumes properly. Add subvol=@ to the line where the / is mounted. And create a similar line for /home like this:

 UUID=3a994a01-9d92-4e67-8440-284ce24465f8 /               btrfs defaults,subvol=@     0       0
UUID=3a994a01-9d92-4e67-8440-284ce24465f8 /home           btrfs defaults,subvol=@home 0       0

Next I re-installed GRUB:

mount --rbind /dev /mnt/@/dev/
mount --rbind /proc /mnt/@/proc/
mount --rbind /sys  /mnt/@/sys/
chroot /mnt/@

Then in the Ubuntu chroot I run:

mount /dev/md127p1 /
grub-install /dev/sda
grub-install /dev/sdb

Grub installs with no errors reported but Ubuntu doesn't successfully boot. It starts to boot but only gets far as the "Push CTRL-D to enter the emergency console" error.

Has anyone successfully pulled this off or can anyone see where I'm going wrong?

Thanks

---

### Post by MAFoElffen on 2023-07-12
All my live machines are ZFS... But have BTRFS VM machines that I build in my test suite... 

I feel like the order you are doing things might be backwards. The way you did that, you first installed the MD device outer container, then installed the system, then created BTRFS subvolumes... Inside of that. I think if you mounted the BTRFS subvolumes, that you are going to find that they are blank, except for what you just installed into them. Right?

When i install BTRFS, ZFS. LVM2, mdadm... I first install the outer layer and work in, then install the system into the volume manager sand filesystem framework. Let me get into some details...

If I boot on the Server Live Installer, past the language and keyboard settings, i use "Help" to use the Command prompt under that.... Then manually do what I want.

I used to use mdadm, then install a volume manger inside of that... about 12 years ago. When i create mdadm RAID, LVM2, ZFS, BTRFS, I do not give them a full raw disk, but add a GPT partition table an put them inside of the partitions. 

I create the directory structure that will support what I want to do. Usually divide things into these pieces.
```

EFI
BIOS_BOOT
SWAP
BOOT
ROOT
HOME
DATA
Network Shares
Disk Caches

```
Now I use RAID inside of LVM2, ZFS or BTRFS... That is not the sticking point of yours, so I will skip ahead... 

But I setup those as the outer containers, whether that is on one disk or spread over 50 disks... Then i setup the Volume Manager. For BTRFS I setup whatever partition and subvolumes that will facilitate the isolation of things, and support the snapshots I want to generate.

Once I get the mounts of all those with their background wiring done, then I either exit back to the installer and let it run, making the mounts to the desired place inside the partitioner, or mount the filesystem, piecing it together, to either Bootstrap, or rsync the system into it. If I use the installer, afterwards, I then mount things at /target. If not, then I mount things at /mnt. Then I fixe the mounts in fstab and the cypttab. Then I install and configure grub. Then I update the initramfs images. 

I have posted ways to do that here For LVM2, ZFS, LUKS, BRTFS, mdadm, etc... I have shared how I mount installed systems here, to repair them, including reinstalling grub...

I might be wrong... But did the order you did things, was it in that order? Somehow, it didn't sound like that to me.

---

### Post by allcoms on 2023-07-12
I did a complete install of Ubuntu server 22.04 to md RAID 1 (formatted with btrfs) without any manual partitioning or other intervention.

I gave up using LVM some time ago because it only ever caused me problems and I never actually used any of its features.

I've not actually tested it but I believe BTRFS + mdraid should let me boot off of both disks (in RAID1) mode. That works with XFS so it should work with BTRFS too I presume. My testing of BTRFS's integrated RAID in past revealed its essentially broken. It can't failover without manual intervention to get the secondary disk to boot.

I've aborted using 22.04 and I've returned to Proxmox + ZFS but it would be great if someone could document the exact steps to add subvolumes to a (Ubuntu server) BTRFS + mdraid install becsause that seems like the best option for Ubuntu server. ZFS has no issues with booting of any disks in the pool thanks to the way Proxmox installs GRUB.

---

### Post by MAFoElffen on 2023-07-13
BTRFS is is supported by the Server LiveCD as a filesystem, but it does not have installer template scripts like the Desktop Edition. Even those scripts are only basic and install with subvolumes @ and @home.

I feel like you are blaming the installer for not doing your work for you. The canned scripts only show / create basic examples of what might possible for a basic User... Not what "is" possible if you do it on your own.

The installer for the 22.04.x Server Live Installer has a good base and partitioner. I, myself, create recipe's to cut and paste into a SSH session while the Live Installer is booted. My recipe's setup the basic framework of whatever Volume manager and Filesystem is the target. Then to complete the wiring of it after the install. I either do the install by having the partitioner recognize that framework, make the correct mounts within it, or debootstrap or rsync a system within it...  

Yesterday I spent the afternoon creating a BTRFS system with an internal BTRFS RAID10 root and internal BTRFS RAID6 for the data storage pool, with subvols for @, @home, @data, @etc, @var, @opt, & @snapshots... Manually from the 22.04.2 Server Live Installer. It can be done. But not automatically.

I do some QA for the installer during the DEV Cycles for the pre-defined canned installs. But, personally, most of my installs for me and my customers are far beyond that. Even on a basic Desktop install, I at least break out the /home folder...

What can be done it to installer as basic, then convert it to more advanced. For example, do the install and when it ends... Jump over to the booted system and chroot into what wa installed, via  mount it to /mnt or /target... . Create the subvol, rsync the contents to it... Then after verifying the contents is there, delete where the subvol is going to cover it... Then fix the fstab to mount the subvol back into the filesystem. Just like you would do if you split off a Home folder to a drive. BTRFS subvolumes are just a containers within the filesystem...

The present partitioner does not recognize BTRFS subvolumes. If you know of one that does, please tell me. No, that is something you have to install manually. In fact, the new 23.04 installer is broken and is not filesystem, nor (any) volume manager aware at all. I have a bug report filed on this.

---

