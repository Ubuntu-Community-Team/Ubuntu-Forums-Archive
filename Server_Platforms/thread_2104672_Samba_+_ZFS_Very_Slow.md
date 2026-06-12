---
title: "Samba + ZFS Very Slow"
date: 2013-01-13
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-01-13
I have been working with ubuntu very hard for about 2 weeks now. I have a upcycled AMD single core 2gb ram and 4 HDD. 

3 of the drives are a ZFS Stripe making a 2.1TB volume labeled Data
The other drive is just a IDE 30gb I used as the OS drive. 

Anyway when I first got Ubuntu up and running with ZFS and Samba everything seemed to work well. Main use is a NAS/Internet PVR for XBMC. Today while trying to watch a 1080P TV show it would stop randomly. And seeking took forever. 720 and lower not bad but 1080 will not work. So I have been all over google looking for answers. If you search samba, zfs, or both slow I have tried it. Through some testing I made a few conclusions. 

1 transfers between zfs and ubuntu system drive (ext2?) are pretty quick. (No bench-marking I could find)

2 transfers from windows to windows through wireless 10-15Mb/s

3 Transfer from ZFS on ubuntu through samba to wireless "n-300" windows client 2-4Mb/s

4 Transfer from ?ext2? to windows on samba 2-4Mb/s

5 Transfer from ZFS through sftp to windows 2-4Mb/s

6 Windows to ZFS or ?ext2? 2-4Mb/s

So from that I figured it must be networking on ubuntu. 
Desktop has Nvidia on-board 10/100 and realtek 10/100 PCI. 
Tried both, same outcome. Transfers inside the server even between file systems seem pretty fast. I couldn't figure out how to get a speed with the "dd" command. But that would suggest its not a file system problem. and sftp is as slow as samba so I think it leaves networking but on both adapters? The Server and the XBMC host are both on 10/100 running through a 10/100/1000 router with ddwrt. DDWRT stays under .1 load when transferring. This is the first problem that google has not solved for me. (209 tabs open at one point)

Hope someone can help. I am sure there are some logs I can get that would be helpful but I dont know what so let me know and I will get them.

Thanks,
Joe

---

