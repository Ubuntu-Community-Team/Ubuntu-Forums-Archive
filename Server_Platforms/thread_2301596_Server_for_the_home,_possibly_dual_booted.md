---
title: "Server for the home, possibly dual booted"
date: 2015-11-03
forum: Server Platforms
---

### Post by Kansasguy on 2015-11-03
I want to set up a server for my home, to back up/sync files, photos, etc. Don't do games or host a website.

I have been dual booting Windows with either Mint or Ubuntu for years, but have never made/used a server. 

I have a Powerspec (Microcenter's brand) PC, with a decent processor, 2gb ram, and sata drives, that was dual booted with Win7 and Mint 17.2, but now has just Win10 on it's original 500mb HD.  I have added two 1TB drives, and have been backing up data by moving around an external HD.  Would like to have a server.

Q. Can I dual boot this machine Win10/Ubuntu server? (I think YES)
Q. If so, should both of these be on the same drive, using the TB drives for
   storage? Or should I keep Win10 (i know, i know) on one drive and Ubuntu
   server on another?  (I would not need both OS at the same time, I use Linux
   for most everything)

I am somewhat comfortable with terminal commands,(can follow well layed-out instructions) but would prefer to use a GUI.  I have used Teamviewer, and have learned about Remmina and VNC recently with a Raspberry Pi2.  From what I see, Owncloud looks promising.  Looking also at rsync with a GUI front end. What I really want is to be able to backup/sync other computers in the house from my Linux version laptop, without having to transfer, and make multiple backups, with an external HD. Nothing online.

Point me in the right direction and I'll go,

Any help greatly appreciated...

---

### Post by bab1 on 2015-11-03
> **Kansasguy said:**
> I want to set up a server for my home, to back up/sync files, photos, etc. Don't do games or host a website.

I have been dual booting Windows with either Mint or Ubuntu for years, but have never made/used a server. 

I have a Powerspec (Microcenter's brand) PC, with a decent processor, 2gb ram, and sata drives, that was dual booted with Win7 and Mint 17.2, but now has just Win10 on it's original 500mb HD.  I have added two 1TB drives, and have been backing up data by moving around an external HD.  Would like to have a server.

Q. Can I dual boot this machine Win10/Ubuntu server? (I think YES)
Q. If so, should both of these be on the same drive, using the TB drives for
   storage? Or should I keep Win10 (i know, i know) on one drive and Ubuntu
   server on another?  (I would not need both OS at the same time, I use Linux
   for most everything)

I am somewhat comfortable with terminal commands,(can follow well layed-out instructions) but would prefer to use a GUI.  I have used Teamviewer, and have learned about Remmina and VNC recently with a Raspberry Pi2.  From what I see, Owncloud looks promising.  Looking also at rsync with a GUI front end. What I really want is to be able to backup/sync other computers in the house from my Linux version laptop, without having to transfer, and make multiple backups, with an external HD. Nothing online.

Point me in the right direction and I'll go,

Any help greatly appreciated...

You don't need to use "Ubuntu Server Edition" to provide server services (HTTP, Samba, NFS, etc.).  If you have limited experience with the command line you certainly don't want to use the "Ubuntu Sever Edition".  It has no GUI interface at all.  There is no functional difference at this point between the kernel used with Ubuntu (desktop) or Ubuntu Server.

In my book the server is the service, not the OS. I would just use the existing Mint and add the services (servers) that you need.

The OS not the determining factor.  For years I used a P3 Pentium with 1GB RAM and Ubuntu Server OS with NFS and Samba.  The lack of a GUI was not a negative for me.  In fact the video card was a weak ATI 128MB card so I would not have been able to run a GUI even if I had wanted to.  The point being that file server hardware needs HDD I/O speed not CPU power so much.

---

### Post by mastablasta on 2015-11-04
i am not sure why you need ubutnu at all. dual boot server is just ridiculous. servers are usualyl on all the time. Ubutnu server has various web guis available for easier administration such as Zentyal or Ajenti. there are also specific OS that are made with webgui in mind such as the Debian based OpenMediaVault.

anyway back to my first point - you can do all that already using default windows. windows share works, so does samba if you use Linux on some PC's. all you would need is to add grsync (has a windows version) since you say you want graphical rsync (and I am not sure why as you could just share the folder...). want to open to internet? install xammp and configure ports correctly. done.

here is my single OS (Ubuntu Linux) setup if you are interested:
server has an 8GB USB stick for root and system. it then has 2 x 2 Tb drives setup in software RAID 1 (very easy to do in Ubuntu).
It has Open SSH server installed and to connect to it form internet you need (for now) keys + password and SSH client (e.g. putty in windows, there is another one in Ubuntu Linux terminal by default) + fail2ban to protect a bit against general hack attempts

I then installed on server Piwigo (to be used for gallery - not decided yet), Owncloud (was installed but I removed it for now-it may replace Piwigo again), Ajenti (for server administration via web).

I use Areca on PC's. Areca is a backup tool that works on Linux as well as on Windows (clients for both OS). I setup a job and in windows it creates batch file in Linux it creates a script. In windows Task manager is running it in Linux Cron. It then does backups automatically to server. and it finally works as it should yay! there are many similar tools, btu for now I chose Areca, as it has the option to send uncompressed files. In my opinion jpeg pictures do not need to be compressed again. other GUI tools for backup usually compress the data. so you have Duplicity, Backintime, UrBackup (this one uses pull method, and is also made for windows), LuckyBackup, Kup, Kbackup.... there are many command line tools. some of them are pretty easy to work with like rdiff-backup.

and that's it so far. I used to have Owncloud - it syncs the folder with server. but sync is not the same as backup. something get's corrupted on server, it get's corrupted on local disk as well. something get's deleted on server it get's deleted on disk as well. it's all synced. although it is very easy to share stuff using sync and owncloud does have versioning. so there is some security in that. 

I don't have much else on it as it was meant to be used only for backups. but we do plan to setup a VPN on it. though, I haven't figured out how to do it the way I want it yet.

---

### Post by Kansasguy on 2015-11-05
Thanks to you both.  In the last few days I have gotten back into Samba, learning it again. For now will stick with Mint because I am used to it. I have used Teamviewer for years with far away relatives, but wanted to use open source whenever I could, so have gotten into VNC, remote desktop, with Remmina as a front end. Will look into NFS.  

Bab, point well taken that it's not the OS, thanks

Blasta, thanks especially for the info on sync vs backup.  I've always been a stickler for backups, I think the desire to sync was just thinking it would be "cool", (beside just constantly learning what these machines can do).

Question for you both:  Since for now I will be sticking with dual booting Win/Linux, and concentrating on LAN server type stuff,and I have always dual booted on one hard drive on all my computers, and don't do any gaming that would need a lot of speed, and I have never done "raid"; on my box with Win10 on a 500gb hd, that also has two 1TB hd's, _should I put Mint on the 500gb with windows, or put it on one of the two 1TB drives? Any advantage either way?_

Haven't ever done that but I think it would only be a case of working with the boot order (not UEFI in this case).  One of the reasons I ask is that I have a few non geeky friends that have bought Win laptops with Win7 or 8; have dual booted them with Mint or Ubuntu because all they do is surf and email, but then it's a problem upgrading to Win 10 without re-configuring the partitions, which is really a problem when talking over the phone several states away.   Thanks again

---

### Post by bab1 on 2015-11-05
> **Kansasguy said:**
> Thanks to you both.  In the last few days I have gotten back into Samba, learning it again. For now will stick with Mint because I am used to it. I have used Teamviewer for years with far away relatives, but wanted to use open source whenever I could, so have gotten into VNC, remote desktop, with Remmina as a front end. Will look into NFS.  

Bab, point well taken that it's not the OS, thanks

Blasta, thanks especially for the info on sync vs backup.  I've always been a stickler for backups, I think the desire to sync was just thinking it would be "cool", (beside just constantly learning what these machines can do).

Question for you both:  Since for now I will be sticking with dual booting Win/Linux, and concentrating on LAN server type stuff,and I have always dual booted on one hard drive on all my computers, and don't do any gaming that would need a lot of speed, and I have never done "raid"; on my box with Win10 on a 500gb hd, that also has two 1TB hd's, _should I put Mint on the 500gb with windows, or put it on one of the two 1TB drives? Any advantage either way?_

Haven't ever done that but I think it would only be a case of working with the boot order (not UEFI in this case).  One of the reasons I ask is that I have a few non geeky friends that have bought Win laptops with Win7 or 8; have dual booted them with Mint or Ubuntu because all they do is surf and email, but then it's a problem upgrading to Win 10 without re-configuring the partitions, which is really a problem when talking over the phone several states away.   Thanks again

I can't really speak to the question of Windows upgrades.  My last windows machine was an XP laptop.  It's my dim understanding is that Windows will try and format the entire HDD.  So for that reason alone I would put Ubuntu on a separate HDD or better yet on a SSD.  I use 128GB SDD's for my Ubuntu machines. The running of the OS's on the same HDD should not be a problem however.

You mentioned RAID.  You do not need to use RAID at all.  It provides no advantage in your situation.  RAID is useful when there is a need for High Availability (HA) such as a high usage database server or web server.  If you have backups of all your data then you are good.  In some cases these days the RAID array will become unrecoverable and the whole thing will need to be reinstalled using backup data anyway.  There is no safety advantage.  I do not use RAID on my home network.  I have had HDD failures and always use a fresh install when grading.  With the backups I have it's usually about 30 minutes of work before I am up and running with any of my setups.

---

### Post by darkod on 2015-11-06
What is the problem upgrading to Win10? Unless you need more space on the partition, there should not be any need for repartitioning at all. Including if you decide to do windows clean install instead of upgrade, you can tell the installer to use the current partition (and format it of course), but that doesn't need repartitioning.

On the other hand, if you want to change partition sizes, yes, that involves repartitioning. But that would be the case even if you are not dual booting, right?

It all depends on you and how you want to organize the partitioning of your machine. From my perspective, I would actually do a dual boot on the 500GB disk, and keep the 1TB disks for data (raided or not). In fact, that's what I currently have on my desktop: win7/ubuntu14.04 dual boot on a 128GB SSD, and two more 250GB HDDs for data (not raided). Having the important data on separate disks/partitions allows for quick reformatting and reinstalling of the OS when ever you need, without affecting your data.

It's all up to you...

---

### Post by mastablasta on 2015-11-09
> **bab1 said:**
> I can't really speak to the question of Windows upgrades.  My last windows machine was an XP laptop.  It's my dim understanding is that Windows will try and format the entire HDD.  So for that reason alone I would put Ubuntu on a separate HDD or better yet on a SSD.  I use 128GB SDD's for my Ubuntu machines. The running of the OS's on the same HDD should not be a problem however.

I too would do as darkod suggested. keeps system disk and data separated. Data (that whole drive) can be in NTFS format so it is easily accessible by both OS if needed.

> 
You mentioned RAID.  You do not need to use RAID at all.  It provides no advantage in your situation.  RAID is useful when there is a need for High Availability (HA) such as a high usage database server or web server.  If you have backups of all your data then you are good.  In some cases these days the RAID array will become unrecoverable and the whole thing will need to be reinstalled using backup data anyway.  There is no safety advantage.  I do not use RAID on my home network.  I have had HDD failures and always use a fresh install when grading.  With the backups I have it's usually about 30 minutes of work before I am up and running with any of my setups.

RAID is not backup, it's a disk redundancy that guard the data in case of disk failure. for example RAID0 is "a joke" regarding data safety, RAID1 however can be useful - if one of the disk fails you can replace it and data will be copied from the good disk to it.

again it is not a backup, so good backup is still needed. but it can be used in backup PC.

you are using desktop on server. it uses additional system resources. furthermore as you start opening the ports it will provide additional attack vector. if you continue with this setup make sure you keep it really up to date (at least security patches). I suggest you enable/setup automated updates: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

if you have time experiment with server distro in virtualbox. there are a couple of distros out there that make prepared images (so no install needed in virtualbox only select password and user). : [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)


dual boot server could turn into an issue again when you start opening ports. you need to make sure ports are managed properly in both OS. example. just opening ssh port brings in 3-5 attempts at breaking (and bans) per day.

---

