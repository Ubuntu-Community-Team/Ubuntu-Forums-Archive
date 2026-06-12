---
title: "RocketRaid640L Build Problem"
date: 2016-02-06
forum: Server Platforms
---

### Post by kazz2 on 2016-02-06
Hello everyone. I'm new to Ubuntu and Linux. I'm not new to server administration, I just stopped doing any of that with any server operating systems back in the late 90s. I had some time under my belt with CP/M and DOS so the command line's not new by any stretch.

I've decided to retire an old MS SBS2003 server and an MS WHS server, consolidating it all on a single Ubuntu 14.04.3 LTS server with a RAID 5 of four 3TB hard drives. I have a lot of older computer equipment around and have pressed a QX9650 processor and 790i motherboard with 4GB of RAM into service. All parts have actually had very little processing time, believe it or not. Stupidly, I purchased a RAID adapter before doing any research beyond mfr claims of compatibility.

I'm slowly learning Ubuntu, having started to do so this week. The server's up and operating on a SATA-connected hard drive. SSH and Samba are running, so I have Putty and a small share available on the server. I've physically installed the Highpoint RocketRaid 640L and four drives, using the adapter's BIOS utilities to configure the RAID 5 array. Now it's time to make Ubuntu see it.

My "guide" is a document here: [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid). I've found it to be quite outdated. My first issues were resolved by asking the mfr for their latest driver. I received RR64xl_Linux_Src_v1.3.11_15_09_30.tar.gz from them and copied it to the share onto the server. With some trial and error and Google I made it to the build step. Here's my outline for having done so:

```
tar -xzf RR64xl_Linux_Src_v1.3.11_15_09_30.tar.gz


cd rr64xl-linux-src-v1.3.11


edited 4 files & added one per doc https://help.ubuntu.com/community/RocketRaid
	1) location is actually inc/linux_32mpa
	2) remove all HPT_KMAP_TYPE lines in osm_linux.c, os_linux.c, osm_linux.h


cd product/rr64xl/linux


make


cd ../../..


sudo mkdir /usr/src/rr64xl-1.3.11


sudo cp -r * /usr/src/rr64xl-1.3.11


sudo dkms add -m rr64xl -v 1.3.11

```

A key part I stumbled into and dealt with to the best of my ability was removing all references to HPT_KMAP_TYPE in the three files mentioned. I removed them from the files mentioned. When they were used as part of a parameter of a function(?) I deleted the preceding comma and space as well as the text itself.

Here is the build command and associated messages:

```
sudo dkms build -m rr64xl -v 1.3.11


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
make KERNELRELEASE=3.19.0-49-generic -C product/rr64xl/linux/ KERNELDIR=/lib/modules/3.19.0-49-generic/build....
ERROR (dkms apport): binary package for rr64xl: 1.3.11 not found
Error!  Build of rr64xl.ko failed for: 3.19.0-49-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rr64xl/1.3.11/build/ for more information.

```
I've tried to find the make.log file with no luck so far.

Any suggestions?

Thanks!

---

### Post by matt_symes on 2016-02-06
Hi

> sudo cp -r * /usr/src/rr64xl-1.3.11

> <snip>
/var/lib/dkms/rr64xl/1.3.11/build/ 

I think you've copied the source into the wrong directory.

It's been years since i've manually built a module using dkms.

I definitely had to put the source in a dkms directory though.

Kind regards

---

### Post by sandyd on 2016-02-06
> **matt_symes said:**
> Hi





I think you've copied the source into the wrong directory.

It's been years since i've manually built a module using dkms.

I definitely had to put the source in a dkms directory though.

Kind regards

dkms add should create a symlink from the source (/usr/src/rr64xl-1.3.11) to the dkms dir (/var/lib/dkms/rr67xl/1.3.11/source)

Can you run
```

ls -l /var/lib/dkms/rr67xl/1.3.11/source
cat /usr/src/rr64xl-1.3.11/dkms.conf
```
May be that dkms.conf directories are incorrect

---

### Post by kazz2 on 2016-02-07
First, thank you for the replies. As one new to Linux and Ubuntu I found the wiki help page to be very disjointed and non-specific at times. For instance, they simply state to download the drivers. They don't say where to put them. Then, at another point, they say to make the .conf file in the root of the build. Again, being new to it all, that wasn't helpful enough. That's why I linked that page and then also listed my outline for getting to the point I was.

sandyd -

the ls command you requested tries to list contents of a directory that doesn't exist. I'm using the 640L and the directory created under dkms' name is rr64xl. Here is what I could run successfully, assuming that change:

```
ls -l /var/lib/dkms/rr64xl/1.3.11/source
lrwxrwxrwx 1 root root 22 Feb  6 15:42 /var/lib/dkms/rr64xl/1.3.11/source -> /usr/src/rr64xl-1.3.11

```

However, if I navigate to the directory and perform an ls, this is the output:

```
ls -l
total 36
drwxr-xr-x 2 root root 4096 Feb  6 15:42 dist
-rw-r--r-- 1 root root  291 Feb  6 15:42 dkms.conf
drwxr-xr-x 3 root root 4096 Feb  6 15:42 inc
drwxr-xr-x 3 root root 4096 Feb  6 15:42 lib
drwxr-xr-x 3 root root 4096 Feb  6 15:42 osm
drwxr-xr-x 3 root root 4096 Feb  6 15:42 product
-rw-r--r-- 1 root root 8224 Feb  6 15:42 README

```
And here is your requested cat command & output:

```
 cat /usr/src/rr64xl-1.3.11/dkms.conf
MAKE="make -C product/rr64xl/linux/ KERNELDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C product/rr64xl/linux/ clean"
BUILD_MODULE_NAME=rr640l
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr64xl/linux/
PACKAGE_NAME=rr64xl
PACKAGE_VERSION=1.3
AUTOINSTALL=yes

```


I'm happy to supply any other info needed and, again, greatly appreciate the help!

---

### Post by darkod on 2016-02-07
Going a step back, would you consider using mdadm software raid? You never needed the raid card, if your board has enough sata ports for all your disks. Just asking...

---

### Post by kazz2 on 2016-02-07
Thanks for the reply. The motherboard I'm using is SATA2 only. I have the internal HD attached to that for boot. Since I'm replacing a SATA3 server in the form of that WHS server, I wanted to use SATA3 and get some redundancy. The best cost per TB sporting decent redundancy on SATA3 I could come up with was the 4 3TB drives on SATA3.

All that said, I would say the most disposable part of my current build would be the RAID controller. But I've not done any homework to see if something cost-comparable is, perhaps, already baked into Ubuntu 14.04.3 to save me some pain. At least I haven't yet!

---

### Post by darkod on 2016-02-07
Hmmm, I don't think mechanical HDDs can fill SATA2. Hence they don't really benefit from SATA3. Only SSDs. You might wanna double check that on the internet, that could open options for you.

Many people would even prefer the mdadm raid instead of raid card, so if the SATA2 is not an issue...

Another option is a SATA3 card (simple SATA3 controller, not raid card) with at least 4 ports but you have to see if you can find one that you can use with your board and that will not be a bottleneck having 4 HDDs connected to it (the bus between the board and the card to be fast enough).

---

### Post by kazz2 on 2016-02-07
Interesting points, darkod. And, IIRC, there are plenty of SATA2 ports on the motherboard. I'll double-check.

So you don't believe a four-disk RAID5 will max out a SATA2 controller? I'll also have to see if they all use the same controller. Bet not. One's probably a third-party anyway, supported by the BIOS.

Thanks for bring up another potential solution.

Still, you'd think what I am trying to do currently wouldn't be so difficult?

Simple minutes and I have a RAID 5 on my onboard SATA2 ports. Thanks.

I've not made a filesystem yet. ext4 seems a default. But is this "silent corruption" seriously worth worrying about? Is it any more possible or frequent than what one would get from a modern-day Windows file system? From a performance persepective, the majority of this servers work will be serving up multimedia. Otherwise it will store documents, drivers, patches, PC backups, etc.

Thanks.

A bit more research has me staring at ZFS. I'll have to undo the array, I presume, in order to use ZFS and RAIDZ. Anybody care to send me another direction?

Thanks.

---

### Post by darkod on 2016-02-07
For storage servers ZFS is a great thing in fact. But in such case you definitely need to plug the disks directly into the board, or flash the raid card to "kill" the raid capability (if it's possible for that card). ZFS needs to work directly with the disks, not with a raid array you had created with a raid card/controller.

As for the previous question whether a four disk raid5 will max out SATA2, that's not precisely correct. Each disk is plugged into a SATA2 port and it doesn't matter if they are in a raid or not (mdadm raid is on the OS level). Each disk has available SATA2 speed, not the whole array as a unit. So you are looking whether single HDD can max out SATA2, not raid5. No?

---

### Post by kazz2 on 2016-02-07
The card is now removed. No need to pursue the RocketRaid discussion further, unfortunately, since from my experience someone needs to get it figured out and documented (updated).

Anyway, I think I will proceed with ZFS. Again, I simply believe I need to break up the array I created with mdadm first so that the ZFS utilities can use them as a Zpool (RAIDZ).

My somewhat rhetorical concern is/was whether simultaneous requests of all four SATA2-connected hard drives will swamp the northbridge. At least I believe it's the northbridge that handles SATA-connected data traffic on my 790i-based motherboard. Of course, that would be a max data rate which would seldom be seen, I would think. I'm still curious.

---

### Post by darkod on 2016-02-07
I wouldn't know about maxing the controller.

And yes, creating the zfs pool will destroy all data on the disks and any existing mdadm configuration or otherwise. But I don't think you need to do anything special in advance. Simply zfs will do its job and blow away everything on the disks.

---

### Post by kazz2 on 2016-02-07
Thanks for all the help today, darkod!

---

### Post by MAFoElffen on 2016-02-07
I brought this up this morning as I was heaing out the door this morning. I just got back and see you are in other direction.

One note... you were worried above data corruption, freezes and mentioned media and the 790i... If you google that, as I remember, those were all in bed together as issues, when that chipset was first released... So you might want to ensure that you have updated your BIOS. They came out with fixes for those issues.

---

### Post by kazz2 on 2016-02-08
I was referring to "silent corruption" of data that happens in many file systems. It's a big selling point for ZFS, I discovered.

I got the 790i up to date and burned in with Win7-64 and some overclocking, running benchmarks, etc. some time back. But the PC never got used much around here. Kids grow up, go to school, and move away. =)

ZFS is installed and running with two datasets so far. Super Bowl distracted me. Will finalize my dataset and shares design and have that spinning today. Then get a big chunk of data on there and start moving it around for a couple of days to be sure the drives are OK, etc. Then start migrating from SBS 2003 with the WHS and Plex as the last step.

Thanks, all!

---

### Post by kazz2 on 2016-02-19
One week later and I've found that my plan to use the motherboard's SATA2 ports and zfs to make a RAIDZ array won't work. Something to do with nVidia's SATA2 ports or lackings in drivers. Regardless, my choice became make a BIOS RAID or figure out how to get the Highpoint RocketRaid 640L working.

I don't like the idea of a BIOS RAID because there's no way to monitor it or manage it. I don't believe, should a drive issue arise, it will even tell me which of the drives is having issues. So I thought I'd give the RAID adapter one more go.

Going through the tech support conversation, getting the latest driver through them, and being given easy, straightforward installation instructions, I now have the adapter installed - theoretically. The instructions made the build and had me use modprobe rr640l to load it. All seems to have gone well. I'll be connecting the drives, defining the array in the adapter's BIOS, etc. In the meantime, I'd like to automate the loading of the adapter.

According to the instructions, I can either "put it into initrd file or configure a /etc/rc.d script" to load it.

Suggestions and some appropriate instructions?

Thanks!

---

