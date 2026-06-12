---
title: "Installing Ubuntu on RAID0 with scheduled backups to separate array"
date: 2018-12-12
forum: Server Platforms
---

### Post by adfgqi on 2018-12-12
This is isn't technically a server setup, rather a workstation, but I guess this is the best place for it.

I've had a Threadripper 1950X for a while now (64GB ram) and 2 M.2 SSDs and I am looking to improve the disk performance of my day-to-day work. Pretty much everything that I produce on this machine ends up in a remote repository, and other stuff (like documents) are on a separate machine that serves as a NAS. So I'm not all that concerned about safety. Still, I would prefer not having to start from scratch in case of SSD failure, so a couple of backups a day during work hours seems like a good idea.

What I leaning towards is getting an additional 2 M.2 SSDs (the price has dropped significantly) for a total of 2TB when RAID0-ed, and 2 cheap HDDs of 2TB in RAID1 in the same machine. Then I can use that separate volume for incremental backups of the RAID0 volume.

That is the general idea, I am looking for some implementation advice. 

XFS seems like a pretty nice choice, using `xfsdump` I can create incremental backups using 9 slots. XFS uses more RAM I read, but I am not really RAM constrained. I was thinking about maybe using 2 of them for a base setup (one for base installation, one for a more fleshed out base) and then use the remaining  7 during each day (the third slot at boot, the remaining as incremental backups during the day). Just thinking aloud, interested to hear other people's take on this.

I've not tried XFS before, nor have I tried installing Ubuntu on a RAID volume for about 10 years so I am also out of the loop on that. Any pointers and or insights are much appreciated.

---

### Post by adfgqi on 2018-12-12
So I found some relevant information for this plan:

Installing Ubuntu on ZFS (doesn't seem too difficult):

[https://github.com/zfsonlinux/zfs/wiki/Ubuntu-18.04-Root-on-ZFS](https://github.com/zfsonlinux/zfs/wiki/Ubuntu-18.04-Root-on-ZFS)

Creating ZFS RAID0 (for the SSDs):

[http://www.zfsbuild.com/2010/06/03/howto-create-zfs-striped-vdev-pool/]("https://www.zfsbuild.com/2010/05/26/zfs-raid-levels/")

Mirrored (for the HDDs):

[http://www.zfsbuild.com/2010/06/03/howto-create-mirrored-vdev-zpool/](http://www.zfsbuild.com/2010/06/03/howto-create-mirrored-vdev-zpool/)

But I don't think I've properly thought this through. If an SSD fails, yes I have a backup, but how am I going to restore it when I am missing an SSD drive... RAID5/Z doesn't seem like a good option for write speeds, so is my only option then just having a spare 200 EUR SSD laying around? Or can I restore to 3 drives using the backup as long as I ensure the usage doesn't exceed 1.5TB?

---

### Post by adfgqi on 2018-12-12
Looking at man page for xfsrestore, it doesn't seem to care about the underlying devices at all and there is even an option to notify the operator when a "medium change is required", suggesting that it doesn't bail when the source volume was larger than the destination. So my best option then is to monitor disk usage and keep 1 SSD worth of disk space empty at all times. That way I still get RAID0 performance of 4 drives, as opposed to having to keep an unemployed SSD laying around.

---

### Post by zorlax on 2018-12-27
I'm not sure I follow you but I'll throw in some feedback anyway.

Do you want XFS or ZFS? They are quite different, especially with regards to RAID.

If you don't want to start from scratch RAID0 is not for you. I would either go RAID10 but that will mean four SSDs or mix RAID1 and 0.
For the mix I would put the base system on a mirror (if you need space and speed you could go for hybrid drives) and the work files that need speedy access and are backed up remotely on a SSD stripe and then rsync the important stuff from the stripe to the mirror.

I almost forgot and this is very important, Ubuntus GRUB does _***NOT ***_support XFS. I haven't tried ZFS on a boot volume but if you want your root to use XFS you will need to create an EFI partition (if you're on EFI) but above all a separate boot partition using one of the EXTs. If you don't do this you machine will not boot. I've wasted hours on this. Hours.

---

### Post by SeijiSensei on 2018-12-28
In my experience XFS cannot tolerate power outages well and can lose data. If you choose XFS, make sure the machine is connected to an uninterruptible power supply.

---

