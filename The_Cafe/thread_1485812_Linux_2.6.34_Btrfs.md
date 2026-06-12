---
title: "Linux 2.6.34 Btrfs"
date: 2010-05-17
forum: The Cafe
---

### Post by iponeverything on 2010-05-17
Hopefully, sometime in the not so distant future when some posts "The upgrade broke my system, how do I downgrade" -- There might be a better answer than to tell them to backup /home and reinstall the old version!

This is cool:

> In this version, Btrfs has the ability to change which subvolume or snapshot is mounted by default. For a while, Btrfs had a "mount -o subvol" option, which mounts into a subvolume instead of using the default root. The new ioctl allows you to set this once with "btrfs subvolume set-default" and have it used as the new default for every mount (without any mount options), until you change it again.

This feature is part of snapshot assisted distro upgrades, where you can take a snapshot of your distro, update it to a beta version, and revert back the default root to the old tree if you want to go back to the old, stable version. Support for such functionality has already been added to the Yum package manager when the "yum-plugin-fs-snapshot" package is installed. This plugin takes snapshots and modifies the GRUB configuration files to show different boot options for each snapshot (note that recent versions of LVM also support changing which snapshot is the default root, so you also can use this feature in LVM/Ext4 systems)


Linux_2_6_34 changelog:

[http://kernelnewbies.org/Linux_2_6_34#head-e677b459b5bd3792f1bfad6a83f8b1ad134c9d77](http://kernelnewbies.org/Linux_2_6_34#head-e677b459b5bd3792f1bfad6a83f8b1ad134c9d77)

---

### Post by RiceMonster on 2010-05-17
Cool.

Btrfs is looking really promising. I'm looking forward to when it reaches stability and the distributions start adopting it as the main file system.

---

### Post by Sporkman on 2010-05-17
> **RiceMonster said:**
> Cool.

Btrfs is looking really promising. I'm looking forward to when it reaches stability and the distributions start adopting it as the main file system.

Might be sooner than you think!

[http://ubuntuforums.org/showthread.php?t=1483534](http://ubuntuforums.org/showthread.php?t=1483534)

---

### Post by RiceMonster on 2010-05-17
> **Sporkman said:**
> Might be sooner than you think!

[http://ubuntuforums.org/showthread.php?t=1483534](http://ubuntuforums.org/showthread.php?t=1483534)

Sweet! Even if they don't adopt it in 10.10, the fact that it's being considered means that it's making good progress.

---

### Post by Eclipse. on 2010-05-17
> **RiceMonster said:**
> Sweet! Even if they don't adoot it in 10.10, the fact that it's being considered means that it's making good progress.

[www.netsplit.com/2010/05/14/](www.netsplit.com/2010/05/14/)**btrfs**-by-default-in-[B]maverick
> 
[/B]I do stress the emphasis of that statement, a number of things would  have to be true for us to take that decision:

   1. btrfs would need to not be marked “experimental” in the kernel  config; we understand that this is planned for 2.6.35, which is the  kernel version we are expecting to ship in Maverick.
   2. btrfs is not currently supported by GRUB2 (our boot loader) or the  installer; these pieces would need to be finished before Feature  Freeze.
   3. If that happens, we may make it the default for Alpha releases to  gain testing; that testing must go smoothly.
   4. The btrfs upstream must be happy with the idea.
   5. We must be happy with the idea.

It’s a tough gauntlet, and it would only made with the knowledge that  production servers and desktops can be run on Lucid as a fully supported  version of Ubuntu at the same time.  I’d give it a 1-in-5 chance. 			 		

In other words, no. 11.04 is more realistic.

---