### Post by darkod on 2016-02-19
Putting it in /etc/modules seem to be the way to go.
[http://askubuntu.com/questions/299676/how-to-install-3rd-party-module-so-that-it-is-loaded-on-boot](http://askubuntu.com/questions/299676/how-to-install-3rd-party-module-so-that-it-is-loaded-on-boot)

---

### Post by kazz2 on 2016-02-19
Thanks. But I'm now a bit confused by what I see. I created the array and rebooted Ubuntu. I saw 640L on multiple lines scrolling by at boot so clearly some aspect of it is installed. Running sudo parted and issuing a print all reveals:

```
GNU Parted 2.3Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print all
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
parted: invalid token: all
OK/Cancel? ok
Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 11720547408 blocks) or continue
with the current setting?
Fix/Ignore? f
Model: HPT DISK_0_0 (scsi)
Disk /dev/sda: 9002GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB               zfs
 9      3001GB  3001GB  8389kB


(parted) print all
Model: HPT DISK_0_0 (scsi)
Disk /dev/sda: 9002GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB               zfs
 9      3001GB  3001GB  8389kB




Model: Seagate Expansion Desk (scsi)
Disk /dev/sdb: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   5001GB  5001GB  ntfs         Basic data partition          msftdata




Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/kazz--u0a1--vg-root: 241GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  241GB  241GB  ext4




Error: /dev/mapper/kazz--u0a1--vg-swap_1: unrecognised disk label

```

Clearly Ubuntu could see the new array through the newly-installed adapter immediately. I took my best guess about fixing the GPT, as you can see. And there are some zfs partitions remaining on the drives.

1) Should I assume I need to delete those partitions on the 9TB array? I believe the proper tool is parted here (manpages is currently down).

2) Should I be concerned about the last line, "Error: /dev/mapper/kazz--u0a1--vg-swap_1: unrecognised disk label"?

Thanks!

---

### Post by darkod on 2016-02-19
Wow... First, keep your LVM VG names short, look how the /dev/mapper device looks now... :) And many dashes in it...

I really don't know your setup. What is that ntfs disk dev/sdb doing there???

If you created new array how come it has the zfs partitions there? Did it pick them up automatically? I would say yes, you need to create new blank partition table on each disk you want to use. Then you can partition it according to your needs and take it from there...

---

### Post by kazz2 on 2016-02-19
Well, let me display more of my ignorance. I'm not sure what LVM and VG are other than the former perhaps being logical volume name? I can assure you I've not assigned any names to anything other than the server, a few directories, and a couple of users.

dev/sdb is the Seagate external 5TB drive just recently added along with a USB 3.0 adapter.

Those four disks were in an array with the motherboard SATA2 ports. I deleted the zpool but I'm guessing I should have done more to wipe them clean before moving them to the add-in SATA3, RAID adapter as Ubuntu somehow found partition segments when it rebooted.

At this point all the drives are great except the 9TB RAID array. I need a method to wipe it clean and create a single partition on it for data. Again, parted?

And is the final line from parted a problem or no?

Thanks!

---

### Post by kazz2 on 2016-02-19
Actually, I should kill the adapter's RAID array and let zfs pool up my drives into a RAIDZ array. Yep.

---

### Post by darkod on 2016-02-19
Yes, LVM is Logical Volume Manager, the linux tool working with logical volumes. It consists of Volume Groups (VG) and Logical Volumes (LV). Did you maybe selected the guided installation option with use of LVM? Otherwise there should not be LVM on the server if you didn't set it up manually.

Don't worry about the swap right now, you can fix that easily later.

Or if you want to, we can tackle it now.

As for the array preparation, yes. Parted is your friend.

Something like this to create new partition spanning whole disk (assuming you want single partition on the whole array):
```
sudo parted /dev/sda
unit MiB
print (make sure sda is the correct disk before deleting the table)
mklabel gpt (new blank gpt partition table)
mkpart 1 xxx DATA
quit
```

Let me explain little my idea... At the parted prompt the unit command is to set the units you want to work with. I prefer MiB (the 1024x1024x1024 binary size, not 1000x1000x1000). Using print after that confirms you are working with the correct disk and gives you its capacity in MiB. You will use this to create the partition.
The mkpart creates partition starting from 1MiB to xxx MiB. You will get the xxx from print. Don't use the max value, I usually subtract 10-15 MiB from the end of the disk. The DATA is a simple label for the partition, use what ever you want.

After you do that you should have the /dev/sda1 partition spanning the whole array. You need to format it, and mount it to use it.

---

### Post by darkod on 2016-02-19
> **kazz2 said:**
> Actually, I should kill the adapter's RAID array and let zfs pool up my drives into a RAIDZ array. Yep.

Exactly. That's why you confused me. I thought you abandoned the zfs idea. Otherwise, zfs should work directly with the disks, not over raid.

---

### Post by kazz2 on 2016-02-19
Actually, I used gdisk (after installing it) to clear the partitions on the adapter's array. Sorry to have confused you. I've just been talking about using the adapter for a couple of days and, when I re-installed it, I set up the RAID for some reason.  I came to my senses today, at least! I have my documentation from when I originally set up the zpool, etc. so that should go smoothly now!

Thanks!

---

### Post by MAFoElffen on 2016-02-19
Hey??? 
I just helped someone a few days ago who has RocketRaid Arrays working on theirs. He was asking about udev rules to set a static drive assignment. I first thought he was "you" and that you got it going... but now see your post today and realize that he is a different person.  If you still had inklings, maybe you might want to message him or post to that thread, to ask him how he got his going... Just an idea.

