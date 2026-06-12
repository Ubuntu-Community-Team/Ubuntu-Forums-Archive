---
title: "Zfs"
date: 2019-07-24
forum: Ubuntu, Linux and OS Chat
---

### Post by cruzer001 on 2019-07-24
I'm liking the sound of this!  Not ready to jump onboard yet; has anyone else?  I read in another article it can cut down read/write cycles.  A big plus for SSD's if that is indeed true.  What's your thoughts?

[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-ZFS-TODO-List](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-ZFS-TODO-List)

---

### Post by mastablasta on 2019-07-24
but how much difference is (for the average user) between ZFS and BTRFS?

---

### Post by cruzer001 on 2019-07-24
Really don't think this (or BTRFS) will matter to the average user.  Guess it will be an install option on future releases for those going beyond point and click.

---

### Post by lammert-nijhof on 2019-07-24
ZFS is the best modern file system. I use it with Ubuntu 19.04 on a Ryzen 3 2200G with 16 GB DDR4. Three months ago I used it on a 2008 HP dc5850 with an 4-core AMD Phenom II and 8 GB DDR2. 
All my stuff is stored in ZFS datapools and I boot from ZFS. I started using it, because the 1-5 power breaks per day in the Caribbean did corrupt many of my music files on ext4. Ext4 only restores the structures on disk, but it can't rescue the files, that were updated during the crash. With ZFS and BTRFS you are sure that those files will not be corrupted through their Copy On Write mechanism. ZFS is more reliable then BTRFS. ZFS has a far better separation between physical entities and logical storage pools, in BTRFS this can be very confusing. It is already possible to boot from ZFS, but support in the installer has been missing, but now it has been planned for Ubuntu 19.10. 

When you have more disks and one SSD, ZFS is superior because the support for the various Raid configurations has been integrated in ZFS. I use it with Raid 0 with three different disks 1TB, 500GB and a 320GB laptop HDD, ZFS nicely distributes the load based on free space and throughput. On top of that I use half my SSD as boot device and the other half as SSD cache for the three HDDs. On top of the SDD cache I allow ZFS to use max 4 GB as memory cache for the disk IO. I have a 3 layer storage hierarchy like Windows StoreMI; memory (4 GB for the Ryzen and 2 GB in the past for the Phenom), SSD (50 GB) and the three HDDs (1.82 TB). I also compress almost all my data and programs on ZFS, because each file occupies less sectors, so to load a program you only need half the number of HDD or SSD reads. 

I work a lot with virtual machines and my Vbox files are stored on a ZFS datapool with SSD cache and memory cache. After the initial boot or load from often the SSD cache, my VMs run completely from memory cache and I have instantaneous response times in those VMs. Memory cache hit rates are 93%, which means that only 6% of disk IO is divided between the three HDDs.  Another advantage is, that you can use ZFS snapshots to recover from  failed updates and this year I already saved my systems (2) or VMs (16)  twice restoring a snapshot.

It also works perfectly on my i5-2520M laptop with 8 GB and a 1 TB SSHD. The Seagate's Solid State Cache (8 GB) is effectively doubled by the compression and it has twice the effective throughput due to the same compression. If you have a SSHD you need ZFS, to get some pleasure out of it :) :)

If you start with ZFS, just put all your data and VMs in ZFS partitions. Wait with booting from ZFS till October, because it requires a number (10-20) of terminal commands to get it installed and working. If you have a simple disk configuration you could start with BTRFS, that has already support in the installer. BTRFS has good memory caching, but I doubt their support for SSD caching and I don't know whether they decompress before or after the cache. In ZFS the whole chain is kept compressed from HDD over SSD cache over memory cache to the decompressed user program buffer.

---

### Post by cruzer001 on 2019-07-24
Hello lammert-nijhof

Yes this is sounding real good to me.  I will be giving it a test drive in November when testing for 20.04 starts.  Thanks for the input.

---

### Post by mastablasta on 2019-07-25
When i went to install Kubuntu i was advised to use BTRFS. but to me it just seem to many new things and setups and i didn't know if all would work as normal or if there is any additional things i would need to setup on some occasions (links etc). so i went with ext4.

Also i think OpenSUSE is using BTRFS in their install. 

like i said i am not sure how the average system would actually notice the fie system change. when exploring btrfs i saw there are quite a few changes. for example (at leats on surface) Ext4 doesn't look that much different than ntfs. ok there is more permissions options and case sensitivity, but overall and for average user things look pretty much the same.

---

### Post by cruzer001 on 2019-07-25
Hello mastablasta

BTRFS is an option built into the Kubuntu installer?  I haven't used a live installer in quite a while and assume when ZFS is official part of the installer it will be easy to set up.  I do currently use the logical volume manager and happy with it, but when ZFS is added I expect to see some sort of performance boost and a file system better suited for SSDs.  Lammert's post suggest this.  Just couirouis of others opinions at this time.  There are people (like lammert) that have jumped through the hoops and currently running ZFS.

---

### Post by lammert-nijhof on 2019-07-25
BTRFS is supported in the Ubuntu installers. I used it for Xubuntu 18.04 and Peppermint 9 (a distro based on Ubuntu 18.04).  It allows to install the system on one BTRFS partition, but after the install you can create other partitions to complete e.g the Raid-0. You need one terminal commands to balance the load over the Raid-0 disks and one command to compress its content. 

ZFS is not part of the installer yet, but it seems to be planned for the next release of Ubuntu 19.10 in October.

I used BTRFS with Peppermint for a Pentium 4 with two 40 GB IDE disks.   That worked fine and that old potato booted in 45 seconds from the LZO   compressed and striped IDE disks. 
Later I used the Pentium with BTRFS and Xubuntu as back-up server for my main PC. I stopped using it, because I lost a complete directory/sub-volume. Maybe I did something wrong or maybe BTRFS is less robust on 32-bits systems. 

Since the Pentium is 32-bits and  ZFS does not support 32 bits on Linux, I could not use ZFS on Linux. I moved to 32-bit FreeBSD (UNIX), ZFS, the XFCE desktop and the XRDP remote display server. So once per week I backup all my stuff to FreeBSD on the Pentium, which now has 2 other IDE disks, 320 and 250 GB and a second 320GB laptop disk on a SATA-1 connector :) 
FreeBSD requires more manual action to install a working desktop like XFCE, but its installer and boot-manager supports ZFS completely, including Raid configurations and compression. 

I use Samba and rsync for the back-up of normal file sizes and the ZFS send/receive for the huge VDI files of the VMs. ZFS send/receive only backs-up and sends the modified physical records/sectors of the directory/dataset containing those 10-40 GB files. That works also between my two completely different OSes (64-bits Ubuntu/Linux with a 2018 Ryzen and 32-bits FreeBSD/UNIX with a 2003 Pentium 4) :) :)

---

