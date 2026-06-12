---
title: "apt-get upgrade refuses to work"
date: 2012-08-14
forum: Server Platforms
---

### Post by Psycholiquid71 on 2012-08-14
I am trying to update my server and I keep running into a error when running either apt-get update or apt-get upgrade. This is what I see:

sudo apt-get update

Fetched 2,163kB in 6s (348kB/s)
Reading package lists... Done
W: GPG error: [http://php53.dotdeb.org](http://php53.dotdeb.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E9C74FEEA2098A6E

sudo apt-get upgrade 


Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-headers-server: Depends: linux-headers-2.6.32-42-server but it is not installed
  linux-headers-virtual: Depends: linux-headers-2.6.32-42-server but it is not installed or
                                  linux-headers-2.6.32-42-generic-pae but it is not installable


If I run "sudo apt-get -f install" I get the  following:

After this operation, 85.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-42 2.6.32-42.95 [10.2MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-42-server 2.6.32-42.95 [833kB]
Fetched 11.0MB in 31s (344kB/s)
(Reading database ... 156310 files and directories currently installed.)
Unpacking linux-headers-2.6.32-42 (from .../linux-headers-2.6.32-42_2.6.32-42.95_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-42_2.6.32-42.95_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.32-42/arch/mips/include/asm/octeon/cvmx-pexp-defs.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-42/arch/mips/include/asm/octeon/cvmx-pexp-defs.h'): No space left on device
No apport report written because the error message indicates a disk full error

You can imagine the rest of the "disk full errors"

Now I have a 5 gig drive (This is virtual) and this was originally setup with a 3 gig. So I GParted the drive up to 5 gig to try and get some more space. This didn't work. Not I run:

sudo parted -l

Disk /dev/sda: 5369MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   5363MB  5106MB  extended
 5      257MB   3220MB  2963MB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/dcvgasv00102-swap_1: 193MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  193MB  193MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/dcvgasv00102-root: 2768MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2768MB  2768MB  ext4

As you can imagine I see the new space but cant reclaim it. Also when booting up the server I see that the drive is only 85% full. Not sure where to go from here. IF anyone knows I would greatly appreciate it.

---

### Post by spjackson on 2012-08-14
I don't know anything about lvm, but:
a) "Disk full" may result from being out of inodes, not only from being out of disk space. "df -i" will show you the position regarding inodes.
b) On Ubuntu, you can't run resize2fs on a mounted filesystem, so gparted won't resize one either. This is a problem for the / partition. The only way I know to deal with this is to boot from a live CD and resize /. Whether this is relevant in lvm-land, I don't know.

---

### Post by thnewguy on 2012-08-14
It looks like there are several problems at work here. As the poster above mentioned, the "disk full" may be an inode problem, rather than a space problem. Cleaning out lots of small, unneeded file swill help that.

The first error suggests signing keys from repositories are missing. Visiting the website hosting the repository will hopefully lead to a way to download and install their signing keys.

Before doing another "apt-get -f install" I suggest running "apt-get clean" to free up some drive space and make sure the packages you're downloading aren't partial downloads or corrupted.

---

### Post by Psycholiquid71 on 2012-08-14
Ok ran the df -i here is the output from that, it  looks like you were right on that part. 98% is probably not good. How do I clean this part up:


Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/dcvgasv00102-root
                      169008  164676    4332   98% /
none                   61940     633   61307    2% /dev
none                   63154       1   63153    1% /dev/shm
none                   63154      35   63119    1% /var/run
none                   63154       3   63151    1% /var/lock
none                   63154       1   63153    1% /lib/init/rw
/dev/sda1             124496     211  124285    1% /boot



As for apt-get clean

I did that earlier and when checking the archives folder it did clean it out. I will look into the site error now.

Thanks guys for jumping in on this one.

---

### Post by Vegan on 2012-08-14
in my experience, its better to install a new version clean. For this reason I use a few virtual machines so that I can copy files back and forth.

Before when I did distribution upgrades, the machine would fail a month later for no apparent reason.

---

### Post by Psycholiquid71 on 2012-08-14
Resolved, extended the LVM across the empty space , rebooted and now I have space again. Thank you guys though you pushed me in the right direction


Also I got the apt-get update fixed.

---

