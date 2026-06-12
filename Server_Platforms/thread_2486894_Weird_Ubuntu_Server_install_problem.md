---
title: "Weird Ubuntu Server install problem"
date: 2023-05-15
forum: Server Platforms
---

### Post by pigseye on 2023-05-15
Hi All,
Trying to build a media server using a Lenovo H500 (Type 10157) PC.
HW Specs
J1800 celeron 2.4gHZ
8gb ram
320 gb hdd
wif, ethernet, one 3.0 usb port and two 2.0 usb ports
Two sata connectors on motheboard, one for hard drive and one for the cdrom.

Install Ubuntu server and jellyfin as a test setup and everything works great.

Decide to add two 2.0TB ssd drives in RAID 1 by disconnecting the cdrom and existing hdd and replace with the two SSDs.

Start install process and set up the SSDs to boot from both and set up the partitions and configure the RAID 1.  add name, server name, username and start install.  Get error message "Sorry there was a problem during install..."  Skim through the gigantic error report but have no idea what it means.

Have repeated this process about 6 times and always end up with the same result.

Any suggestions on what is going wrong?  Ubuntu Server worked great on the single 320gb hdd but with these two 2.0TB SSDs in RAID it won't install.

Thanks

---

### Post by TheFu on 2023-05-15
Had to know what you are trying to do based on the description.  There are multiple possible interpretations based on what's written.

Just because USB storage seems to work most of the time, that doesn't mean it should be used for RAID, ever.  Booting RAID 1 is non-trivial in the best situations.  I'd rather see you have a delayed mirror (aka use rsync) than have RAID1.

USB is a terrible idea for RAID-anything.  The USB-storage command set isn't the same as the SATA, eSATA, SAS, SCSI or NVMe command set.

You'll need to look through the system error logs and start solving/looking up each error, in order.

BTW, you never said which type of RAID was being used. FakeRAID? SW-RAID? HW-RAID?  The only way I've seen RAID work with Ubuntu Server is
a) using LVM where the normal 1-disk setup happened during the install, then a mirror was added for each LV post-install.
b) using $350+ quality HW-RAID cards.

Fake-RAID is what motherboards provide.  They have all the limitations of HW-RAID with poor performance, so there is little use in using any FakeRAID on Linux.  Remember, RAID can never replace backups and RAID solves 2 issues only - High-Availability and improved performance. If you don't have sufficient storage for backups of all the data, then there's no reason to consider RAID-anything.  Backups solve 1001 issues, including corrupted RAID arrays.

Perhaps someone else would look at logs (that's part of my $day $job). I have little interest in reading someone else's log files. I get enough of that every morning and all day long already.
If you have specific questions about a specific error in the logs, the courteous way to post them is with about 10 lines around the error, using forum code-tags. Nobody wants to see entire log files.

Please try to be clearer exactly how the storage is connected and how it was connected during the install AND post-install.  No need to mention stuff that wasn't used/connected.  Something simple like how the SSDs are connected to the system would be very helpful.  Are they NVMe or SATA? Is there an adapter being used?  Does the BIOS see both SSDs?  Some SSDs need firmware updates to be seen by Linux.

Every 6 months or so, someone will get a 2TB - 40TB SSD for $54 and wonder why it doesn't work.  It is because the SSD is a fake and doesn't actually have the promised storage.  [https://www.theverge.com/2023/1/16/23557569/amazon-scam-review-merging-16tb-external-ssds](https://www.theverge.com/2023/1/16/23557569/amazon-scam-review-merging-16tb-external-ssds)  People in these forums have fallen for this a few times.

---

### Post by pigseye on 2023-05-15
> **TheFu said:**
> Had to know what you are trying to do based on the description.  There are multiple possible interpretations based on what's written.

Just because USB storage seems to work most of the time, that doesn't mean it should be used for RAID, ever.  Booting RAID 1 is non-trivial in the best situations.  I'd rather see you have a delayed mirror (aka use rsync) than have RAID1.

USB is a terrible idea for RAID-anything.  The USB-storage command set isn't the same as the SATA, eSATA, SAS, SCSI or NVMe command set.

You'll need to look through the system error logs and start solving/looking up each error, in order.

BTW, you never said which type of RAID was being used. FakeRAID? SW-RAID? HW-RAID?  The only way I've seen RAID work with Ubuntu Server is
a) using LVM where the normal 1-disk setup happened during the install, then a mirror was added for each LV post-install.
b) using $350+ quality HW-RAID cards.

Fake-RAID is what motherboards provide.  They have all the limitations of HW-RAID with poor performance, so there is little use in using any FakeRAID on Linux.  Remember, RAID can never replace backups and RAID solves 2 issues only - High-Availability and improved performance. If you don't have sufficient storage for backups of all the data, then there's no reason to consider RAID-anything.  Backups solve 1001 issues, including corrupted RAID arrays.

Perhaps someone else would look at logs (that's part of my $day $job). I have little interest in reading someone else's log files. I get enough of that every morning and all day long already.
If you have specific questions about a specific error in the logs, the courteous way to post them is with about 10 lines around the error, using forum code-tags. Nobody wants to see entire log files.

Please try to be clearer exactly how the storage is connected and how it was connected during the install AND post-install.  No need to mention stuff that wasn't used/connected.  Something simple like how the SSDs are connected to the system would be very helpful.  Are they NVMe or SATA? Is there an adapter being used?  Does the BIOS see both SSDs?  Some SSDs need firmware updates to be seen by Linux.

Every 6 months or so, someone will get a 2TB - 40TB SSD for $54 and wonder why it doesn't work.  It is because the SSD is a fake and doesn't actually have the promised storage.  [https://www.theverge.com/2023/1/16/23557569/amazon-scam-review-merging-16tb-external-ssds](https://www.theverge.com/2023/1/16/23557569/amazon-scam-review-merging-16tb-external-ssds)  People in these forums have fallen for this a few times.

Hello,
As you can probably tell I'm new to Ubuntu server and RAID configurations.  Unfortunately that means I probably do not know what to convey when there are problems.

I also completely understand why you do not want to review god awful long error reports.

Let's start with my objective.  I want to use this old low power Lenovo PC as a media server.  i was able to successfully install ubuntu server and jellyfin on an old single 320GB hard drive and the system worked great on my network.  However it was a lot of work to set up and configure and I thought setting up a RAID 1 system would provide redundancy and be fun to learn. 

Here are some insights of my situation:
Both SSDs are installed on SATA ports on the motherboard.  USB is NOT being used to configure RAID and the SSDs.
The two 2TB SSDs I purchased both have 1.86T available and I was able to install ubuntu server to each drive individually and boot up on either drive and on either sata port.  So both drives appear to function properly.
I'm trying to use SW RAID in ubuntu server and am not using LVM.  I don't even know how to use LVM.  I'm following guides from youtube where they were able to set up RAID 1 using smaller hard drives (40 to 50 GB)  
When configuring the RAID set up I reformat both drives to wipe out the previous partitions and then designate both SSDs as boot drives, create an 8gb swap partition on both drives, create a 1.77T partition on both drives, then format the 1.77T partition to ext4.  Approximately 95GB is left on each drive as unallocated space.
Then I start the install and enter my name, server name, and user name and then it starts and after a few seconds crashes.

A couple specific questions.
1)  Does the size of the SSDs affect the ability to create a Ubuntu Server SW RAID 1 set up?  Seeing the youtube videos with smaller drives makes it look fairly straight forward.
2) Is there another way to accomplish my goal of on the fly redundancy?
3) Is there another simple way to accomplish my goal of maintaining back ups of the system that do not include pulling the drives and cloning them externally.  Use RSYNC?  is this like timeshift?  more insight on how to do this would be great.

