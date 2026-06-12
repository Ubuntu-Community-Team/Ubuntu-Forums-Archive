---
title: "Grub2 cannot find RAID1 arrays at startup"
date: 2010-09-29
forum: Server Platforms
---

### Post by bitter_buffalo on 2010-09-29
[FONT=Arial]I'm currently running Ubuntu 9.10 Server with a single IDE hard drive.  Having recently lost a drive at home, and realizing the magnitude of losing this one at work, I need to implement a RAID1 mirror using mdadm.  (Let's debate the merits of software vs. hardware elsewhere.)

[/FONT]      [FONT=Arial]I've been trying to do this for the past two days with no success.  Grub2 does not recognize the arrays at startup.  I feel like there is a simple solution to this, and hope that someone here can point out what I've done wrong or left out.  Here's what I've done so far, loosely using and adapting [this outdated guide from linuxconfig.org]("http://www.linuxconfig.org/Linux_Software_Raid_1_Setup").  I want to write-up this process if I can get it working &#8211; seems like a common enough task &#8211; so please pardon if there's a lot of detail.  Thanks in advance for any help.

[/FONT]
[FONT=Arial]**1.  Install new drive of the exact make and model as the existing drive.**  
[/FONT]   [FONT=Arial][INDENT]The existing drive is partitioned as follows:
  
  Disk /dev/sda: 500.1 GB, 500107862016 bytes
  255 heads, 63 sectors/track, 60801 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Disk identifier: 0x0004cd54
  
     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1   *           1       60770   488134993+  83  Linux
  /dev/sda2           60771       60801      249007+   5  Extended
  /dev/sda5           60771       60801      248976   83  Linux
  
  and mounted thus:
  
  /dev/mapper/Server-root on / type ext4 (rw,errors=remount-ro)
  proc on /proc type proc (rw)
  none on /sys type sysfs (rw,noexec,nosuid,nodev)
  none on /sys/fs/fuse/connections type fusectl (rw)
  none on /sys/kernel/debug type debugfs (rw)
  none on /sys/kernel/security type securityfs (rw)
  udev on /dev type tmpfs (rw,mode=0755)
  none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
  none on /dev/shm type tmpfs (rw,nosuid,nodev)
  none on /var/run type tmpfs (rw,nosuid,mode=0755)
  none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
  none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
  /dev/sda5 on /boot type ext2 (rw)[/INDENT][/FONT][FONT=Arial]Also, /dev/sda1 contains a volume group &#8220;Server&#8221; with logical volumes &#8220;root&#8221; and &#8220;swap_1&#8221;.


[/FONT]         [FONT=Arial]**2. Copy the partition table from /dev/sda to /dev/sdb.** 
[/FONT]   [FONT=Arial][INDENT]# sfdisk -d /dev/sda | sfdisk /dev/sdb[/INDENT][/FONT]      [FONT=Arial][B]
3. Set partition ID's on /dev/sdb to RAID autodetect (fd)[/B]
[/FONT]   [FONT=Arial][INDENT]# sfdisk --change-id /dev/sdb 1 fd[/INDENT][/FONT][INDENT][FONT=Arial]# sfdisk --change-id /dev/sdb 5 fd

[/FONT]      [FONT=Arial]*Is there an issue with sdb5 residing on extended partition sdb2?  I'm not able to exactly replicate the partition structure on the array... just md1 and md5 [/FONT][/INDENT][FONT=Arial]
[/FONT]   [FONT=Arial]**4. Create arrays using mdadm and format them**
[/FONT]   [FONT=Arial][INDENT]# mdadm --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb1[/INDENT][/FONT][INDENT][FONT=Arial]# mdadm --create /dev/md5 --level=1 --raid-disks=2 missing /dev/sdb5