### Post by rubylaser on 2013-01-14
Hello.  You are in a tough situation.  ZFS is an awesome filesystem, but it has some pretty high hardware needs if you want good performance. 2GB of RAM and an old single core AMD aren't going to cut it.  Next, Samba isn't a fast filesharing protocol (it is faster in Solaris or Openindiana because if it's native CIFS implementation, but it would still be slow on your hardware).

I would like to know what your read and write speeds are to the array locally.
```
dd if=/dev/zero of=**/your/array/**testfile.out bs=1M count=10000
sleep 30
dd if=**/your/array/**testfile.out of=/dev/null bs=1M
rm **/your/array/**testfile.out
```

Replace** /your/array **with the path to your array, and please post the results back here.  Also, the overhead of networking + Samba is going to make these numbers even worse.  Can you try an FTP client or NFS to see what your performance looks like?

My final advise is if you just want storage for XBMC, I'd be using [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") on your hardware. It doesn't have the hardware requirements of ZFS, is easy to manage, and you can still run a check on your array to prevent bitrot.

```
snapraid check
```

---

### Post by TheFu on 2013-01-14
Which ZFS are you using?  Kernel module or usermode?  Usermode will be slow - painfully slow.

It is unclear how your disks are connected - all SATA?

It is unclear if you are using wifi or wired ethernet for every transfer. Please avoid all wifi transfers.

If there are any USB2 or slower HDDs involved, those will always have slow throughput.

Be very clear on Mbps and MBps.  Most networks are 100Mbps, so about 10MBps is the top speed available. 

I use Samba between Windows and Linux and routinely see 70+MBps (650-ish Mbps) throughput on the GigE network here - no router involved because an unmanaged GigE switch is the connection. 

There are some tuning parameters for both the ethernet and disk drives that can make a difference, but these are usually not a great idea if the system isn't a pure file server.  Be extremely careful if the buffers become too large - this isn't a good thing always.

Laptop disk controllers are notoriously slow when compared to standard desktop components. My testing shows 7200 rpm disks in both to be 2.5x slower in a laptop than a desktop. You didn't say anything about laptops being used, but I figured that info could be helpful.

[http://www.smallnetbuilder.com/nas/nas-features/30717-intel-atom-vs-via-c7-which-makes-a-faster-cheaper-nas?start=3](http://www.smallnetbuilder.com/nas/nas-features/30717-intel-atom-vs-via-c7-which-makes-a-faster-cheaper-nas?start=3) might be helpful too, though he doesn't use ZFS.

---

### Post by jpaytoncfd on 2013-01-14
> **rubylaser said:**
> Hello.  You are in a tough situation.  ZFS is an awesome filesystem, but it has some pretty high hardware needs if you want good performance. 2GB of RAM and an old single core AMD aren't going to cut it.  Next, Samba isn't a fast filesharing protocol (it is faster in Solaris or Openindiana because if it's native CIFS implementation, but it would still be slow on your hardware).

I would like to know what your read and write speeds are to the array locally.
```
dd if=/dev/zero of=**/your/array/**testfile.out bs=1M count=10000
sleep 30
dd if=**/your/array/**testfile.out of=/dev/null bs=1M
rm **/your/array/**testfile.out
```

Replace** /your/array **with the path to your array, and please post the results back here.  Also, the overhead of networking + Samba is going to make these numbers even worse.  Can you try an FTP client or NFS to see what your performance looks like?

My final advise is if you just want storage for XBMC, I'd be using [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") on your hardware. It doesn't have the hardware requirements of ZFS, is easy to manage, and you can still run a check on your array to prevent bitrot.

```
snapraid check
```

Ran the codes you told me:

```
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 101.003 s, 104 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 100.83 s, 104 MB/s

```

I do like the ZFS but I really am only using it because I moved from FreeNAS. The only raid feature I am really interested in is making 4-6 drives show as one volume. I also like the ability for one drive to fail and not loose the whole dataset. 

TheFU:

ZFS is ubuntu-zfs, I followed this guide, [http://www.servercobra.com/freenas-to-ubuntu-initial-fileserver-setup-with-zfs/](http://www.servercobra.com/freenas-to-ubuntu-initial-fileserver-setup-with-zfs/)

All of the ZFS drives (3) are SATA. The system drive (1) is IDE all of the 5400RPM

The most common transfers are through 100Mb LAN. I am in the process of ordering gbit cards. Any suggestions or brand or chipset?
Also some WIFI backup from laptops. Small ammount of data on 300Mb WLAN-N. The faster the better but not important. 

No USB Drives

Curious about using an unmanaged switch. Although with 2 laptops and the server the load on my router never goes over .2

This serer runs as a file server, runs Sabnzbd-Couchpotato-SickBeard (2.5MB average download speed), Webserver, DLNA Media server (Serviio), and at some point Motion for security. Maybe also a home DNS.

I am working on getting new hardware but power consumption is a consern. We are working on going to solar so I really want to get it under 100w. Currently 110-130w but I need more power. I have a prolient server w/ dual, dual core xenon @ 3.2 only has scsi controler and wont boot from anything else.

---

### Post by TheFu on 2013-01-14
> **jpaytoncfd said:**
> ZFS is ubuntu-zfs, I followed this guide, [http://www.servercobra.com/freenas-to-ubuntu-initial-fileserver-setup-with-zfs/](http://www.servercobra.com/freenas-to-ubuntu-initial-fileserver-setup-with-zfs/)

All of the ZFS drives (3) are SATA. The system drive (1) is IDE all of the 5400RPM

The most common transfers are through 100Mb LAN. I am in the process of ordering gbit cards. Any suggestions or brand or chipset?
Also some WIFI backup from laptops. Small ammount of data on 300Mb WLAN-N. The faster the better but not important. 

No USB Drives

Curious about using an unmanaged switch. Although with 2 laptops and the server the load on my router never goes over .2

This serer runs as a file server, runs Sabnzbd-Couchpotato-SickBeard (2.5MB average download speed), Webserver, DLNA Media server (Serviio), and at some point Motion for security. Maybe also a home DNS.

I am working on getting new hardware but power consumption is a consern. We are working on going to solar so I really want to get it under 100w. Currently 110-130w but I need more power. I have a prolient server w/ dual, dual core xenon @ 3.2 only has scsi controler and wont boot from anything else.

I love the Intel PRO/1000 line of NICs. Newegg usually sells them for $25-ish. They ARE the GigE standard and cheap enough that I don't try to save $6 on an off-brand that might suck.

Being below 100W is easy if there isn't a powerful GPU involved.  I have an AMD E350 for xbmc that uses about 25W - best $100 I've spent.  Of course storage is on the LAN, not local.

I've used GigE switches for years with slower 100base-tx routers. I needed the extra ports and run storage on a different network than everything else.  "Server" hardware, especially old server hardware, sucks power that isn't needed anymore.  A Core i5 will do phenomenal things for less power if you don't need the SERVER class capabilities for hot-swap and direct storage access through a virtual machine.

I run the DNS on the router, myself.

I was pissed to discover that my laptop WiFi-N card was only 75Mbps capable. The onboard NIC is GigE on the same machine. What vendor does that crap?  Dell.  Of course, they "offered" a $20 upgrade to a better wifi-N chip, but without clearly saying why, I didn't bother. Plus we all know that wifi sucks, regardless. Most people don't get anywhere near the theory for wifi bandwidth.  During a 1200 location wifi deployment, I learned the **dirty truth about wifi. **Every powered on device halves the bandwidth. If the connection is marginal, it is worse.  A 300Mbps N connection with 1 device, on average, will push 150Mbps. Add another device and both drop to 75Mbps (assuming both are 300 capable). Whatever the slowest device on the wifi-LAN supports, that will be the new max **before** you start halfing everything. 

I don't have time to read that ZFS link. Usermode or kernel mode is all that matters.

---

### Post by jpaytoncfd on 2013-01-14
> **TheFu said:**
> I love the Intel PRO/1000 line of NICs. Newegg usually sells them for $25-ish. They ARE the GigE standard and cheap enough that I don't try to save $6 on an off-brand that might suck.

Being below 100W is easy if there isn't a powerful GPU involved.  I have an AMD E350 for xbmc that uses about 25W - best $100 I've spent.  Of course storage is on the LAN, not local.

I've used GigE switches for years with slower 100base-tx routers. I needed the extra ports and run storage on a different network than everything else.  "Server" hardware, especially old server hardware, sucks power that isn't needed anymore.  A Core i5 will do phenomenal things for less power if you don't need the SERVER class capabilities for hot-swap and direct storage access through a virtual machine.

I run the DNS on the router, myself.

I was pissed to discover that my laptop WiFi-N card was only 75Mbps capable. The onboard NIC is GigE on the same machine. What vendor does that crap?  Dell.  Of course, they "offered" a $20 upgrade to a better wifi-N chip, but without clearly saying why, I didn't bother. Plus we all know that wifi sucks, regardless. Most people don't get anywhere near the theory for wifi bandwidth.  During a 1200 location wifi deployment, I learned the **dirty truth about wifi. **Every powered on device halves the bandwidth. If the connection is marginal, it is worse.  A 300Mbps N connection with 1 device, on average, will push 150Mbps. Add another device and both drop to 75Mbps (assuming both are 300 capable). Whatever the slowest device on the wifi-LAN supports, that will be the new max **before** you start halfing everything. 

I don't have time to read that ZFS link. Usermode or kernel mode is all that matters.

I'm not sure what you mean by usermode or kernelmode I couldent find any deffination. I think from context I am running in usermode as I have not updated or changed the kernel.

---

### Post by rubylaser on 2013-01-14
If you are using ubuntu-zfs, you are using the kernel module.  The other, older method uses FUSE which is terribly slow. Those are decent read/write speeds on the machine. Have you tried using another transfer protocol other than Samba as a test?

---

### Post by TheFu on 2013-01-14
> **jpaytoncfd said:**
> I'm not sure what you mean by usermode or kernelmode I couldent find any deffination. I think from context I am running in usermode as I have not updated or changed the kernel.

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS) - I was using "usermode" really to mean "not kernel mode."  A better way would have been to say FUSE or kernel?

Your testing returned 100MBps, which is what slower HDDs like yours should produce. I do not think you are using FUSE.  FUSE file systems have a place, but not when performance is a concern.  As an example, I use** sshfs** for convenience from time to time, but it is very slow.

Sorry, I'm at a loss for an answer to the ZFS performance issue.  Here's another thread about ZFS you might find interesting: [http://ubuntuforums.org/showthread.php?t=2061495](http://ubuntuforums.org/showthread.php?t=2061495)  Compression and deduplication have performance impacts, if enabled.

---

### Post by tgalati4 on 2013-01-14
Put your mount in /etc/fstab and rerun your video streaming tests.  Kernel-space are processes that are started and managed by the system--typically at startup.  User-space are those processes initiated by the user in their own account.  Opening up nautilus and "network" places to perform a file transfer is user-space.  Starting a mount using /etc/fstab is kernel-space and tends to be faster.

---

### Post by TheFu on 2013-01-14
> **tgalati4 said:**
> Put your mount in /etc/fstab and rerun your video streaming tests.  Kernel-space are processes that are started and managed by the system--typically at startup.  User-space are those processes initiated by the user in their own account.  Opening up nautilus and "network" places to perform a file transfer is user-space.  Starting a mount using /etc/fstab is kernel-space and tends to be faster.

This doesn't sound correct, if I'm reading it right.

Kernel modules are closer to the hardware, more trusted, and reduce the extra layers involved for moving data around. There are fewer permissions gates.

User-space, or FUSE file systems, run at the same level of the OS as any other end-user process. This means it has more permissions to request to accomplish the same tasks. **A FUSE file system can easily be mounted from the /etc/fstab,** but it will still be slower, sometimes significantly slower than the same file system mounted using a kernel module.

[https://en.wikipedia.org/wiki/Filesystem_in_Userspace](https://en.wikipedia.org/wiki/Filesystem_in_Userspace) explains more.

FUSE has been reworked to significantly improve performance, but it usually does not compare well to kernel module versions of the same file system.  CPU utilization is almost always much, much higher for FUSE.  Nothing shows this like benchmarks - [http://www.phoronix.com/scan.php?page=article&item=zfs_fuse_performance&num=1](http://www.phoronix.com/scan.php?page=article&item=zfs_fuse_performance&num=1)

OTOH, I could be completely wrong.

---

### Post by jpaytoncfd on 2013-01-14
I tried sftp through ssh and got exactly the same speeds as samba. and I have tried transfers from both the ZFS mount and the system drive with both protocols. So it doesn't seem like it is the file system or samba. 

I just traded a TV for a small desktop that I think I am going to put into service as my XBMC host. As long as the video card from my current one fits its going. I will then take the current XBMC host and swap it into service as the NAS. Once I run a new Ethernet drop I will move that into a closet. 

So I am going to start fresh with Ubuntu server on the new hardware and hopefully get away from the ZFS. LVM I am guessing. Unless you guys can suggest something better for 4 drives of different size. I am still trying to wrap my head around the Raid stuff. Like data striping. That seems like a bad idea in my situation because if one drive fails I lose all data in the mount. So what setup would allow one drive to fail and only lose files stored on that disk? I don't want to do any redundancy because this is just storing movies and TV shows they can be recovered easily. I would rather have the space than the redundancy. 

Also XBMC is capable of NFS as well would that be better than Samba?

Thanks

---

### Post by tgalati4 on 2013-01-14
The Phoronix article was written in 2010.  I wonder if there have been improvements in zfs performance under linux.  Based on that article, one would not want to use zfs on linux, but stick with ext4 for most workloads.

NFS can be faster than SAMBA, but it depends on how it is mounted and where your network bottlenecks are.

---

### Post by rubylaser on 2013-01-14
NFS is typically faster than CIFS (not true with ZFS because of it's sync() behavior, unless you disable it). But, your main limitation right now with ZFS is older hardware and the fact ZFS on Linux still hasn't been tuned.  You really want to have a minimum of 8GB of RAM with ZFS to get decent performance.

---

### Post by jpaytoncfd on 2013-01-16
Just an update I have gotten my new server set up and a LVM mount formatted ext2. Transfering everything from the old to the new at 10.5MB/s. The new XBMC host has gigabit and I have ordered a card for the new server. hopefully this will speed things up over all. Thanks for your help!

---

### Post by rubylaser on 2013-01-16
Why did you go with LVM with ext2.  I would assume at a minimum, you would have wanted a journaled filesystem.

---

### Post by jpaytoncfd on 2013-01-16
I went with LVM as I want several drives as one storage space. What is a journaled filesystem compared to what I have done?

---

### Post by tgalati4 on 2013-01-16
If you are storing videos and music, ext2 is fine.  Ext3 and ext4 are journaled file systems that store metadata (information about the files) in different locations so in the event of a sudden shutdown, the filesystem has a better chance of recovery.  With static data, you will get better performance with ext2 and you are reading the data more than you are writing the data.

I would assume that an ext2 partition that is mounted through fstab (as a remote share) would give you the fastest transfer speeds through the network.  Everything else adds overhead and thus lower transfer speeds.

---

### Post by TheFu on 2013-01-16
> **rubylaser said:**
> Why did you go with LVM with ext2.  I would assume at a minimum, you would have wanted a journaled filesystem.
**+100**

Not using a journal-ed file system means that fsck checks, which we all should try to do every 60 days or so, will be long-running.  With a journaled file system, corruption due to power issues are minimized AND fscks are much, much quicker.  Ext3 is the minimum these days, thought I do still have some JFS around here.  I can't think of any good reason not to use at least ext3 in either a Linux desktop or server on x86 hardware.

About the only place for ext2 these days would be an unencrypted /boot partition for an encrypted Linux install. I wouldn't use it anywhere else.

**Random comments**:

I'm I the only person who researches file systems at length before deciding which to use?  They all have different pros/cons which need to be weighed carefully for the specific application.

ZFS has many, many fantastic things about it, but they are not without a cost. It is not well used across the Linux world and it isn't GPL, so it doesn't get the same love that other FSes do.  Ext4 is proving to be a great general purpose solution for most users.  A few will want XFS or ZFS instead.  There's no way I'd trust BTRFS yet.  Perhaps in 2-4 more years it will be ready for me.

Use of LVM is a different concern.  When I was new to using LVM, I merged 3 disks into a single file system. When one of those failed, I was not able to access data on any of the 3 disks. It was a bad time. I wasn't doing backups then either.  Within a few months, I'd deployed a RAID5 array AND a backup solution.  That RAID5 array was unchanged until about 4 months ago. I switched to RAID1 with larger HDDs and added some new backup storage on the network.

I'm slow to adopt new file systems and have **backup religion**. Until last summer, I wasn't deploying any ext4.

---

### Post by jpaytoncfd on 2013-01-16
I like your points thefu I chose not to do any backup as the files are not important and can easily be replaced. I can download tv and movies faster than I can watch them so a loss isint a huge deal. However I really would like an option that would allow a single disk to fail and only loose the data on that disk. The other issue is rear/write speed over network. Right now I only have one XBMC host and downloads at 2.5MB/s But I want to add online streaming (Private, just me) and a second and maybe third xbmc host. So I seem to now be maxing the 10/100 hardware in the old server but I want to be sure I can max a 10/100/1000 Is there a way to upgrade to ext4 without destroying the data? (I realize the answer is probley no but dosent hurt to ask.)

I dont mean to be misinformed, I use google to learn and there are so many guides and forum posts that it is hard to keep track of what is current or outdated. I went with LVM because when I searched for using multiple disks as one volume and thats what every port said. This guide I chose used ext2 but it was written in 2012 so I went with it. 

ZFS was only because I was coming from FreeNAS. I really dident like it. Mounting on boot seemed to be hit or miss. 

SO! Before I do anything else,

LVM for merging storage space together
ext 4 as the resulting file system 
SMB for windows clients, NFS for the XBMC host
sftp as a backup. 

Does all that make sense? I looked at fstab, not sure how it makes things faster. Just looks like it would make mounting faster and easier to manage. 

BTW. I appreciate all the help and input. The only forum I have been on that is as helpful as you guys is jeep forum. Glad to see you support the hobby side of things. I posted on another forum the first time I tried to use Ubuntu server and the response I got was "Servers are for professionals only. You should stick with windows desktop and programs like dropbox." And it was a mod who closed the thread. 

thanks,
again

---

### Post by TheFu on 2013-01-16
Can't answer all your issues/questions.  
A few thoughts:
* CIFS is the new version of SMB protocol. **mount -t cifs**
* ext4 is fine. There is a way to migrate from ext2, to ext3, to ext4. **man fs** will help you find those. I'd do a backup and restore to the new fs myself.
* I run XBMX/Linux, not XBMC/Windows and have for a few yrs.
* If you want to share XBMC databases, setup a centralized mysql with that data so that every XBMC machine on the network will share this data.
* XMBC supports having multiple mount points for the different types of media, so if that is the reason you are trying to retain a single file system for multiple disks, I think the added complexity isn't worth the added risk. Someone with more positive LVM experience should chime in.
* I'd keep separate disks on separate mount points. It isn't like you'll have to learn much to do that.
```
/m/tv1
/m/tv2
/m/tv3
/m/movie1
/m/movie2
/m/movie3
/m/music1
/m/music2
/m/music3

```work for me.  It is critical that the mounts appear the same across all XBMC machines.  Splitting this way lets you split your collection (rated G for the kids on one mount) and limit access for the kids and have a different XBMC account/profile for the adults.

For backups, I strongly suggest using a Linux file system (it can appear as whatever Windows needs, but the opposite is NOT true) and **rdiff-backup**. Rdiff-backup will use the ssh channel by default and is very efficient for every backup after the very first.  If sftp works, then rdiff-backup should work too, but it depends on your specific setup.  There are many great backup alternatives under Linux now.  The ones based on **duplicity** are pretty cool too if you are willing to have backup blobs that need a tool to explore.  I completely understand not bothering to backup huge data, but we still need to backup the XMBC settings, DB, OS, plus the non-media files.

Those performance numbers suck. Your dd tests show you should be getting much, much, much better performance regardless of the file system used.  2.5Mbps simple sucks.  I think the worst I've ever seen on spinning disks is 15Mbps for a RAID5 setup, but I see 650Mbps+ for files that aren't bound by disk IO (i.e. they fit inside the cache of the server).  

Google is great to find step-by-step instructions, but not so great for understanding **why**.  For that, the longer guides that aren't fun to read are necessary.  redbooks.ibm.com (developerworks too) is a good place and there is the** Linux Documentation Project** [http://tldp.org/](http://tldp.org/) .  With these, it doesn't matter too much that a specific command has changed. The ideas behind how it works and how to use it are evolutionary and do not change overnight.  Always read the **man page** for the command on your specific system. Howto guides are not always written by a pro - sometimes it is just some guy that found a way to do something and got lucky without any understanding.  

For how-to guides,** HowToForge.com **isn't too bad. They do not explain **why**, so some of the things they do are less-than-secure or just a terrible idea for most people.  Of course, that is my opinion. What do I know?  My knowledge has huge gaps too.

* [http://wiki.tldp.org/LVM-HOWTO](http://wiki.tldp.org/LVM-HOWTO)
* [http://linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html](http://linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html)
* [http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)
Should get you started.

I use LVM when I want snapshots or know that I'll need to grow and shrink file systems on the fly. I keep file systems to a single disk unless there is protected storage of some kind, however.  I've been burned.

For backup storage, I follow the KISS principle. [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle)  Anything too complex will make it diffucult to restore, with little sleep, after a night of drinking, after a 45 minute drive that I didn't want to make. If there is any chance that I could screw up the restore, then my restore process is too complex.  Testing of this method has proven workable, more times than I'd like to admit.  ;)

Ext4 does not have all the great tools when things to badly that ext3 does.  I've needed to use the ext3 tools twice in a decade.  These days, I prefer to trust backups rather than hope that some data searching tool can recover the data I've lost.

NFS is a little faster than CIFS and preferred for Linux-to-Linux sharing. Be certain to lock down the IPs involved and consider noexec and readonly for 100% data-only mounts. If your front-end network is busy, consider making a storage-only network to limit congestion.

I never asked this, but do you have any USB storage connected?  On my main file server, when I connect USB3 storage and have multiple programs accessing it, sometimes the queue gets confused and appears to lock up the entire quad-core machine for about 20-30 seconds, not just those programs involved. THE ENTIRE MACHINE. USB2 seemed to have this same issue on my machines. I've never seen these issues with SATA or IDE storage.  If I limit the user of that USB storage to 1 process, it never locks up.  Initially, I thought it was related to the HDD spinning down, but was able to remove that from the scenario.

I'm still very interested in ZFS and have run it on Solaris a few times. It is probably ready for use on specific Linux distros that include it - [https://www.nexenta.com/](https://www.nexenta.com/) for example. My storage servers are not high power enough to run ZFS on current FreeNAS releases. They are clearly targeting corporate users, not hobbyist.

Using the fstab is only a convenience once the mandatory file systems are mounted.  If you get the settings incorrect, it can suck.  **man fstab** explains each field.  It is probably NOT a good idea to copy the line from the / partition for other storage, but you are the admin of your boxes, not me.  I always want to use it, so I don't forget to mount some storage after a reboot.  Strange things can happen, especially if you forget to mount the backup partition(s) - it is likely the backup job will still run and fill up / partition.  Then when you do mount it, all that storage is used, but you can't see it, because the mount point covers it.  Using the fstab is better.  It has ZERO to do with performance.

Hopefully I didn't pontificate too much to show off all my ignorance at once.

---

### Post by jpaytoncfd on 2013-01-16
> **TheFu said:**
> Can't answer all your issues/questions.  
A few thoughts:
* CIFS is the new version of SMB protocol. **mount -t cifs**
* ext4 is fine. There is a way to migrate from ext2, to ext3, to ext4. **man fs** will help you find those. I'd do a backup and restore to the new fs myself.
* I run XBMX/Linux, not XBMC/Windows and have for a few yrs.
* If you want to share XBMC databases, setup a centralized mysql with that data so that every XBMC machine on the network will share this data.
* XMBC supports having multiple mount points for the different types of media, so if that is the reason you are trying to retain a single file system for multiple disks, I think the added complexity isn't worth the added risk. Someone with more positive LVM experience should chime in.
* I'd keep separate disks on separate mount points. It isn't like you'll have to learn much to do that.
```
/m/tv1
/m/tv2
/m/tv3
/m/movie1
/m/movie2
/m/movie3
/m/music1
/m/music2
/m/music3

```work for me.  It is critical that the mounts appear the same across all XBMC machines.  Splitting this way lets you split your collection (rated G for the kids on one mount) and limit access for the kids and have a different XBMC account/profile for the adults.

For backups, I strongly suggest using a Linux file system (it can appear as whatever Windows needs, but the opposite is NOT true) and **rdiff-backup**. Rdiff-backup will use the ssh channel by default and is very efficient for every backup after the very first.  If sftp works, then rdiff-backup should work too, but it depends on your specific setup.  There are many great backup alternatives under Linux now.  The ones based on **duplicity** are pretty cool too if you are willing to have backup blobs that need a tool to explore.  I completely understand not bothering to backup huge data, but we still need to backup the XMBC settings, DB, OS, plus the non-media files.

Those performance numbers suck. Your dd tests show you should be getting much, much, much better performance regardless of the file system used.  2.5Mbps simple sucks.  I think the worst I've ever seen on spinning disks is 15Mbps for a RAID5 setup, but I see 650Mbps+ for files that aren't bound by disk IO (i.e. they fit inside the cache of the server).  

Google is great to find step-by-step instructions, but not so great for understanding **why**.  For that, the longer guides that aren't fun to read are necessary.  redbooks.ibm.com (developerworks too) is a good place and there is the** Linux Documentation Project** [http://tldp.org/](http://tldp.org/) .  With these, it doesn't matter too much that a specific command has changed. The ideas behind how it works and how to use it are evolutionary and do not change overnight.  Always read the **man page** for the command on your specific system. Howto guides are not always written by a pro - sometimes it is just some guy that found a way to do something and got lucky without any understanding.  

For how-to guides,** HowToForge.com **isn't too bad. They do not explain **why**, so some of the things they do are less-than-secure or just a terrible idea for most people.  Of course, that is my opinion. What do I know?  My knowledge has huge gaps too.

* [http://wiki.tldp.org/LVM-HOWTO](http://wiki.tldp.org/LVM-HOWTO)
* [http://linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html](http://linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html)
* [http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)
Should get you started.

I use LVM when I want snapshots or know that I'll need to grow and shrink file systems on the fly. I keep file systems to a single disk unless there is protected storage of some kind, however.  I've been burned.

For backup storage, I follow the KISS principle. [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle)  Anything too complex will make it diffucult to restore, with little sleep, after a night of drinking, after a 45 minute drive that I didn't want to make. If there is any chance that I could screw up the restore, then my restore process is too complex.  Testing of this method has proven workable, more times than I'd like to admit.  ;)

Ext4 does not have all the great tools when things to badly that ext3 does.  I've needed to use the ext3 tools twice in a decade.  These days, I prefer to trust backups rather than hope that some data searching tool can recover the data I've lost.

NFS is a little faster than CIFS and preferred for Linux-to-Linux sharing. Be certain to lock down the IPs involved and consider noexec and readonly for 100% data-only mounts. If your front-end network is busy, consider making a storage-only network to limit congestion.

I never asked this, but do you have any USB storage connected?  On my main file server, when I connect USB3 storage and have multiple programs accessing it, sometimes the queue gets confused and appears to lock up the entire quad-core machine for about 20-30 seconds, not just those programs involved. THE ENTIRE MACHINE. USB2 seemed to have this same issue on my machines. I've never seen these issues with SATA or IDE storage.  If I limit the user of that USB storage to 1 process, it never locks up.  Initially, I thought it was related to the HDD spinning down, but was able to remove that from the scenario.

I'm still very interested in ZFS and have run it on Solaris a few times. It is probably ready for use on specific Linux distros that include it - [https://www.nexenta.com/](https://www.nexenta.com/) for example. My storage servers are not high power enough to run ZFS on current FreeNAS releases. They are clearly targeting corporate users, not hobbyist.

Using the fstab is only a convenience once the mandatory file systems are mounted.  If you get the settings incorrect, it can suck.  **man fstab** explains each field.  It is probably NOT a good idea to copy the line from the / partition for other storage, but you are the admin of your boxes, not me.  I always want to use it, so I don't forget to mount some storage after a reboot.  Strange things can happen, especially if you forget to mount the backup partition(s) - it is likely the backup job will still run and fill up / partition.  Then when you do mount it, all that storage is used, but you can't see it, because the mount point covers it.  Using the fstab is better.  It has ZERO to do with performance.

Hopefully I didn't pontificate too much to show off all my ignorance at once.

*CIFS good to know. I knida thought it was just the same thing.
*Found out while scrolling through to find the format command again that it is ext3 not ext2. 
*I have tried xbmcbuntu a few times without much luck. I use event ghost to send IR commands from remote presses and system actions as well as serial commands to my TV to turn it on and off. (Samsung EX-Link) 
*Already has the mysql in mind. (Plus I can back that up on my web-hosting. 
*I did consider multiple mount points but SABNZBD, SickBeard, CouchPotato, and Serviio do not support things that way. At least not easily. 
*As far as fail proofing I think I have been explaning myself wrong, Say I hae 3 2TB HDD. If the data is stripped then one drive failure means that every file in the file system is unrecoverable. If you do not stripe and one drive fails, theoretically you would only lose the files stored on that disk. I totally agree with you guys on backups. If I was storing important things on this server I would 100% use a raid setup of some sort. But all my pitures, videos, documents are stored on services like google drive and Photobucket. (Automatically!) So the stuff on the server could be redownloaded at no cost if the system fails (I should say when) Rather than paying for the extra storage space. (and power to run that space). Right now I keep my XBMC backed up on Google Drive. I simply tell google drive to sync the user data folder. Works Great. 
*Currently all my important info is stored in google drive. I mostly just want to save system files and settings on the Server. 
*No USB Storage
*I am using fstab and I did exactly that. Copied 240GB of movies on to the root filesystem. Now I think I need to unmount to delete the data from the root filesystem. 

It looks like I can use vgcfgbackup (Cron job maybe) to be able to recover from a drive failure minus that data on the failed drive. 

I have gotten into the habit of reading the man pages or at least --help when using new commands so I understand them better. The main reason I like going to forums and guides for stuff like this is there a many ways to do things and I like to talk to people with first had experience. 

P.S. Got gigabit in the old server. I have a HP Prolient rack server. I pulled one of the PCI-X Gigabit cards and installed it in a PCI slot and it works. Not sure how well though. I went from 10.5 to 11.5... I wasted more time putting the damn thing in than I saved with the 1MB/s boost... oh well 103 items. Last I checked I was at about 15... Time to wait...

---

### Post by TheFu on 2013-01-16
> **jpaytoncfd said:**
> P.S. Got gigabit in the old server. I have a HP Prolient rack server. I pulled one of the PCI-X Gigabit cards and installed it in a PCI slot and it works. Not sure how well though. I went from 10.5 to 11.5... I wasted more time putting the damn thing in than I saved with the 1MB/s boost... oh well 103 items. Last I checked I was at about 15... Time to wait...

CAT5e or CAT6 cables? CAT5 isn't good enough.

Is your switch or router GigE?  Doesn't do any good to have GigE NICs on a switch that only does 100baseTx.

---

### Post by jpaytoncfd on 2013-01-16
> **TheFu said:**
> CAT5e or CAT6 cables? CAT5 isn't good enough.

Is your switch or router GigE?  Doesn't do any good to have GigE NICs on a switch that only does 100baseTx.

My own stupidity, the new server is only 100baseTx. The router is GigE I have to check the cables. I am pretty sure they are all at least 5e. I am debating on getting a Gigabit pci card for the new server. 

This PCI-X is server grade. and it works.

Another question. IP addresses. Is it better to use the DHCP reservation from the router or manually configure the IP in Ubuntu. or is there much difference. The router seems hit or miss some times when it is rebooted. Some work and some dont.

---

### Post by TheFu on 2013-01-17
> **jpaytoncfd said:**
> Another question. IP addresses. Is it better to use the DHCP reservation from the router or manually configure the IP in Ubuntu. or is there much difference. The router seems hit or miss some times when it is rebooted. Some work and some dont.

I use both, but here's my thought process.
* I prefer static IPs for all my devices
* If a device will move - travel, then it is easier to leave in DHCP mode, so I use dd-wrt for reservations on the home router. I use 7 day reservations and limit real DHCP ranges to no more than what will ever be seen on the network. I'd rather have failures than let 20 unknown devices on the network.
* if a device will never move, I set it with a static IP, so when I swap out routers or there is any network hiccup, then it still has that static IP. Much easier for troubleshooting.
* BTW, guests are placed on their own wired and wifi network and have their own public IP. To my internal system firewalls, those IPs might as well be in China. 3 routers here, thought the guest router isn't powered until guests are expected. I run a few physical servers (many VMs) for small businesses that don't need much bandwidth and aren't willing to spend $300/month just for a server in a cage. I'd rather not have to explain how a house guest hacked their data.

BTW, I stopped using "server class" machines about 5 yrs ago. They sucked too much power compared to desktops (provided there isn't a 700W GPU inside).  3 servers (all desktop class) use under 250W of power total. That includes external arrays too.

I've never had any issues with DHCP reservations except over wifi and at extreme range. Wifi sucks. I once designed and implemented wifi for 1200 locations. I avoid it unless there is ZERO other choice. Too many variables that cannot be controlled by a single human involved.

We probably need to close this thread. It is WAY off topic now.

---

### Post by jpaytoncfd on 2013-01-17
That is what I am doing now. Seems to be working well. I will have to put the killawatt back on once im done I was running 220-250 with 2 computers and surround sound. (plus modem, router, battery backup)I am hoping to see under 150. I stopped having a guest network all together at my home. We still have one for the farm but it requires a password and we require an ID to use it. (Had a neighbor looking up illegal porn that was traced to us. Luckley he had his host name as his full name. lol. 

Thanks for all your help. I marked the thread solved (Dident know I could do that, lol)

---

### Post by ryao on 2013-01-18
> **rubylaser said:**
> NFS is typically faster than CIFS (not true with ZFS because of it's sync() behavior, unless you disable it). But, your main limitation right now with ZFS is older hardware and the fact ZFS on Linux still hasn't been tuned.  You really want to have a minimum of 8GB of RAM with ZFS to get decent performance.

I registered specifically to say that this is incorrect. Unless the original poster is using data deduplication, his hardware should have no problems using ZFS. There are plenty of people using ZFS with 2GB of RAM, which include myself.

I maintain ZFS in Gentoo Linux and so far, I have yet to receive reports of the problems you claim ZFS to have. There was no reason for the original poster to have migrated off ZFS. It had nothing to do with his problem.

Note that I am simplifying the memory situation to avoid a more thorough explanation of ZFS' internals, but, I can give you the following rules of thumb. 512MB of RAM is the practical minimum for a system using ZFS until page cache unification is done. 2GB of RAM is comfortable. This of course assumes that you are not doing data deduplication, in which case, you would ideally want at least 5GB of system RAM for every 1TB of storage. While ZFS does require more processing power than most systems, any 64-bit system manufactured in the past 10 years should have ample processing power to serve as a home fileserver using ZFS. You should only use ZFS on 64-bit hardware until the ARC is unified with the page cache.

---

### Post by rubylaser on 2013-01-18
> **ryao said:**
> I registered specifically to say that this is incorrect. Unless the original poster is using data deduplication, his hardware should have no problems using ZFS. There are plenty of people using ZFS with 2GB of RAM, which include myself.

I maintain ZFS in Gentoo Linux and so far, I have yet to receive reports of the problems you claim ZFS to have. There was no reason for the original poster to have migrated off ZFS. It had nothing to do with his problem.

Note that I am simplifying the memory situation to avoid a more thorough explanation of ZFS' internals, but, I can give you the following rules of thumb. 512MB of RAM is the practical minimum for a system using ZFS until page cache unification is done. 2GB of RAM is comfortable. This of course assumes that you are not doing data deduplication, in which case, you would ideally want at least 5GB of system RAM for every 1TB of storage. While ZFS does require more processing power than most systems, any 64-bit system manufactured in the past 10 years should have ample processing power to serve as a home fileserver using ZFS. You should only use ZFS on 64-bit hardware until the ARC is unified with the page cache.

I didn't say it wouldn't work... I said it would be slow via CIFS (well short of saturating a gigabit connection). I am VERY familiar with both SOHO and enterprise deployments of ZFS, so I didn't just make this up :)

---

### Post by rubylaser on 2013-01-18
jpaytoncfd, another option for you would be SnapRAID.  It's great for home media storage, and runs on very minimal hardware.  I have some setup instructions in my signature.

---

### Post by TheFu on 2013-01-18
> **ryao said:**
> that you are not doing data deduplication, in which case, you would ideally want at least 5GB of system RAM for every 1TB of storage. While ZFS does require more processing power than most systems, any 64-bit system manufactured in the past 10 years should have ample processing power to serve as a home fileserver using ZFS. You should only use ZFS on 64-bit hardware until the ARC is unified with the page cache.

Thanks for bringing this back OT.  I'd read that 1G was the min and 2G sufficient for almost everyone, but since I've never used a pure ZFS file server on Linux, I didn't want to say anything.

Any 64-bit hardware? Are you certain?  For example, would an AMD E-350 be sufficient?  It is a 2 yr old Atom-like APU with x64 instructions.  Ubuntu Unity runs, but not well, IME.  Then again, I've seen Unity bring a Core i7 to its knees.

Some of my home storage sits on VIA C7 CPUs too, obviously NOT x64 capable. ;(

[B]Do you believe an APU-class machine will be good enough for ZFS?
[/B]Heck, I have a spare partition on that box, guess I could try ZFS out and see for myself.

---

### Post by rubylaser on 2013-01-18
> **TheFu said:**
> Thanks for bringing this back OT.  I'd read that 1G was the min and 2G sufficient for almost everyone, but since I've never used a pure ZFS file server on Linux, I didn't want to say anything.

Any 64-bit hardware? Are you certain?  For example, would an AMD E-350 be sufficient?  It is a 2 yr old Atom-like APU with x64 instructions.  Ubuntu Unity runs, but not well, IME.  Then again, I've seen Unity bring a Core i7 to its knees.

Some of my home storage sits on VIA C7 CPUs too, obviously NOT x64 capable. ;(

[B]Do you believe an APU-class machine will be good enough for ZFS?
[/B]Heck, I have a spare partition on that box, guess I could try ZFS out and see for myself.

Any modern 64 bit CPU will work fine (Your Atom processor will work).  If you want performance, you really do need RAM.  2GB of RAM is fine if your goal isn't to saturate gigabit, but with the price of RAM today, why not go to 8GB?  The HP Microserver is a nice, inexpensive home box for ZFS.

---

### Post by tgalati4 on 2013-01-18
I'm running ZFS on 256MB of RAM on a 188 MHz (overclocked) Pentium I whitebox PC using freenas 7.2 with a SATA card and several TB of drives.  Freenas 8.3 needs more horsepower, but you can run ZFS with minimal hardware.

---

### Post by ryao on 2013-01-18
> **rubylaser said:**
> I didn't say it wouldn't work... I said it would be slow via CIFS (well short of saturating a gigabit connection). I am VERY familiar with both SOHO and enterprise deployments of ZFS, so I didn't just make this up :)

It depends on the workload. ZFS ARC could ensure that many operations occur as if the backing storage was a RAM disk. You seem to be suggesting that there is a bad interaction between ZFS and CIFS, but it is not clear to me what that is.

> **TheFu said:**
> Thanks for bringing this back OT.  I'd read that 1G was the min and 2G sufficient for almost everyone, but since I've never used a pure ZFS file server on Linux, I didn't want to say anything.

Any 64-bit hardware? Are you certain?  For example, would an AMD E-350 be sufficient?  It is a 2 yr old Atom-like APU with x64 instructions.  Ubuntu Unity runs, but not well, IME.  Then again, I've seen Unity bring a Core i7 to its knees.

Some of my home storage sits on VIA C7 CPUs too, obviously NOT x64 capable. ;(

[B]Do you believe an APU-class machine will be good enough for ZFS?
[/B]Heck, I have a spare partition on that box, guess I could try ZFS out and see for myself.

People use ZFS on 32-bit hardware, but that requires tuning the vmalloc kernel commandline parameter because of the limited virtual address space. It is not a recommended configuration for that reason and a few others. Other reasons include 32-bit bugs are a low priority for upstream and the limited available registers mean that 64-bit operations often spill onto the stack, which is slow.

Anyway, I have no idea how an APU-class machine would be an exception to what I said. If it is 64-bit and manufactured in the past decade, it will be fine for home use.

> **tgalati4 said:**
> I'm running ZFS on 256MB of RAM on a 188 MHz (overclocked) Pentium I whitebox PC using freenas 7.2 with a SATA card and several TB of drives.  Freenas 8.3 needs more horsepower, but you can run ZFS with minimal hardware.

Wow. I knew that was possible, but I had no idea anyone actually did it. What pool configuration do you have and what is the sequential IO performance?

---

### Post by tgalati4 on 2013-01-18
I'm running a simple mirror pool of 2 1TB drives (RAIDZ1).  I haven't done throughput testing.  I just built it because I had a bunch of PC parts and said "why not?".  I wanted to get some experience with freenas and ZFS.  I maxed out the RAM at 256MB on the board and I added a pci SATA card with some 1TB Hitachi Death Stars and a couple of Seagate spinners.  I want to add an SSD and do some throughput testing.  I couldn't get my gigabit network card to work in it, so I'm only running 100 MBit right now.  If I try a few more gigbit cards and find one that works, then I might do some serious throughput testing.  I can easily saturate the network at 12.5 MBytes/sec (the limit of the 100 MBit/sec card) and I routinely copy 1 GB ISO's across the network via wireless.  And because it runs at 35 watts, I haven't been motivated to buy a real NAS since they run at 24 watts and have a generally crappy OS.

So my main limitation is finding a PCI gigabit network card that freenas can drive properly.  There seems to be a timing issue (100 MHz clock speed needed vs 33 MHz available on the PCI bus).  Some motherboards allow overclocking the PCI bus to 66 or 100 MHz, but I have to investigate it.  I'm overclocking a 166 MHz Pentium to 188.  I had it running at 233 MHz, but I didn't want to push it since it runs 24/7.

Current uptime:  44 day(s) 3 hour(s) 40 minute(s) 39 second(s)

OK, I did a quick test:

From Seagate 500GB 7200 RPM Barracuda PATA drive (EXT2) to 2 Hitachi Deathstars, 7200 RPM SATA in a mirrored ZFS pool (RAIDZ1) 

1 GB DVD ISO copied from PATA drive to ZFS 2-drive pool on PCI SATA card:

freenas:/mnt/Freenas1/ISOs# time ls -la
total 990164
drwxrwxrwx   2 ftp   wheel        4096 Dec 28 14:31 .
drwxrwxrwx  14 root  wheel        4096 Dec 28 14:30 ..
-rwxrw-rw-   1 ftp   wheel  1012924416 Dec 28 10:00 linuxmint-14.1-mate-dvd-32bit.iso
0.014u 0.022s 0:00.03 100.0%	40+928k 0+0io 0pf+0w
freenas:/mnt/Freenas1/ISOs# time cp linuxmint-14.1-mate-dvd-32bit.iso /mnt/Freenas_Mirror
0.174u 95.307s 8:21.66 19.0%	20+1068k 7979+0io 1pf+0w

So that's 1012924416 Bytes in 502 seconds equals 2017779 Bytes/sec or 2.018 MBytes per second.  Not great, but I rarely copy from drive to drive with this NAS.  It's normally from external machines to the NAS.  For that use case, I saturate the network card with wired connections (~10-12MB/sec) and get ~2MB/sec on wireless g.

RAM use was about 60%, CPU was running 80% or so.  

iperf of wireless is:

tgalati4@Dell600m-mint14 ~ $  iperf -c 192.168.1.162 -w 1024k -i 2 -t 20
------------------------------------------------------------
Client connecting to 192.168.1.162, TCP port 5001
TCP window size:  256 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.108 port 59985 connected with 192.168.1.162 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  4.00 MBytes  16.8 Mbits/sec
[  3]  2.0- 4.0 sec  4.12 MBytes  17.3 Mbits/sec
[  3]  4.0- 6.0 sec  3.88 MBytes  16.3 Mbits/sec
[  3]  6.0- 8.0 sec  4.00 MBytes  16.8 Mbits/sec
[  3]  8.0-10.0 sec  4.00 MBytes  16.8 Mbits/sec
[  3] 10.0-12.0 sec  4.12 MBytes  17.3 Mbits/sec
[  3] 12.0-14.0 sec  4.12 MBytes  17.3 Mbits/sec
[  3] 14.0-16.0 sec  4.00 MBytes  16.8 Mbits/sec
[  3] 16.0-18.0 sec  3.12 MBytes  13.1 Mbits/sec
[  3] 18.0-20.0 sec  3.75 MBytes  15.7 Mbits/sec
[  3]  0.0-20.1 sec  39.2 MBytes  16.4 Mbits/sec

And to a 1 GHz Celeron server:

tgalati4@Dell600m-mint14 ~ $ iperf -c 192.168.1.114 -w 1024k -i 2 -t 20
------------------------------------------------------------
Client connecting to 192.168.1.114, TCP port 5001
TCP window size:  256 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.108 port 40344 connected with 192.168.1.114 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  4.88 MBytes  20.4 Mbits/sec
[  3]  2.0- 4.0 sec  4.50 MBytes  18.9 Mbits/sec
[  3]  4.0- 6.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3]  6.0- 8.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3]  8.0-10.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3] 10.0-12.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3] 12.0-14.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3] 14.0-16.0 sec  4.75 MBytes  19.9 Mbits/sec
[  3] 16.0-18.0 sec  4.88 MBytes  20.4 Mbits/sec
[  3] 18.0-20.0 sec  4.88 MBytes  20.4 Mbits/sec
[  3]  0.0-20.1 sec  47.8 MBytes  19.9 Mbits/sec

So you can see the hit taken between 188 MHz server and a 1 GHz server both connected to the same gigabit switch.

Wired network from 1Ghz Celeron Dapper Drake server to 188 MHz Pentium Freenas server

tgalati4@tubuntu2:~$  iperf -c 192.168.1.162 -w 1024k -i 2 -t 20
------------------------------------------------------------
Client connecting to 192.168.1.162, TCP port 5001
TCP window size:   206 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.114 port 58093 connected with 192.168.1.162 port 5001
[  3]  0.0- 2.0 sec  16.5 MBytes  69.0 Mbits/sec
[  3]  2.0- 4.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3]  4.0- 6.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3]  6.0- 8.0 sec  16.4 MBytes  68.8 Mbits/sec
[  3]  8.0-10.0 sec  16.1 MBytes  67.6 Mbits/sec
[  3] 10.0-12.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3] 12.0-14.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3] 14.0-16.0 sec  16.3 MBytes  68.6 Mbits/sec
[  3] 16.0-18.0 sec  16.3 MBytes  68.5 Mbits/sec
[  3]  0.0-20.0 sec    162 MBytes  68.0 Mbits/sec

Run again with the -f M switch (MegaBytes/sec)

tgalati4@tubuntu2:~$  iperf -c 192.168.1.162 -w 1024k -i 2 -t 20 -f M
------------------------------------------------------------
Client connecting to 192.168.1.162, TCP port 5001
TCP window size: 0.20 MByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.114 port 51541 connected with 192.168.1.162 port 5001
[  3]  0.0- 2.0 sec  16.4 MBytes  8.22 MBytes/sec
[  3]  2.0- 4.0 sec  16.4 MBytes  8.18 MBytes/sec
[  3]  4.0- 6.0 sec  16.4 MBytes  8.21 MBytes/sec
[  3]  6.0- 8.0 sec  16.3 MBytes  8.16 MBytes/sec
[  3]  8.0-10.0 sec  16.2 MBytes  8.11 MBytes/sec
[  3] 10.0-12.0 sec  16.3 MBytes  8.14 MBytes/sec
[  3] 12.0-14.0 sec  16.4 MBytes  8.19 MBytes/sec
[  3] 14.0-16.0 sec  16.3 MBytes  8.16 MBytes/sec
[  3] 16.0-18.0 sec  16.3 MBytes  8.17 MBytes/sec
[  3] 18.0-20.0 sec  16.3 MBytes  8.16 MBytes/sec
[  3]  0.0-20.0 sec    163 MBytes  8.17 MBytes/sec


~8.2 MB/sec throughput from one slow server to another via gigabit switch.

My freenas server is OK for home use and it didn't cost anything.  Except for the drives, all of the equipment was curbside.  If I need the performance, I have a couple of rack-based Dell PowerEdge 1750's, but they burn 200 watts each and sound like airplanes taking off.  They have dual gigabit cards, but not bonded, so I should combine them and do some comparisons with hardware RAID and server class hardware, 2x Xeon dual core, 2.8 GHz.

---

### Post by rubylaser on 2013-01-18
> **ryao said:**
> It depends on the workload. ZFS ARC could ensure that many operations occur as if the backing storage was a RAM disk. You seem to be suggesting that there is a bad interaction between ZFS and CIFS, but it is not clear to me what that is.

I'm saying with 2GB of RAM, it will be slow regardless of transfer protocol, CIFS, NFS, AFP.  Like I said, I've been ZFS in commercial and home applications for a long time, I understand very well how the ARC works I don't feel I need to prove myself to you.  If you are happy running on 2GB of RAM, great. 

What I said was 2GB of RAM would provide less than ideal throughput, and is not enough RAM to saturate gigabit...period (not with CIFS, NFS, or AFP) unless you've got an SSD pool, which if you only have 2GB of RAM is just silly.  The OP is only seeing 2-4MB/s on a 10/100 network, so I'm not sure what you are trying to prove.  I love ZFS, and agree it does work on lesser hardware, it's just not very performant (RAM being the easiest way to improve performance).  Since the OP has moved on to ext2, and the thread is marked **[SOLVED]**, I'll be making my exit.  Thanks for taking the time to register, to try to prove your point. 

tgalati4, thanks for providing the benchmarks.  It's amazing that ZFS works on such minimal hardware :) Saturating 10/100 is a feat with that.

---

### Post by ryao on 2013-01-18
> **rubylaser said:**
> I'm saying with 2GB of RAM, it will be slow regardless of transfer protocol, CIFS, NFS, AFP.  Like I said, I've been ZFS in commercial and home applications for a long time, I understand very well how the ARC works I don't feel I need to prove myself to you.  If you are happy running on 2GB of RAM, great. 

What I said was 2GB of RAM would provide less than ideal throughput, and is not enough RAM to saturate gigabit...period (not with CIFS, NFS, or AFP) unless you've got an SSD pool, which if you only have 2GB of RAM is just silly.  The OP is only seeing 2-4MB/s on a 10/100 network, so I'm not sure what you are trying to prove.  I love ZFS, and agree it does work on lesser hardware, it's just not very performant (RAM being the easiest way to improve performance).  Since the OP has moved on to ext2, and the thread is marked **[SOLVED]**, I'll be making my exit.  Thanks for taking the time to register, to try to prove your point. 

tgalati4, thanks for providing the benchmarks.  It's amazing that ZFS works on such minimal hardware :) Saturating 10/100 is a feat with that.

I have written a few dozen patches that have been merged into ZFSOnLinux (bug fixes). If you are using ZFSOnLinux, then you are using code that I wrote. This does not have anything to do with "proving yourself". If there is a bad interaction between ZFS and CIFS, I would like to know about it so that I can add it to my list of things to fix. If not, then please withdraw your statements. Your statements caused the original poster to switch to an inferior storage stack on false premises.

---

### Post by TheFu on 2013-01-19
> **tgalati4 said:**
> I'm running a simple mirror pool of 2 1TB drives (RAID0).

It is probably a typo, but RAID0 is not mirroring. It is spanning - no protection.
RAID1 is mirroring.  [https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels)

Using RAID0 makes sense where performance is much more important than the data.  Scratch disks for temporary files, not for long term storage.  Yes, I've used RAID0 and yes, I've lost data due to a disk failure.

---

### Post by rubylaser on 2013-01-19
> **ryao said:**
> I have written a few dozen patches that have been merged into ZFSOnLinux (bug fixes). If you are using ZFSOnLinux, then you are using code that I wrote. This does not have anything to do with "proving yourself". If there is a bad interaction between ZFS and CIFS, I would like to know about it so that I can add it to my list of things to fix. If not, then please withdraw your statements. Your statements caused the original poster to switch to an inferior storage stack on false premises.

I'm going to try this one more time. The OP's problem was with throughput.  I mentioned that without more RAM this was not likely to happen.  One of my 2 home servers runs on ZFSOnLinux in Ubuntu, but all of my work servers are running either Solaris or Openindiana.  I do find the Linux version of CIFS to be slower than the native, in kernel Solaris/OI implementation, but that's not a knock on ZFS.

The OP switched to an "inferior" storage platform, because ZFS wasn't meeting his needs for streaming to his XBMC box without stuttering.  Even with all the cool data protection features ZFS has, it wasn't fulfilling that original goal.  He now has a working solution and the thread is solved. ZFS can certainly be a solution to XBMC streaming as I have used ZFS to share files with my XBMC boxes for years without a problem, but that was on better hardware with more RAM (OpenSolaris, then OI, and now Ubuntu with ZFSOnLinux).  

This has somehow turned into a debate over ZFS that I wasn't trying to have.  Again, I really ***LOVE*** ZFS and use it daily.  I'm ecstatic it's been ported to Linux, but in this use case, it didn't solve the problem.  If you have some insight, please direct the OP so that it can be made to perform better on his hardware, so that he can have stutter free playback in XBMC and still enjoy the data protection that ZFS has to offer.

Thank for you work with ZFS. I spent some time this morning looking at your Github repos and can see that unlike most people that claim to be code contributors, you actually are.

---

### Post by tgalati4 on 2013-01-19
Correct. I believe I have RAIDZ1 set up, because it has extra functions over simple RAID1. (Correction--there is no such thing as RAIDZ1, it's simply RAID1). I did discover that Freenas 7.2 only has a few gigabit network cards built into the kernel module collection, because it is based on a much older freenas base distribution.  So I need to find an Intel Pro 1000/100 card, because that is known to work well with this older freenas distro.  Freenas 8 (which needs much newer hardware) has better support for gigabit network cards.

I like the features of ZFS, but it requires careful selection of hardware and attention to network topology to realize better performance over SMB/CIFS.  It's certainly not plug-n-play, but it brings some interesting protection features (like detection of silent data corruption) that can be handy for certain use cases.

I just learned that the old freenas 7.2 has been resurrected as [http://www.nas4free.org](http://www.nas4free.org).  So if you have older hardware and you want a slimmed down home server, give it a shot.

---

### Post by jpaytoncfd on 2013-01-20
Just as a scale point, When I had ZFS on freenas throughput speeds were pretty good. (6-7MB/s) Over 100Mb lan. All using samba

ZFS on FreeNas 8.3         (6-7 MB/s)
ZFS on Ubuntu 12.10 server (3 MB/s) 
LVM-EXT3 on Ubuntu 12.10 Server (11.5 MB/s)

   I havent tried the LVM Over the 100% Gigabit but I have streamed 1080P 5.1AAC seamlessly.

---

### Post by TheFu on 2013-01-20
> **jpaytoncfd said:**
> Just as a scale point, When I had ZFS on freenas throughput speeds were pretty good. (6-7MB/s) Over 100Mb lan. All using samba

ZFS on FreeNas 8.3         (6-7 MB/s)
ZFS on Ubuntu 12.10 server (3 MB/s) 
LVM-EXT3 on Ubuntu 12.10 Server (11.5 MB/s)

   I havent tried the LVM Over the 100% Gigabit but I have streamed 1080P 5.1AAC seamlessly.

I don't have access to ZFS systems anymore (were all Solaris), but they did much higher throughput over gigE ... then again, 24G of RAM was our low-end box.

I've had a GigE network at home almost a decade and have tested performance for RAID5, RAID1 over SATA2 (Infiniband connected to srv) and with Black, Blue and Green drives on eSATA, SATA3, USB3 and USB2 (nearly worthless) connections.

Read and read-write speeds can vary tremendously.  
Chipsets and controllers can vary the speeds tremendously.

Laptops (Dell XPS lines) are about 2.5x slower for the same disk hardware.

I do not have SSD disks.

Anyway, some simple data for reading and writing a 7+G file over GigE.
* Writes to Linux software RAID5 (using MD) were less than 8MB/s
* Reads from RAID5 were around 47MB/s
* Writes to an EXT4 SATA internal data drive (not OS), were 41MB/s
* Reads from EXT4 SATA were around 51MB/s

Using **hdparm** test mode, buffered reads from these disks where configured after testing to be about:
* Black - 80MB/s
* RAID5 - 200MB/s
* USB2 - 32MB/s (much slower than all others)

At the time I did these tests, no LVM storage was available. Sorry. The boxes are all fairly cheap and home-built. 

ZFS still intrigues me for the added capabilities and proven use inside enterprises, but I don't have the hardware to throw at it as a storage system.

As you can see, I'm all about facts and data.  "Feeling" something is slow with a reproducible test isn't good enough. Apples-to-apples comparisons are needed to actually see better results and know whether some tuning actually did help or not. Without data, that is never clear.

---

### Post by psypher on 2013-01-21
Hey all. I would like to chime in with my experience in trying to troubleshoot ZFS slow response. I asked a question on askubuntu about this but have not yet had a satisfactory answer:
[http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs/229412](http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs/229412)

My issue is as such. When using either CIFS, SSH or rsync I get continuous fluctuating write speed to the ZFS volume. Between 16mbp/s then dropping to 1mbp/s. From what I have found on the internet I am not alone in this and some of this is by design and I need to tweak ZFS to solve this. Something to do with bursty IO that's often seen with ZFS.

As stated in my askubuntu question I have no idea how to apply these tweaks to the [NATIVE ZFS ON UBUNTU]("https://launchpad.net/~zfs-native/+archive/stable/"). I cannot find anywhere on the internet what the steps are for THIS implementation of ZFS.

Am I on the right track?

Does anyone know how to apply stuff like:
vfs.zfs.prefetch_disable="1"
vfs.zfs.txg.timeout="5"
kern.maxvnodes=250000
vfs.zfs.write_limit_override=1073741824
vfs.zfs.arc_min="512M"
vfs.zfs.arc_max="1536M"
vm.kmem_size_max="8G"
vm.kmem_size="6G"

Which is mentioned in the general tuning section. Other sources say use sysctl. But when I do I get this: sudo sysctl vfs.zfs.prefetch_disable="1" sysctl: cannot stat /proc/sys/vfs/zfs/prefetch_disable: No such file or directory

I cannot find anything for vfs or zfs in /proc/sys.

My hardware should be sufficient, I have 4 GB ram and CPU does not max out when performing writes. It's not my network, this is most definitely ZFS causing the fluctuations, like it's trying to write the cache to the disk and not buffering correctly. As far as I can tell dedup is turned off as well (no idea how to turn on or off just like other options) 

I would prefer to use ZFS for many reasons and I would also like to solve this issue that many are experiencing:
[http://hardforum.com/showthread.php?t=1522895](http://hardforum.com/showthread.php?t=1522895)
[http://forums.nas4free.org/viewtopic.php?f=66&t=1540](http://forums.nas4free.org/viewtopic.php?f=66&t=1540)

Any help would be MUCH appreciated, I have been dealing with this for months. 

Thanks

---

### Post by rubylaser on 2013-01-21
This sounds like ZFS Breathing (Google it).  What is your hardware, NIC card (also, how is your network setup), your pool configuration? Please run these commands and paste the results back.

```
cat /proc/cpuinfo
lspci
zpool status
df -h
```

I would agree that with 4GB of RAM, you should certainly be able to do more that 2MB/s on the high side (your 16mbps converted to MB/s).

---

### Post by psypher on 2013-01-30
> **rubylaser said:**
> This sounds like ZFS Breathing (Google it).  What is your hardware, NIC card (also, how is your network setup), your pool configuration? Please run these commands and paste the results back.

```
cat /proc/cpuinfo
lspci
zpool status
df -h
```

I would agree that with 4GB of RAM, you should certainly be able to do more that 2MB/s on the high side (your 16mbps converted to MB/s).

zfs breathing could be it. Here are the details you wanted. During copies my CPU does fluctuate but there's always spare capacity.

cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II Neo N36L Dual-Core Processor
stepping	: 3
microcode	: 0x10000c8
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 2595.66
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II Neo N36L Dual-Core Processor
stepping	: 3
microcode	: 0x10000c8
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 2595.66
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)


sudo zpool status

  pool: RAID1
 state: ONLINE
 scrub: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	RAID1       ONLINE       0     0     0
	  mirror-0  ONLINE       0     0     0
	    sdb2    ONLINE       0     0     0
	    sdc2    ONLINE       0     0     0

errors: No known data errors

  pool: RAID5
 state: ONLINE
 scrub: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	RAID5       ONLINE       0     0     0
	  raidz1-0  ONLINE       0     0     0
	    sda     ONLINE       0     0     0
	    sdb1    ONLINE       0     0     0
	    sdc1    ONLINE       0     0     0
	    sdd     ONLINE       0     0     0


df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde6        26G   20G  4,5G  82% /
udev            1,9G  4,0K  1,9G   1% /dev
tmpfs           791M  1,2M  790M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,0G  448K  2,0G   1% /run/shm
none            100M   28K  100M   1% /run/user
cgroup          2,0G     0  2,0G   0% /sys/fs/cgroup
RAID5           2,7T  2,7T  3,1G 100% /RAID5

I'm running this on an HP Microserver. How do I get rid of the breathing effect?

---

