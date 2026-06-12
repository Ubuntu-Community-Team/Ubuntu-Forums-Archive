---
title: "Can virtualization help me with my home server?"
date: 2009-01-20
forum: Virtualisation
---

### Post by samosamo on 2009-01-20
I was thinking it's probably not a good idea to run my 5+ services on one machine.  It's not performance I am concerned about.  It is stability.  I am the only user, but if I mess up the file system on accident all 10+ services go down.

I am also interested in learning about virtualization. It seems to be getting popular.

So that brings me here.  Would implementing virtualization be helpful to me on my headless home server?  There would be one each for FTP, WWW, file server, squid, openvpn, etc services, and maybe more in the future.

[LIST]
[*]Each virtual OS would probably be ubuntu server, but what would be the base OS?
[*]Is there an OS designed to handle this possibly with a web GUI?  Commandline is fine too. Freeware or commercial?  Freeware preferred.
[*]In regards to the base system, there is a RAID1 disk for OS and RAID5 disk for data.  Would the virtual OS's be able to share the RAID5 for data?  Or would they have to mount via NFS?
[*]Would I be able to assign different IPs to each virtual OS?
[*]Would a Core2Duo with 4GB ram be able to handle this task?
[*]Are there any limitations to running OS's virtually?
[/LIST]

---

### Post by dmizer on 2009-01-21
> **samosamo said:**
> I was thinking it's probably not a good idea to run my 5+ services on one machine.  It's not performance I am concerned about.  It is stability.  I am the only user, but if I mess up the file system on accident all 10+ services go down.

I am also interested in learning about virtualization. It seems to be getting popular.

So that brings me here.  Would implementing virtualization be helpful to me on my headless home server?  There would be one each for FTP, WWW, file server, squid, openvpn, etc services, and maybe more in the future.

[LIST]
[*]Each virtual OS would probably be ubuntu server, but what would be the base OS?
[*]Is there an OS designed to handle this possibly with a web GUI?  Commandline is fine too. Freeware or commercial?  Freeware preferred.
[*]In regards to the base system, there is a RAID1 disk for OS and RAID5 disk for data.  Would the virtual OS's be able to share the RAID5 for data?  Or would they have to mount via NFS?
[*]Would I be able to assign different IPs to each virtual OS?
[*]Would a Core2Duo with 4GB ram be able to handle this task?
[*]Are there any limitations to running OS's virtually?
[/LIST]
Answers (and advice) in no particular order:

Guest limitations are high end graphics and sound. This means that, while you can comfortably use a Windows or a full install of Ubuntu as a guest, you won't be able to game, and 3d effects are not supported. As for server specific functions, I've not run into anything yet.

Yes, you will be able to assign both different IPs as well as different subnets if that is desirable.

I built a core2duo box specifically for this purpose. It has 4 gig of ram, and I have had up to 7 virtual machines running at the same time with zero slowdown.

I did this primarily for security reasons. The more services you have open to the world, the easier it is to compromise, so my theory was to isolate everything, that way if FTP is compromised, your WWW is still safe.

I run vmware-server in ubuntu 8.04 64bit server edition (no GUI install). I use Hardy rather than Ibex for two reasons. First, because Hardy is LTS which means I get 5 years of security updates (Ibex is only a year? and then you have to distribution-upgrade) and second, because Vmware works well in Hardy. I installed vmware-server-client on one of my laptops and I can manage the entire virtual environment remotely without ever touching the host's command line. Everything else I do via SSH.

I wouldn't bother with raid. Most raid controllers (unless you spend $100s of dollars) are pretty worthless, and software raid is only as good as the person maintaining it. Software raid can also bork on kernel updates.

