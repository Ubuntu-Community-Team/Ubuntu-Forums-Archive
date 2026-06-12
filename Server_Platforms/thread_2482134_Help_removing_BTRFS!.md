---
title: "Help removing BTRFS!"
date: 2022-12-21
forum: Server Platforms
---

### Post by cthog on 2022-12-21
Hey Everybody,

Several years ago, when tinkering with my homelab, I jumped on the BTRFS bandwagon, and formatted my drives with it.  I'm not clever enough to really know how to properly use BTRFS, and it's caused a lot of problems.  Fortunately, it's no longer on my system drive, but I have some other drives that still use it.  I'd like to nuke it, but I haven't been able to.  I used fdisk to create an ext4 partition on one disk, which works fine, but the device still shows up as BTRFS, which makes me nervous.  Can someone give me some guidance on the proper commands to completely wipe the drive?  I have my data backed up, so can restore it, I just want to nuke this bad boy from orbit (it's the only way to be sure.)

--Chris

---

### Post by howefield on 2022-12-21
More information would likely be appreciated by anyone willing to step up and give you some suggestions. Also, responding to replies would be good, or is this another drive by thread of yours?

Operating system and configuration of disks would be a start.

---

### Post by cthog on 2022-12-21
Right.  Operating system is ubuntu server, just updated to 22.04 from 16.04.  That was also fun, as the new kernel didn't like the BTRFS drive, and for some reason I can't get Grub to show up, but I managed to boot on an older kernel with a boot disk and fix the issue.

I'm running an old r710.  It's got a PERC raid controller, but disks are JBOD.  I'm happy to give any system details you think are pertinent, but I'm really just looking for some basic commands to completely reset the disk and remove any vestige of BTRFS.

---

### Post by slickymaster on 2022-12-21
Thread moved to **Server Platforms** for a better fit

---

### Post by cthog on 2022-12-21
Whoops, sorry about that.  Thanks!

---

### Post by darkod on 2022-12-21
Can you post the output of the following commands (please post in CODE tags for easier reading).

```
sudo parted -l (that is small L)
sudo blkid
```

---

### Post by cthog on 2022-12-21
Certainly, sorry for the delay--it took about an hour to reboot my increasingly slow system, so I think this BTRFS nonsense is really gumming up the works.

To make things easy, I'll split posts.  First is parted -l:

```
Model: DELL PERC H700 (scsi)Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   499GB  498GB   ext4
 3      499GB   500GB  1023MB  linux-swap(v1)                        swap




Model: DELL PERC H700 (scsi)
Disk /dev/sdb: 10.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  10.0TB  10.0TB  ext4




Model: DELL PERC H700 (scsi)
Disk /dev/sdc: 10.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  10.0TB  10.0TB  ext4




Model: DELL PERC H700 (scsi)
Disk /dev/sdd: 4000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4000GB  4000GB  ext4




Model: DELL PERC H700 (scsi)
Disk /dev/sde: 3000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  3000GB  3000GB  btrfs        Server5



```

---

### Post by cthog on 2022-12-21
FWIW, /dev/sdb has an ext4 partition, but apparently is somehow still btrfs, and /dev/sde is full on btrfs.  I don't care about saving data, I just want to exorcise my disks of btrfs, lol.  

Here is blockid:

```
/dev/sdd1: UUID="7534765b-9de3-47e6-b1be-6b6dff45ad15" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="19ca0e38-08f5-4744-adc9-dce2098a7b19"/dev/sdb1: UUID="ff86e6ea-c27e-4ad4-bf10-1d5e38ede3ff" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="18925bf4-1d8d-c44d-b8af-04ae8c5649c9"
/dev/sde1: LABEL="Server5" UUID="b160a95d-4a31-4e7a-9513-89a6c066df20" UUID_SUB="01013cf6-3167-4e88-bd95-1eb8f4903b50" BLOCK_SIZE="4096" TYPE="btrfs" PARTLABEL="Server5" PARTUUID="91252089-597a-462b-a0e5-435f09b13574"
/dev/sdc1: UUID="49bd4f02-c0fc-47de-8b7a-bda6e9101ed7" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="9fd58e40-a8df-4187-bfab-107a554fcea9"
/dev/sda2: UUID="ab5412f4-fe35-4bc4-8fdb-998e4a687ecd" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="5a7a254b-eebf-4ced-8583-dc66759a8bf6"
/dev/sda3: UUID="c4177f20-a83b-4432-a7ef-6b2ef6aefbbb" TYPE="swap" PARTUUID="64387fae-8346-48f7-841f-ed1d2a8c1f79"
/dev/sda1: UUID="43F6-5CA1" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f363fb6c-d37c-492f-a4ea-f0447743689e"
/dev/loop1: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"



```

