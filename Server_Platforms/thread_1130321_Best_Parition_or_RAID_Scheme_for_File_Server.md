---
title: "Best Parition or RAID Scheme for File Server"
date: 2009-04-19
forum: Server Platforms
---

### Post by Noah0504 on 2009-04-19
So, here is my problem.  I currently have a home server running Ubuntu 8.10 (soon Ubuntu 9.04).  I currently have 1TB HDD, but I'm going to be adding another identical 1TB HDD this week.  As there isn't much on the server now, I'm going to backup what's there and reload.

I plan on using the server for a few things.  The biggest use will be as a Samba server to allow the other PCs in my house to share and store files.  I also have a media center that will pull media from the Samba share.  Secondly, I plan on backing up data from my MacBook Pro using rsync.  It's easy and it works.

I'm trying to figure out how I should partition my drives or if I should at all.  I see that that Ubuntu 9.04 Server has LVM preselected, but I'm not familiar with using LVM at all.  I understand the concept, but other than that, I'm clueless.

I thought about just keeping the drives seperate.  One for the OS, and one for other data, but that will leave a lot of extra space on the main drive.  I also thought about just striping the drives as even if on died, I'm not losing data as it is from another source in the first place.  Or, I thought about going RAID 1 to have an extra backup.  And the last option I've considered is picking up 1 more drive and going with RAID 5 to get the best of both worlds.

If I partition the drives using LVM, what's the best partition scheme to use.  Any advice would be welcomed!

---

### Post by bigbearomaha on 2009-04-19
Predominantly, you use LVM to combine space across multiple hard drives.  You can add and remove hard drives to attain more 'continuous' storage space, if that's what you need.

RAID, especially if you have hardware raid, can accomplish the same thing  or can be used for duplicity.  ie, you have three hd's of same size that are mirror duplicates of each other, therefore, if one hd dies, you don't necessarily lose your data, just remove the bad hd and replace it with a good one of same size.  the other two will 'mirror' the data to it after it is installed.

What type of file serving are you doing with the server?  will it be web facing?

will it be an nfs/samba file server, or use a web based app like ajaXplorer to provide files to signed in users?

FTP files server?

more than likely, you will want to have a seperate /, swap, /home, /var and one or more custom 'data' partitions.

you might also consider using XFS to format the data partitions and ext3/4 for the others.


Big Bear

---

### Post by Noah0504 on 2009-04-19
It will basically be a Samba file server as the only non-Windows machine on the network is my MacBook Pro.  I know Windows can deal with NFS using Microsoft's Unix Tools for Windows, but I think it will just be easier to use Samba as it works.  (I also just discovered a trick to use a SMB share for Time Machine... I wonder how well it works!)

Other than the SMB shares, it will server out a few things with Apache and maybe do a little BitTorrent seeding.  Mostly it's going to be an overpowered file server.  Ha.

---

### Post by bigbearomaha on 2009-04-19
when dealing with windows machines on a LAN, it usually is best to stick with samba.

---

### Post by Noah0504 on 2009-04-19
Yeah, especially when the folks will be using the shares as well.  I like to have things work for them.  I hate getting phone calls when I'm out and about!  :)

If I wanted to set my server up now, how would I use LVM to be able to span over to the new HDD once it arrives?

---

### Post by bigbearomaha on 2009-04-19
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

This link is as good as any to get started using LVM.

Big Bear

---

### Post by Noah0504 on 2009-04-20
Well, after reading that and a few other things, I think I have the simple idea of it down.  It seems like there are a lot more things that can be done, but expanding the volume and snapshots are really all I need.  Thank you!

---

