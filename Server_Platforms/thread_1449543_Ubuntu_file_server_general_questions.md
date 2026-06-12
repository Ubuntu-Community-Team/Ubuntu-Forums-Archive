---
title: "Ubuntu file server general questions"
date: 2010-04-08
forum: Server Platforms
---

### Post by Loki57701 on 2010-04-08
Currently, I'm running Ubuntu server 9.10 on an old PC for use as file server. I have everything up and running, but I have a few questions.

- Should I store files on the same hard drive the OS resided on, or install a second internal hard drive?

- Can I use an external USB hard drive as my primary storage drive, or use it as an rsync backup destination?

- Do any of you run ubuntu file servers, and if so, what has your experience been so far?

My needs for this server are very modest and honestly I don't need a full blown server OS, but I wanted to try it. What I'm most concerned about is reliability, I realize linux servers pretty much run the internet, but I've had some... bad luck with the desktop versions of linux in the past. I don't want to end up losing all my data in some random system crash. I know, multiple backups blah blah lol. Is there anything I can do aside from backups and regular updates to ensure the stability of the system?

---

### Post by dudumomo on 2010-04-08
Hi Loki,
You can directly store all your files on the same partition. But it is preferable to have a dedicated partition. If you have second hard drive it would be even better.

An external hard drive is fine too. But if you are going to use it all day long, why using it as an external one ?
However, it is really important to perform some backup on a external hard drive, so here you go.

I'm new with Ubuntu Server, but so far so good !
I did quite a lof with it and I don't have any problem.
(You can check my tutorials if you want to)

And, ton ensure the stability of the system, I would say..to have your server properly configured. Otherwise, backup + update should be fine.

Good luck

---

### Post by iissmart on 2010-04-08
1) Doesn't matter, but I like to keep things organized and have my OS on its own drive. It's up to you.

2) Yes, it should automount itself after every reboot too. If you are setting up an automated backup script using rsync I would advise you to *always* check if the drive is mounted prior to performing the backup though, just to be sure.

3) I do, I have one drive as the OS drive (~60GB, lots of wasted space), and 3x1TB drives set up in an LVM so there is a single "storage" mount point.

Server OS's like Ubuntu Server are generally tuned and tweaked for specific uses including what you are describing, so I wouldn't think of it as "overkill" by any means. What you should do is think hard about what filesystem your drives will be using; that is where the reliability aspect comes into play when a server loses power randomly and the disk just happened to be writing to the filesystem when it happened. Can it recover from random corruption? Some can. There are plenty of resources out there to make a knowledgeable decision (*cough*, wiki).

I would actually advise against regular updates (besides critical/security updates, of course) on your server. The old saying "if it ain't broke, don't fix it" comes to mind here...I've spent many hours trying to figure out how to get my server back up and running after doing a full update only to find out it overwrote some of my config files/things weren't mounting properly/dependency issues/etc..

Oh, and multiple backups blah blah.

---

### Post by Loki57701 on 2010-04-08
Thanks for the response dudomomo.

---

### Post by arloth on 2010-04-08
1. It's best to store them on a separate hard drive.  You can then format it in XFS, or other file system that meets your needs.  This leaves your boot drive free for programs, or in the worst case leaves you free from some of the worries of OS meltdown.  Do some research into this and find one that meets your needs.  I like XFS myself, it's well established and has online defragmentation which comes in handy after years of use.

2. In my experience USB is too unreliable for your primary storage.  USB hubs can reset themselves due to static, power surges, or other things, resulting in lost data. It might sound good, but you'll get better results with a regular internal drive.  They're fine for backup however, you just don't want to rely on them being connected 100% of the time 365 days a year.

3. I have one, it's been good to me the last few years, I use a cheap Netcell raid card with 5 drives for 2TB.  Samba performance can be spotty at times (esp to other linux machines ><).  I actually run Xubuntu on it because I want the option to use the gui for configuring it.  Oh! One important thing to remember, if you upgrade your packages and samba is one of them, all your clients will get the boot when it restarts the service, so plan accordingly when you update it so that no files are open on clients.  Once running though, usually the worst that will happen is a drive failure, I've had no data corruption issues.  Although, xfs_fsr did refuse to defrag a 40GB file for me, it didn't actually corrupt the file system in the process.

---

### Post by Loki57701 on 2010-04-08
Unfortunately, when I installed the server, I didn't select the LVM option because I wasnt sure how to set it up. I guess maybe I should have?

I still need to add extra hard drives to the server. I'm not 100% sure on how to do that through linux, but I'm sure there's a ton of guides out there.

 I'm not sure how a file server handles the compatibility between different OS's. For instance macs cant read from NTFS without a plugin, and windows can't read from HFS by default without a middle man app. So how can those two OS's both read and write on ext3/4 with no problems? Is the server able to interpret the data and write it on the native file-system regardless of it's source?

Thanks for the update info, I will keep that in mind.

---

### Post by arloth on 2010-04-12
> **Loki57701 said:**
> Unfortunately, when I installed the server, I didn't select the LVM option because I wasnt sure how to set it up. I guess maybe I should have?

I still need to add extra hard drives to the server. I'm not 100% sure on how to do that through linux, but I'm sure there's a ton of guides out there.

 I'm not sure how a file server handles the compatibility between different OS's. For instance macs cant read from NTFS without a plugin, and windows can't read from HFS by default without a middle man app. So how can those two OS's both read and write on ext3/4 with no problems? Is the server able to interpret the data and write it on the native file-system regardless of it's source?

Thanks for the update info, I will keep that in mind.

Linux can read/write just about any file system with the correct libraries installed.  The trick is when you're sharing files between computers over a network they're not actually writing or reading the file system directly.  In most cases they're using CIFS to talk to each other. Don't confuse CIFS with smbfs either, as smbfs is deprecated.  

There are lots of how-tos written on setting up Samba.  Adding hard drives is pretty easy as well, just picking where you want it mounted and adding a line to fstab once it's formatted.  Formatting them is fairly easy with gparted. LVM isn't bad, but imho, in most cases it's not needed.

Phoronix does benchmarks on file-systems once in a while as well as other aspects of Linux on a fairly regular basis.  So they should be able to provide you with a good benchmark of what to expect.  It's generally a battle between xfs, btrfs, and ext4.  XFS generally excelling at the large read/write tests, while ext4 and btrfs generally doing better with the small read/writes and high client counts.  BTRFS will probably become the go to filesystem for servers once it's finally released as a stable version, as its feature set and performance are very promising.

---