Any other insight you can provide is greatly appreciated.  Especially if you think this is a dumb idea.

Thanks

---

### Post by pigseye on 2023-05-16
Hi TheFu,
I've carefully reread your response and will drop the RAID 1 idea and move to backing up the system.  I'll do more research on rsync and rsnapshot and if I have questions I'll come back.

Appreciate you pointing me in this direction.

Thanks

---

### Post by lillyrowling18 on 2023-05-16
> **pigseye said:**
> Start install process and set up the SSDs to boot from both and set up the partitions and configure the RAID 1. add name, [[COLOR=222]idiom[/COLOR]]("https://www.theidioms.com/") server name, username and start install.
[COLOR=#252525]I just came to see if anyone else also had this problem since I also came across the same problem, but on my second attempt, I was able to install it. Working pretty well now.[/COLOR]

---

### Post by TheFu on 2023-05-16
> **pigseye said:**
> As you can probably tell I'm new to Ubuntu server and RAID configurations.  Unfortunately that means I probably do not know what to convey when there are problems.


Would be good to know which release you are attempting to use.  You haven't said and Canonical has been changing the installations drastically over the last few LTS releases.  Never use a non-LTS release, unless you are a tester or have a habit of distro hopping every few months (less than 6).  For production systems, the support period for non-LTS systems is just too short to be worth using.

My Jellyfin/Ubuntu/NFS box runs 20.04.  I'm just not upgrading another mirrored system from 18.04 to 20.04 (this week?).  22.04 has some things I'd rather avoid. I'll probably move to Debian for my next server upgrades to avoid that less-than-great stuff Canonical has decided to push.  Everyone needs to decide for themselves.  20.04 has a few of those little things being pushed that I'd rather not be forced to use. Sigh.

We each have to start somewhere.  Much knowledge in Unix/Linux can only be learned over time, through experience.  I've been an admin for Linux systems almost 30 yrs now.

I see AVOIDING issues as my main tool for having stable systems. I do that by NOT doing things that aren't commonly done, outside of test locations or virtual machines.  Storage design/setup is a core thing to avoid problems.  I'd never do what you are trying for a number of reasons, but hey - it is your machine, your hardware, and your time. 

> **pigseye said:**
> I also completely understand why you do not want to review god awful long error reports.

Someone needs to look at them. Figure out which errors are truly errors, and fix each. Allowing errors to remain will lead to problems.

> **pigseye said:**
> 
Let's start with my objective.  I want to use this old low power Lenovo PC as a media server.  i was able to successfully install ubuntu server and jellyfin on an old single 320GB hard drive and the system worked great on my network.  However it was a lot of work to set up and configure and I thought setting up a RAID 1 system would provide redundancy and be fun to learn. 

You choose to learn RAID is fine, but trying to make it boot is non-trivial for most inexperienced people.  Have you considered using RAID for just the data areas?  mdadm (I assume you are using that) isn't hard to use for that purpose.  However, generally, for people new to Linux, RAID1 becomes a way to write corrupted files to 2 different file systems faster.  Hence why I'd strongly recommend a delayed backup method for media files.  That way, new and changed files are only at risk for a day (at most) before another copy is pushed to other storage.  Honestly, I would never, ever, ever, use an SSD for backups.  That storage is too expensive for that purpose.  I'd get a 2-10TB HDD, and make that be the backup drive for all the systems (including tablets and phones) on the network.

  I love automatic, daily, versioned, backups, but media files are huge. I'm unwilling to have sufficient storage to have multiple versions of those in my backups. OTOH, normal files like photos, documents, code, all need to be versioned.  So, I use 2 different methods for backing up data.
a) rdiff-backup for all the things that need to be versioned. I started out with 30 days of versioned backups, but quickly found that rdiff-backup was efficient enough to allow 90 days of backups that still fit into my 2TB backup storage for that purpose. High risk systems always had 180 days of versioned backups, but I realized they were using such small amounts of storage that holding 366 days of versioned backups effectively made zero difference.
b) rsync for media files. I have just 1 extra copy of most media files, unless I have the CD/DVD too, then there are 3 copies. I refuse to allow Bluray into my house. I think that technology was designed broken.

> **pigseye said:**
> 
Here are some insights of my situation:
Both SSDs are installed on SATA ports on the motherboard.  USB is NOT being used to configure RAID and the SSDs.
The two 2TB SSDs I purchased both have 1.86T available and I was able to install ubuntu server to each drive individually and boot up on either drive and on either sata port.  So both drives appear to function properly.


Are you 100% certain they aren't fake? Did you pay the expected amount for that size ($100-$200 each)? Are they name-brand and bought by walking into a real store?  2TB is becoming more common  and fakes usually have outlandish size claims, so you are probably ok.

> **pigseye said:**
> 
I'm trying to use SW RAID in ubuntu server and am not using LVM.  I don't even know how to use LVM.  I'm following guides from youtube where they were able to set up RAID 1 using smaller hard drives (40 to 50 GB)  
When configuring the RAID set up I reformat both drives to wipe out the previous partitions and then designate both SSDs as boot drives, create an 8gb swap partition on both drives, create a 1.77T partition on both drives, then format the 1.77T partition to ext4.  Approximately 95GB is left on each drive as unallocated space.
Youtube people are probably showing how to do it within virtual machines.
LVM is an enterprise volume manager and brings many enterprise capabilities.  If you are new to Linux LVM isn't really needed, but it does make handling storage extremely flexible.  For the last 20+ yrs, it was common to see SW-RAID with LVM on top to make parsing out the RAID storage more flexible.  In the last 10 yrs, LVM added RAID features, though some of what they did is a bit ugly/confusing when using normal storage tools.  For example, here's a play ubuntu server using LVM RAID1 for the OS:
```
$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9500;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /

$ df -hT -x squashfs -x tmpfs -x devtmpfs $@ |sort -k7 -k6 -k1
Filesystem               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0 ext4  9.8G  3.5G  5.8G  38% /
/dev/vda2                ext4  739M  246M  439M  36% /boot

u2204-srv:~$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 rwi-aor--- 10.00g                                    100.00          
  lv-swap vg-00 -wi-ao----  1.00g                                                    
u2204-srv:~$ sudo vgs
  VG    #PV #LV #SN Attr   VSize  VFree
  vg-00   2   2   0 wz--n- 26.49g 5.48g
u2204-srv:~$ sudo pvs
  PV         VG    Fmt  Attr PSize   PFree
  /dev/vda3  vg-00 lvm2 a--  <13.25g 2.24g
  /dev/vdb3  vg-00 lvm2 a--  <13.25g 3.24g

```
I setup the system last fall to play with LVM RAID.  vda3 and vdb3 are where the mirroring happens.  lv-0 is the root file system.  I didn't mirror the boot or swap areas ... didn't know if that will work and it wasn't important to me.  With mdadm, the normal tools see the RAID1 storage in more expected ways with md0, md1, etc as the devices. The ugliness of the lsblk output is unfortunate. I'll probably never use just LVM for RAID1 again. It was an interesting experiment, however.  Fortunately, SSD storage is so reliable these days that I don't feel the need to have RAID-anything.  I have excellent backups.

> **pigseye said:**
> 
Then I start the install and enter my name, server name, and user name and then it starts and after a few seconds crashes.

And what do the logs show at that time?

