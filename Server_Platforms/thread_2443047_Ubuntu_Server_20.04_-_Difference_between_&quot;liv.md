---
title: "Ubuntu Server 20.04 - Difference between &quot;live&quot; and &quot;legacy&quot;"
date: 2020-05-10
forum: Server Platforms
---

### Post by LHammonds on 2020-05-10
NOTE: [Similar thread regarding 18.04 differences]("https://ubuntuforums.org/showthread.php?t=2390785").

[Ubuntu 20.04 Release Notes]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes")

Not much is mentioned in the release notes about the differences between the "live" installer verses the Debian installer now called "legacy" except that live now has [more support for automated installs]("https://wiki.ubuntu.com/FoundationsTeam/AutomatedServerInstalls").

This thread will attempt to list any notable differences between the installers.

The purpose being that if you still need to use the legacy installer today, you had better let your voice be heard about what needs to change in the live installer because it has been said that 22.04 will only have the live installer from that point forward.

[SIZE=5]Difference #1[/SIZE]

The list of packages installed are slightly different.

Installed packages from 20.04 live that are not present in 20.04 legacy are:

```

cloud-init/focal,now 20.1-10-g71af48df-0ubuntu5 all
console-setup/focal,now 1.194ubuntu3 all
eatmydata/focal,now 105-7 all
gdisk/focal,now 1.0.5-1 amd64
libeatmydata1/focal,now 105-7 amd64
python3-distutils/focal,now 3.8.2-1ubuntu1 all
python3-importlib-metadata/focal,now 1.5.0-1 all
python3-jinja2/focal,now 2.10.1-2 all
python3-json-pointer/focal,now 2.0-0ubuntu1 all
python3-jsonpatch/focal,now 1.23-3 all
python3-jsonschema/focal,now 3.2.0-0ubuntu2 all
python3-lib2to3/focal,now 3.8.2-1ubuntu1 all
python3-markupsafe/focal,now 1.1.0-1build2 amd64
python3-more-itertools/focal,now 4.2.0-1build1 all
python3-pyrsistent/focal,now 0.15.5-1build1 amd64
python3-serial/focal,now 3.4-5.1 all
python3-setuptools/focal,now 45.2.0-1 all
python3-zipp/focal,now 1.0.0-1 all
thermald/focal,now 1.9.1-1build1 amd64

```

Installed packages from 20.04 legacy that are not present in 20.04 live are:

```

installation-report/focal,focal,now 2.62ubuntu1 all
language-pack-en-base/focal,focal,now 1:20.04+20200416 all
language-pack-en/focal,focal,now 1:20.04+20200416 all
laptop-detect/focal,focal,now 0.16 all
tasksel-data/focal,focal,now 3.34ubuntu16 all
tasksel/focal,focal,now 3.34ubuntu16 all

```

[SIZE=5]Difference #2[/SIZE]

Custom partitioning such as a separate /boot and LVM are a bit more confusing to configure now and requires a workaround.  [Reference topic]("https://ubuntuforums.org/showthread.php?t=2441984")

[SIZE=5]Difference #3[/SIZE]

20.04 Live:
```

# snap list
Name    Version   Rev    Tracking         Publisher   Notes
core18  20200427  1754   latest/stable    canonical&#10003;  base
lxd     4.0.1     14954  latest/stable/&#8230;  canonical&#10003;  -
snapd   2.44.3    7264   latest/stable    canonical&#10003;  snapd

```

20.04 Legacy:
```

# snap list
No snaps are installed yet. Try 'snap install hello-world'.

```

[SIZE=5]Difference #4[/SIZE]