[/FONT]      [FONT=Arial]# mkfs.ext4 /dev/md1
[/FONT]   [FONT=Arial]# mkfs.ext2 /dev/md5  
[/FONT]   [FONT=Arial](I'm using ext2 & ext4 to mirror the options for /dev/sda I chose at installation)[/FONT][/INDENT][FONT=Arial][B]
5. Create /dev/sda1 equivalent lvm2 volume groups and logical volumes on /dev/md1[/B][/FONT]
[FONT=Arial][INDENT]# pvcreate /dev/md1
  # vgcreate raid_vg /dev/md1
  # lvcreate -l(same) -nraid_root raid_vg
  # lvcreate -l(same) -nraid_swap raid_vg
 [/INDENT][/FONT]   [FONT=Arial][B]
6. Copy the data from /dev/sda to the array.[/B]
[/FONT]   [FONT=Arial][INDENT]# mount /dev/md5 /media[/INDENT][/FONT][INDENT][FONT=Arial]# rsync -aqxP /boot/* /media (using dd yielded a partition error)
[/FONT]   [FONT=Arial]# umount /media

[/FONT]      [FONT=Arial]# dd if=/dev/mapper/Server-root of=/dev/mapper/raid_vg-raid_root bs=64M
[/FONT]   [FONT=Arial]
# mkswap /dev/mapper/raid_vg-raid_swap[/FONT][/INDENT][FONT=Arial][B]
7. Append array info to /etc/mdadm/mdadm.conf.[/B]
[/FONT]   [FONT=Arial][INDENT]# cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.orig[/INDENT][/FONT][INDENT][FONT=Arial]# mdadm --detail --scan >> /etc/mdadm/mdadm.conf[/FONT][/INDENT][FONT=Arial][B]
8. Edit /etc/fstab so that it mounts the arrays at startup. [/B]
[/FONT]   [FONT=Arial][INDENT]Old fstab:[/INDENT][/FONT][INDENT][FONT=Arial]proc            /proc           proc    defaults        0       0
[/FONT]   [FONT=Arial]/dev/mapper/Server-root /               ext4    errors=remount-ro 0       1
[/FONT]   [FONT=Arial]UUID=33ede685-ed72-4149-83d1-749ace28e169 /boot           ext2    defaults        0       2
[/FONT]   [FONT=Arial]/dev/mapper/Server-swap_1 none            swap    sw              0       0
[/FONT]   [FONT=Arial]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/FONT]   [FONT=Arial]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[/FONT]      [FONT=Arial]New fstab:

[/FONT]      [FONT=Arial]proc            /proc           proc    defaults        0       0
[/FONT]   [FONT=Arial]/dev/mapper/raid_vg-raid_root /               ext4    errors=remount-ro 0       1
[/FONT]   [FONT=Arial]UUID=7df2beb1-0d79-47a4-b6d6-84bbf7184ec6 /boot           ext2    defaults        0       2
[/FONT]   [FONT=Arial]/dev/mapper/raid_vg-raid_swap none            swap    sw              0       0
[/FONT]   [FONT=Arial]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/FONT]   [FONT=Arial]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[/FONT]      [FONT=Arial]* UUID value for /dev/md5 obtained from blkid command[/FONT][/INDENT][FONT=Arial][B]
9. Mount array as /boot and update-grub.[/B]
[/FONT]      [FONT=Arial][INDENT]# umount /dev/sda5[/INDENT][/FONT][INDENT][FONT=Arial]# mount /dev/md5 /boot
[/FONT]   [FONT=Arial]# update-grub 

[/FONT]      [FONT=Arial]* grub finds kernels in /boot, finds Ubuntu 9.10 on /dev/mapper/raid_vg-raid_root, and rewrites grub.cfg[/FONT][/INDENT][FONT=Arial]
[/FONT]   [FONT=Arial]**10.  Reboot**
[/FONT]   [FONT=Arial][INDENT]Here&#8217;s where I don&#8217;t understand what goes wrong.  Grub loads normally, but when I check to make sure I&#8217;m using the arrays, I get this:[/INDENT][/FONT][INDENT][FONT=Arial]# mount 

[/FONT]      [FONT=Arial]/dev/mapper/Server-root on / type ext4 (rw,errors=remount-ro)
[/FONT]   [FONT=Arial]proc on /proc type proc (rw)
[/FONT]   [FONT=Arial]none on /sys type sysfs (rw,noexec,nosuid,nodev)
[/FONT]   [FONT=Arial]none on /sys/fs/fuse/connections type fusectl (rw)
[/FONT]   [FONT=Arial]none on /sys/kernel/debug type debugfs (rw)
[/FONT]   [FONT=Arial]none on /sys/kernel/security type securityfs (rw)
[/FONT]   [FONT=Arial]udev on /dev type tmpfs (rw,mode=0755)
[/FONT]   [FONT=Arial]none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
[/FONT]   [FONT=Arial]none on /dev/shm type tmpfs (rw,nosuid,nodev)
[/FONT]   [FONT=Arial]none on /var/run type tmpfs (rw,nosuid,mode=0755)
[/FONT]   [FONT=Arial]none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
[/FONT]   [FONT=Arial]none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
[/FONT]   [FONT=Arial]/dev/md5 on /boot type ext2 (rw) 

[/FONT]      [FONT=Arial]It appears to be booting from the array, and using the array&#8217;s swap space, but will not root to the array.  From the grub menu at startup, when I hit &#8216;e&#8217; to look at the underlying file, it still points to root at /dev/sda.  So from the command line I entered:

[/FONT]      [FONT=Arial]insmod raid
[/FONT]   [FONT=Arial]insmod lvm
[/FONT]   [FONT=Arial]ls

[/FONT]      [FONT=Arial]And it still doesn&#8217;t show any md devices.[/FONT][/INDENT][FONT=Arial]

Any ideas?  Am I leaving out an initramfs update?  If so, where does it go and what, exactly, does it do?  Should I manually edit the grub.cfg file to add the raid and lvm modules &#8211; even though the file says not to?

[/FONT]      [FONT=Arial]Thanks again.[/FONT]

---

