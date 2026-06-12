---
title: "Raid1/Grub Boot Problems"
date: 2012-01-24
forum: Server Platforms
---

### Post by Zookee on 2012-01-24
Hi All,

Just started using Ubuntu and I'm a first time poster, so please be gentle :p

We've recently decided to migrate our file and database servers from Windows to Ubuntu and have been playing with a server and setting up raid.  Everything seemed to be going well until we followed the "Test your raid" ([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)) section by unplugging the primary drive.

Instead of getting a degraded boot, grub briefly flashes up and then the machine resets and this cycle continues.  This only occurs if the primary drive is unplugged.  However it seems to boot happily (degraded) if the secondary drive isn't present.

To throw a bit more light on the subject, here's some (possibly relevant) info;

Ubuntu 11.04 32bit.

We have been following this guide:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

We checked grub is installed on both drives by typing:
sudo dd bs=512 count=1 if=/dev/sda 2>/dev/null | strings
sudo dd bs=512 count=1 if=/dev/sdb 2>/dev/null | strings

[COLOR=Gray][I]ZRr=
`|f
\|f1
GRUB
Geom
Hard Disk
Read
 Error
[/I][/COLOR]

Checked each disk to ensure it's bootable with:
sudo fdisk -lu 

[COLOR=Gray][I]Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056b18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   484204543   242101248   fd  Linux RAID autodetect
/dev/sdb2       484206590   488396799     2095105    5  Extended
/dev/sdb5       484206592   488396799     2095104   fd  Linux RAID autodetect

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d22cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484204543   242101248   fd  Linux RAID autodetect
/dev/sda2       484206590   488396799     2095105    5  Extended
/dev/sda5       484206592   488396799     2095104   fd  Linux RAID autodetect

Disk /dev/md1: 2144 MB, 2144325632 bytes
2 heads, 4 sectors/track, 523517 cylinders, total 4188136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 247.9 GB, 247910490112 bytes
2 heads, 4 sectors/track, 60525022 cylinders, total 484200176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
[/I][/COLOR]
I notice that /dev/md0 and /dev/md1 are reported as not having a valid partition table.  Is this something to do with the raid set-up, or have we misconfigured?


Checked the mdstat output with:
cat /proc/mdstat
[I][COLOR=Gray]
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[1] sda1[0]
      242100088 blocks super 1.2 [2/2] [UU]

md1 : active raid1 sdb5[1] sda5[0]
      2094068 blocks super 1.2 [2/2] [UU]

unused devices: <none>[/COLOR][/I]


So I'm thinking it's either something trivial and simple that we've missed due to inexperience or something horrible with our hardware - either way we're scratching our heads at the moment and not really sure why this is happening.

We'd really like to move from Windows to Ubuntu but we need to ensure that our data will be safe and that mirroring works correctly and we can recover it in an emergency.

Any advice, tips or solutions would be most appreciated.  Likewise, if there's any further info required I can grab it.

Many thanks

---

### Post by jsra on 2012-01-24
Hello,
did you try to remove and re-add your 2nd hdd to RAID1? Please remember to backup as this could cause data loss if other hdd could fail.

---

### Post by Zookee on 2012-01-25
I've not tried that, but at this stage I'm willing to give it a go as we'd really like to get it running.

---

### Post by SeijiSensei on 2012-01-25
Most times I'm building a RAID1 array.  For those I'll create a separate boot partition on each disk that sits outside the RAIDed partition.  After installation, I'll copy over the files in /boot to the equivalent partition on the second drive as a backup.

In detail, I run fdisk on each drive, create a 512 MB Linux (type 83) partition for /boot, create a second partition at least as large as physical memory for swap (type 82), then create a third partition encompassing the remainder of the drive and assign it to partition type "fd" (Linux RAID).  After assembling the array with mdadm, I assign the RAID partition to /.

If I have more disks and want to use RAID5, I prefer to keep the OS on one of the disks and use RAID on the remaining ones.  I'll usually divide the RAID disks into two partitions and create two separate arrays, one for /home and one for /var.  Once the system is booted, most read/write operations are concentrated in these directories.  The OS disk gets much less usage in this scenario, so it's not that prone to failure.  Even if it dies, since it only has a copy of the OS, it's easy to replace.

A more flexible solution is to use one partition on the RAID drives, but install [LVM]("http://www.howtoforge.com/linux_lvm") on top of that to create virtual partitions.  That has the advantage of letting you resize the partitions after the fact, but I've found that ability less valuable in practice than it might appear.  With disks as large as they are today, the need to resize isn't as great as it once was.

---

### Post by Zookee on 2012-01-25
> **SeijiSensei said:**
> Most times I'm building a RAID1 array.  For those I'll create a separate boot partition on each disk that sits outside the RAIDed partition.  After installation, I'll copy over the files in /boot to the equivalent partition on the second drive as a backup.


Ok, that makes a lot of sense, I like that idea and will give it a try!  When you say "copy over the files" do you literally just copy everything from one partition to the other from the command line with a cp -r or is the partition cloned exactly?  I'm not 100% sure on the best way to do this.  Would I also need to install GRUB on each boot partition?

> **SeijiSensei said:**
> 
In detail, I run fdisk on each drive, create a 512 MB Linux (type 83) partition for /boot, create a second partition at least as large as physical memory for swap (type 82), then create a third partition encompassing the remainder of the drive and assign it to partition type "fd" (Linux RAID).  After assembling the array with mdadm, I assign the RAID partition to /.


So if I understand correctly you end up with 3 partitions per disk;

1 Boot, 1 Swap, 1 Data.  Only the data partition is mirrored in the raid array.
Each disk can boot independently from it's boot partition and can use it's swap space as and when needed - neither of these being mirrored or in the array?

I think I can probably do this with a bit of time and playing around, but if you have any specific copy-paste examples that would also be a great help until I find my feet and figure it all out.

Thanks

---

### Post by SeijiSensei on 2012-01-25
> **Zookee said:**
> Ok, that makes a lot of sense, I like that idea and will give it a try!  When you say "copy over the files" do you literally just copy everything from one partition to the other from the command line with a cp -r or is the partition cloned exactly?  I'm not 100% sure on the best way to do this.  Would I also need to install GRUB on each boot partition?

I use rsync for most bulk copying tasks like this:

```

