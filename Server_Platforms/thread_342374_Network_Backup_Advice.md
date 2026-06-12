---
title: "Network Backup Advice"
date: 2007-01-20
forum: Server Platforms
---

### Post by rickyjones on 2007-01-20
Hey everyone,

I'm the IT guy for my church. Now I've found myself in the middle of a small issue. In the last few months we've expanded the IT section - adding a domain controller, central file server, network monitoring, several more workstations, etc... Now I'm trying to figure out a simple and cost-effective backup system.

I currently have two actual servers:

1) Sun: Windows Server 2003. Active Directory. Fileserver. DHCP. DNS. This server has two 120GB sata drives in a RAID1 array (Mirrored).
2) Mars: Ubuntu 6.06 Server. Network monitoring server. This server is just a single harddisk machine that runs Nagios to monitor the network.

All in all I have about 30GB of data on the server Sun that needs to be backed up (this includes it's system state and user files). The church staff creates a moderate amount of office files every week. We also record sermons on Sunday morning, which is an additional 80MB of space taken up every week.

For a backup system, I was thinking of a dedicated machine with 8 hard drives. Hard drives 1 - 6 would be for incremental backups for Sunday through Friday. Hard drive 7 would be for a full weekly backup - this weekly backup is overwritten every week. Hard drive 8 would be a fully monthly backup once per month - I would have 3 of these and after each monthly backup the drive would be removed, taken offsite, and replaced with the oldest of the 3.

This sounds good in principle, and on paper, but I'm not sure how I would take care of the monthly backup drive. I don't want to shutdown the server once a month to replace the hard drive - does anyone know of a hotswappable hard drive tray that would work in Linux?

Now this whole thing sounds good to me - but would anyone with more experience care to weigh in on this?

Thanks for the help!

-Richard

---

### Post by jtc on 2007-01-20
Well, I'm not entirely sure I would do it the exactly same way myself. Any particular reasons why you want to store everything on separate physical harddrives? Sounds like the amount of storage you need could be found on one single harddrive and if you want more harddrives to protect your data, how about using a [RAID]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks")-solution?

The easiest way today to get a somewhat hotswapable harddrive today is simply using an external USB-drive. You do have to unmount it, but except  that it is simply to remove it.

One thing which concerns me thought is that offsite-backups are only taken once a month. If something really bad happended at the absolute worst time you'd lose almost a month full of data.

Using movable harddrives it would be inconvenient to carry them back and forth to often, but how about some buying offsite network storage? Myself I use [rsync.net]("http://www.rsync.net/") and have only good things to say about them. Buying 30gb offsite-storage is a significant cost thought. A good comprise then is to only backup rescent data to the offsite network-storage.

---

### Post by chrisfay on 2007-01-20
> Sounds like the amount of storage you need could be found on one single harddrive 

For a production backup solution? hmmmm....

 > how about using a RAID-solution?

did you even read the guys post?

> I currently have two actual servers:

1) Sun: Windows Server 2003. Active Directory. Fileserver. DHCP. DNS. This server has two 120GB sata drives in a RAID1 array (Mirrored).

Seems he's fairly familiar with RAID.

> If something really bad happended at the absolute worst time you'd lose almost a month full of data.

Considering he'd have to loose all 6 incrimental drives, the 7th 'weekly' drive, the 8th 'monthly' backup drive and finally the offsite monthly backups, I hardly think that a more frequent schedule would be necessary. 

> Using movable harddrives it would be inconvenient to carry them back and forth to often, but how about some buying offsite network storage?

If the money's a non-issue, hot swap it. I would never trust someone else to maintain my critical data. And I couldn't think of a much easier method than grabbing a drive and yanking it out when you need it. Not sure what's so 'inconvenient' about it.

All in all, your plan seems quite good, if not borderline neurotic for the ammount of data.

We use a few different swappable systems in our datacenter for a bunch of our unix systems, but I'd have to double check on model info for a recommendation.

