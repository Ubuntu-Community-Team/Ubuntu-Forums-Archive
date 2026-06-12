---
title: "WD MyCloud back to Amazon, hate it.  SEEK RECOMMENDATIONS for a REAL NAS $300 or less"
date: 2016-01-17
forum: The Cafe
---

### Post by MechaMechanism on 2016-01-17
The WD MyCloud is not a real NAS in my opinion.  It's performance is sub par.  It also presents issues with Linux as it is Windows focused.  I am looking for a OS agnostic NAS for under $300 USD in the USA.  I prefer Amazon.  I do not want media servers or helpful software crap.  I just want the NAS to be seen by any OS using smb or NFS, hopefully both at the same time.  I will use the NAS to backup computers.  I will use Windows 10 built in backup tools and Ubuntu 14.04 and 15.10 backup program.  Remote access over the Internet would be nice using TLS and a secure web server, but this is not necessary.  SSH not needed either.  Actually remote access is not needed, but if it comes standard then I will find a use for it.

1000 Ethernet a must as the entire network is 1000 Ethernet.  Low power modes are a nice thing to have.  Redundancy raid preferred.  Warranty as long as possible.  Have 4 old first generation sata drives, will consider NAS that comes with hard drives.  4 TB needed.  Will be in a low dust environment.  Fanless is the way to go.  Should just plug in NAS and Windows 10 picks it up right away.  Built in Windows backup tools file and system image should work out of the box.  Ubuntu should find it right away too.  Nice to browse NAS as if it was internal storage.

Am I missing anything.  Something I'm not considering?

What do my fellow Ubuntu people recommend.  Can you give links to Amazon product pages.

Thanks.  Nate.

---

### Post by MechaMechanism on 2016-01-17
I'm probably am going to go with this one.

**Link:** [http://amzn.com/B00RBGYQN8](http://amzn.com/B00RBGYQN8)

Looks like I can ignore the applications and I get to choose my own hard drives.  And I get multiple raid choices.  The reviews are great.  Con, expensive.  I only have to come up with $100 more, I can do that.  Plus dual Ethernet port which I can link together for better throughput.

---

### Post by mastablasta on 2016-01-18
i just got a server - the HP Proliant N54L. i don't know what models replaces is ( think they might still sell this old one here and there). it has one fan but is super quiet as it is a large fan. it's fast compared to NAS, can take up to 8 GB ECC ram, runs Ubuntu (certified). Many run FreeNAS on it with ZFS. you can install what you want (services) and configure how you want it. for example for backup you can use Areca or rdiff-backup (for smalelr files) or rsync or Duplicati or BackupPC... so many to choose from. if you want a GUI there are Ajenti, Zentyal, OMV (debian), FreeNAS (BSD), Nas4Free (BSD) to name a few. it costs about the same as this NAS you presented, except it can do many other things. if i went with prebuilt NAS i would go with Synology or something similar. 

if i had time i would build a PC and use it as NAS (e.g. mini ITX board with SoC + large box for many drives + a PSU). you say you will use it only for backup. for that a Raspberry PI + external USB drives would do just fine.

---

### Post by MechaMechanism on 2016-01-19
> **mastablasta said:**
> i just got a server - the HP Proliant N54L. i don't know what models replaces is ( think they might still sell this old one here and there). it has one fan but is super quiet as it is a large fan. it's fast compared to NAS, can take up to 8 GB ECC ram, runs Ubuntu (certified). Many run FreeNAS on it with ZFS. you can install what you want (services) and configure how you want it. for example for backup you can use Areca or rdiff-backup (for smalelr files) or rsync or Duplicati or BackupPC... so many to choose from. if you want a GUI there are Ajenti, Zentyal, OMV (debian), FreeNAS (BSD), Nas4Free (BSD) to name a few. it costs about the same as this NAS you presented, except it can do many other things. if i went with prebuilt NAS i would go with Synology or something similar. 

if i had time i would build a PC and use it as NAS (e.g. mini ITX board with SoC + large box for many drives + a PSU). you say you will use it only for backup. for that a Raspberry PI + external USB drives would do just fine.That's food for thought.

---

### Post by coldraven on 2016-01-19
Regarding ZFS  I found this article to be very interesting.
[http://arstechnica.co.uk/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/](http://arstechnica.co.uk/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/)

---

### Post by mastablasta on 2016-01-19
BTRFS (in linux) has similar functionality to ZFS, only it is considered as so mature. It will in time probably become the default file system it is not there yet.

Just to mention if you go your own way and if you venture outside Ubuntu there are two good Web GUI interfaces (distros) based on RedHatt/CentOS and that is ClearOS and Nethserver. With CentOS long support time it would probably be more setup and forget for the next 10 years...

If I had more money & less time Synology seems good. I think you can also buy just the OS from them (it's BSD based I believe). My cousin uses it in their office. They are very pleased. Their PCs are all windows and they use NAS for backup and various office things. there was another one that is also pretty good in the same price range but I forgot what the brand is. I know I saw it in Berlin on a fair once...but can't remember the brand.

---

### Post by MechaMechanism on 2016-01-27
I went with the below.  Just hook it up to my router's USB 3.0 port and I have a network drive.  No apps, no nothing.  Just a dumb drive.  Sounds good.

[http://amzn.com/B00TKFEEBW](http://amzn.com/B00TKFEEBW)  :guitar:

Thanks for the feedback everybody.  It was helpful in driving my decision.

---