If you keep your host system on a dedicated disk, you can recover from anything from drive failure to hacking in a matter of minutes. Simply [image the host os](http://ubuntuforums.org/showthread.php?t=581680) after you have everything configured and off you go. Keep your virutal machines on a separate disk and use [chron and rsync](http://ubuntuforums.org/showthread.php?t=639979) to make automated incremental backups of your virtual machines.

Look into [ext4](http://en.wikipedia.org/wiki/Ext4) as a file system as it handles large file sizes better than ext3. It was given stable status recently, and I understand it's not difficult to install support into Hardy (8.04). I haven't personally implemented it yet, but I will be soon.

---

### Post by Ein2015 on 2009-01-21
I opened a [similar thread]("http://ubuntuforums.org/showthread.php?t=1045741") on this subject.

From the recommendations there, I would suggest looking into [ESXi]("http://en.wikipedia.org/wiki/ESXi").

I too am building a home virtualization server so I can run services in different VMs as well as make them movable between boxes, should I ever need to do that.  :)

---

### Post by samosamo on 2009-01-21
Everything here is good news except for the independent OS per disk.  That would be extremely inefficient. It would be very difficult to be able to manage this.  I have 750GB's in RAID5 so I can have one central location of data and of course redundancy.  If I ran one OS per disk, on some I would run out of space, on others I wouldn't use all the space, and if the drive failed I'd be dead.

Is there a way to keep my RAID5 array, and share data in between virtual OS? 

This is just an idea, but as I mentioned in the first post, I could use NFS.  IE: 5 virtual OS's running on my RAID1 array.  And FreeNAS running on the RAID5 array, sharing data via NFS to all the virtual OS's.

---

### Post by samosamo on 2009-01-21
> **Ein2015 said:**
> I opened a [similar thread]("http://ubuntuforums.org/showthread.php?t=1045741") on this subject.

From the recommendations there, I would suggest looking into [ESXi]("http://en.wikipedia.org/wiki/ESXi").

I too am building a home virtualization server so I can run services in different VMs as well as make them movable between boxes, should I ever need to do that.  :)

Our situations are very similar.  I just thought this question would be better suited here.

---

### Post by dmizer on 2009-01-21
> **samosamo said:**
> Everything here is good news except for the independent OS per disk.  That would be extremely inefficient. It would be very difficult to be able to manage this.

No, this is not necessary at all. I was just addressing your concern about raid. I misread, and assumed that you were considering raid rather than had actually implemented it, and I was simply suggesting not using raid at all. Rather than use raid, here is how I created a system with seamless recovery capability:

I have 4 disks.
20 gb = host OS
500 gb = virtual machines
1 tb = shared storage (network share)
1 tb = backups

I also have a second desktop with large storage space for redundant backups. Your virutal machines should run fine on your raid array, but I would still highly suggest using ext4 for your file system instead of ext3.

As for mounting your raid 5 array:  With vmware, you will not be able to mount physical drives located on the host (that I am aware). You must think of your virtual machines as though they were completely independent computers. Here is some more discussion on this: [http://communities.vmware.com/thread/94783?tstart=8505](http://communities.vmware.com/thread/94783?tstart=8505). So to more pointedly address your question, yes ... you would definitely need NFS.

---

### Post by Dedoimedo on 2009-01-22
Hi there,

* Each virtual OS would probably be ubuntu server, but what would be the base OS?

Base OS? Well, if you ask me, I'd go for Ubuntu as well, mostly because of commonality. Although personally, I prefer RedHat / CentOS due to its more classic server nature.

* Is there an OS designed to handle this possibly with a web GUI? Commandline is fine too. Freeware or commercial? Freeware preferred.

Virtualization software (some) comes with GUI. Ease wise, VirtualBox, VMware Server seem like your best choice. Both are free.

* In regards to the base system, there is a RAID1 disk for OS and RAID5 disk for data. Would the virtual OS's be able to share the RAID5 for data? Or would they have to mount via NFS?

I do not recommend sharing physical partitions due to possible data loss. If you must, use a dedicated, non-OS hard disk. Although I'd recommend simply using a dedicated storage virtual machine.

* Would I be able to assign different IPs to each virtual OS?

Yup. VMware handles the network stack better than VB. In this regard, the Server seems like the most sensible option to me.

* Would a Core2Duo with 4GB ram be able to handle this task?

You can boost virtualization performance:
[http://www.dedoimedo.com/computers/virtualization-tips.html](http://www.dedoimedo.com/computers/virtualization-tips.html)

Servers, depending on what they do will need ram and so will the base OS. It seems a little tight to me. Without GUI, you'll be able to manage a few vms simultaneously fine, but I/O will not be the best on just one disk. See tips above.

If you're tight in RAM, then maybe you should look into openVZ.
[http://openvz.org/](http://openvz.org/)

* Are there any limitations to running OS's virtually?

3d and peripherals might not work as expected, including wireless devices, bluetooth, serial, parallel, usb etc, depending what and how the host uses them. But for normal server tasks, you'll be fine.

Personal example:

I'm running 3 CentOSs as virtual machines on a single hard disk, with 512mb ram dedicated to each; one of the CentOS is a multi-purpose servers, others are clients; it works fine. I got a total of 2gb ram on that host, 2 hard disks, vms on the second.

Dedoimedo

---