Live Installer does not recognize luks encrypted boot partition.   [Reference link](https://ubuntuforums.org/showthread.php?t=2465735).

---

### Post by rsteinmetz70112 on 2021-08-12
On Difference #2 which is more confusing?

---

### Post by Doug S on 2021-08-12
> **LHammonds said:**
> The purpose being that if you still need to use the legacy installer today, you had better let your voice be heard about what needs to change in the live installer because it has been said that 22.04 will only have the live installer from that point forward.
Oh. I only use the "legacy" installer and do not like the live installer.

---

### Post by MAFoElffen on 2021-08-13
I am **very** interested in this... I could easily get in trouble discussing some of these things. In fact, I had to edit my post, before even sending it. Too emotional. Those changes are above our heads.

I'm testing 21.10 for KVM and such. Getting a peek at some of those changes for/before 22.04. We'll see this Winter.

---

### Post by LHammonds on 2021-08-16
Added another issue found regarding the installer not recognizing a luks encrypted boot partition.  [Reference post](https://ubuntuforums.org/showthread.php?t=2465735)

LHammonds

---

### Post by MAFoElffen on 2021-08-16
I have one for you that also falls into with the partitioner... Pre-partitioned disks... You should be able to go to each partition and edit how you want to mount... and what you want to do right?

I had to create a test disk, to test a system rescue scenario:
```
Disk is GPT with sda[1-7]
sda1 is marked as bios_grub 5MB, unformatted
sda2 is EFI 500MB, fat32 (marked as ESF and Bootable)
sda3 is 1GB and ext4 (Boot)
(sda4-7 are evenly divided up.)
sda4 is / ext4
sda[5-7] are RAID5 and /home

#Without LVM
```
Even first going into it, with nothing selected, it will not let you select any disk as the boot disk. The option stays greyed out and you cannot go on from there.

If you try to delete any partitions the message is: "Cannot delete partition of local disk- Cannot delete a single partition of a disk that already has partitions."

It will let you delete "All" the partitions, but is labeled in it's menu's as "Reformat", of the disk popup menu, then when selected, says it's going to delete all the partitions on the disk. LOLIf you delete them all, then it will let you select the disk to boot from it. Now does that really make sense?

So even though it had been a dual-boot UEFI and BIOS bootable disk, that could be pulled out and put into anything, and all the partition flags where there, the new partitioner does not recognize them. The 18.04 and 20.04 Desktop partitioner does. The installer for "Something Else" really falls short in many ways. Besides not recognizing the partition flags, it will not recognize partition labels, filesystems (correctly), nor filesystem labels. There of those partitions were marked as RAID...

Even when doing something standard, options are greyed out... and when you try to go them, it will give you warnings that it is a "bad idea." (In those words exact words. LOL)

Even more so with RAID. In the old, you could customize many settings. No with the newer. There are only basic options.

To retest on the same disk, I had to delete all and start fresh... Then later go back to move things to allow for a dual boot rescue scenario.

I don't know. I always figured if you went into advanced settings, with would be a custom install, you "should" be able to 'do things' without having to hack it and use work-arounds.

I know I don't end up doing normal things for testing... But most of it isn't that far from the norm.

EDIT:
<<I have screen shots>>

All it will let you add as the first partition on a new GPT disk on UEFI is the /boot/efi partition. No matter what you try... You can say 5mb, unformatted, and unmounted. It automatically adds a 512MB ?boot/efi partition. And if you add it manually outside of it, it is back at square one.

When it does finished an installation, you can manually shrink that partition and add the bios_grub partition back in... and it will boot just fine still.

Oh... The logic for LVM on RAID is incorrect. In the partitioner, it thinks you need to install on RAID before there is a partition on the Array... Once a partition is added to the Array, then it thinks that LVM cannot be on it... And if you create an Array, it only thinks LVNM can only be installed to RAID, and ignores any regular partitions as eligible.

---

### Post by LHammonds on 2021-08-18
> **MAFoElffen said:**
> snip

[Would these steps help any]("https://ubuntuforums.org/showthread.php?t=2441984&page=2&p=13955557#post13955557")?  The main magic sauce being "Format: Leave unformatted"

---

### Post by MAFoElffen on 2021-08-18
"Maybe." LOL. Some of those things don't seem to make logical sense. And some of those are creating support issues later. (Example: LVM installed without being within a partition)

It doesn't like pre-configured disks, unless you do it by popping in and out of the installer to do it manually, at the time, to trick it. Or save some steps for after the install, which creates more work. The mystery is, that you can do some of those things we can't do in Live, in the autoinstaller script recipe.

---