sudo mkdir /boot2
sudo mount /dev/sdb1 /boot2
cd /boot
rsync -av . /boot2

```

As for installing grub on the second disk, you could do that, though I never went through the process of figuring out how.  In practice I never encountered a system where the first drive failed.  One other solution to the booting issue is to create a bootable USB pendrive, install grub and /boot on that, then tell the BIOS to boot from the USB drive.  If you're clever enough to dissect the syntax of /boot/grub/grub.conf, you should be able to write two stanzas in that file that would enable you to select which drive to use for the OS when booting from the USB drive.  (See the root= parameter in the kernel statement for examples.)

> So if I understand correctly you end up with 3 partitions per disk; 1 Boot, 1 Swap, 1 Data.  Only the data partition is mirrored in the raid array.
Each disk can boot independently from it's boot partition and can use it's swap space as and when needed - neither of these being mirrored or in the array?

Generally yes, but with these additional features.  First you can actually combine both swap partitions and use them on either OS.  Just add them to /etc/fstab like this:

```

/dev/sda2 swap swap defaults 0 0 
/dev/sdb2 swap swap defaults 0 0

```

following the layout I described.  You can also assign them as swap during the Ubuntu installation rather than editing /etc/fstab manually.

After /boot and swap, I usually assign the remainder of each disk to a single extended partition (/dev/sda3 and /dev/sdb3), then create two logical partitions on each drive that will be RAIDed together for /home and /var.  (Logical partitions are numbered starting with five, so the first logical partition on the primary hard drive is /dev/sda5.)  /var will be holding the databases if you use PostgreSQL or MySQL, along with logs, mail spools, and the like.  You'd have to work hard to make /var exceed 50 GB, but if you have huge databases and large drives you might want to allocate more.  /home will contain all the users' files. I usually also create a user to own any files that will be shared among the users and adjust the privileges in the OS and Samba to control access.

> I think I can probably do this with a bit of time and playing around, but if you have any specific copy-paste examples that would also be a great help until I find my feet and figure it all out.

Here's a general schematic:

1) Create a boot CDROM or USB key with [Ubuntu Server distribution]("http://www.ubuntu.com/download/server/download") you wish to use; boot from that device, then choose the "Rescue Mode" option from the menu.  Just follow the prompts and eventually you'll come to a dialog box asking if you want to run a root shell.  Say yes, and you'll end up at a "BusyBox" shell with root privileges.

2) At the prompt, type "fdisk /dev/sda" to partition the first hard drive.  The "n" command will create a partition; the "t" command will change its type.  Follow the prompts to create two primary partitions and one extended one.  Use the "t" command to set the initial partition to type 83 (Linux), the next partition to type 82 (swap), and the two logical partitions to type "fd" (Linux RAID).  When you're done type "w" to write the partitioning table to the drive then "q" to quit.  Now type "fdisk /dev/sdb" and follow the identical procedure on the second drive.  The "p" command will show the current partitioning table; the "m" command provides help.

3) Now reboot with the CDROM or USB stick and run the installer.  When you get to the disk management part of the process, you'll be able to select each of the partitions.  Tell Ubuntu to put an ext2 filesystem on /dev/sda1 and /dev/sdb1 and mount them as /boot and /boot2.  Then tell it to create a RAID1 array from /dev/sda5 and /dev/sdb5.  Put an ext4 filesystem on it and tell Ubuntu to mount it as /var.  Follow the same procedure and mount it as /home.  (I use ext2 on /boot because its too small to need a journalled filesystem like ext3 or ext4.)

It's less complicated than it sounds!  It may be possible to manage the partitioning via the normal installer, but I prefer to set up the disks in advance.  I've also been known to create one set of partitions, decide I didn't like it, then repartition the drives and install again.  Installation is so quick that I don't mind doing it a couple of times if I'm not happy with the result the first time around.

---

### Post by Monkey Nuts on 2012-07-16
Hi,

I'm exactly the same position (moving away from Windows Home Server 2011, in favour of an Ubuntu Server) and am having exactly the same problem.

I followed the same guide for setting up the RAID partitions and everything works perfectly, until I remove the SATA cable from the primary drive. When this happens, the bootloader screen appears then the PC reboots shortly after. This happens until the primary drive is reattached, then everything works correctly again.

Did you manage to resolve this problem?

---

### Post by Zookee on 2012-07-21
What version of Ubuntu are you using?  I *think* on 12.04 LTS it's working correctly as intended - although I'm not 100% sure.  I played around with other versions on a VM and if I remember correctly this didn't happen in 12.04.

I also tried Debian 6 (on which Ubuntu is based) and that also worked correctly, so my current guess is this is a bug specific to 11.04.

Have a try with 12.04 and see if that helps.  My current 11.04 server is still in that state, so hopefully I won't get any disc failures :p

---

### Post by Monkey Nuts on 2012-07-24
Hey, thanks for the response :)

I've tried again with VMWare Server and get exactly the same problem with 12.04 Server.

The build i'm currently using is 11.04 (as I can get it to work with VMWare Server) but i'd considered changing to 12.04 as i've discovered you can use Virtual Box on 12.04. Not so sure though, now the RAID problem happens on 12.04 too.

Am I just misunderstanding how RAID1 is supposed to work? I can see that it would be relatively easy to recover from a failed primary disk (using an Ubuntu Live CD), even if it doesn't happen automatically.

Perhaps i'll need to settle for that (still preferable to using Windows Home Server!)?

---

### Post by Zookee on 2012-07-25
Hmmm, maybe I also had the issue on 12.04 but as it was a while ago I can't remember for sure. At first I thought it may be hardware but getting the problem on a VM made me think that's not the case as everything is generic and emulated.

I would consider trying it on Debian 6 now, on a vm. The procedure is almost identical and you can find into online. Ubuntu is Debian based anyway. See how you get on.

I find it hard to believe that Ubuntu has shipped since 11.04 with faulty raid (although possible I guess) but whatever I do I couldn't get it working either. 

If some Ubuntu whizz happens across this thread -- please try and recreate and advise because I'm stumped as is the other poster.  One of my machines is running Debian 6 as it needs to auto reboot on failure as its unattended, I'd prefer Ubuntu but reliability needs to come first and I can't get it to work with Ubuntu :(

---

### Post by GabrielSyme on 2012-10-23
Zookee, I'm definitely not an Ubuntu whizz by any stretch, but after beating my head against this problem for hours on end I found a solution in [this thread.]("http://ubuntuforums.org/showpost.php?p=11353696&postcount=12") Hope this helps!

---

