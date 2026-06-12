---
title: "What are the benefits of a file server over a desktop machine?"
date: 2011-02-15
forum: Server Platforms
---

### Post by Maheriano on 2011-02-15
One of my clients has a server in their office storage room except it's not really a server, it's a headless Windows 7 box. For now I set up VNC on one of the other machines so I can remote into it and I also set up the files as a mapped drive on every computer in the office.

If they have a fire all their files will be wiped out so I'm going to set up a crontab job to backup all their files nightly onto a remote hosting service somewhere but I'm wondering if this application would warrant (for any reason) making this machine into a proper Apache file server. I guess I could load SVN onto it but there's really only 1-2 people that modify the files and they're mainly just client files of jobs they've done for the year along with some Quikbooks payroll stuff. Any benefit?

---

### Post by Maheriano on 2011-02-15
What the hell? How did my post get on another website?

[http://www.oblurb.com/other_os-what-are-the-benefits-of-a-file-server-over-a-desktop-machine.html](http://www.oblurb.com/other_os-what-are-the-benefits-of-a-file-server-over-a-desktop-machine.html)

---

### Post by snkiz on 2011-02-15
Welcome to the wonderful world of data mining and content farming. As to your question.
I would think it would be better to have a proper LAMP stack that is designed to run with minimal supervision. I shudder to think what would happen to a Windows box left unattended and connected for any length of time. It could be weeks before someone notices there is something amiss, since the job of serving files is pretty straight forward and low overhead.

---

### Post by tgalati4 on 2011-02-15
Find and old computer and install freenas on it with some newer/bigger drives.  That will cover a small office for years with much less maintenance than a Windows machine.

---

### Post by Maheriano on 2011-02-16
I'll put Apache on the box they're using and set everything up as a mapped drive again.
Would it be better to set up a crontab job to run a PHP file with FTP_PUT() code in it or to simply use RSYNC in Apache to back up the files to a remote server? I'm just looking at what my options are now.

---

### Post by dtfinch on 2011-02-16
I suppose it'd work fine with less than 10 users (the limit of Windows client editions). And it'd be easy for an average person to administer if you're not there.

Backups on Windows are a little complicated, due to the fact that any file can be locked deny-read by a client, preventing it from being read short of creating a full-volume snapshot and reading the snapshot volume. I use a tool called [HoboCopy](http://alt.pluralsight.com/wiki/default.aspx/Craig/HoboCopy.html) just for that, to copy data files that are frequently locked prior to running a backup (usually with cwRsync), unless you use a backup program that already uses shadow copies. You may also want to design your backup so that if files are deleted or corrupted, those files won't be removed from or overwritten on the backup destination on next backup.

I'd also worry about the lack of a raid, though with good backups a disk failure would just mean loss of any work since the last backup, and having to rebuild the system from scratch.

Also, Windows is locked to the motherboard and disk controller that you install it on, so a failure of either would also mean reinstalling the system from scratch even though the data's intact, while on Linux you'd just plug the hard drives into a new system and boot it up.

---

### Post by Maheriano on 2011-02-16
> **dtfinch said:**
> I suppose it'd work fine with less than 10 users (the limit of Windows client editions). And it'd be easy for an average person to administer if you're not there.

Backups on Windows are a little complicated, due to the fact that any file can be locked deny-read by a client, preventing it from being read short of creating a full-volume snapshot and reading the snapshot volume. I use a tool called [HoboCopy](http://alt.pluralsight.com/wiki/default.aspx/Craig/HoboCopy.html) just for that, to copy data files that are frequently locked prior to running a backup (usually with cwRsync), unless you use a backup program that already uses shadow copies. You may also want to design your backup so that if files are deleted or corrupted, those files won't be removed from or overwritten on the backup destination on next backup.

I'd also worry about the lack of a raid, though with good backups a disk failure would just mean loss of any work since the last backup, and having to rebuild the system from scratch.

Also, Windows is locked to the motherboard and disk controller that you install it on, so a failure of either would also mean reinstalling the system from scratch even though the data's intact, while on Linux you'd just plug the hard drives into a new system and boot it up.

So if I understand you correctly you're saying I should:
- tell them to buy a second hard drive
- install Ubuntu Server edition with Apache
- configure RAID0
- use RSYNC

---

### Post by mciverza on 2011-02-16
> **Maheriano said:**
> So if I understand you correctly you're saying I should:
- tell them to buy a second hard drive
- install Ubuntu Server edition with Apache
- configure RAID0
- use RSYNC

Instead of using Ubuntu Server ed, rather try Zentyal (which is Ubuntu server + extras with a nice web-based management console). [www.zentyal.org](www.zentyal.org)

NOTE: I don't work for zentyal, I just like it.

---

### Post by dtfinch on 2011-02-16
Never use raid 0.

---

### Post by Maheriano on 2011-02-16
> **dtfinch said:**
> Never use raid 0.

Pourquoi?

---

### Post by James78 on 2011-02-16
> **Maheriano said:**
> Pourquoi?
Pourquoi que RAID 0 is very unsafe. RAID 0 is fast, but there's no guarantee your data is safe. Using RAID 0 with 3 drives for example increases your risk of hard drive failure and loosing all your data by 3-fold. If you want the speed benefits of RAID 0 but none of the fallbacks, you need to use a safe alternative, such as RAID 5 (3 drive minimum), which has parity striping (data backup, or more technically bits that detect errors).

More information on Wikipedia.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by Maheriano on 2011-02-16
So what are my options with just 2 drives?

---

### Post by James78 on 2011-02-17
Only RAID 0 and RAID 1 I'm afraid. RAID 1, as Wikipedia puts it..

*"In RAID 1 (mirroring without parity or striping), data is written identically to multiple disks (a "mirrored set")."*

So essentially you have 1 disk being used as normal, and another disk which is a dedicated data backup in case of hard drive failure. That means that if I have 2 120GB hard drives, with this setup, I only get to use 120GB instead of 240GB, however this provides peace of mind for me since I know that if 1 drive fails I still have all my data.

Please note that while this is a data backup in case of hard drive failure, it does not replace the regular function of backing up data. E.g. if you delete /home/, it will be mirrored and deleted on all other drives as well.

RAID's generally start getting really useful with 3 drives and more (in my opinion), because then you can start doing advanced combinations such as data striping (which makes your drives as fast as nX; (n&#8722;1)X in the case of RAID 5, here n is how many drives you have in the RAID). In the case of RAID 1 you get a read benefit of nX but a write benefit of 1X (or nothing)

If you don't mind reinstalling if your system gets messed up, you simply may be able to just do regular backups of system critical information, e.g. /home/, and your configurations in /etc/, and just skip using a RAID. However, this of course leaves you vulnerable in case of hard drive failure (unless you backup to another drive/place).

---

### Post by koenn on 2011-02-17
any particular reason you think a web server (apache) is going to be any good when you're looking for windows file sharing and/or backups ?

---

### Post by jvin248 on 2011-02-17
I was wondering why the Apache overhead too?  They just need a network storage solution and an enhancement is backups.

Find two Pentium-2 233Mhz or newer computers, put two identical high capacity Hard disk drives in each, install FreeNAS on both machines.

Setup with RAID-1 on both machines and then put one of the two machines at a different location and set up rsync between them (web gui menu item on FreeNAS).

I like using the P2's as they were quite solid motherboards and have the ability for drive spin-down and energy savings (idle <25watts, full-on about 55watts).

---

### Post by Maheriano on 2011-02-17
> **jvin248 said:**
> I was wondering why the Apache overhead too?  They just need a network storage solution and an enhancement is backups.

Find two Pentium-2 233Mhz or newer computers, put two identical high capacity Hard disk drives in each, install FreeNAS on both machines.

Setup with RAID-1 on both machines and then put one of the two machines at a different location and set up rsync between them (web gui menu item on FreeNAS).

I like using the P2's as they were quite solid motherboards and have the ability for drive spin-down and energy savings (idle <25watts, full-on about 55watts).

That's the whole point of this post, asking if I should move to Apache or just keep the Windows desktop machine they're using.
Does FreeNAS do incremental backups?

---

### Post by koenn on 2011-02-18
> **Maheriano said:**
> That's the whole point of this post, asking if I should move to Apache or just keep the Windows desktop machine they're using.
In your OP you're asking about an "Apache File server" which would make people here wonder what it is you're trying to do : a web server (apache) ? a file server ? or - for some exotic reason you forgot to mention -  using a web server as file server ? 

So; you want a file server / NAS / ... type of solution then ? 
If so, think Samba (~ Windows File Sharing) or something like FreeNAS, which has been suggested a couple of times.

If you want backups, you'll have to add a backup thingy to that - could be anything from a copy command to a fullblown backup suite (Bacula, Armada, ...).

---

### Post by Maheriano on 2011-02-18
Oh snap, Apache is a webs erver base? I thought it was just a server backend for an operating system. That's where the confusion lies, okay. So no Apache, I'll look into NAS.

---

