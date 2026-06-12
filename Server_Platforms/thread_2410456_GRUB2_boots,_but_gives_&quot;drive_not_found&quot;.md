---
title: "GRUB2 boots, but gives &quot;drive not found&quot; error when attempting update"
date: 2019-01-15
forum: Server Platforms
---

### Post by redadept on 2019-01-15
Server edition - Ubuntu 16.04, XFCE desktop
RAID 1 configuration with 1 hot spare - mdstat:

```
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[3] sdb1[4] sdc1[2](S)
      14324 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sdc2[2](S) sda2[3] sdb2[4]
      976745336 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
```

Today I updated the system in order to install about 3 months of updates, which froze halfway into the update (systemd? system-journal? something like that)-- I didn't write it down, figuring to re-boot and complete the upgrade.  Long story short, the system took about 10 minutes to shut down, and upon reboot began to re-sync the RAID drives.  I attempted the usual 'sudo dpkg --configure -a' to continue the upgrade, which worked, except for grub-pc and 3 other packages, which returned this worrying error message:

```
Setting up grub-pc (2.02~beta2-36ubuntu3.20) ...
Generating grub configuration file ...
grub-probe: error: disk `mduuid/0b332fe0048b87be574e721ad520ca94' not found.
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up friendly-recovery (0.2.31ubuntu2) ...
Generating grub configuration file ...
grub-probe: error: disk `mduuid/0b332fe0048b87be574e721ad520ca94' not found.

```

If I try 'sudo grub-probe /boot/grub' on the identical (working) backup server, I get the response 'ext2'  When I try it on this server I get the same error as when upgrading:
```
grub-probe: error: disk `mduuid/0b332fe0048b87be574e721ad520ca94' not found.
```
Running 'blkid' gives the following output:
```
/dev/sda1: UUID="84fb6a65-5556-b6c4-3a00-42d3bdbbca0d" UUID_SUB="650b5441-ec83-1c59-a8fc-246c1acdeb7c" LABEL="drupal-server:0" TYPE="linux_raid_member"
/dev/sda2: UUID="0b332fe0-048b-87be-574e-721ad520ca94" UUID_SUB="94674221-2a5f-f02d-c6dc-6c65f0fc0059" LABEL="drupal-server:1" TYPE="linux_raid_member"
/dev/sdb1: UUID="84fb6a65-5556-b6c4-3a00-42d3bdbbca0d" UUID_SUB="a9d57793-f19c-4127-b9d0-ec81bd26eb4b" LABEL="drupal-server:0" TYPE="linux_raid_member"
/dev/sdb2: UUID="0b332fe0-048b-87be-574e-721ad520ca94" UUID_SUB="d661c1db-8f1f-cf34-0587-0095b4950b7f" LABEL="drupal-server:1" TYPE="linux_raid_member"
/dev/sdc1: UUID="84fb6a65-5556-b6c4-3a00-42d3bdbbca0d" UUID_SUB="be529f27-5b81-1915-a811-b47125255e7e" LABEL="drupal-server:0" TYPE="linux_raid_member"
/dev/sdc2: UUID="0b332fe0-048b-87be-574e-721ad520ca94" UUID_SUB="1c2844c4-6988-3aee-c7b5-4ea1b611b8e5" LABEL="drupal-server:1" TYPE="linux_raid_member"
/dev/md1: UUID="2db88bd0-5338-47d9-b766-5131a31b1716" TYPE="ext4"
/dev/md0: UUID="08cb30f9-fdaf-4eb3-b85f-ed56835e41da" TYPE="swap"
```
which tells me that the UUID for sda2 and sdb2 match what GRUB says it cannot find.  When I checked the grub.cfg file, I found that the system had attempted to create a new file, but failed with a truncated version (grub.cfg.new) that never got re-named to grub.cfg.  Here is a snippet from the beginning of the old (working) grub.cfg
```
set root='mduuid/0b332fe0048b87be574e721ad520ca94'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='mduuid/0b332fe0048b87be574e721ad520ca94'  2db88bd0-5338-47d9-b766-5131a31b1716
else
  search --no-floppy --fs-uuid --set=root 2db88bd0-5338-47d9-b766-5131a31b1716
