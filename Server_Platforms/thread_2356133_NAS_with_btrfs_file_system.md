---
title: "NAS with btrfs file system"
date: 2017-03-20
forum: Server Platforms
---

### Post by umsp on 2017-03-20
I have Ubuntu server with LXD & KVM virtual machines, now I’m going to add NAS . OS installed on SSD drive.
I’m familiar with managing web servers  etc, but this is the first time Samba involved.


 NAS file systems will be btrfs, RAID 1 for now, in the future may change.
 NAS will have media file (photos, music & movie), shared disk (samba and NFS shares)


 I could not decide how should I create file system for NAS.
Should I create large filesystem and then create sub-volumes for each purpose (SMB share, media, backups)? 
Media files  going to access by plex VM, I can export media sub-volume


 Or should I create separate file system for home so each user could  use their home drive as samba share. Media and backup in another file  system.


 Is there advantage mixing SSD  with spinning hard disk in same btrfs file system? 
Is this may help to reduce wakeup spinning disks from power saving mode?


 Hope someone have previous experience to the advantage and disadvantage


 Thank  you,

---

### Post by mastablasta on 2017-03-20
how many users will be accessing the NAS server concurrently?

---

### Post by TheFu on 2017-03-20
A few years ago there was a major issue with mixing KVM and btrfs. Sometimes these issues seem to never get fixed, so be extra certain your plans aren't impacted. Let me see if I can find that link: [http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM) - all the way at the bottom.
> Don't use the linux filesystem btrfs on the host for the image files. It will result in low IO performance. The kvm guest may even freeze when high IO traffic is done on the guest. Again, I think there is a fix, but don't know if it is normal for Ubuntu's version or default settings.

When I design my storage, making backups AND restores as easy as possible overrides day to day convenience. Fortunately, my media server allowed multiple file systems (at least 3 for each media type, but I suspect 50 won't be an issue either) to be logically grouped INSIDE the media center, so I don't have to do that in a file system.

I know that if you use ZFS, then you can mark an SSD as the cache device, so everything will feel faster.

Don't think samba matters at all, except the lower security that comes with it. On a home LAN, that usually isn't a big issue. For samba, I find that different shares for the different types of access are best - rw, ro, and different groups.

With your NFS, be certain to use Kerberos and NFSv4 so the servers and client authenticate to each other.

---

### Post by umsp on 2017-03-21
Hi mastablasta,
Only 2 or 3 at the SAMBA users, only myself using  NFS. Plex will access media. It is pure home server and few plex will be  in one VM.  

Hi TheFu,
I'm not planing to use btrfs for any VM. Most will be on raw disk.

I know btrfs could use SSD as cache as well, but what I want less  spinning disk  awake from power saving mode. SSD as btrfs cache may  help. Just need to find out who had experience or tested.

---

### Post by TheFu on 2017-03-21
Starting and stopping disks is bad for their lifetime.  

I use plex too. No need for Samba at all. It speaks NFS directly. I would not put NAS inside a VM.

I don't worry much about electric bills, since they are already lower than 99% of all my neighbors (according to the power company). I disable the spin-down for all my storage devices and only have 1 SSD (in a netbook). For media, high performance just doesn't matter.  For VMs, I use black 7200 rpm disks. The other 28TB (raw) is spinning, always, across a mix of systems. Drive life trumps power use for me.

Of course, backups are automatic, nightly, versioned for everything that is NOT media.  Media backups are simple rsync with par2 check files to fight bit-rot and corruption.  Started doing that with my optical media backups and it has saved some data over the years. When I migrate to new storage, plan to use ZFS, which is the only file system that validates non-corrupt data on the disk.

---

### Post by mastablasta on 2017-03-21
for that many users even a USB 2.0 stick for system disk is overkill :-). yes, i am doing it, on a 2.0 plug with a USB3.0 16GB stick. i had the 8.0 GB but it got corrupted after some time. so regarding your two questions, i dont' see much issues in server accesibility. the setup is USB stick for system disk, RAID1 mdadm on ext4 (WD red drives). no issues with "mixing" the disks. at some point.

server has owncloud installed and Ajenti for some administration. it is also used for automated backup from 2 local PC (win+Linux) and 3 offsite PCs (linux +windows again). 

i am accessign via sFTP for any file browsing and i have to say it is quite responsive.

not realyl sure what is required from a NAS, but either way first time you connect you will need to wait for a bit (few secs). i see same thing here at work where we have windows all over the place, with a much more pro server setup. and either way first time you connect (open shared folder, disk), is you wait a bit then it is smooth.

---