---

### Post by darkod on 2022-12-22
I have to say I have never worked with btrfs and I don't know if there are any "special" steps needed when removing them. I also don't know how exactly were you changing partitions from btrfs to ext4.

In blkid output I see everything normal except one thing. The sdb1 does not show there (as any filesystem) and it should. sdc1 and sdd1 show es ext4 and you already know sde1 is still btrfs. So that part looks OK.

I usually do partitions with parted. Creating a new partition table and partitions on sdb would be something like:
```
sudo parted /dev/sdb (after this command you are in parted prompt)
unit MiB (I like MiB for showing partition size and total size, you can use other if you want)
print (make sure you are working on the correct disk)
mklabel gpt (create new empty gpt partiton table)
mkpart DISKB 1 <end in MiB> (create new partition with label DISKB starting on 1MiB and ending just little less then total MiB of the disk, you can see this value in the print output above)
print (confirm it looks good)
quit (exit parted) 
```

I like creating filesystem separately from partitions so I don't do it inside parted. To format the new sdb1 es ext4 you would do:
```
sudo mkfs.ext4 /dev/sdb1
```

After this you should be able to mount and use sdb1.

---

### Post by cthog on 2022-12-22
Thank you for all the replies, I think I've figured it out.  BTRFS is like an Alabama tick, you really have to dig it out.  What (I think/hope) worked for me is the following:

wipefs -a /dev/sdx, followed by [COLOR=var(--black-800)][FONT=var(--ff-mono)]dd if=/dev/zero of=/dev/sdx bs=512 count=1 conv=notrunc for good measure.

Then using fdisk /dev/sdx, create a partition.  It will STILL see btrfs, but ask if you want to remove it.  As there's no "F* yes" option, simply choose Yes.

Then, as Darko noted, format with mkfs.ext4 /dev/sdx and should be good.  Again, this solution is not for anyone trying to save data.[/FONT][/COLOR]

---

### Post by darkod on 2022-12-22
Glad you got it resolved. FYI, removing the first 512 bytes with dd is usually the same as creating new blank partition table. The mklabel in parted would have done that as I mentioned.

Please mark the thread as SOLVED, you can do that in Thread Tools above the first post.

---

### Post by #&amp;thj^% on 2022-12-22
Yep same here. Happy it's sorted.
I just use something in the way of:
```
sudo wipefs --all -t btrfs /dev/sda /dev/sdb
```
Adjust /dev/sdxx to fit your needs, and check with:
```
sudo btrfs fi show
Label: 'KaisenLinux'  uuid: 162d1229-7a43-4cbe-bf16-a3a02742e97c
	Total devices 1 FS bytes used 86.33GiB
	devid    1 size 237.02GiB used 99.02GiB path /dev/mapper/kaisenlinux--rolling--vg-root

Label: 'KaisenBoot'  uuid: 309eab92-9f8d-4e1a-92bc-2a2a27cb556c
	Total devices 1 FS bytes used 91.36MiB
	devid    1 size 977.00MiB used 345.62MiB path /dev/sdb2



```
I Like btrfs it will take some time to understand all the uses it has under the hood though.

---

### Post by cthog on 2022-12-22
As a supplemental note, my 9tb disk ended up with an MBR partition again, oddly enough.  Again, for the uninitiated (as I was), deleting the partition in this case actually didn't delete data (I had started copying my old data back when I noticed.)  Used gdisk to convert to GPT, then (after rebooting the drive unmounted) ran resize2f /dev/sdx, and problem solved.  Hope this helps someone else.

---

### Post by volkswagner on 2022-12-24
I'm curious if the issues cthog had were due to using fdisk on a GPT partitioned disk.

I believe fdisk currently supports GPT, but I think early versions of fdisk did not.

What's the installed version of fdisk?

On my 20.04 upgraded to 22.04 and the installed version is:
```
fdisk from util-linux 2.37.2
```

I see in [this post]("https://wiki.archlinux.org/title/fdisk"), util-linux versions > 2.23 support GPT.

---