```
And finally, (with apologies for the length) here are the results of running the BootInfo script:

```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

md/1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/md1 is already mounted or /tmp/BootInfo-Z3rZ3W1z/MDRaid/md/1 busy
       /dev/md1 is already mounted on /

md/0: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048        30,719        28,672  fd Linux raid autodetect
/dev/sda2    *         30,720 1,953,523,711 1,953,492,992  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048        30,719        28,672  fd Linux raid autodetect
/dev/sdb2    *         30,720 1,953,523,711 1,953,492,992  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048        30,719        28,672  fd Linux raid autodetect
/dev/sdc2    *         30,720 1,953,523,711 1,953,492,992  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/md0         08cb30f9-fdaf-4eb3-b85f-ed56835e41da   swap       
/dev/md1         2db88bd0-5338-47d9-b766-5131a31b1716   ext4       
/dev/sda1        84fb6a65-5556-b6c4-3a00-42d3bdbbca0d   linux_raid_member drupal-server:0
/dev/sda2        0b332fe0-048b-87be-574e-721ad520ca94   linux_raid_member drupal-server:1
/dev/sdb1        84fb6a65-5556-b6c4-3a00-42d3bdbbca0d   linux_raid_member drupal-server:0
/dev/sdb2        0b332fe0-048b-87be-574e-721ad520ca94   linux_raid_member drupal-server:1
/dev/sdc1        84fb6a65-5556-b6c4-3a00-42d3bdbbca0d   linux_raid_member drupal-server:0
/dev/sdc2        0b332fe0-048b-87be-574e-721ad520ca94   linux_raid_member drupal-server:1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md1         /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
```

So there appears to be an error - "Mounting failed:   mount: /dev/md1 is already mounted or /tmp/BootInfo-Z3rZ3W1z/MDRaid/md/1 busy
       /dev/md1 is already mounted on /"  unless this is an error caused by running the script from within an already mounted drive rather than from a USB or repair disk.

Many, many thanks for anyone who can point me towards a solution.

Best

Darrell Eifert
Lane Memorial Library
Hampton, NH

---

### Post by oldfred on 2019-01-15
Do not know servers.

But if grub wrote the .new file that is because of  some error on one of the grub configuration files.
I had that years ago with my 40_custom. I had created some boot stanza including an old install that I was not using. Did not notice that it never was in my grub.cfg. Then with a grub update, it noticed that that stanza did not have an ending } and only wrote  the .new version of grub. Or they improved error checking. Also seen it where /etc/default/grub file has an error.

Check your grub configuration files.

---

### Post by redadept on 2019-01-15
Thank you Fred, but I'm not really sure what I'm looking for. I have not done any custom work on the existing grub.cfg file, so my best guess is that something became corrupted when the upgrade process did not successfully complete the first time.  Is there a way to safely force GRUB to scan the current RAID configuration and generate a new .cfg file?  I tried 'sudo update-grub' but that also returned the 'disk not found' error.

-- Darrell

---

### Post by darkod on 2019-01-15
I would simply purge the grub-pc and grub-common packages (when the OS is booted) and install them again.

Once the OS is booted and working, it is perfectly safe to purge grub and reinstall it. However, if there are any errors reinstalling DO NOT reboot otherwise it might not boot correctly.

Purging and reinstalling will give it a chance to create all the files from scratch. And remember that grub should be installed on the actual disks (like /dev/sda, /dev/sdb, etc), not on md devices or partitions.

---

### Post by redadept on 2019-01-25
Hello Darko and all  --

Thank you for all the helpful suggestions.  We had a tech look at the system and it turns out that at some time during the failed upgrade, the GRUB device.map went missing from the /boot/grub folder.  Running ```
grub-mkdevicemap
```restored the missing file and now all is well.  Hope this helps others who might run into the same problem.

Best,

-- Darrell

---