This was the thread:
[http://ubuntuforums.org/showthread.php?t=2313929](http://ubuntuforums.org/showthread.php?t=2313929)

---

### Post by kazz2 on 2016-02-19
I'm sorry. I just skimmed that post. And from my - admittedly very brief - experience with Ubuntu, which drive is /dev/sda or /dev/sdb, /dev/sdc, etc. changes when you add drives, remove drives (even USB drives), etc. I have no idea how someone can dictate which physical drive at which physical connection ends up being /dev/sda or /dev/sdb.  Sorry, but I'm of no help to that individual. At the moment, my build seems to be working well.

---

### Post by kazz2 on 2016-02-20
Just to update and hoping I'm not jinxing anything - all's well.

A Highpoint RocketRaid 640L SATA3 RAID adapter is installed in Ubuntu Server 14.04.3 LTS with four Hitachi Deskstar 3TB hard drives. This is in an EVGA 790i Ultra SLI motherboard with 8GB RAM, an EVGA 8800GTX GPU (yep), an Insignia USB 3.1 add-in adapter, a USB3 Seagate external 5TB drive, a DVDRW optical drive and a 500GB SATA drive both connected to the onboard SATA2 ports.

The four 3TB drives have been used to create a RAIDZ array with zfs resulting in an available 7.3TB zfs partition. Approximately 1.3TB of data has been migrated to the array and backups using rsync have been successful to the external 5TB, USB 3.0 drive. zpool status shows no read or write errors.

The on-board SATA2 ports configured as RAIDZ with the same 3TB drives as above created multiple read and write errors and would seemingly create brief lockups. It's worth pointing out that EVGA is standing behind their lifetime warranty on the motherboard and has offered to replace it due to the SATA2 issues. I've declined so far. Perhaps when LTS expires in 2019 I'll take them up on their offer!

Thanks for all the help here. I can't say I have my Ubuntu server sealegs yet. But with the help of everyone here I think I'm on my way!

---

### Post by MAFoElffen on 2016-02-20
Understood.

Yes, I've always had good dealings with EVGA for my own, and my customers (both for video cards and SLI motherboards). Standing behind your products goes a long ways...

---

### Post by kazz2 on 2016-02-23
New fun.

I know I've rebooted this server a couple of times since I set up the array, shares, etc. Over the last two days I used rsync to backup data moved to the shares from the old servers to the external drive. That all went well. I needed to put the cover on the server so I shut it down, secured it, and booted it. The adapater's BIOS identifies the drives just fine. But the array and shares are missing when running a df -h. A quick review of the boot.log shows the auto-load(?) of zfs failed:

```
[COLOR=#000000]Begin: Loading essential drivers ... done.[/COLOR]Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
 * Stopping Send an event to indicate plymouth is up[74G[ OK ]
 * Stopping adjust system clock and timezone[74G[ OK ]
 * Starting Automatically import OpenZFS pools before mountall starts.[74G[[31mfail[39;49m]
 * Stopping Read required files in advance[74G[ OK ]
 * Starting Mount filesystems on boot[74G[ OK ]
 * Starting Populate and link to /run filesystem[74G[ OK ]
 * Stopping Populate and link to /run filesystem[74G[ OK ]
 * Stopping Track if upstart is running in a container[74G[ OK ]
 * Starting mount available cgroup filesystems[74G[ OK ]
 * Starting Initialize or finalize resolvconf[74G[ OK ]
 * Starting set console keymap[74G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 * Starting Bridge udev events into upstart[74G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[74G[ OK ]
 * Stopping set console keymap[74G[ OK ]
 * Starting device node and kernel event manager[74G[ OK ]
 * Starting load modules from /etc/modules[74G[ OK ]
 * Starting cold plug devices[74G[ OK ]
 * Starting log initial device creation[74G[ OK ]
 * Stopping load modules from /etc/modules[74G[ OK ]
 * Starting Uncomplicated firewall[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Bridge socket events into upstart[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting load fallback graphics devices[74G[ OK ]
 * Stopping load fallback graphics devices[74G[ OK ]
 * Starting enable remaining boot-time encrypted block devices[74G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[74G[ OK ]
 * Starting Clean /tmp directory[74G[ OK ]
 * Stopping Clean /tmp directory[74G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[74G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[74G[ OK ]
 * Starting Samba Winbind[74G[ OK ]
 * Starting SMB/CIFS File Server[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting flush early job output to logs[74G[ OK ]
 * Starting Plex Media Server[74G[ OK ]
 * Stopping Failsafe Boot Delay[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Stopping flush early job output to logs[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Starting Bridge file events into upstart[74G[ OK ]
 * Starting system logging daemon[74G[ OK ]
 * Starting D-Bus system message bus[74G[ OK ]
 * Starting SystemD login management service[74G[ OK ]
 * Starting early crypto disks...       [80G 
[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Setting up X socket directories...       [80G 
[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting KVM[74G[ OK ]
 * Starting automatic crash report generation[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Starting MD monitoring service mdadm --monitor       [80G 
[74G[ OK ]
 * Restoring resolver state...       [80G 
[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting OpenSSH server[74G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[74G[ OK ]
 * Starting NetBIOS name server[74G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[74G[[31mfail[39;49m]
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
 *  [COLOR=#000000] * Stopping System V runlevel compatibility[74G[ OK ][/COLOR]
```

fdisk confirmed the array drives weren't visible. The boot drive and external are visible and seem fine. So I thought I would try to load the driver for the RAID adapter in case, for some reason, that didn't autoload this time. A sudo modprobe rr640l told me that the module wasn't found. I don't know where modules should be, so I took it at it's word and re-created it. I navigated to the proper directory and issued the sudo make install which yielded this:

```
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-51-generic'  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/os_linux.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/osm_linux.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/div64.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/hptinfo.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/config.o
  LD [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/rr640l.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/.him_rr640l.o.cmd for /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/him_rr640l.o
  CC      /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/rr640l.mod.o
  LD [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/rr640l.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-51-generic'
You made a module which is for current kernel 3.19.0-51-generic.
Deleting previous installed driver module rr640l...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
backup /boot/initrd.img-3.19.0-51-generic to /boot/initrd.img-3.19.0-51-generic.rr640l.
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
```

IIRC, I received those warnings the first time I ran the make. At any rate, the sudo modprobe rr640l yielded no errors and returned me to the prompt. From here I thought I'd see if the zfs module and array had magically loaded with a sudo status zpool. That told me that the ZFS modules weren't loaded and to try running '/sbin/modprobe zfs' as root. Doing so told me that the module zfs is not found.

I decided it was time to stop and ask for help.

Why would these two modules disappear?

How do I keep this from happening again?

I believe that in order to have a module start at boot it's name (sans modprobe) needs to be added to /etc/modules. I confirmed all that is in there now is lp and rtc. Do I need to add rr640l and zfs to the modules file in order to have them load - assuming they exist, of course?

Thanks for any help and insights!

---

### Post by darkod on 2016-02-23
First, the problem with making your own modules (drivers) is that most often they do not re-do themselves on kernel update. So if you installed a new kernel, next reboot when the new kernel will load it will not load your module. Even if the module loads on boot. You can test this by loading a previous kernel (and if you remember the kernel used when building the module).

Second, how did you decide to load it on boot? Using the /etc/modules as suggested or another way?

Third, how did you install/build zfs? Because maybe the same from above applies, it doesn't rebuild itself on new kernel installation.

Which ubuntu server version are you running?

---

### Post by kazz2 on 2016-02-23
Thanks for the speedy reply. And I'm on 14.04.3 LTS.

I have no idea how to install a new kernel, I'm afraid. If it's a specific, intentional process then it hasn't happened. If it could be part of another process, I suppose it's possible. I recall, during the auto-install, being asked if I wanted auto-updates and I *think* I chose security-related updates only. Could that be the culprit?

I've done no editing of the modules file. Nor have I attempted to auto-load the rr640l or zfs modules - they've auto-loaded since they were created and loaded with the commands I listed - until today, of course.

ZFS was installed with the following commands:

```

sudo add-apt-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get install ubuntu-zfs

```

From there I created the pool, or array.

I guess your reply begs the questions:

How do I control when the kernel gets updated and does not get updated?

How do I retain modules for use in future kernel updates or do I always have to re-create them?

And is there any issue if I put the commands in the modules file but they're auto-loading anyway?

Thanks!

---

### Post by MAFoElffen on 2016-02-23
When you two started talking about ZFS, I tested Xenial Server against this Wiki doc and all was well... Tested it with 3 volumes in the pool.
[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

What is there for ZFS, is currently also in 15.10.

---

### Post by kazz2 on 2016-02-23
So that means, should I upgrade to Xenial, 15.05, that I wouldn't have to re-install zfs?

I'd still have the rr640l to install, though...

---

### Post by darkod on 2016-02-23
No, hold on... He just commented that zfs is included in the next LTS, 16.04. I wouldn't upgrade to 15.10 first of all because it's not a LTS and second because it's not a one step upgrade.
How you installed zfs with that ppa is how I have tested it with 14.04 and it works. It also supports kernel updates because the module is rebuilding itself.
I would focus on the rr module first, and making it survive reboots and kernel updates. I will answer the kernel update question when I get home.
Without the rr module loading and working fine, the rest is pointless. Even thought you tried few reboots it doesn't look like the rr module is working as it should. You say it wasn't loaded after the last reboot.

---

### Post by kazz2 on 2016-02-23
Thanks for the clarification. And I knew it wasn't LTS, but when grasping for air...

Anyway, your thought is that should I get the rr640l to auto-load ZFS should fire up? I would think ZFS should fire up regardless of the adapter since it's a filesystem and not dependent upon that adapter or anything connected to it. I suppose that it might fail to load if it has a record of a pool out there and doesn't find it. But it makes more sense for it to load and then just issue an error IMHO.

I'll focus on auto-load of the rr640l for now.

Thanks!

---

### Post by kazz2 on 2016-02-23
Followed all the steps to get the adapter driver rebuilt and loaded:

```
sudo apt-get install dkmsReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.19.0-41-generic linux-image-3.19.0-42-generic
  linux-image-extra-3.19.0-41-generic linux-image-extra-3.19.0-42-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  debhelper
The following packages will be DOWNGRADED:
  dkms
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 97 not upgraded.
Need to get 72.4 kB of archives.
After this operation, 1,024 B disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://ppa.launchpad.net/zfs-native/stable/ubuntu/ trusty/main dkms all 2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty [72.4 kB]
Fetched 72.4 kB in 0s (89.3 kB/s)
dpkg: warning: downgrading dkms from 2.2.0.3-1.1ubuntu5.14.04.5 to 2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty
(Reading database ... 164380 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty) over (2.2.0.3-1.1ubuntu5.14.04.5) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty) ...








 sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-51-generic'
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/os_linux.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/osm_linux.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/div64.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/hptinfo.o
  CC [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/config.o
  LD [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/rr640l.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/.him_rr640l.o.cmd for /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/him_rr640l.o
  LD [M]  /home/lrju0/admin/rr64xl-linux-src-v1.3.11/product/rr64xl/linux/.build/rr640l.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-51-generic'
You made a module which is for current kernel 3.19.0-51-generic.
Deleting previous installed driver module rr640l...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.








sudo modprobe rr640l
```

The downgrading of dkms bothered me, but didn't figure I had much of a choice. Seems more proof that kernel or something has changed since it was originally installed.

Anyway, I then rebooted. Magically, sudo fdisk -l now sees the four drives attached to the adapter. df -h doesn't show the partition, however. That implies to me that ZFS still needs to be (re-)installed. While all the data exists on other sources in-house, it's still 3.3+TB of data I'd rather not have to re-install, let alone the work to create the shares, permissions, etc.

So, if I re-install zfs now will it see the old array or will it wipe it?

---

### Post by darkod on 2016-02-23
Reinstalling the zfs package will not delete anything. I have done such tests. In fact zfs is very good guarding data.
But do NOT create new zpool, nothing. Just reinstall the package itself.
Then you will need to import your existing pools. I have to get home to check my notes for the exact commands. But they are easy to find on google too. Search for importing zfs pools or zpools.

---

### Post by kazz2 on 2016-02-23
I know you don't have reference to your notes. And I greatly appreciate all your help. But I'm hesitating about a zpool import because, after the sudo apt-get install ubuntu-zfs, a sudo zpool status tells me that zfs is not installed. And running the recommended sudo /sbin/modprobe zfs tells me module zfs not found.

I'm going to try an import anyhow once I figure out the syntax to my satisfaction. I'm certain it's just like the create with a couple of different parameters. But I thought that the zfs not found was odd.

I have a couple of other things I need to attend to but will post back here once I return and try the import.

Thanks again!

---

### Post by darkod on 2016-02-23
Hmmm, strange. zfs is needed for the import anyway, so if somehow it is not installed then the command will not run.

There is also quick way to check with 'man' because when zfs is installed the man pages for zfs and zpool are also installed. Do they open with 'man zfs' or 'man zpool'?

---

### Post by darkod on 2016-02-23
To check all pools available for import (and whether their members are online), use:
```
sudo zpool import
```
[http://docs.oracle.com/cd/E19253-01/819-5461/gazru/index.html](http://docs.oracle.com/cd/E19253-01/819-5461/gazru/index.html)

To import a pool once you have its name from the previous command:
```
sudo zpool import <name>
```
[http://docs.oracle.com/cd/E19253-01/819-5461/gazuf/index.html](http://docs.oracle.com/cd/E19253-01/819-5461/gazuf/index.html)

Let us know how it goes, together with zfs installing process...

---

### Post by kazz2 on 2016-02-23
man zfs and man zpool yield results. sudo zpool import claims zfs is not installed. Odd. I've even removed and re-installed zfs with no errors...

---

### Post by darkod on 2016-02-23
Yes, very odd. So the system still claims zfs is not installed and can't install it? I assume you still have the ppa active, otherwise apt-get install would give you an error that it can't find the ubuntu-zfs package.

---

### Post by kazz2 on 2016-02-23
Hm. Rebooted to see what's what and bad news in dmesg:

```
[COLOR=#000000][    0.000000] Initializing cgroup subsys cpuset[/COLOR][    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-51-generic (buildd@lgw01-51) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #57~14.04.1-Ubuntu SMP Fri Feb 19 14:36:55 UTC 2016 (Ubuntu 3.19.0-51.57~14.04.1-generic 3.19.8-ckt13)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-51-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000095fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000096000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfeeffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfef2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfef3000-0x00000000bfefffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 0.4 present.
[    0.000000] DMI:  EVGA  132-CK-NF79/132-CK-NF79, BIOS   P10  12/30/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 8191M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbfef0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f3fd0-0x000f3fdf] mapped at [ffff8800000f3fd0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000090000] 90000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
[    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23fdfffff]
[    0.000000]  [mem 0x220000000-0x23fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfeeffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbfdfffff] page 2M
[    0.000000]  [mem 0xbfe00000-0xbfeeffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21fffffff]
[    0.000000]  [mem 0x100000000-0x21fffffff] page 2M
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x34d94000-0x366c1fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7FA0 000014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 0x00000000BFEF3040 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 0x00000000BFEF30C0 000074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT 0x00000000BFEF3180 005447 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x00000000BFEF0000 000040
[    0.000000] ACPI: HPET 0x00000000BFEF8740 000038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: WDRT 0x00000000BFEF87C0 000047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: MCFG 0x00000000BFEF8880 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 0x00000000BFEF8640 000098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: OEMN 0x00000000BFEF8900 004AED (v01 NVIDIA NTUNEOEM 20302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23fff6000-0x23fffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00095fff]
[    0.000000]   node   0: [mem 0x00100000-0xbfeeffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x23fffffff]
[    0.000000] On node 0 totalpages: 2096773
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3989 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12220 pages used for memmap
[    0.000000]   DMA32 zone: 782064 pages, LIFO batch:31
[    0.000000]   Normal zone: 20480 pages used for memmap
[    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00096000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef0000-0xbfef2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef3000-0xbfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xbff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88023fc00000 s86144 r8192 d32640 u524288
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2063988
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-51-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8147084K/8387092K available (7926K kernel code, 1174K rwdata, 3760K rodata, 1408K init, 1292K bss, 240008K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3000.150 MHz processor
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.30 BogoMIPS (lpj=12000600)
[    0.004251] pid_max: default: 32768 minimum: 301
[    0.004372] ACPI: Core revision 20141107
[    0.010959] ACPI: All ACPI Tables successfully acquired
[    0.011190] Security Framework initialized
[    0.011320] AppArmor: AppArmor initialized
[    0.011433] Yama: becoming mindful.
[    0.012074] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.015550] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.017110] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.017250] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.017730] Initializing cgroup subsys memory
[    0.017852] Initializing cgroup subsys devices
[    0.017969] Initializing cgroup subsys freezer
[    0.018085] Initializing cgroup subsys net_cls
[    0.018202] Initializing cgroup subsys blkio
[    0.018317] Initializing cgroup subsys perf_event
[    0.018434] Initializing cgroup subsys net_prio
[    0.018552] Initializing cgroup subsys hugetlb
[    0.018688] CPU: Physical Processor ID: 0
[    0.018801] CPU: Processor Core ID: 0
[    0.018911] mce: CPU supports 6 MCE banks
[    0.019028] CPU0: Thermal monitoring enabled (TM1)
[    0.019147] process: using mwait in idle threads
[    0.019267] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.019267] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.019551] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.023234] ftrace: allocating 30037 entries in 118 pages
[    0.032535] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075851] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.080000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.080000] ... version:                2
[    0.080000] ... bit width:              40
[    0.080000] ... generic registers:      2
[    0.080000] ... value mask:             000000ffffffffff
[    0.080000] ... max period:             000000007fffffff
[    0.080000] ... fixed-purpose events:   3
[    0.080000] ... event mask:             0000000700000003
[    0.080000] x86: Booting SMP configuration:
[    0.080000] .... node  #0, CPUs:      #1
[    0.091563] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.091933]  #2 #3
[    0.118225] x86: Booted up 1 node, 4 CPUs
[    0.118430] smpboot: Total of 4 processors activated (24001.20 BogoMIPS)
[    0.120151] devtmpfs: initialized
[    0.127318] evm: security.selinux
[    0.127435] evm: security.SMACK64
[    0.127543] evm: security.SMACK64EXEC
[    0.127653] evm: security.SMACK64TRANSMUTE
[    0.127765] evm: security.SMACK64MMAP
[    0.127875] evm: security.ima
[    0.127981] evm: security.capability
[    0.128041] PM: Registering ACPI NVS region [mem 0xbfef0000-0xbfef2fff] (12288 bytes)
[    0.128347] pinctrl core: initialized pinctrl subsystem
[    0.128347] RTC time: 20:46:14, date: 02/23/16
[    0.128483] NET: Registered protocol family 16
[    0.132007] cpuidle: using governor ladder
[    0.136007] cpuidle: using governor menu
[    0.136176] ACPI: bus type PCI registered
[    0.136288] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.136481] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.136669] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.137139] PCI: Using configuration type 1 for base access
[    0.144126] ACPI: Added _OSI(Module Device)
[    0.144245] ACPI: Added _OSI(Processor Device)
[    0.146046] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.146163] ACPI: Added _OSI(Processor Aggregator Device)
[    0.150621] ACPI: Interpreter enabled
[    0.150735] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.151014] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.151309] ACPI: (supports S0 S3 S4 S5)
[    0.151421] ACPI: Using IOAPIC for interrupt routing
[    0.151628] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.151767] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.156822] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.156960] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.157229] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug]
[    0.157441] acpi PNP0A08:00: _OSC: OS now controls [PME AER PCIeCapability]
[    0.157815] PCI host bridge to bus 0000:00
[    0.157929] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.158049] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.158174] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.158300] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.158429] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.158559] pci_bus 0000:00: root bus resource [mem 0xbff00000-0xfebfffff]
[    0.158697] pci 0000:00:00.0: [10de:0800] type 00 class 0x060000
[    0.158812] pci 0000:00:00.1: [10de:0808] type 00 class 0x050000
[    0.158923] pci 0000:00:00.2: [10de:0809] type 00 class 0x050000
[    0.159031] pci 0000:00:00.3: [10de:080a] type 00 class 0x050000
[    0.159152] pci 0000:00:00.4: [10de:080b] type 00 class 0x050000
[    0.159277] pci 0000:00:00.5: [10de:080c] type 00 class 0x050000
[    0.159382] pci 0000:00:00.6: [10de:080d] type 00 class 0x050000
[    0.159490] pci 0000:00:00.7: [10de:080e] type 00 class 0x050000
[    0.159598] pci 0000:00:01.0: [10de:080f] type 00 class 0x050000
[    0.159697] pci 0000:00:01.1: [10de:0810] type 00 class 0x050000
[    0.159797] pci 0000:00:01.2: [10de:0811] type 00 class 0x050000
[    0.159895] pci 0000:00:01.3: [10de:0812] type 00 class 0x050000
[    0.159994] pci 0000:00:01.4: [10de:0813] type 00 class 0x050000
[    0.160100] pci 0000:00:01.5: [10de:0814] type 00 class 0x050000
[    0.160199] pci 0000:00:01.6: [10de:081a] type 00 class 0x050000
[    0.160319] pci 0000:00:01.7: [10de:080e] type 00 class 0x050000
[    0.160438] pci 0000:00:02.0: [10de:0815] type 01 class 0x060400
[    0.160521] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160573] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.160754] pci 0000:00:04.0: [10de:0817] type 01 class 0x060400
[    0.160846] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160899] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.161096] pci 0000:00:09.0: [10de:0369] type 00 class 0x050000
[    0.161344] pci 0000:00:0a.0: [10de:0360] type 00 class 0x060100
[    0.161352] pci 0000:00:0a.0: reg 0x10: [io  0xfc00-0xfc7f]
[    0.161455] pci 0000:00:0a.1: [10de:0368] type 00 class 0x0c0500
[    0.161468] pci 0000:00:0a.1: reg 0x10: [io  0xf800-0xf83f]
[    0.161490] pci 0000:00:0a.1: reg 0x20: [io  0xf400-0xf43f]
[    0.161497] pci 0000:00:0a.1: reg 0x24: [io  0xf000-0xf03f]
[    0.161534] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.161622] pci 0000:00:0b.0: [10de:036c] type 00 class 0x0c0310
[    0.161632] pci 0000:00:0b.0: reg 0x10: [mem 0xdffff000-0xdfffffff]
[    0.161677] pci 0000:00:0b.0: supports D1 D2
[    0.161678] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.161720] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.161881] pci 0000:00:0b.1: [10de:036d] type 00 class 0x0c0320
[    0.161891] pci 0000:00:0b.1: reg 0x10: [mem 0xdfffe000-0xdfffe0ff]
[    0.161938] pci 0000:00:0b.1: supports D1 D2
[    0.161940] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.161995] pci 0000:00:0b.1: System wakeup disabled by ACPI
[    0.162162] pci 0000:00:0d.0: [10de:036e] type 00 class 0x01018a
[    0.162186] pci 0000:00:0d.0: reg 0x20: [io  0xec00-0xec0f]
[    0.162197] pci 0000:00:0d.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.162329] pci 0000:00:0d.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.162456] pci 0000:00:0d.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.162588] pci 0000:00:0d.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.162802] pci 0000:00:0e.0: [10de:037f] type 00 class 0x010485
[    0.162814] pci 0000:00:0e.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.162819] pci 0000:00:0e.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.162825] pci 0000:00:0e.0: reg 0x18: [io  0x0970-0x0977]
[    0.162830] pci 0000:00:0e.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.162836] pci 0000:00:0e.0: reg 0x20: [io  0xd800-0xd80f]
[    0.162841] pci 0000:00:0e.0: reg 0x24: [mem 0xdfffd000-0xdfffdfff]
[    0.162941] pci 0000:00:0e.1: [10de:037f] type 00 class 0x010485
[    0.162952] pci 0000:00:0e.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.162958] pci 0000:00:0e.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.162963] pci 0000:00:0e.1: reg 0x18: [io  0x0960-0x0967]
[    0.162969] pci 0000:00:0e.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.162974] pci 0000:00:0e.1: reg 0x20: [io  0xc400-0xc40f]
[    0.162980] pci 0000:00:0e.1: reg 0x24: [mem 0xdfffc000-0xdfffcfff]
[    0.163079] pci 0000:00:0e.2: [10de:037f] type 00 class 0x010485
[    0.163091] pci 0000:00:0e.2: reg 0x10: [io  0xc000-0xc007]
[    0.163096] pci 0000:00:0e.2: reg 0x14: [io  0xbc00-0xbc03]
[    0.163102] pci 0000:00:0e.2: reg 0x18: [io  0xb800-0xb807]
[    0.163107] pci 0000:00:0e.2: reg 0x1c: [io  0xb400-0xb403]
[    0.163113] pci 0000:00:0e.2: reg 0x20: [io  0xb000-0xb00f]
[    0.163118] pci 0000:00:0e.2: reg 0x24: [mem 0xdfffb000-0xdfffbfff]
[    0.163223] pci 0000:00:0f.0: [10de:0370] type 01 class 0x060401
[    0.163294] pci 0000:00:0f.0: System wakeup disabled by ACPI
[    0.163457] pci 0000:00:0f.1: [10de:0371] type 00 class 0x040300
[    0.163469] pci 0000:00:0f.1: reg 0x10: [mem 0xdfff0000-0xdfff3fff]
[    0.163522] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.163567] pci 0000:00:0f.1: System wakeup disabled by ACPI
[    0.163740] pci 0000:00:11.0: [10de:0373] type 00 class 0x068000
[    0.163754] pci 0000:00:11.0: reg 0x10: [mem 0xdfffa000-0xdfffafff]
[    0.163760] pci 0000:00:11.0: reg 0x14: [io  0xac00-0xac07]
[    0.163765] pci 0000:00:11.0: reg 0x18: [mem 0xdfff9000-0xdfff90ff]
[    0.163771] pci 0000:00:11.0: reg 0x1c: [mem 0xdfff8000-0xdfff800f]
[    0.163816] pci 0000:00:11.0: supports D1 D2
[    0.163817] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163864] pci 0000:00:11.0: System wakeup disabled by ACPI
[    0.164036] pci 0000:00:12.0: [10de:0373] type 00 class 0x068000
[    0.164049] pci 0000:00:12.0: reg 0x10: [mem 0xdfff7000-0xdfff7fff]
[    0.164055] pci 0000:00:12.0: reg 0x14: [io  0xa800-0xa807]
[    0.164061] pci 0000:00:12.0: reg 0x18: [mem 0xdfff6000-0xdfff60ff]
[    0.164066] pci 0000:00:12.0: reg 0x1c: [mem 0xdfff5000-0xdfff500f]
[    0.164111] pci 0000:00:12.0: supports D1 D2
[    0.164113] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164161] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.164326] pci 0000:00:15.0: [10de:0374] type 01 class 0x060400
[    0.164372] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164417] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.164584] pci 0000:00:18.0: [10de:0377] type 01 class 0x060400
[    0.164629] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164674] pci 0000:00:18.0: System wakeup disabled by ACPI
[    0.164913] pci 0000:01:00.0: [10de:0191] type 00 class 0x030000
[    0.164922] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.164931] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.164939] pci 0000:01:00.0: reg 0x1c: [mem 0xda000000-0xdbffffff 64bit]
[    0.164945] pci 0000:01:00.0: reg 0x24: [io  0x9c00-0x9c7f]
[    0.164951] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.165016] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.165212] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.165334] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.165338] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.165343] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.165411] pci 0000:02:00.0: [1103:0641] type 00 class 0x010400
[    0.165421] pci 0000:02:00.0: reg 0x10: [io  0x8c00-0x8c07]
[    0.165427] pci 0000:02:00.0: reg 0x14: [io  0x8800-0x8803]
[    0.165433] pci 0000:02:00.0: reg 0x18: [io  0x8400-0x8407]
[    0.165440] pci 0000:02:00.0: reg 0x1c: [io  0x8000-0x8003]
[    0.165446] pci 0000:02:00.0: reg 0x20: [io  0x7c00-0x7c1f]
[    0.165452] pci 0000:02:00.0: reg 0x24: [mem 0xdfeff000-0xdfeff7ff]
[    0.165459] pci 0000:02:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.165492] pci 0000:02:00.0: PME# supported from D3hot
[    0.172014] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.172139] pci 0000:00:04.0:   bridge window [io  0x7000-0x8fff]
[    0.172144] pci 0000:00:04.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.172223] pci 0000:00:0f.0: PCI bridge to [bus 03] (subtractive decode)
[    0.172355] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.172357] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.172359] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.172361] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.172362] pci 0000:00:0f.0:   bridge window [mem 0xbff00000-0xfebfffff] (subtractive decode)
[    0.172417] pci 0000:04:00.0: [197b:2363] type 00 class 0x010601
[    0.172488] pci 0000:04:00.0: reg 0x24: [mem 0xdfdfe000-0xdfdfffff]
[    0.172544] pci 0000:04:00.0: PME# supported from D3hot
[    0.172601] pci 0000:04:00.1: [197b:2363] type 00 class 0x010185
[    0.172617] pci 0000:04:00.1: reg 0x10: [io  0x6c00-0x6c07]
[    0.172626] pci 0000:04:00.1: reg 0x14: [io  0x6800-0x6803]
[    0.172634] pci 0000:04:00.1: reg 0x18: [io  0x6400-0x6407]
[    0.172642] pci 0000:04:00.1: reg 0x1c: [io  0x6000-0x6003]
[    0.172650] pci 0000:04:00.1: reg 0x20: [io  0x5c00-0x5c0f]
[    0.172740] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.172938] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.173059] pci 0000:00:15.0:   bridge window [io  0x5000-0x6fff]
[    0.173061] pci 0000:00:15.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.173134] pci 0000:05:00.0: [1912:0015] type 00 class 0x0c0330
[    0.173168] pci 0000:05:00.0: reg 0x10: [mem 0xdfcfe000-0xdfcfffff 64bit]
[    0.173335] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.180020] pci 0000:00:18.0: PCI bridge to [bus 05]
[    0.180145] pci 0000:00:18.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.180573] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.181296] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.182009] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.182721] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.183434] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[    0.184020] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 *10 11 14 15)
[    0.184592] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 *10 11 14 15)
[    0.185174] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 *11 14 15)
[    0.185745] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.186317] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.186890] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.187476] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.188039] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.188754] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.189326] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.190038] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 *10 11 14 15)
[    0.190615] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.191188] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[    0.191788] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.192202] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.192613] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.193034] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.193445] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0, disabled.
[    0.193855] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.194267] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.194679] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.195091] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0, disabled.
[    0.195558] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0, disabled.
[    0.196046] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0, disabled.
[    0.196504] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0, disabled.
[    0.196972] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[    0.197430] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[    0.197889] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[    0.198347] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0, disabled.
[    0.198805] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[    0.199263] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0, disabled.
[    0.199722] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0, disabled.
[    0.200150] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0, disabled.
[    0.200660] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.200660] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.200660] vgaarb: loaded
[    0.200660] vgaarb: bridge control possible 0000:01:00.0
[    0.200740] SCSI subsystem initialized
[    0.200876] libata version 3.00 loaded.
[    0.200876] ACPI: bus type USB registered
[    0.200876] usbcore: registered new interface driver usbfs
[    0.200876] usbcore: registered new interface driver hub
[    0.200876] usbcore: registered new device driver usb
[    0.200876] PCI: Using ACPI for IRQ routing
[    0.209043] PCI: pci_cache_line_size set to 64 bytes
[    0.209116] e820: reserve RAM buffer [mem 0x00096000-0x0009ffff]
[    0.209118] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.209216] NetLabel: Initializing
[    0.209325] NetLabel:  domain hash size = 128
[    0.209439] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.209568] NetLabel:  unlabeled traffic allowed by default
[    0.209713] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.209713] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.209713] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.212040] Switched to clocksource hpet
[    0.218556] AppArmor: AppArmor Filesystem Enabled
[    0.218741] pnp: PnP ACPI init
[    0.218940] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.219067] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.219192] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.219316] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.219440] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.219565] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.219690] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.219800] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.219925] system 00:01: [io  0x0295-0x0314] has been reserved
[    0.220062] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.220187] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.220241] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.220399] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.220865] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.220994] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.221105] system 00:05: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.221234] system 00:05: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.221365] system 00:05: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.221495] system 00:05: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.221625] system 00:05: [mem 0xbfef0000-0xbfefffff] could not be reserved
[    0.221756] system 00:05: [mem 0xffff0000-0xffffffff] has been reserved
[    0.221884] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.222015] system 00:05: [mem 0x00100000-0xbfeeffff] could not be reserved
[    0.222145] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.222276] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.222404] system 00:05: [mem 0xfeff0000] has been reserved
[    0.222528] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.222535] pnp: PnP ACPI: found 6 devices
[    0.231363] pci 0000:01:00.0: BAR 6: assigned [mem 0xdd000000-0xdd01ffff pref]
[    0.231539] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.231659] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.231787] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.231919] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.232113] pci 0000:02:00.0: BAR 6: assigned [mem 0xdfe00000-0xdfe0ffff pref]
[    0.232288] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.232408] pci 0000:00:04.0:   bridge window [io  0x7000-0x8fff]
[    0.232536] pci 0000:00:04.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.232670] pci 0000:00:0f.0: PCI bridge to [bus 03]
[    0.232793] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.232912] pci 0000:00:15.0:   bridge window [io  0x5000-0x6fff]
[    0.233038] pci 0000:00:15.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.233171] pci 0000:00:18.0: PCI bridge to [bus 05]
[    0.233290] pci 0000:00:18.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.233423] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.233425] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.233426] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.233428] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.233430] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.233432] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.233433] pci_bus 0000:01: resource 1 [mem 0xda000000-0xddffffff]
[    0.233435] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.233437] pci_bus 0000:02: resource 0 [io  0x7000-0x8fff]
[    0.233438] pci_bus 0000:02: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.233440] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.233442] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.233444] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.233445] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.233447] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.233449] pci_bus 0000:04: resource 0 [io  0x5000-0x6fff]
[    0.233450] pci_bus 0000:04: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.233452] pci_bus 0000:05: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.233477] NET: Registered protocol family 2
[    0.233804] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.234223] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.234705] TCP: Hash tables configured (established 65536 bind 65536)
[    0.234872] TCP: reno registered
[    0.234988] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.235162] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.235365] NET: Registered protocol family 1
[    0.235812] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    0.304356] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    0.304704] pci 0000:01:00.0: Video device with shadowed ROM
[    0.304708] pci 0000:04:00.0: async suspend disabled to avoid multi-function power-on ordering issue
[    0.304897] pci 0000:04:00.1: async suspend disabled to avoid multi-function power-on ordering issue
[    0.305267] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[    0.305518] PCI: CLS 64 bytes, default 64
[    0.305570] Trying to unpack rootfs image as initramfs...
[    0.681462] Freeing initrd memory: 25784K (ffff880034d94000 - ffff8800366c2000)
[    0.681669] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.681796] software IO TLB [mem 0xbbef0000-0xbfef0000] (64MB) mapped at [ffff8800bbef0000-ffff8800bfeeffff]
[    0.682257] microcode: CPU0 sig=0x1067a, pf=0x10, revision=0xa07
[    0.682397] microcode: CPU1 sig=0x1067a, pf=0x10, revision=0xa07
[    0.682542] microcode: CPU2 sig=0x1067a, pf=0x10, revision=0xa07
[    0.682679] microcode: CPU3 sig=0x1067a, pf=0x10, revision=0xa07
[    0.682878] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.684815] Scanning for low memory corruption every 60 seconds
[    0.685221] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.685362] Initialise system trusted keyring
[    0.685495] audit: initializing netlink subsys (disabled)
[    0.685633] audit: type=2000 audit(1456260374.684:1): initialized
[    0.686162] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.687974] zpool: loaded
[    0.688108] zbud: loaded
[    0.688366] VFS: Disk quotas dquot_6.5.2
[    0.688514] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.689156] fuse init (API version 7.23)
[    0.689409] Key type big_key registered
[    0.690277] Key type asymmetric registered
[    0.690393] Asymmetric key parser 'x509' registered
[    0.690545] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.690788] io scheduler noop registered
[    0.690904] io scheduler deadline registered (default)
[    0.691056] io scheduler cfq registered
[    0.691653] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[    0.692038] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.692177] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.692307] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.692324] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    0.692454] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.692584] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    0.692598] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.692728] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.692856] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.692985] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.692999] pcieport 0000:00:18.0: Signaling PME through PCIe PME interrupt
[    0.693129] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    0.693258] pcie_pme 0000:00:18.0:pcie01: service driver pcie_pme loaded
[    0.693264] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.693400] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.693566] intel_idle: does not run on family 6 model 23
[    0.693637] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.693820] ACPI: Power Button [PWRB]
[    0.693977] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.694154] ACPI: Power Button [PWRF]
[    0.694586] GHES: HEST is not enabled!
[    0.694831] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.696700] Linux agpgart interface v0.103
[    0.698219] brd: module loaded
[    0.699019] loop: module loaded
[    0.699330] libphy: Fixed MDIO Bus: probed
[    0.699445] tun: Universal TUN/TAP device driver, 1.6
[    0.699564] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.699730] PPP generic driver version 2.4.2
[    0.700046] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    0.700170] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 1
[    0.705742] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.705872] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.706048] usb usb1: Product: xHCI Host Controller
[    0.706165] usb usb1: Manufacturer: Linux 3.19.0-51-generic xhci-hcd
[    0.706292] usb usb1: SerialNumber: 0000:05:00.0
[    0.706511] hub 1-0:1.0: USB hub found
[    0.706629] hub 1-0:1.0: 2 ports detected
[    0.706827] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    0.706950] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 2
[    0.709138] usb usb2: We don't know the algorithms for LPM for this host, disabling LPM.
[    0.709335] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.709465] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.709640] usb usb2: Product: xHCI Host Controller
[    0.709758] usb usb2: Manufacturer: Linux 3.19.0-51-generic xhci-hcd
[    0.709884] usb usb2: SerialNumber: 0000:05:00.0
[    0.710096] hub 2-0:1.0: USB hub found
[    0.710215] hub 2-0:1.0: 2 ports detected
[    0.710413] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.710543] ehci-pci: EHCI PCI platform driver
[    0.710779] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    0.710902] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 3
[    0.711083] ehci-pci 0000:00:0b.1: debug port 1
[    0.711220] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    0.711235] ehci-pci 0000:00:0b.1: irq 22, io mem 0xdfffe000
[    0.720028] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.720191] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.720321] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.720496] usb usb3: Product: EHCI Host Controller
[    0.720614] usb usb3: Manufacturer: Linux 3.19.0-51-generic ehci_hcd
[    0.720740] usb usb3: SerialNumber: 0000:00:0b.1
[    0.720955] hub 3-0:1.0: USB hub found
[    0.721071] hub 3-0:1.0: 10 ports detected
[    0.721368] ehci-platform: EHCI generic platform driver
[    0.721496] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.721623] ohci-pci: OHCI PCI platform driver
[    0.721853] ohci-pci 0000:00:0b.0: OHCI PCI host controller
[    0.721978] ohci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 4
[    0.722175] ohci-pci 0000:00:0b.0: irq 23, io mem 0xdffff000
[    0.778045] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.778174] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.778350] usb usb4: Product: OHCI PCI host controller
[    0.778470] usb usb4: Manufacturer: Linux 3.19.0-51-generic ohci_hcd
[    0.778597] usb usb4: SerialNumber: 0000:00:0b.0
[    0.778826] hub 4-0:1.0: USB hub found
[    0.778944] hub 4-0:1.0: 10 ports detected
[    0.779247] ohci-platform: OHCI generic platform driver
[    0.779374] uhci_hcd: USB Universal Host Controller Interface driver
[    0.779544] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.779673] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.780484] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.780700] mousedev: PS/2 mouse device common for all mice
[    0.780954] rtc_cmos 00:02: RTC can wake from S4
[    0.781202] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.781356] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.781540] i2c /dev entries driver
[    0.781709] device-mapper: uevent: version 1.0.3
[    0.781897] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.782092] ledtrig-cpu: registered to indicate activity on CPUs
[    0.782419] PCCT header not found.
[    0.782608] TCP: cubic registered
[    0.782821] NET: Registered protocol family 10
[    0.783146] NET: Registered protocol family 17
[    0.783269] Key type dns_resolver registered
[    0.783679] Loading compiled-in X.509 certificates
[    0.784682] Loaded X.509 cert 'Magrathea: Glacier signing key: ebc2f4d3948f5d880fb401fc4e980ddeef6bdf5c'
[    0.784891] registered taskstats version 1
[    0.786779] Key type trusted registered
[    0.789963] Key type encrypted registered
[    0.790080] AppArmor: AppArmor sha1 policy hashing enabled
[    0.790203] ima: No TPM chip found, activating TPM-bypass!
[    0.790337] evm: HMAC attrs: 0x1
[    0.790866]   Magic number: 4:63:802
[    0.791082] rtc_cmos 00:02: setting system clock to 2016-02-23 20:46:15 UTC (1456260375)
[    0.791370] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.791494] EDD information not available.
[    0.791662] PM: Hibernation image not present or could not be loaded.
[    0.792189] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    0.792368] Write protecting the kernel read-only data: 12288k
[    0.792755] Freeing unused kernel memory: 252K (ffff8800017c1000 - ffff880001800000)
[    0.793095] Freeing unused kernel memory: 336K (ffff880001bac000 - ffff880001c00000)
[    0.803577] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.806093] rr640l: module license 'Proprietary' taints kernel.
[    0.806219] Disabling lock debugging due to kernel taint
[    0.806458] rr640l: module verification failed: signature and/or  required key missing - tainting kernel
[    0.806970] rr640l:RocketRAID 640L/642L/644L/RR644LS SATA controller driver v1.3.11
[    1.136535] usb 2-2: new SuperSpeed USB device number 2 using xhci_hcd
[    1.158180] usb 2-2: New USB device found, idVendor=0bc2, idProduct=3322
[    1.158310] usb 2-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    1.158442] usb 2-2: Product: Expansion Desk
[    1.158556] usb 2-2: Manufacturer: Seagate
[    1.158669] usb 2-2: SerialNumber: NA8ENCK0
[    1.178792] rr640l:adapter at PCI 2:0:0, IRQ 16
[    1.192010] rr640l:[0 0  ] start port.
[    1.192010] rr640l:[0 0  ] start port hard reset (probe 1).
[    1.192010] rr640l:[0 1  ] start port.
[    1.192010] rr640l:[0 1  ] start port hard reset (probe 1).
[    1.680024] tsc: Refined TSC clocksource calibration: 2999.958 MHz
[    1.800039] rr640l:[0 2  ] start port.
[    1.800039] rr640l:[0 2  ] start port hard reset (probe 1).
[    1.800039] rr640l:[0 3  ] start port.
[    1.800039] rr640l:[0 3  ] start port hard reset (probe 1).
[    2.680107] Switched to clocksource tsc
[    4.200005] rr640l:[0 0  ] start port soft reset (probe 1).
[    5.408003] rr640l:[0 1  ] start port soft reset (probe 1).
[    5.412001] rr640l:[0 2  ] start port soft reset (probe 1).
[    5.412001] rr640l:[0 0  ] port started successfully.
[    5.412001] rr640l:[0 0 0] device probed successfully.
[    5.412001] rr640l:Backup stamp 5261775f sum 0 backed 1
[    5.412001] rr640l:Master stamp 5261775f sum 0 backed 1
[    5.412001] rr640l:raw ffff8802326a8438 bad_sector 0
[    5.412001] rr640l:[0 3  ] start port soft reset (probe 1).
[    5.412001] rr640l:[0 1  ] port started successfully.
[    5.412001] rr640l:[0 1 0] device probed successfully.
[    5.412001] rr640l:Backup stamp 5261775f sum 0 backed 1
[    5.412001] rr640l:Master stamp 5261775f sum 0 backed 1
[    5.412001] rr640l:raw ffff8802326a8038 bad_sector 0
[    7.478987] rr640l:[0 2  ] port started successfully.
[    7.479105] rr640l:[0 2 0] device probed successfully.
[    7.480001] rr640l:Backup stamp 5261775f sum 0 backed 1
[    7.480001] rr640l:Master stamp 5261775f sum 0 backed 1
[    7.480001] rr640l:raw ffff8802326a7c38 bad_sector 0
[    7.480001] rr640l:[0 3  ] port started successfully.
[    7.480001] rr640l:[0 3 0] device probed successfully.
[    7.480001] rr640l:Backup stamp 5261775f sum 0 backed 1
[    7.480001] rr640l:Master stamp 5261775f sum 0 backed 1
[    7.480001] rr640l:raw ffff8802326a7838 bad_sector 0
[    7.599993] scsi host0: rr640l
[    7.600234] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HUA72303 MKAO PQ: 0 ANSI: 5
[    7.600483] scsi 0:0:1:0: Direct-Access     ATA      Hitachi HUA72303 MKAO PQ: 0 ANSI: 5
[    7.600728] scsi 0:0:2:0: Direct-Access     ATA      Hitachi HUA72303 MKAO PQ: 0 ANSI: 5
[    7.600970] scsi 0:0:3:0: Direct-Access     ATA      Hitachi HUA72303 MKAO PQ: 0 ANSI: 5
[    7.601950] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.601967] sd 0:0:0:0: [sda] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    7.602012] sd 0:0:0:0: [sda] Write Protect is off
[    7.602014] sd 0:0:0:0: [sda] Mode Sense: 2f 00 00 00
[    7.602030] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.602729] sd 0:0:1:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    7.602945] sd 0:0:1:0: [sdb] Write Protect is off
[    7.602953] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    7.603184] sd 0:0:1:0: [sdb] Mode Sense: 2f 00 00 00
[    7.603200] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.603326] sd 0:0:2:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    7.603342] sd 0:0:2:0: [sdc] Write Protect is off
[    7.603343] sd 0:0:2:0: [sdc] Mode Sense: 2f 00 00 00
[    7.603354] sd 0:0:2:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.603890] sd 0:0:2:0: Attached scsi generic sg2 type 0
[    7.604186] sd 0:0:3:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    7.604211] sd 0:0:3:0: Attached scsi generic sg3 type 0
[    7.604516] sd 0:0:3:0: [sdd] Write Protect is off
[    7.604640] sd 0:0:3:0: [sdd] Mode Sense: 2f 00 00 00
[    7.604651] sd 0:0:3:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.631422]  sdb: sdb1 sdb9
[    7.631759] sd 0:0:1:0: [sdb] Attached SCSI disk
[    7.632309]  sda: sda1 sda9
[    7.632578] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.634160]  sdc: sdc1 sdc9
[    7.634487] sd 0:0:2:0: [sdc] Attached SCSI disk
[    7.636603]  sdd: sdd1 sdd9
[    7.636935] sd 0:0:3:0: [sdd] Attached SCSI disk
[    7.640400] systemd-udevd[132]: starting version 204
[    7.662522] pata_amd 0000:00:0d.0: version 0.4.1
[    7.663329] scsi host1: pata_amd
[    7.663563] scsi host2: pata_amd
[    7.663733] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    7.663864] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    7.664034] ata1: port disabled--ignoring
[    7.664060] ata2: port disabled--ignoring
[    7.664619] sata_nv 0000:00:0e.0: version 3.5
[    7.664823] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    7.664957] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    7.665625] scsi host3: sata_nv
[    7.668723] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    7.669125] scsi host4: sata_nv
[    7.669350] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    7.669484] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    7.669864] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    7.669997] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    7.672661] scsi host5: pata_jmicron
[    7.672703] usbcore: registered new interface driver usb-storage
[    7.674145] scsi host7: pata_jmicron
[    7.674302] ata5: PATA max UDMA/100 cmd 0x6c00 ctl 0x6800 bmdma 0x5c00 irq 16
[    7.674434] ata6: PATA max UDMA/100 cmd 0x6400 ctl 0x6000 bmdma 0x5c08 irq 16
[    7.674591] ahci 0000:04:00.0: version 3.0
[    7.674812] ACPI: PCI Interrupt Link [AXV8] enabled at IRQ 16
[    7.676019] scsi host6: sata_nv
[    7.678261] scsi host9: uas
[    7.678447] usbcore: registered new interface driver uas
[    7.678788] scsi 9:0:0:0: Direct-Access     Seagate  Expansion Desk   9401 PQ: 0 ANSI: 6
[    7.679467] sd 9:0:0:0: Attached scsi generic sg4 type 0
[    7.679704] sd 9:0:0:0: [sde] 9767541167 512-byte logical blocks: (5.00 TB/4.54 TiB)
[    7.679894] sd 9:0:0:0: [sde] 4096-byte physical blocks
[    7.680040] scsi host8: sata_nv
[    7.680217] ata7: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    7.680356] ata8: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    7.680688] sd 9:0:0:0: [sde] Write Protect is off
[    7.680812] sd 9:0:0:0: [sde] Mode Sense: 4f 00 00 00
[    7.680944] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    7.681074] sd 9:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.681274] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    7.681679] xhci_hcd 0000:05:00.0: ERROR Transfer event for disabled endpoint or incorrect stream ring
[    7.681861] scsi host10: sata_nv
[    7.681993] scsi host11: sata_nv
[    7.682052] ata9: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    7.682060] ata10: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    7.682118] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    7.682328] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    7.682747] xhci_hcd 0000:05:00.0: @0000000232eb6460 00000000 00000000 1b000000 01038001
[    7.688031] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    7.688217] ahci 0000:04:00.0: flags: 64bit ncq led clo pmp pio 
[    7.688732] scsi host12: ahci
[    7.688960] scsi host13: ahci
[    7.689118] ata11: SATA max UDMA/133 abar m8192@0xdfdfe000 port 0xdfdfe100 irq 16
[    7.689297] ata12: SATA max UDMA/133 abar m8192@0xdfdfe000 port 0xdfdfe180 irq 16
[    7.991182] random: nonblocking pool is initialized
[    7.992014] ata7: SATA link down (SStatus 0 SControl 300)
[    7.992016] ata9: SATA link down (SStatus 0 SControl 300)
[    7.993993]  sde: sde1 sde2
[    7.994998] sd 9:0:0:0: [sde] Attached SCSI disk
[    8.008023] ata12: SATA link down (SStatus 0 SControl 300)
[    8.008171] ata11: SATA link down (SStatus 0 SControl 300)
[    8.136019] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.160133] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
[    8.192132] ata3.00: configured for UDMA/100
[    8.194094] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[    8.208487] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:04:4b:17:22:9a
[    8.208683] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    8.209101] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    8.210258] sr 3:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.210450] cdrom: Uniform CD-ROM driver Revision: 3.20
[    8.210664] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    8.210729] sr 3:0:0:0: Attached scsi generic sg5 type 5
[    8.676019] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.684303] ata4.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
[    8.684437] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    8.700335] ata4.00: configured for UDMA/133
[    8.700532] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 3B01 PQ: 0 ANSI: 5
[    8.700914] sd 4:0:0:0: [sdf] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    8.700989] sd 4:0:0:0: Attached scsi generic sg6 type 0
[    8.701261] sd 4:0:0:0: [sdf] Write Protect is off
[    8.701388] sd 4:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    8.701410] sd 4:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.726395]  sdf: sdf1 sdf2 < sdf5 >
[    8.726753] sd 4:0:0:0: [sdf] Attached SCSI disk
[    8.732463] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x50ef @ 1, addr 00:04:4b:17:22:9b
[    8.732645] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    9.176011] ata8: SATA link down (SStatus 0 SControl 300)
[    9.488010] ata10: SATA link down (SStatus 0 SControl 300)
[   10.672031] floppy0: no floppy controllers found
[   11.777175] md: linear personality registered for level -1
[   11.779482] md: multipath personality registered for level -4
[   11.781778] md: raid0 personality registered for level 0
[   11.784347] md: raid1 personality registered for level 1
[   11.852021] raid6: sse2x1    4974 MB/s
[   11.920008] raid6: sse2x2    5795 MB/s
[   11.988010] raid6: sse2x4    8778 MB/s
[   11.988041] raid6: using algorithm sse2x4 (8778 MB/s)
[   11.988075] raid6: using ssse3x2 recovery algorithm
[   11.989246] xor: measuring software checksum speed
[   12.028002]    prefetch64-sse: 12549.000 MB/sec
[   12.068001]    generic_sse: 11057.000 MB/sec
[   12.068031] xor: using function: prefetch64-sse (12549.000 MB/sec)
[   12.069118] async_tx: api initialized (async)
[   12.075499] md: raid6 personality registered for level 6
[   12.075536] md: raid5 personality registered for level 5
[   12.075572] md: raid4 personality registered for level 4
[   12.080571] md: raid10 personality registered for level 10
[   17.107491] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[   17.107538] EXT4-fs (dm-0): write access will be enabled during recovery
[   18.407332] EXT4-fs (dm-0): recovery complete
[   18.411950] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   20.049725] init: zpool-import pre-start process (341) terminated with status 1
[   23.096383] systemd-udevd[515]: starting version 204
[   23.829282] lp: driver loaded but no devices found
[   26.032852] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.066096] i2c i2c-0: nForce2 SMBus adapter at 0xf400
[   26.066157] i2c i2c-1: nForce2 SMBus adapter at 0xf000
[   26.866746] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   26.866754] snd_hda_intel 0000:00:0f.1: Disabling MSI
[   27.780015] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   27.780019] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   27.780022] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   27.780024] sound hdaudioC0D0:    mono: mono_out=0x0
[   27.780027] sound hdaudioC0D0:    dig-out=0x11/0x1e
[   27.780029] sound hdaudioC0D0:    inputs:
[   27.780032] sound hdaudioC0D0:      Front Mic=0x19
[   27.780035] sound hdaudioC0D0:      Rear Mic=0x18
[   27.780037] sound hdaudioC0D0:      Line=0x1a
[   27.780039] sound hdaudioC0D0:    dig-in=0x1f
[   28.840029] floppy0: no floppy controllers found
[   29.227528] audit: type=1400 audit(1456260403.932:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=642 comm="apparmor_parser"
[   29.227534] audit: type=1400 audit(1456260403.932:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   29.227538] audit: type=1400 audit(1456260403.932:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[   29.227568] audit: type=1400 audit(1456260403.932:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=643 comm="apparmor_parser"
[   29.227574] audit: type=1400 audit(1456260403.932:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=643 comm="apparmor_parser"
[   29.227578] audit: type=1400 audit(1456260403.932:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=643 comm="apparmor_parser"
[   29.227593] audit: type=1400 audit(1456260403.932:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=641 comm="apparmor_parser"
[   29.227602] audit: type=1400 audit(1456260403.932:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=641 comm="apparmor_parser"
[   29.227607] audit: type=1400 audit(1456260403.932:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=641 comm="apparmor_parser"
[   29.227902] audit: type=1400 audit(1456260403.932:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   29.640450] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input3
[   29.640520] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input4
[   29.640588] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
[   29.640654] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
[   29.640720] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
[   29.640782] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
[   29.640869] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
[   29.640968] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
[   29.985477] forcedeth 0000:00:11.0 eth0: MSI enabled
[   41.114662] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   41.173977] EXT4-fs (sdf1): mounting ext2 file system using the ext4 subsystem
[   41.209336] EXT4-fs (sdf1): mounted filesystem without journal. Opts: (null)
[   41.884854] init: failsafe main process (1066) killed by TERM signal
[   42.738455] audit_printk_skb: 24 callbacks suppressed
[   42.738458] audit: type=1400 audit(1456260417.121:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1245 comm="apparmor_parser"
[   42.738469] audit: type=1400 audit(1456260417.121:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1245 comm="apparmor_parser"
[   42.738474] audit: type=1400 audit(1456260417.121:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1245 comm="apparmor_parser"
[   42.738846] audit: type=1400 audit(1456260417.121:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1245 comm="apparmor_parser"
[   42.738850] audit: type=1400 audit(1456260417.121:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1245 comm="apparmor_parser"
[   42.739035] audit: type=1400 audit(1456260417.121:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1245 comm="apparmor_parser"
[   42.950840] audit: type=1400 audit(1456260417.333:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/libvirtd" pid=1247 comm="apparmor_parser"
[   42.979059] audit: type=1400 audit(1456260417.361:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/libvirt/virt-aa-helper" pid=1246 comm="apparmor_parser"
[   43.051560] audit: type=1400 audit(1456260417.433:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1250 comm="apparmor_parser" [COLOR=#000000][   43.051885] audit: type=1400 audit(1456260417.433:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1248 comm="apparmor_parser"[/COLOR]
```

specifically these lines:

```
[COLOR=#000000][    0.806093] rr640l: module license 'Proprietary' taints kernel.[/COLOR][    0.806219] Disabling lock debugging due to kernel taint
[    0.806458] rr640l: module verification failed: signature and/or  required key missing - tainting kernel [COLOR=#000000][    0.806970] rr640l:RocketRAID 640L/642L/644L/RR644LS SATA controller driver v1.3.11[/COLOR]
```

However, parted shows all four drives so clearly the driver *is* loading. I wonder if that would prevent zfs from loading. But I would think something would tell us that.

dkms seems to play a role. Is there something to check there?  I've found some references to issues:

[http://askubuntu.com/questions/552201/failed-to-load-zfs-module-stack](http://askubuntu.com/questions/552201/failed-to-load-zfs-module-stack)
[https://github.com/zfsonlinux/zfs/issues/3922](https://github.com/zfsonlinux/zfs/issues/3922)
[http://askubuntu.com/questions/615001/zfs-broken-after-upgrading-package-spl](http://askubuntu.com/questions/615001/zfs-broken-after-upgrading-package-spl)

A server operating system that will update itself automatically is doomed to fail. I wish I'd realized it would do that.

---

### Post by darkod on 2016-02-23
Update itself? You are referring to the automatic security updates? They wouldn't break this... And other type of updates are manual, the standard apt-get update, apt-get dist-upgrade process. If you don't do it, it won't run automatically.

But I have to say I do regular dist-upgrade on quite a number of servers and it still hasn't broken anything... So even if you update your system, it doesn't mean it will break.

The zfs thing is still bothering me. Maybe try to comment out the ppa in /etc/apt/sources.list, run apt-get update, and then enable the ppa again and run apt-get update again. Then try installing the ubuntu-zfs again (or reinstalling it).

As for the rr640l module, you say the disks are reported by parted despite those dmesg messages. Did you check if the module is loaded, just to make sure. I agree the disks shouldn't be there if it isn't, but you never know.
```
lsmod | grep rr640
```

---

### Post by kazz2 on 2016-02-23
I'm afraid I drove myself further down the rabbit hole. Remains to be seen as to whether I'm closer to getting out than I was before. The following is what I've done.

So, deciding to try more of a re-install/config from near scratch I executed the following:


```



sudo apt-get remove zbs
sudo apt-get remove dkms
sudo shutdown -r now


do-release-upgrade
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install dkms




Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 libcuda1-304 libdrm-intel1 libdrm-nouveau2
  libdrm-radeon1 libfontenc1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libice6 libllvm3.4 libsm6 libtxc-dxtn-s2tc0 libx11-xcb1 libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-sync1
  libxfont1 libxkbfile1 libxmu6 libxshmfence1 libxt6 libxv1 libxvmc1
  linux-headers-3.19.0-41 linux-headers-3.19.0-41-generic
  linux-headers-3.19.0-49 linux-headers-3.19.0-49-generic
  linux-image-3.19.0-49-generic linux-image-extra-3.19.0-49-generic
  nvidia-libopencl1-304 nvidia-opencl-icd-304 x11-xkb-utils xfonts-base
  xfonts-encodings xfonts-utils xserver-common xserver-xorg-core
Use 'apt-get autoremove' to remove them.
Suggested packages:
  debhelper
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/72.4 kB of archives.
After this operation, 350 kB of additional disk space will be used.
Selecting previously unselected package dkms.
(Reading database ... 152850 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.1+zfs10~trusty) ...


sudo apt-get autoremove
```


And the output from the autoremove is interesting because of this portion:


```
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
dkms.conf: Error! No 'BUILT_MODULE_NAME' directive specified for record #0.
Error! Bad conf file.
File:
does not represent a valid dkms.conf file.



```


I followed that via google to this post:


[http://askubuntu.com/questions/227258/error-could-not-locate-dkms-conf-file?rq=1](http://askubuntu.com/questions/227258/error-could-not-locate-dkms-conf-file?rq=1)


I found an rr64xl directory in the dkms directory and it seemed to me that was a name of a folder from my first, aborted attempt to install the rr640l with some old information. So, I deleted and rebooted. Then I re-issued the sudo apt-get autoremove:


```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-42 linux-headers-3.19.0-42-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 80.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 96650 files and directories currently installed.)
Removing linux-headers-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
Removing linux-headers-3.19.0-42 (3.19.0-42.48~14.04.1) ...



```


Then went to the driver directory and re-issued the sudo make install followed by sudo modprobe rr640l. And a parted print all showed the four drives attached to the adapter. After a reboot I tried your lsmod command and the following was the output:

```
rr640l                249856  0
```

From there:

```
sudo add-apt-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get install ubuntu-zfs

```

This was a very lengthy install:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  spl-dkms zfs-dkms
Suggested packages:
  zfs-auto-snapshot
The following NEW packages will be installed:
  spl-dkms ubuntu-zfs zfs-dkms
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,440 kB of archives.
After this operation, 11.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Selecting previously unselected package spl-dkms.
(Reading database ... 71690 files and directories currently installed.)
Preparing to unpack .../spl-dkms_0.6.5.4-1~trusty_all.deb ...
Unpacking spl-dkms (0.6.5.4-1~trusty) ...
Setting up spl-dkms (0.6.5.4-1~trusty) ...
Loading new spl-0.6.5.4 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-51-generic
Building initial module for 3.19.0-51-generic
Done.


spl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


splat.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


Running the post_install script:


depmod.......


DKMS: install completed.
Selecting previously unselected package zfs-dkms.
(Reading database ... 71975 files and directories currently installed.)
Preparing to unpack .../zfs-dkms_0.6.5.4-1~trusty_amd64.deb ...
Unpacking zfs-dkms (0.6.5.4-1~trusty) ...
Selecting previously unselected package ubuntu-zfs.
Preparing to unpack .../ubuntu-zfs_8~trusty_amd64.deb ...
Unpacking ubuntu-zfs (8~trusty) ...
Setting up zfs-dkms (0.6.5.4-1~trusty) ...
Loading new zfs-0.6.5.4 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-51-generic
Building initial module for 3.19.0-51-generic
Done.


zavl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


zcommon.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


znvpair.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


zpios.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


zunicode.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


zfs.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-51-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up ubuntu-zfs (8~trusty) ...



```

All to no avail as a sudo zpool status told me the zfs module wasn't loaded.

I'll be trying your suggestion involving the ppa next.

Thanks!

---

### Post by kazz2 on 2016-02-23
Well, I used nano in an attempt to edit sources.list where you specified. I tried to find any ppa or z with a ^w. No instance of either was found. That took me back to dkms which took me to the dkms status command and saw it's output:

```
 sudo dkms status
spl, 0.6.5.4, 3.19.0-51-generic, x86_64: installed
zfs, 0.6.5.4, 3.19.0-51-generic, x86_64: installed
```

So something thinks zfs is installed?

---

### Post by darkod on 2016-02-23
Hmmm... A do-release-upgrade is used to upgrade the ubuntu version to the next one. I hope that didn't go through... And the ubuntu-zfs install looks normal. Are there any strange messages in /var/log/syslog when you try using zfs?

---

### Post by kazz2 on 2016-02-23
Well, I was trying to get back to a raw build and figured I need to get to the latest. A -d is required to get a developer version.

---

### Post by darkod on 2016-02-23
I might be wrong thinking the native-zfs ppa would go in sources.list. But it should be in /etc/apt or subfolder. If it's added, it stays there. You will even be able to do updates of the ubuntu-zfs package when they are available.

I think there was a subfolder /etc/apt/sources.d, maybe there...

---

### Post by kazz2 on 2016-02-23
You
are
not
going
to
believe
this.

It's now working. All I did since the [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install ubuntu-zfs[/FONT][/COLOR] was a reboot. Does it take a while after the installation for the module to start working???

---

### Post by darkod on 2016-02-23
> **kazz2 said:**
> Well, I was trying to get back to a raw build and figured I need to get to the latest. A -d is required to get a developer version.

No, no, no, no.... With all the issues you already have, you decided it's a good thing to go to developer version (unreleased)??? That's still unstable man... The 16.04 LTS that hasn't been released yet...

But there is no going back now...

If I new that, I would have told you you don't need the ppa now. zfs is built into 16.04, that's what we told you earlier...

Here is how you install zfs from 15.10 onwards: [https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

They even call the package under a different name.

Try to purge ubuntu-zfs now and get rid of the ppa. Then try to install the one built-into 16.04.

---

### Post by darkod on 2016-02-23
> **kazz2 said:**
> You
are
not
going
to
believe
this.

It's now working. All I did since the [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install ubuntu-zfs[/FONT][/COLOR] was a reboot. Does it take a while after the installation for the module to start working???

Good, but refer to my previous post. You can still keep this package for now... But in 16.04 you had another option too, without the ppa...

I'm not sure if it needs a reboot or not. It might need... That's why it started working after next reboot.

---

### Post by kazz2 on 2016-02-23
No, I'm sorry, somehow I'm not being clear. the -d parameter on that command installs the latest development version. The command I issued did not have a -d. And, when I ran it, it claimed I was already on the latest version.

---

### Post by darkod on 2016-02-23
Few... I thought you did it... :) So great, the do-release-upgrade didn't do anything... So you still has 14.04 and not ubuntu-zfs is working... Yes?

Did you try the zpool import yet?

---

### Post by kazz2 on 2016-02-23
That's the odd thing. Array is up, shares mounted just like nothing ever happened.

Now, I didn't check the shares first thing this AM. I just knew the backup was complete and I needed to get the side panel on. So I shut her down, put on the panel, and started her back up. That's what started all the drama today. So what bugs me most is why did it happen. But being a noob I'm not sure I can describe things and ask questions with all the right terms, etc. as I don't understand them all yet. But I do need to know what happened and how to avoid it.

First, I installed Ubuntu a number of weeks ago and went through all I went through to get the array working, etc. Today's the first time I've done a do-release-upgrade. So how else could I have compromised my build with the 3rd party adapter and zfs over the past few days since the backup? You mentioned sudo apt-get update as potentially creating a problem, yes? As well as sudo apt-get upgrade? Those are things to avoid when making server changes as it risks currently installed non-distribution software and drivers?

Thanks!

---

### Post by darkod on 2016-02-23
Now, here is where it becomes interesting, and confusing... :) Canonical really could have done a better job organizing the naming of the commands...

apt-get update -> it actually only updates the database of apt to know which is the latest version of the packages available in the repositories. It does not update anything else, you can run it as many times as you want. Before you want to update packages you better run it to get the latest version.

apt-get dist-upgrade (similar effect as apt-get upgrade) -> this is the command that updates all packages to their latest version, if there is a newer available. It does not upgrade the ubuntu version to another release, only the packages within the same release.

do-release-upgrade -> this is the one that is upgrading ubuntu if there is a newer version. For LTS servers that usually means LTS to next LTS. But only after the first point release is out for the new server version. For example, 16.04 comes out in April but 16.04.1 comes out approx in August and then you will start seeing a message on your server that there is a newer version available if you want to run do-release-upgrade. That is your choice, it will never run automatically. Only manually, so you have full control.

Now, in your situation I think you need to be careful with the rr640 module if you decide to run dist-upgrade. You can choose never to run it, but that means as time goes by the packages will not receive the latest patches, etc. Which is still not a big deal... I do run dist-upgrade regularly on servers, but on the other hand I don't have modules compiled manually... I do like when packages are up to date, but if you see more risk with the rr640 module, don't do the updates and that's it... :)

---

### Post by kazz2 on 2016-02-23
I can handle canonical weirdness once I understand it exists!

So how did my system get borked? For some reason the rr640l module no longer loaded. Could it have been from installing some other package? What about an apt-get upgrade?

Also, if the automatic security updates aren't going to create issues with 3rd party drivers like the SATA adapter I'll be happy. What you're saying is that the only way I can create issues for myself is if I do it myself.

Once stable (which I thought I was until I shut her down this morning and restarted her), I'll get a Clonezilla Live backup of the entire boot disk to an external drive and the only thing that should suffer changes - other than data contents - would be updates of Plex. And those are .deb files. I can't imagine it would do anything so invasive as to affect the adapter.

---

### Post by lukeiamyourfather on 2016-02-26
I ditched my HighPoint card for one of these because HighPoint support for Linux is awful.

[http://www.supermicro.com/products/accessories/addon/AOC-SAS2LP-MV8.cfm](http://www.supermicro.com/products/accessories/addon/AOC-SAS2LP-MV8.cfm)

It was around $100 and it's supported out of the box on Linux. It's perfect for a low cost ZFS build.

---

### Post by kazz2 on 2016-02-26
Noted for the future, thanks!

---

### Post by kazz2 on 2016-02-27
So, this morning when I log in I'm greeted with the message *** system restart required ***.

I learned to check /var/run/reboot-required.pkgs to see why. The contents of that file are:

```

libssl1.0.0
linux-image-3.19.0-51-generic
linux-base
linux-base

```

So, my question is, will this recompile the kernel and require me to re-install the driver for the rr640l?

Thanks.

---

### Post by darkod on 2016-02-27
Whether it will need a reinstall of the driver I don't know. That's a new kernel, and when I was trying ubuntu-zfs I could see it rebuilding the module upon new kernel installation, not on the next reboot. You have only security updates installed automatically right? In such case this new kernel was installed when you did apt-get dist-upgrade or apt-get upgrade. I you were looking at the lines going by while doing it, you should have seen the zfs module being rebuild.

As for your rr640l module, I don't know. It might have shown something too. And you said earlier you didn't need to rebuild it after each kernel update, so it might not be needed...

---

### Post by kazz2 on 2016-02-27
I'm sorry, but this is all very confusing. I *thought* I told it security-only when I did the install. I was told that wouldn't create kernel updates. I've rebooted since all the updating/upgrading mess.

How can I tell what updates I'm set for and how can I change that?

I guess I'll just have to reboot and see the results.

---

### Post by MAFoElffen on 2016-02-27
Once you had it worked out and tested...Did you use dkms to auto-install the module on a kernel update?

If not, then then this (although for a network category kernel module) should give you hints at that:
[http://idolinux.blogspot.com/2011/10/auto-update-kernel-modules-with-dkms.html](http://idolinux.blogspot.com/2011/10/auto-update-kernel-modules-with-dkms.html)

Hint: dkms.conf

Embrace updates as a way of life... but config for their eventuality.

---

### Post by darkod on 2016-02-27
This is older but it should help you: [http://askubuntu.com/questions/172524/how-can-i-check-if-automatic-updates-are-enabled](http://askubuntu.com/questions/172524/how-can-i-check-if-automatic-updates-are-enabled)

Usually the dpkg-reconfigure is the way to go to change settings already set on packages. You shouldn't need to go into editing files manually, but it has a bit info about that too.

---

### Post by MAFoElffen on 2016-02-27
@Darkod-- But unattended-upgrades is used for selecting what you will allow and not allow on an upgrade. right? He currently is trying to prevent a kernel upgrade, which that would... Where he thinks that he should have to install the kernel manually, to ensure that his module "gets" installed with the new kernel.

Whereas configuring dkms to point to where his source for his module is, and where his module should be located (end up)... and on new kernel update, would recompile his source and install that module with his new (updated) kernel. Right? That is what I do with Graphics Layer modules...

Having done that manually over the course of the last few weeks, he already has all the information to configure that successfully as an automatic install through dkms... Then he doesn't have to worry about that again. Right?

Or am I missing something that you see, where that would be a problem?

---

### Post by darkod on 2016-02-27
No, I'm not saying not to check into whether the module is rebuilt on kernel update. That should definitely be checked and set up to rebuild the module if possible.

I was just answering the direct question how to reconfigure the automatic updates level (all or security only), to make sure only the updates you want are done automatically without asking you first.

---

### Post by MAFoElffen on 2016-02-27
LOL, okay... You "both" are doing great on this... I've been following with interest.

---

### Post by CharlesA on 2016-02-27
> **lukeiamyourfather said:**
> I ditched my HighPoint card for one of these because HighPoint support for Linux is awful.

[http://www.supermicro.com/products/accessories/addon/AOC-SAS2LP-MV8.cfm](http://www.supermicro.com/products/accessories/addon/AOC-SAS2LP-MV8.cfm)

It was around $100 and it's supported out of the box on Linux. It's perfect for a low cost ZFS build.

Off topic here, but that was my experience with Highpoint cards too, but that might be because I was using a cheap card.

I also advice caution when building modules for the card the OP has via DKMS as I had a nasty problem with that when I used HPT cards, so word of warning.

Always test DKMS and before you have booted into a new kernel is a good time to do so.

---

### Post by kazz2 on 2016-02-27
FWIW, I rebooted and the zpool'd drives look just fine. I appreciate and am taking note of all the great input here but now have a few more questions:

Is there a log for what happened during this "update" at reboot?

And, what logs are worth checking a) after any reboot, b) on any periodic basis over extended uptime periods?

Thanks!

---

### Post by kazz2 on 2016-02-27
Apparently just security updates but checked daily.

```
/etc/apt/apt.conf.d$ cat 10periodic
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";



/etc/apt/apt.conf.d$ cat 20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";



/etc/apt/apt.conf.d$ cat 50unattended-upgrades
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};


// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};


// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";


// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";


// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";


// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";


// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";


// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";


// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade
//Unattended-Upgrade::Automatic-Reboot "false";


// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";


// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";

```

---

### Post by CharlesA on 2016-02-27
> **kazz2 said:**
> FWIW, I rebooted and the zpool'd drives look just fine. I appreciate and am taking note of all the great input here but now have a few more questions:

Is there a log for what happened during this "update" at reboot?

And, what logs are worth checking a) after any reboot, b) on any periodic basis over extended uptime periods?

Thanks!

Logs are here:

```
/var/log/unattended-upgrades/
```

---

### Post by kazz2 on 2016-02-28
Thanks. Looks like a bunch of near-gibberish to me about dpkg, linux-headers, postinst.d, initrd, etc. I'll consider them just "security" updates, I suppose.

---

### Post by lukeiamyourfather on 2016-02-29
Security updates can include the kernel in some cases so if you plan on using one off manually compiled drivers from source code (like HighPoint) I'd disable automatic updates completely and watch out for any kernel updates when you manually run updates because you'll have to recompile the driver after any kernel updates. DKMS is one way to automate this process so when the kernel changes it'll recompile the driver for you but it will require configuration and maybe some troubleshooting. YMMV but spending $100 on a properly supported SAS HBA (like the one I linked to) was worth ten times that price in peace of mind and free-time to spend on other things that make me happy versus frustrated and exhausted. HighPoint just doesn't get it when it comes to supporting Linux and as a result they've lost my business and the business of many other folks like me.

---

### Post by kazz2 on 2016-02-29
Thanks. I understand and agree. The whole point of this project was to use this motherboard. Since the SATA2 ports won't work in a zpool and the mfr will replace it under its lifetime warranty, the right move would be to stop the project immediately, get the replacement motherboard, and start over. Cheaper than a $100 SATA adapter and moves the tech of the motherboard up from 2005. LOL

And, that reminds me, I still have the RMA to replace the DOA Highpoint USB3 adapter to follow-up on.

---