> **pigseye said:**
> 
A couple specific questions.
1)  Does the size of the SSDs affect the ability to create a Ubuntu Server SW RAID 1 set up?  Seeing the youtube videos with smaller drives makes it look fairly straight forward.
I doubt it. There aren't really any size limitations with RAID or any file system in Linux.  However, there are many reasons why having 1 huge partition for everything is a terrible, terrible, terrible, idea.  How you layout your storage will impact how easy it is to backup, how easy it is to upgrade the OS, how likely run-away logs and other issues are to impact system stability, and the risks to other non-OS files.  For a "server", I want separate file systems. For example, 
```
nvme0n1                          465.8G disk                        
&#9500;&#9472;nvme0n1p1                         50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                        600M part ext4        boot       /boot
&#9492;&#9472;nvme0n1p3                        465G part LVM2_member            
  &#9500;&#9472;vg00-swap                      4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                   35G lvm  ext4        root       /
  &#9500;&#9472;vg00-var                        55G lvm  ext4        var        /var
  &#9492;&#9472;vg00-home                       26G lvm  ext4        home       /home
$ dft (this is an alias)
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p1                              vfat   50M  6.1M   44M  13% /boot/efi
/dev/nvme0n1p2                              ext4  574M  280M  252M  53% /boot
/dev/mapper/vg00-root--00                   ext4   35G   27G  5.7G  83% /
/dev/mapper/vg00-var                        ext4   54G   13G   39G  26% /var
/dev/mapper/vg00-home                       ext4   26G  9.9G   15G  41% /home
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  7.1G   12G  39% /var/lib/jellyfin

```
I didn't show the jellyfin storage, but it is separated between the /var/lib/jellyfin stuff (DB and media metadata) and all the media files which I haven't shown storage for.  I mount the media files under /d/D1, D2, D3, D4, D6, D7 .... and backups for them under /d/b-D1, b-D2, b-D3, b-D4, b-D6, b-D7.  Simple. Clear. Effective.  The system has been migrated as a media server since around 2012 with just a single 4TB HDD for everything.  Over all this time, it has had 3 disk failures. Twice the failed disk contained the OS.  When I moved to an NVMe SSD last upgrade, things seem to be mostly fine. 

The /var above is much larger than I'd normally have, but since that system also runs LXD and a few KVM/QEMU virtual machines, /var needed to be larger for toy VMs.  I actually use LVM directly to hold most virtual machine storage.  It isn't mounted onto the host system.
You'll note that I have a separate /boot and /boot/efi using different file system types.  EFI must be FAT32 according to standards and it is mandatory for UEFI booting systems.  I think having a separate /boot is required on 20.04 and earlier if LVM is used, but may not be on 22.04.  I don't have 22.04 on any real hardware and don't plan to ... er ... ever.

> **pigseye said:**
> 
2) Is there another way to accomplish my goal of on the fly redundancy?
Not a good answer that I know and have used.

> **pigseye said:**
> 
3) Is there another simple way to accomplish my goal of maintaining back ups of the system that do not include pulling the drives and cloning them externally.  Use RSYNC?  is this like timeshift?  more insight on how to do this would be great.
Simple?  Well, that depends. You are running a server and there are expectations around your skills in doing that.  All my backups happen over the network, except on the system actually doing the backups.  I use "pulled" backups. The client machines don't have any access to the storage where backups are placed.  The backup server "pulls" the data from each client.  This is an important protection against malware and crypt-locker issues.

> **pigseye said:**
> 
Any other insight you can provide is greatly appreciated.  Especially if you think this is a dumb idea.
I don't think it is dumb, but I don't know how to accomplish what you seek either.  We all have limited knowledge.  At work, we'd use HW-RAID and be done.  Actually, we use SANs and have the SAN storage frame handle all the redundancy the SAN frames also handle pushing backups to other locations overnight using huge WAN links.  Of course, most home users don't have that hardware/networking.

Get your backups working well.  That's my first suggestion. Until you have daily, automatic, versioned, backups working (except for media fiels), there's no good reason for RAID.  BTW, I setup RAID using mdadm on another system here back in 2008.  That RAID array has been upgraded, migrated, and brought forward for all these years.  In the beginning, I had lots of issues with SATA connectors coming loose every few weeks.  The solution was to get 90° SATA cables to connect into all the drives.  Seeing /dev/sdf constantly dropping from the RAID set was a major hassle.   Here's another system that has some data storage as RAID1.  Initially, it was RAID5 with 320GB HDDs.  It has had 2TB HDDs for some time now.  A few have failed (2TB Seagate HDDs failed after about 1 yr) over the years.  
```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sde2[1] sdd2[0]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sdc2[3] sdb3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
```
The RAID devices held file-based virtual machines.  I stopped using those and switched to LVM-based storage for VMs  ... perhaps around 2017 to get more flexibility and performance. I moved to SSD storage about that same time.  

I attended a regional Linux conference around 2015 and spoke with storage vendors. They had all already moved to SSDs for their storage.  During a "hallway track" talk with the vendor, he was very clear that SSD reliability was so high that using RAID wasn't necessary even for banks, credit card processors, and other huge transactional businesses.  He also said that these businesses had been using RAID so long that they'd never change and he'd happily take their money to provide 2x the storage they actually needed.  Of course, he was selling high-end storage for enterprises, not the $50 SSD you and I would get at a local Target store.  OTOH, that was a long time ago (in IT timespans) and the respected name-brand SSDs that are available today either fail quickly or last to their published Endurance TBW numbers.  By avoiding SSD storage that doesn't specifically include TBW as part of the warranty, we can effectively get similar reliability.  Just monitor the SMART data weekly.

---

### Post by TheFu on 2023-05-16
Someone else asked a similar question today, so that caused me to do a little research.  

