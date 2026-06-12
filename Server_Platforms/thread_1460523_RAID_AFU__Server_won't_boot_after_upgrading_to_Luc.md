---
title: "RAID AFU / Server won't boot after upgrading to Lucid RC1"
date: 2010-04-22
forum: Server Platforms
---

### Post by darkpixel on 2010-04-22
Ran 'do-release-upgrade -d' on my server running Hardy.

No problems during the upgrade.

Rebooted after the upgrade completed, and I was presented with the new plymouth screen.  This sucks for servers.  It sat there displaying the logo for ~5 minutes.  Hit CTRL+ALT+F1 through F8 and didn't see anything on the virtual consoles.  Finally figured out that I had to hit ESC on the plymouth screen to actually see what was going on.

It said /dev/sdi1 had problems along with /dev/md0.

It sat there forever with no fsck status and no HDD lights blinking.

SysRq+REISUB and tweaked the boot parameter to remove 'quiet splash' and appended 'S' for single-user mode.

Got the attached screenshot.

The box has been sitting like this for ~15 minutes.

Very lame.

Not entirely sure what to report a bug against at the moment.  Plus the somewhat-new requirement of running 'ubuntu-bug' is pretty retarded in this situation.  (Yeah, I know I can add some string to the URL to get around it.  Why is it such a pain in the *** to report a bug?)

I'm going to do some more digging to try and find out what is dying during boot.  The new boot process is a bit of a mystery to me still, so if anyone has pointers or any devs want more detailed information, please let me know.

---

### Post by darkpixel on 2010-04-23
Well, I'm lost.

I can boot off an 8.04 CD and all the drives show up and fsck without errors.
Rebooting into the newly installed 10.04 and the system says drives have unexpected inconsistencies and that fsck will run.  The system hangs and that's it.

Thinking that fsck or something may be running in the background, I left the system on all night.  No change.

---

### Post by Medwyyn42 on 2010-04-23
I have a similar issue that I've been working on for a few days. 9.10 upgrade to 10.04, just a home server. Primary is an 80GB PATA that runs fine, and I have a dual 1GB SATA RAID-1 (software) array. If I manually add the RAID array to fstab, the system will halt in the same state - system passes primary drive then hangs. If I comment out the array, the system boots with no issues. Then I just use Gnome Disk Utility to start array and mount (if I'm feeling lazy), also with no issues. I can't find anything in dmesg log to help diagnose the issue. Try commenting the array out of fstab and see if you get any further.... might work as a starting point. The other mount points in fstab are done using the UUID, the array is the old /dev/md0p1 format that worked fine in 9.10

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b187553a-f7b4-4acf-9ef8-bd14d8f352e4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=333fb6c1-6650-4020-83c4-8979307bc349 none            swap    sw              0       0

#RAID array

#/dev/md0p1  /media/Array  ext4  defaults  0  0

---

### Post by darkpixel on 2010-04-23
I thought that too, but after commenting out my RAID array, it still doesn't boot.

Tomorrow when I have a bit more time, I'm going to pull the drives from the array leaving only the system drive and see if that helps.

---

### Post by Medwyyn42 on 2010-04-23
Yeah, the other thing that I was hit by is that Lucid has drivers enabled by default for dmraid stuff. Took forever (and a fresh install, plus hours of array rebuilds) to clear out the fake-raid double entry for the array (I had turned on the fake-raid on the card to test it out on a prev. install and forgot about it). I really lucked out getting that one fixed. I had to turn off the fake-raid on the card, rebuilt the array, kill one drive, rebuild meta-data, then rebuild the array. The meta-data was 1.2 on one drive and .90 on the other. Still have all my data though. I also have a rc/init.d combo that is catching the system out - I run a small Teamspeak server and have Webmin installed, both set to start on boot. The Teamspeak server comes up, but Webmin never does. Not sure if this is involved in any way at all, but still working on that as well. Good luck.

---