---

### Post by jtc on 2007-01-20
> **chrisfay said:**
> For a production backup solution? hmmmm....
Was primarily curious why he wanted one physical drive for each increment.
 
> **chrisfay said:**
> 
did you even read the guys post?
Seems he's fairly familiar with RAID.

You are right, I might have read his post a bit quickly.

> **chrisfay said:**
> 
Considering he'd have to loose all 6 incrimental drives, the 7th 'weekly' drive, the 8th 'monthly' backup drive and finally the offsite monthly backups, I hardly think that a more frequent schedule would be necessary. 

Yes, but all those increment are all stored at the same physical location as the original data, at least that is the impression I got. What I'm considering is a worst case scenario with something happen to the church.

> **chrisfay said:**
> 
If the money's a non-issue, hot swap it. I would never trust someone else to maintain my critical data. And I couldn't think of a much easier method than grabbing a drive and yanking it out when you need it. Not sure what's so 'inconvenient' about it.

If it were the right company I would trust them with critical data. Since such a company specialize in backup and storage they have the potential of having better resources for safekeeping of data. Of course since I like to be extra safe I'd like to keep local backups as well.

The inconvenient part I refer to is it being manually. It is something which can be forgotten, delayed for unexpected reasons etc. My very personal opinion is that backups are generally best done completely automatic.

---

### Post by rickyjones on 2007-01-20
Wow - some nice information here :).

My goal here is to have the incrementals at the church - and yes, worst case scenario would be that we could lose a months worth of data... but that would be if the whole server room/church office was blown up (or flooded I guess). If that were to happen... I don't think the data would be the highest worry at the time.

The main question left on my mind, however, is the monthly off-site backup method. I see two possibilities: 1) Hot-swappable harddrives, which would mean a special cage in the computer (and Linux support). 2) External USB drives.

I wouldn't mind going w/ the external USB drive, it seems quite practical and a little more cost-effective. However, the last time I used an external USB drive w/ Linux was this past summer on my laptop. I was running Ubuntu 6.04 (I think that was the version - it was Breezy Badger), and after about 20 minutes the USB hard drive would be inaccessible. I couldn't read/write to it, nor could I unmount it. My USB mouse would also stop working. I'd have to restart to get it working again. Not sure if it was just Ubuntu having issues w/ my laptop or what, but it /did/ concern me a little bit.

Other than that, it wouldn't be such a bad idea to use external USB drives. I could easily write a script that would unmount the USB drive after the backup, allowing me to just pop it out.

My last thought here is the /way/ the backups would be run - mind reviewing my idea here as well?

My plan is to use samba to broadcast the shares (password protected of course for the backup routine): Each hard drive would have it's own Samba entry. So we have Sunday through Friday, then Saturday Full. The monthly off-site would not be in Samba. Instead a script would run that would copy the latest Saturday Full to the off-site monthly backup, then unmount the drive and allow me to swap it out. For the daily intervals, I would have scripts on the server Sun and Mars (and any other eventual servers) that would copy the data to the specific Samba share for the day.

The way I see it, I'd have 6 days of backups, in addition to 2 full months behind.

Any other suggestions?

Thanks for the help!

-Richard

---

### Post by tagra123 on 2007-01-20
Here's a script I made and use.

[http://www.ubuntuforums.org/showpost.php?p=1402091&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1402091&postcount=1)

It does daily, hourly and weekly backups

You can simply copy the 4 weekly backups for a monthly backup to a cd or dvd for offsite storage.

You should be able to set up the script in less than an hour.

---

### Post by nix4me on 2007-01-20
For your setup, I would use sbackup and a couple external usb2 drives.  You already have a raid setup on the server, so i wouldn't go overkill with 8 harddrives and a seperate server.

Use either sbackup or make a simple rsync script to dump the dailys, weeklys and monthy's off to the external usb drives.

nix4me

---