> Getting ubuntu to boot with mdadm may be possible. IDK. If I have time, I'll try on a VM system running 20.04. I don't have any use for 22.04, sorry. [https://gist.github.com/fevangelou/2...302727665bf80a](https://gist.github.com/fevangelou/2...302727665bf80a) shows a layout and says that the Ubuntu Documentation is wrong.

Google found this guide [https://forums.linuxmint.com/viewtopic.php?t=391037](https://forums.linuxmint.com/viewtopic.php?t=391037) for Mint 21.1 (Ubuntu 22.04). The key steps are the chroot at the end and the initramfs rebuild. Hummmm. 

I can see a good reason to use RAID for the OS/booting stuff, but I'd definitely keep all of that separate from RAID/storage for pure data.  They wouldn't share the same logical array.

---

### Post by MAFoElffen on 2023-05-16
@TheFu --

I have a few mdadm test VM's with RAID5 on root, that boots great.

When someone was helping someone else and mentioned LVM Mirrors, I created an LMV2 internal RAID 7 on root, LV group, which was recognized by the 22.04 Live Install disk, without a separate boot partition, and it booted fine... Until the first update and then turned to toast. LOL. Oh well. I think it would have been fine with returning to a separate Boot partition, which the newest installer goes back to for LVM and encrypted LUKS disks.

EDIT: I used to use Hard RAID cards for everything, then mdadm grew up. I have a lot more experience with mdadm and raidz (and now with dRAID), than on LVM RAID arrays, but have done bad things to LVM2 Arrays, all in testing.

---

### Post by TheFu on 2023-05-17
> **MAFoElffen said:**
>  
When someone was helping someone else and mentioned LVM Mirrors, I created an LMV2 internal RAID 7 on root, LV group, which was recognized by the 22.04 Live Install disk, without a separate boot partition, and it booted fine... Until the first update and then turned to toast. LOL. Oh well. I think it would have been fine with returning to a separate Boot partition, which the newest installer goes back to for LVM and encrypted LUKS disks. 

Did you rebuild the initramfs via chroot after the failure?

On my play 22.04 server with LVM-RAID1 for the OS, I removed one of the disks and it didn't degrade nicely. It refused to boot without updating LVM to remove the missing mirror first ... which sorta sucks.  Booting in a degraded mode seems like a core feature for any RAID solution.  I added the missing virtual disk back, setup the PV/VG/LVs again and forced a re-sync, then it all worked.  Perhaps I did something wrong.  But if a power cable fails to a disk and it just disappears, the RAID should keep working and be able to be used with an OS at boot time.

Sigh.  So much easier to use quality SSDs, no RAID for the OS, and have excellent backups.  SSD failures after the initial failure period (say 30 days) until the TBW is hit are pretty rare, unless heating is a problem and the SSD just burns.

---

### Post by SeijiSensei on 2023-05-17
I didn't read all the detail here, but I never build systems that try to boot off a raid device. I always have another drive for booting and the filesystem root. I then mount the RAID array to /home.

If you can't accommodate another drive, you can repartition the existing drives so that they have one partition for boot/root and a second partition that is a component of the RAID device.

---

### Post by pigseye on 2023-05-20
Hi TheFU,
Sorry about the delayed follow up.

Regarding:
[COLOR=#000000]*"Would be good to know which release you are attempting to use."*
[/COLOR]22.04

[COLOR=#000000]*"You choose to learn RAID is fine, but trying to make it boot is non-trivial for most inexperienced people."*
A couple of points here. You are correct that the youtube videos I watched were people using VMs. And yes, I agree as simple as it looks in a video this is a very challenging thing to do correctly for a noob.
[/COLOR][COLOR=#000000]*"Are you 100% certain they (SSds) aren't fake?"*
[/COLOR][COLOR=#000000]No I am not. I purchased them from amazon and they are off brand and were about $70 for 2TB. I'm going to return one of them and keep this one as I'm not doing raid and then back up the system in case of failure. My next SSD will be brand name from Microcenter.

*"*[/COLOR][I][COLOR=#000000]Youtube people are probably showing how to do it within virtual machines.[/COLOR]
[/I][COLOR=#000000]*LVM is an enterprise volume manager and brings many enterprise capabilities."*
[/COLOR][COLOR=#000000]Your layout of LVM on RAID shows me this is way over my head at this time.

*"*[/COLOR]*[COLOR=#000000]And what do the logs show at that time?[/COLOR]*[COLOR=#000000]*"*
Unfortunately, I couldn't tell you. I tried reading them and they are WAY over my head. All I know is they were ungodly long.
[I]
"[/I][/COLOR]*[COLOR=#000000]Get your backups working well. That's my first suggestion. Until you have daily, automatic, versioned, backups working.[/COLOR]*[COLOR=#000000]*"*
This is what I'm going to do. As this is only a media server it is not mission critical and since it doesn't really change until I add another ripped dvd, daily backups are not necessary. I'm probably fine with weekly backups. Once I have this figured out I'll consider looking into RAID but only for humor. Nothing I do is critical and a good back up system is truly all I need to make my life easier if there is a problem in the future.

*"*[/COLOR]*[COLOR=#000000]I've been an admin for Linux systems almost 30 yrs now.[/COLOR]*[COLOR=#000000]*"*
Well it shows. You level of knowledge is something I'll never achieve at my advanced age but I am having fun scratching the linux surface and learning a few new things.

I do want you to know how much I appreciate your insight and your willingness to share your knowledge.

Thank you!
[/COLOR]

---

### Post by TheFu on 2023-05-20
Just be certain to keep the OS and home and data inside different partitions, if not different drives.  Then you can boot from an Ubuntu Desktop (any flavor you like), go into the "Try Ubuntu" running and get your media server up and running again using the backup storage and a chroot.  When the OS disk on my Jellyfin server failed, I ran this way for nearly a week ... with just enough of jellyfin setup so that others in the house didn't want to kill me while I slept.  Don't cut off the media.  If you do, you may never wake up. ;)

I got a new SSD today. Planning to do a fresh 20.04 install soon. (the system has 18.04 still).  I've migrated all the VMs off to another system already running 20.04. The migration was deceptively simple thanks to LVM, though not as easy as file-based VM storage would have been.

> 
"Are you 100% certain they (SSds) aren't fake?"

No I am not. I purchased them from amazon and they are off brand and were about $70 for 2TB. I'm going to return one of them and keep this one as I'm not doing raid and then back up the system in case of failure. My next SSD will be brand name from Microcenter.

I've seen semi-reputable SSD brands for $70 with 2TB. My rule of thumb is not to by any SSD that doesn't advertise their TBW (endurance) specifications and doesn't have at least a 5 yr warranty. Some of the newer SSD brands refuse to release the TBW numbers. I contacted their pre-Sales and they refused to tell me the numbers, so all I could do is take my money elsewhere.  Anyway, $70 for 2TB isn't outside the realm of possibilities.  We've seen 4TB-60TB SSDs advertised for less than $99.  Those are all fake. They end up having 2 microSD 8GB cards inside, but report whatever storage size was advertised.  Copies are really slow and the firmware just overwrites the same 16GB over and over and over.  [https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/](https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/) and [https://arstechnica.com/gadgets/2023/01/64gb-microsd-cards-are-posing-as-16tb-portable-ssds-on-amazon/](https://arstechnica.com/gadgets/2023/01/64gb-microsd-cards-are-posing-as-16tb-portable-ssds-on-amazon/) have more info.
And be careful with external SSDs from SanDisk [https://arstechnica.com/gadgets/2023/05/sandisk-extreme-ssds-keep-abruptly-failing-firmware-fix-for-only-some-promised/](https://arstechnica.com/gadgets/2023/05/sandisk-extreme-ssds-keep-abruptly-failing-firmware-fix-for-only-some-promised/)

I spent $70 for 1TB - a Samsung 980 (not PRO).  It will take over for a 500G Micron 1100, though I'll leave the Micron SSD in the system (it won't be there during the install). Adding it post-install will make for a nice, fast, data area for some churn with video processing/editing.  My motherboard isn't 4th-gen PCIe and I probably won't replace it for 8+ more years, so it didn't make sense to get the 980 PRO for speeds I'll never get.  The warranty and TBW endurance numbers were identical, so that's another reason I didn't bother spending more.

---

### Post by pigseye on 2023-05-21
I really like your idea of separating the OS from Jellyfin and the media files onto different SSDs.

Unfortuantely, I installed ubuntu Server 22.04 and jellyfin all on the same drive.  My guess is that it is not trivial to move ubuntu server to a 120GB SSD and then move jellyfin and media files to the 2TB SSD.

Would this be a near impossible task for a noob? 

 I could start all over too if that would be the cleanest way to go.  Heck this is like the 3rd or 4th time I've reinstalled ubuntu server and jellyfin and I learn something every time so it probably wouldn't be a total waste of time. 

Another question.  Should I be installing Jellyfin in a container like Docker?  is there any benefit in that on a dedicated media server?  I never plan to migrate the jellyfin install... again.  haha! 

Your insight is greatly appreciated.

Thanks Again!

---

### Post by TheFu on 2023-05-21
> **pigseye said:**
> I really like your idea of separating the OS from Jellyfin and the media files onto different SSDs.

Why would you waste money with an SSD for media files?  That makes no sense to me.  You're paying over 2x for really fast storage that any slow spinning drive could easily meet the needs for.  I suppose, some people aren't as cheap as me and don't need to optimize their spending.  SSD for the OS and jellyfin DB. Spinning rust for everything else.  Leave at least 20% of the SSD unused, so those extra free sectors are available for wear leveling inside the SSD.

> **pigseye said:**
> 
Unfortuantely, I installed ubuntu Server 22.04 and jellyfin all on the same drive.  My guess is that it is not trivial to move ubuntu server to a 120GB SSD and then move jellyfin and media files to the 2TB SSD.

Would this be a near impossible task for a noob? 


Don't think "drive", think "partition".  MSFT messed up so many people when they called things that are "partitions", "drives" and use the term "drive letter" - they aren't drives - they are partitions.  While I use LVM, a logical volume, LV, can be thought of as a really, really, flexible partition.  It can be modified while still being used, unlike partitions, which can only be modified when unmounted.  

LVs can be increased in size in about 5 seconds, so the smart method is to under size them at creation time, then extend their size AS-NEEDED. I try to size for 3 months, leaving much of the storage free.  Right now, I have 2 systems worth of VMs on a system system, so my Volume Group, VG, is a little fuller than normal:
```
$ sudo vgs
  VG             #PV #LV #SN Attr   VSize    VFree  
  vg00             1  14   0 wz--n- <464.98g **123.67g**

```
Typically, I have 5 VMs running each on 2 different physical systems. They share the load, but either alone can do everything, if needed. 1 system running everything is the current setup as I prepare to wipe and do that fresh install on the now-nearly-empty system. In theory, by the end of day today, I should have a new fresh install, with all the prior data/settings returned and 50% of the VMs moved back to the newly installed system.  Wish me luck.

Whether anything is trivial depends on skill.  It is trivial for me. I wouldn't know what is and isn't trivial for you.

> **pigseye said:**
> 
 I could start all over too if that would be the cleanest way to go.  Heck this is like the 3rd or 4th time I've reinstalled ubuntu server and jellyfin and I learn something every time so it probably wouldn't be a total waste of time. 

If you are new, why are you installing Ubuntu Server?  Use a desktop distro. It isn't like anything important is different, just don't put the desktop directly on the internet, accepting inbound network connections.

> **pigseye said:**
> 
Another question.  Should I be installing Jellyfin in a container like Docker?  is there any benefit in that on a dedicated media server?  I never plan to migrate the jellyfin install... again.  haha! 

I don't.  I haven't seen the need.  The standard packages in the repos have handled upgrades well enough.  I haven't had any friction between jellyfin and the OS.   Well, besides the fact they use crappy DotNET SDKs for their code, but I suppose that bloat is something only developers like me consider a failure.

Jellyfin is 1000x better than Plex, especially if you care about privacy.  If you don't need transcoding or don't record OTA broadcast TV using an HDHR tuner or don't need to support multiple clients in the household or don't need a pretty GUI webapp for W-A-F reasons, then there are lighter, easier, smaller, solutions to be a media server.  MiniDLNA is easy and light.

I don't use Plex for playback.  It is mostly a backend server and TV recorder.  For playback, I use OSMC on raspberry pi media players. I do use the android Jellyfin app to control those OSMC systems using the "send to" capability of Jellyfin and DLNA.  I need transcoding for some media, but not most.  By default, I store media as h.264/vorbis/mkv files. The raspberry pis can playback that type of file at 1080p resolution.  I don't have any 4K resolution screens.  
My pis are older, so they can't handle h.265 video.  They try, and choke every time.

---

### Post by MAFoElffen on 2023-05-21
Ah... Well...

I think I have explained this a few times (many times, LOL) and am no trying to step in. I have been following this with interest.

I try to explain things by painting a picture to visualize. Think of storage as containers to hold things. As TheFu said, separate your data into another container, way from your OS... And never, never, never assign a whole drive to mdadm, LVM2, ZFS, or BTRFS without a partition. It is possible, but most of the time, even with the same brand and model of drive, end up with problems. With putting them inside of a partition, you have 'control', and can set a specific size that you want to give to things, allocated like slices of a pie. And with VM's, never assign 100% of the VG to LV's. TheFu can tell you how he feels about that, for room for other things, like snapshots... Plan for the just-in-cases.

Here is one of my Test VM's with LVM2 internal RAID Members, that I use to test my 'system-info' script on:
View at: [https://termbin.com/1bvt](https://termbin.com/1bvt)
(Tip: <Cntrl><F>... Search on string "LVM2 Information" to skip to that section of the report.)

This test machine has 10 drives, each with partitions added as PV's. /dev/sda has extra partitons for EFI (ef00), /boot (linux 8300,ext4), and the swap PV extent. 

All the LVM containers were created before the actual install, as TheFu described. Even though Ubuntu will do LVM and encryption without a separate boot partition in 20.04 and 22.04... In 23.04, that has changed back to split that out again. I have always used a separate boot partition. It is just less problems, as long as you keep up with the maintenance of it. 2 drives with their partitions given to vg-root, 7 drives with their partitions given to vg-home...

On creating the Volume groups for the OS (ROOT), Swap, Home, Data, etc... I set the devices of PV's that I assign for each.  2 drives with their partitions given to vg-root, 7 drives with their partitions given to vg-home... I set the RAID in LV, set to the specific VG...

So you can see where the separation of partitions and drives come from that now, right?

I used to buy large HHD's. That has changed in the past year. Now I buy name-brand reconditioned SATA SSD and NVMe drives from a named brand source (for a about 33% of new cost).

Personally, I use ZFS, ZFS RAIDz, with SLOG caches and L2ARC caches on NVMe and SATA SSD vdevs. I just converted my last pools from HHD. My I/O speed and throughput is crazy. That is not what I recommend to someone that is new, or doesn't know what they are doing. Learn with LVM2 first.

LVM has so many features and capabilities that most people do not even touch on. You could learn a lot on LVM2. TheFu knows "whole lots" about LVM2. Mostly, learn and condition yourself to the methodology, and common practices, that you can use and apply to many other things "in how" you do things.

EDIT: I should note that the LTS installers for 20.04 and 22.04 are LVM2 aware when you choose "Other" for the partitioner... But I can't guaranty that for LTS 24.04. The new installer for 23.04 is **not** LVM2 aware. I feel that is a big problem. We shall see if they get that straightened out before the release of 24.04. I feel we should enlisted all that use LVM to join this bug, so that it can get corrected before LTS 24.04: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

---

### Post by TheFu on 2023-05-21
Compared to MAFoElffen, I am only an egg. Grok?

---

### Post by MAFoElffen on 2023-05-21
What? Because I am old? LOL

No... Seriously, I have the highest respect for TheFu, and I consider him a lot better than I with LVM2, backups, and many other things... 

Besides, I consider TheFu as a very good friend, and I will always have his back. LOL

He is very good and patient at explaining "complex things" to others.

---

### Post by TheFu on 2023-05-22
> **MAFoElffen said:**
> What? Because I am old? LOL

It was a quote from a famous book by Heinlein. I thought the "Grok" would give away the book, so the quote meaning would be universally understood.

---

### Post by MAFoElffen on 2023-05-22
Robert A. Heinlein, "Stranger in a Strange Land"... LOL.

---

### Post by pigseye on 2023-05-23
Thanks guys!  You both have convinced me to learn more about LVM/LVM2.  Some reaction comments;

From TheFU,
[I][COLOR=#000000]"Why would you waste money with an SSD for media files?"[/COLOR]      
I wasn't worried about the cost difference as I got the PC for free.  I do use spinning drives for all my backups and use ssds if the cost difference isn't significant to me.  

[/I]"[COLOR=#000000]Whether anything is trivial depends on skill. It is trivial for me. I wouldn't know what is and isn't trivial for you.[/COLOR]"  
Trying to migrate my system would not be trivial for me as I have low skill level.  I'm going to do a complete new install and use LVM2.  It's a good learning opportunity.

"[COLOR=#000000]If you are new, why are you installing Ubuntu Server? [/COLOR]"
For fun!  A media server is not mission critical for my family and I wanted to be forced into learning more about CLI and remote access.  I will admit that the jump from LinuxMint to Ubuntu Server has been incredibly significant but I am learning so many things that I would never learn with a desktop distro.

Regarding Docker
Based on your input I won't use Docker for this media server.  There are other applications where it makes sense, this probably isn't one of them.

 From [COLOR=#000000]*MAFoElffen,*[/COLOR]
[I][COLOR=#000000]"So you can see where the separation of partitions and drives come from that now, right?"
[/COLOR][/I]I sure do.  I appreciate the explanation and the examples.  

"[COLOR=#000000]Now I buy name-brand reconditioned SATA SSD and NVMe drives from a named brand source (for a about 33% of new cost).[/COLOR]"
Would you mind sharing your name brand source or sources?  

Thanks again!

---

### Post by pigseye on 2023-05-23
Dumb Question guys

I'm loading ubuntu server 22.04 onto an lvm on a 120GB ssd.  If I add a second 2TB SSD for jellyfin media files do I install jellyfin on the 2TB drive or would it be better to install jellyfin on the 120GB SSD and store all the media files on the 2TB drive?

Thanks!

---

### Post by MAFoElffen on 2023-05-23
I regularly buy Geek squad reconditioned and "open box" drives from "BestBuy" online, and have then shipped to my house. 

Here are the drives, filesystem, and layout of my server:
```

mafoelffen@Mikes-B460M:~$ sudo fdisk -l -o device,size,type | grep '^/dev/\|Disk model' | grep -v loop
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme0n1p1  1.8T Solaris reserved 1
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme1n1p1  1.8T Solaris reserved 1
Disk model: WD Blue SN570 1TB                       
/dev/nvme4n1p1  512M EFI System
/dev/nvme4n1p2    2G Linux swap
/dev/nvme4n1p3    2G Solaris boot
/dev/nvme4n1p4  927G Solaris root
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme2n1p1  1.8T Solaris reserved 1
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme3n1p1  1.8T Solaris reserved 1
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme6n1p1 1000G Solaris reserved 1
Disk model: Samsung SSD 970 EVO 2TB                 
/dev/nvme5n1p1  1.3T Solaris reserved 1
/dev/nvme5n1p2  583G Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sdb1   1.8T Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sdc1   1.8T Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sda1   1.8T Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sde1   1.8T Solaris reserved 1
Disk model: Crucial_CT512MX1
/dev/sdd1     16M Microsoft reserved
/dev/sdd2  476.3G Microsoft basic data
/dev/sdd3    607M Windows recovery environment
mafoelffen@Mikes-B460M:~$ sudo lsblk -o name,label,fstype,mountpoint,state -e7
NAME        LABEL    FSTYPE     MOUNTPOINT STATE
sda                                        running
&#9492;&#9472;sda1      datapool zfs_member            
sdb                                        running
&#9492;&#9472;sdb1      datapool zfs_member            
sdc                                        running
&#9492;&#9472;sdc1      datapool zfs_member            
sdd                                        running
&#9500;&#9472;sdd1               ext4                  
&#9500;&#9472;sdd2               ntfs                  
&#9492;&#9472;sdd3               ntfs                  
sde                                        running
&#9492;&#9472;sde1      datapool zfs_member            
nvme0n1                                    live
&#9492;&#9472;nvme0n1p1 kpool    zfs_member            
nvme1n1                                    live
&#9492;&#9472;nvme1n1p1 kpool    zfs_member            
nvme4n1                                    live
&#9500;&#9472;nvme4n1p1          vfat       /boot/efi  
&#9500;&#9472;nvme4n1p2          swap       [SWAP]     
&#9500;&#9472;nvme4n1p3 bpool    zfs_member            
&#9492;&#9472;nvme4n1p4 rpool    zfs_member            
nvme2n1                                    live
&#9492;&#9472;nvme2n1p1 kpool    zfs_member            
nvme3n1                                    live
&#9492;&#9472;nvme3n1p1 kpool    zfs_member            
nvme6n1                                    live
&#9492;&#9472;nvme6n1p1 datapool zfs_member            
nvme5n1                                    live
&#9500;&#9472;nvme5n1p1          zfs_member            
&#9492;&#9472;nvme5n1p2                                
mafoelffen@Mikes-B460M:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
datapool                                           777G  2.65T      776G  /data
datapool/DATA                                      558K  2.65T      279K  none
datapool/DATA/ubuntu_2cwpns                        279K  2.65T      279K  /data
kpool                                             1.54T  1.87T      279K  /KVM_Pool
kpool/KVM                                         1.54T  1.87T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.54T  1.87T     1.54T  /KVM_Pool
rpool                                             20.0G   872G       96K  /
rpool/ROOT                                        12.7G   872G       96K  none
rpool/ROOT/ubuntu_2cwpns                          12.7G   872G     6.65G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   872G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   872G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   872G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.09G   872G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   872G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  5.90G   872G     5.76G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   872G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    168K   872G      168K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              94.8M   872G     94.8M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             46.1M   872G     46.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   196M   872G      196M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   872G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.50M   872G     1.50M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   872G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   872G       96K  /var/www
rpool/USERDATA                                    7.21G   872G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  7.20G   872G     7.20G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.82M   872G     1.82M  /root
mafoelffen@Mikes-B460M:~$ sudo fdisk -l -o device,size,type | grep '^/dev/\|Disk model' | grep -v loop
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme0n1p1  1.8T Solaris reserved 1
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme1n1p1  1.8T Solaris reserved 1
Disk model: WD Blue SN570 1TB                       
/dev/nvme4n1p1  512M EFI System
/dev/nvme4n1p2    2G Linux swap
/dev/nvme4n1p3    2G Solaris boot
/dev/nvme4n1p4  927G Solaris root
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme2n1p1  1.8T Solaris reserved 1
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme3n1p1  1.8T Solaris reserved 1
Disk model: Samsung SSD 970 EVO Plus 2TB            
/dev/nvme6n1p1 1000G Solaris reserved 1
Disk model: Samsung SSD 970 EVO 2TB                 
/dev/nvme5n1p1  1.3T Solaris reserved 1
/dev/nvme5n1p2  583G Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sdb1   1.8T Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sdc1   1.8T Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sda1   1.8T Solaris reserved 1
Disk model: Samsung SSD 870 
/dev/sde1   1.8T Solaris reserved 1
Disk model: Crucial_CT512MX1
/dev/sdd1     16M Microsoft reserved
/dev/sdd2  476.3G Microsoft basic data
/dev/sdd3    607M Windows recovery environment

```
Me? I keep my OS'es on drives to themselves... Then I keep the data storage on their own drive pools, which I have separated into two RAIDz pools. Two of the nvme drives, I just use for SLOG Log and L2ARC caches, for the SSD RAID pool... which I reconfigure, as my conditions and workloads change. I took off the caches on my NVMe RAID pool, as it was not needed. My slower SSD RAID data pool's throughput is over 1.6MB/s on sustained writes...

I have a Plex server, on my Workstation (that has 4 x 5TB HDD drives and a 500GB SSD system drive), but TheFu and my son have convinced my to convert that to Jellyfin. I really respect theFu's thoughts on things.

Yes, I separate things out, just as TheFu does, OS/Home/Data... but use ZFS. Export my home and data pools. Reinstall a newer release. Restore my configs. Create my mountpoints. Import the pools to the mountpoints. back in business.

---

### Post by TheFu on 2023-05-24
> **pigseye said:**
> Dumb Question guys

I'm loading ubuntu server 22.04 onto an lvm on a 120GB ssd.  If I add a second 2TB SSD for jellyfin media files do I install jellyfin on the 2TB drive or would it be better to install jellyfin on the 120GB SSD and store all the media files on the 2TB drive?

Thanks!

I literally, just setup a new system the last 2 days. It is running 20.04 server (fresh install with fvwm as the WM)  to match another system - they are failover for each other, but not for jellyfin.
The drives in the box are:
```
$ inxi -dz
Drives:
  Local Storage: total: 1.83 TiB used: 142.84 GiB (7.6%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 980 1TB size: 931.51 GiB 
  ID-2: /dev/sda vendor: Hitachi model: HDP725050GLA360 size: 465.76 GiB 
  ID-3: /dev/sdb vendor: Micron model: 1100 MTFDDAV512TBN size: 476.94 GiB 
  Message: No Optical or Floppy data was found. 

```
The NVMe is new and where I placed the OS and even switched to using UEFI for booting.  The Micron 1100 can be ignored, for now. It was where the old OS was.
Here's the partitioning.  I created the partition and LVM2 objects after booting the installer, but before getting to the disk setup portion.  Ubuntu's disk setup sucks.

```
$ sudo fdisk -l /dev/nvme0n1
Disk /dev/nvme0n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 980 1TB                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 131072 bytes
Disklabel type: **gpt**
Disk identifier: AA2A1763-553C-4097-9CFD-D3621DFC2FE5

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048       4095       2048     1M BIOS boot
/dev/nvme0n1p2    4096     106495     102400    50M EFI System
/dev/nvme0n1p3  106496    1540095    1433600   700M Linux filesystem
/dev/nvme0n1p4 1540096 1953525134 1951985039 930.8G Linux LVM

```

The disks look like this from a filesystem perspective:

```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01           ext4   35G  5.5G   27G  17% /
/dev/nvme0n1p3                    ext4  672M  145M  479M  24% /boot
/dev/nvme0n1p2                    vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-home01           ext4  9.8G  4.8G  4.6G  52% /home
/dev/mapper/vg01-tmp01            ext4  3.9G  916K  3.7G   1% /tmp
/dev/mapper/vg01-var01            ext4   20G  889M   18G   5% /var
/dev/mapper/vg01-libvirt--01      ext4  132G  131G     0 100% /var/lib/libvirt
/dev/mapper/vg--hadar-lv--backups ext4  459G  686M  458G   1% /Backups

```
Note, there are 2 partitions with file systems ... these are for boot and EFI needs. The others are all LVM objects.  Another view of that:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                              SIZE TYPE FSTYPE      MOUNTPOINT
nvme0n1                         931.5G disk             
&#9500;&#9472;nvme0n1p1                         1M part ext2        
&#9500;&#9472;nvme0n1p2                        50M part vfat        /boot/efi
&#9500;&#9472;nvme0n1p3                       700M part ext4        /boot
&#9492;&#9472;nvme0n1p4                     930.8G part LVM2_member 
  &#9500;&#9472;vg01-swap01                   4.1G lvm  swap        [SWAP]
  &#9500;&#9472;vg01-root01                    35G lvm  ext4        /
  &#9500;&#9472;vg01-var01                     20G lvm  ext4        /var
  &#9500;&#9472;vg01-tmp01                      4G lvm  ext4        /tmp
  &#9500;&#9472;vg01-home01                    10G lvm  ext4        /home
  &#9500;&#9472;vg01-libvirt--01              135G lvm  ext4        /var/lib/libvirt
  &#9492;&#9472;vg01-lxd--containers--01       30G lvm              

```
Even though it is a 1TB SSD, I'm only using about 200GB from it today.

I use KVM and libvirt. By default, file-based VM storage goes into  /var/lib/libvirt, which is why I have that as a separate LV.
I use LXD for Linux containers.  I've created lxd--containers--01, but haven't mounted it.  I plan to lay-down a ZFS file system there, since LXD **really** prefers ZFS be used.
/var is 20G ... this is mainly for accidental snap packages that get installed.  I only plan to have lxd, but even with just lxd installed, a few other snaps were shoveled in.
```
$ snap list
Name    Version        Rev    Tracking       Publisher   Notes
core20  20230503       1891   latest/stable  canonical&#10003;  base
lxd     4.0.9-a29c6f1  24061  4.0/stable/&#8230;   canonical&#10003;  -
snapd   2.59.2         19122  latest/stable  canonical&#10003;  snapd
```

I have a separate /tmp mounted for security reasons.  The mount options for it aren't the same as for any other file system.
Anyway, that my layout after a fresh install.

For how to setup LVM before doing an install, you can read [Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144) I don't use LUKS encryption, so just ignore that part.  Also, something they don't say, but you need to know - all VGs, volume groups, inside a system must be unique, so if you ever plan to pull the SSD/HDD and connect it to a different system, you need to avoid VG name clashes.

I'm not picky about keeping the OS on 1 drive and everything else somewhere else, but I definitely keep them in separate file systems.  At the file system level, that's where my backup design works.  I already have "pull" backups from this system to my backup server working.
```
$ sudo du -sh /d/D7/backups/hadar*
6.0G    /d/D7/backups/hadar
14G     /d/D7/backups/hadar-18.04
```
the old backups held 90 days of daily, versioned, backups```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May 21 00:03:44 2023         5.74 GB           5.74 GB   (current mirror)
Sat May 20 00:03:44 2023         34.2 MB           5.78 GB
Fri May 19 00:03:48 2023         36.6 MB           5.81 GB
...
Wed Feb 22 00:05:12 2023         7.18 MB           13.4 GB
Tue Feb 21 00:03:50 2023         3.85 MB           13.4 GB
Mon Feb 20 00:03:50 2023         3.82 MB           13.4 GB

```
Everything needed to get the system back to exactly where it was in under 45 minutes, should the storage fail. This assumes 15 min for a fresh OS install.

---

### Post by TheFu on 2023-05-24
Looks like my sizing of the libvirt area is just a little too tight.  
```
$ \df .
Filesystem                   1K-blocks      Used Available Use% Mounted on
/dev/mapper/vg01-libvirt--01 138226184 137348184         0 **100%** /var/lib/libvirt
```

Thanks to LVM, I can add 2G trivially, 
```
$ sudo lvextend -r -L +2G /dev/mapper/vg01-libvirt--01 
  Size of logical volume vg01/libvirt-01 changed from 135.00 GiB (34560 extents) to 137.00 GiB (35072 extents).
  Logical volume vg01/libvirt-01 successfully resized.
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/vg01-libvirt--01 is mounted on /var/lib/libvirt; on-line resizing required
old_desc_blocks = 17, new_desc_blocks = 18
The filesystem on /dev/mapper/vg01-libvirt--01 is now 35913728 (4k) blocks long.

$ df .
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/vg01-libvirt--01  **134G**  131G     0 100% /var/lib/libvirt

```Much better, without waste. BTW, that command to extend the LV took about 2 seconds. I didn't umount the storage. I didn't reboot the system.  I ran that single command.  This is possible because the VG has plenty of empty space. 
```
$ sudo vgs
  VG       #PV #LV #SN Attr   VSize    VFree   
  vg01       1   7   0 wz--n- <930.78g <**690.68g**

```

---

### Post by MAFoElffen on 2023-05-24
Most of my work and testing is in KVM... That is why I also separate my VM storage pools out into my storage pools... I have a 'few' storage area's for VM images.
> **TheFu said:**
> ***"This is possible because the VG has plenty of empty space.*"**  
Yes, yes, yes, yes. Important tidbit to take note of and pay attention to... 

I think TheFu hasn't mentioned this enough (here), though he *usually* does. Most people allocate 100% of all their space, out at their install. I think he should explain this more, because he words that so well, and I think that methodology is important to practice. I'm with TheFu in that if you hold some back, then you can allocate it out when you need it, on demand. If it was already allocated out, then, well... You need some of that buffer space reserved for snapshops, housekeeping, and for the just-in-cases.

This methodology is something I practice, in many file managers and in storage management. If you allocate everything out at once, one day, it is filled, and you have no buffer to fall back on. Even with that, most OS'es and file systems live best if below 80% capacity. I have scripts that routinely check my storage capacities, and warn me if I get above a certain level on them.

@TheFU --- I am sorry for posting this. I don't mean to be a distraction. Back to watching and following this with interest.

---

### Post by TheFu on 2023-05-24
I thought post #23 covered that, but perhaps I'm too subtle and made it too dense with other information that the best practice of allocating only what you need for the next 3 months, not more, is the goal.  
For SSDs, I strive to leave at least 20% unused, to increase the lifetime of the SSD.  Providing more unused storage lets the smart controllers in SSDs do better wear leveling across more cells. This is beyond the unused space that is needed for snapshots and other needs that are not long term for the storage.

Allocate what you need, no more.  That's the rule for LVM and other volume managers.  With simple partitioning, this is too much hassle, so nobody does it.  With LVM, increasing the storage for an LV is really easy.  Over the decades that I've been an admin, I've never, ever, not 1 single time, guessed what storage was going to be needed for which areas for more than a few months at a time.

Think of it this way, if you allocate all the storage, when it is full, it is too late to do anything useful to buy storage on sale over the next 3-6 months.  OTOH, if we allocate storage as needed, we'll be forced to check the amount remaining from time to time and can make better decisions months before it becomes an emergency.  Like I show above, adding 1GB - 500GB of storage via LVM commands takes just a few seconds, has ZERO impact on performance and doesn't require any downtime.  Literally, nobody will notice, and we have all the flexibility that LVM provides for allocating storage from the VG to the LVs where it is needed.   Of if we have some new program ... say Plex Media Server ... and the DB for that tool grows larger than we thought it would, adding more space to that LV is easy, also with zero downtime.  On a different system, I specifically have an LV just for Jellyfin, 
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  8.3G   11G  45% /var/lib/jellyfin

```
I used to run Plex and it was using 90GB of storage just for the DB and metadata.  Jellyfin is more frugal.  I gave it 20G initially and only 8.3G are being used today.  That's with, let me check, 
```
$ inxi -d
Drives:
  Local Storage: total: 37.13 TiB used: 24.73 TiB (66.6%) 

```
Well, nearly 25TB of media connected (I do a 50/50 split with primary and backup storage).  I have been removing media files the last few years and migrating older storage to become backup storage, while newer storage becomes primary.  By doing this, I'm not hit with a $600 storage bill all at once.  I try to buy $150 in storage each year and slowly retire the really old stuff from any important use.

BTW, when I need to move storage from 1 disk to another, **pvmove** makes that easy - no downtime necessary if the new and old storage are connected to the same system.  It is possible to use **vgmove**, though I've never used it.  I have migrated LVs across systems, regardless of the PV and VG involved.  I was surprised when that just worked.  Moved about 10 virtual machines that way a few weeks ago. They all migrated easily. Only had to change 1 line in the KVM/QEMU libvirt XML file for each VM - the name of the VG/LV used on the new system.

---

### Post by pigseye on 2023-05-25
WOW!  So much of this is way over my head but I am starting to understand some of the concepts (I think).  

As my Jellyfin server is an old low power lenovo desktop and will not be used for other purposes I decided to load Jellyfin onto the OS 120GB SSD and keep the media files on a 2TB SSD.  I've created a clonezilla image of the OS and Jellyfin drive and all the media files are backed up on another external drive on my working OC running linuxmint.  

Here is what my system looks like from df -h.
Filesystem                  Size  Used Avail Use% Mounted on
tmpfs                       784M  1.4M  783M   1% /run
/dev/sdb4                    74G  5.5G   65G   8% /
tmpfs                       3.9G     0  3.9G   0% /dev/shm
tmpfs                       5.0M     0  5.0M   0% /run/lock
/dev/sdb1                   1.1G  6.1M  1.1G   1% /boot/efi
/dev/mapper/JS6002TB-Media  1.1T  349G  634G  36% /Media2TB
tmpfs                       784M  4.0K  784M   1% /run/user/1000

I made the LVM for media files a little too large but there is still about 25% unallocated space on the 2TB drive.  At this point the system is running very well and is backed up so i'm not going to keep tweaking it.  Seems like I always eventually break something trying to make it a little bit better.  

Thanks!

---

### Post by TheFu on 2023-05-25
Please use forum code-tags when posting terminal output, especially when there are columns involved.

And for df, please, please, please, use this alias:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
so we see real storage, not fake storage.

Getting perfectly aligned column output is just a copy/paste from the terminal, then use the Advanced Editor to select the terminal output and press the (#) edit format button.  

The harder you make it to read what you've posted, the less likely anyone is to actually look at it.  Fortunately, the email with your input did retain the correct columns. I removed the fake storage
```
Filesystem                  Size  Used Avail Use% Mounted on
/dev/sdb4                    74G  5.5G   65G   8% /
/dev/sdb1                   1.1G  6.1M  1.1G   1% /boot/efi
/dev/mapper/JS6002TB-Media  1.1T  349G  634G  36% /Media2TB

```
I'm confused by the /Media2TB mount. Something seems odd about it. Use the alias above.  The alias will show the file system, so we can tell some things.

Another handy alias:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
This provides a nice overview of the storage, including LVM objects.

Your / is much too large.  35G really should be all that any OS and programs are provided and that allows for tremendous bloat.
I'd be certain to split off /var/ into a separate partition. There are many reasons for this. /var is likely to fill up and it is best to keep separate and monitor it.  For a server, logwatch is a handy, daily, log monitoring tool. It wants to send a report via email using the installed MTA.  These things are part of running a "server."  Let the system email you about issues.

---

### Post by pigseye on 2023-05-28
Whoa, this alias thing is very cool.  I had no idea this was possible.  Unfortunately, so many things you are telling em are way over my head, even how to keep columns aligned. So it might take me a while to figure things out.

Here is my file system using the alias and trying to keep columns aligned.
```

Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/sdb4                  ext4   74G  5.7G   64G   9% /
/dev/sdb1                  vfat  1.1G  6.1M  1.1G   1% /boot/efi
/dev/mapper/JS6002TB-Media ext4  1.1T  391G  593G  40% /Media2TB

```

As you can see I have not reduced the size of sdb4 yet.  Interested in reading what you think is weird about the JS6002TB.

Thanks

---

### Post by TheFu on 2023-05-29
> **pigseye said:**
> 
```

Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/JS6002TB-Media ext4  1.1T  391G  593G  40% /Media2TB

```

As you can see I have not reduced the size of sdb4 yet.  Interested in reading what you think is weird about the JS6002TB.

The device link says "LVM2", but you aren't using LVM anywhere else.  Most people who use LVM would specifically want to use it for their OS, not just data.
If you use the **lsblkt** alias or run **sudo lvs** we can know for certain.

---

### Post by pigseye on 2023-05-29
```
 LV    VG       Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  Media JS6002TB -wi-ao---- <1.03t       
```

Crap.  you're right.  I thought I was installing Ubuntu server and jellyfin on a LVM on a 120GB ssd.  oh well I'm just going to leave it for now.  Everything is working good so far.  

I'm thinking of eventually getting rid of ubuntu server and going to a lightweight distro like you suggested earlier.  If I do that I'll try to use LVM for that install.


Thanks

---