### Post by darkpixel on 2010-04-24
No such luck on my end.
The RAID array is commented out in fstab and it still fails.
I remove the two fakeraid cards from my system (so there's only a single SATA drive and an IDE CD drive) and it works.

The moment the fakeraid cards are installed, the boot fails with no useful error.

Booting off the 9.10 server CD and using 'system rescue' allows me to see the array, but if I read/write data to it for about 15 seconds, the I get a core dump.  I don't actually see any useful error message, but the capslock and scrolllock lights alternatingly flash.

Booting off the 8.04 LTS CD allows me to see the array and access all the data with no issues.

---

### Post by Medwyyn42 on 2010-04-24
Hmm. I tried using UUID to automount in fstab resulting in same halt. The system checks out /dev/sda1 then starts AppArmour, and continues on with the array commented out.  Have you run update-initramfs -u after your changes? My dmesg sees the 2 SATA drives during the boot cycle but won't bring the array up automatically.

Message from boot that finished:
fsck from util-linux-ng 2.17.2 
/dev/sda1: clean, 216119/4685824 files, 1381376/18730240 blocks 
(stops here without array commented out)
 * Starting AppArmor profiles

dmesg:
[    2.247183] scsi2 : sata_sil
[    2.254096] scsi3 : sata_sil
[    2.254185] ata3: SATA max UDMA/100 mmio m512@0xfeaffc00 tf 0xfeaffc80 irq 22
[    2.254190] ata4: SATA max UDMA/100 mmio m512@0xfeaffc00 tf 0xfeaffcc0 irq 22
[    2.283931] md: raid1 personality registered for level 1
[    2.596034] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.604379] ata3.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    2.604384] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.620388] ata3.00: configured for UDMA/100
[    2.620536] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    2.620760] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.621132] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.621195] sd 2:0:0:0: [sdb] Write Protect is off
[    2.621199] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.621230] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.621423]  sdb: sdb1
[    2.640909] sd 2:0:0:0: [sdb] Attached SCSI disk
~~~~~~
[    2.940039] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.948374] ata4.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    2.948378] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.964388] ata4.00: configured for UDMA/100
[    2.964538] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    2.964707] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.964905] sd 3:0:0:0: [sdc] Write Protect is off
[    2.964909] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.964940] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.965192] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.965453]  sdc: sdc1
[    2.983420] sd 3:0:0:0: [sdc] Attached SCSI disk

And after I manually start and mount array:

[   86.894681] md: md0 stopped. (huh?)
[   86.948187] md: bind<sdb1>
[   86.948420] md: bind<sdc1>
[   86.991521] raid1: raid set md0 active with 2 out of 2 mirrors
[   86.991562] md0: detected capacity change from 0 to 1000202101760
[   87.003291]  md0: p1
[   92.637357] EXT4-fs (md0p1): mounted filesystem with ordered data mode

Are you actually using the dmraid mode or just software RAID? Could the card(s) not be detected correctly? There are a few tutorials floating around that have the user changing the RAID controller type because it was mis-reported.... Is the meta-data out of sync?

---

### Post by darkpixel on 2010-04-24
> **Medwyyn42 said:**
> Are you actually using the dmraid mode or just software RAID? Could the card(s) not be detected correctly? There are a few tutorials floating around that have the user changing the RAID controller type because it was mis-reported.... Is the meta-data out of sync?

I've never been using the dmraid functionality.  They are setup as JBOD in the fakeraid cards and then I've used mdadm to assemble them into a RAID6 array.  They've been running this way since 5.05.

With 10.04 both controllers and all the drives are detected, there's just some hang in the boot process that I can't see because either nothing is outputting text or plymouth is screwed up.

No worries though.  I just finished switching my server to Debian a few minutes ago and everything is working.

---

### Post by Medwyyn42 on 2010-04-25
Strange. Yes, the no output to debug bothers me as well. Glad you found a solution. I'm still going to work away at this until it is fixed. Don't want to spend the time switching around, and I don't reboot much anyway. I had big issues when I had the Sil card doing (fake)RAID and Ubuntu doing software RAID - whenever I booted, one drive was in the software array with metadata 1.2 and the other in the drmraid with metadata 0.9. Screwed things up royally. Both "arrays" would come up degraded (understandably), only one would mount, and often neither would have any members, but still show up as an array. I wish I could tell what went on between fschk and AppArmour starting.

---

