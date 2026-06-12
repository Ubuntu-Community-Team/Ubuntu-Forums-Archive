---
title: "Building an small ubuntu backup server"
date: 2011-12-27
forum: Server Platforms
---

### Post by daedalo on 2011-12-27
Hi everyone!

Please excuse my English, it´s not my native language and I will probably make some horrible grammar mistakes on this text.

I just started working as a Tech support on a small company and these guys really have problems with their backups (they are using a network HDD right now... bad idea if you ask me) , so the first idea that came to my mind was to build a Ubuntu server for backups, I have used Ubuntu for Web servers so the initial installation it´s not a problem, but i know nothing about backup software or good practices.

Right now we need to backup periodically the information of at least 20 PC, all of them with Windows (XP and Seven), i also want to store a lot of images on the server and some web applications.

My question is, how would you approach this? My idea right now is to use SAMBA to allow the computers to write the server, then create a single user for everyone of them so they may handle their information, then build some scripts for automatic backups of their important information (like the Outlook files) and then, another script to copy all the information to another disk every 30 days, i´m on the right track?

Thanks for your opinion guys(and girls)! I´m very exited to start showing this people how to make thing happen with Open Source software :).

César

---

### Post by memilanuk on 2011-12-27
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

Should do pretty much everything you mentioned, minus the trial and error.

---

### Post by daedalo on 2011-12-27
Thanks memilanuk!

I´m reading their webpage, you have already deploy this Distro?

---

### Post by Lars Noodén on 2011-12-27
I would just do rsync over SSH.  

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by memilanuk on 2011-12-27
Years ago, I did have a functional server big enough to handle backups from all the various house-hold PCs and laptops and yes, I did use BackupPC.  I need to get back to that state...

---

### Post by daedalo on 2011-12-27
Thanks Lars!

My initial approach was using something like a cron running a script that should copy every file on a given folder, then store everything on a folder with a name with the date and some useful data on it (name of the user, department) ... rsync looks like a better way to do it :P.

I´m going to try memilanuk option (i just read on the BackupPC website some information about the DHCP that would mess my initial idea, but BackupPC it´s capable to handle) and if this somehow fail, they i will do it with rsync, thanks for the link!

---

### Post by jchung on 2011-12-27
Have you considered Backula?

[http://www.bacula.org/en/](http://www.bacula.org/en/)

I believe it should be available via an apt package. And they have clients for most platforms.

---

### Post by jchung on 2011-12-27
Hmmmm.... let me provide a fuller response...

Seems you have a couple things you want to do:

1. Backup Windows PCs
2. General File Server for images and apps
3. Backup the backups. 


Let me give you some info on what I do at home:

1. I have 2 file servers: Primary and Secondary
2. All systems backup to Primary (either via backup software for my Mac, i.e. Carbon Copy Cloner, or via rsync scripts)
3. Primary file server has 1 RAID array (software RAID 6 across 8 drives),  and all clients backup to filesystems created on that 1 RAID array.
4. Secondary File server has 2 RAID arrays (software RAID 6 across 8 drives, and a software RAID 5 across 4 drives). This file server maintains the secondary and tertiary copies of my files.
5. The Primary and Secondary copies of my data are all on ext4 filesystems.
6. My tertiary copy is on a BTRFS filesystem.
7. Scripts run on the Secondary Server which creates the secondary and tertiary copies. The script runs daily. For the Tertiary copy, prior to updating the copy, the script creates a snapshot. I maintain a minimum of 14 days of snapshots and up to 60 days of snapshots.

So... in this setup, here is what you would do:

1. Backup each Windows PC to a filesystem on the Primary server. Either a Client/Server backup software like Backula or Tivoli, or Windows Backup to an SMB share exported from the Primary server
2. Filesystems shared via SMB from the Primary server to serve general file server duties. Create separate accounts with specific ownerships and permissions as required.
3. Have a script running on the Secondary server which makes backups of everything on the Primary server and also updates the Tertiary copy.
4. Run the script as often as you are comfortable. (I run them daily via cron).


Hope this gives you some ideas.

Joo

---

### Post by collisionystm on 2011-12-27
Are all of your windows machines in a domain?

If so you can easily use rsnapshot which is an rsync program on your server.

You mount your windows computers in /etc/fstab on the server and just have rsnapshot backup the mounted directories to a folder. Rsnapshot is nice because you can go back in time several days/weeks/months depending on much storage you have.

Just be careful using rsync with anything running sql.

if you prefer to have your windows machines just back to the server from the windows side, you can have a simple batch script dump specific folders to it. 

I would do it with FTP because it is faster.

Instructions here, [http://www.pcreview.co.uk/forums/ftp-xcopy-t2693331.html](http://www.pcreview.co.uk/forums/ftp-xcopy-t2693331.html)

However, if you prefer to do samba, you need to mount the samba share in windows and then you can use this batch script
NOTE: xcopy does not handle large files to well.
You should use robocopy if you experience any problems.

Robocopy is pretty much Microsoft's version of rsync.
[http://ss64.com/nt/robocopy.html](http://ss64.com/nt/robocopy.html)
[http://technet.microsoft.com/en-us/library/cc733145(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc733145(WS.10).aspx)

> 
@echo off

set drive=B:\   <<< drive letter of mounted samba share

set backupcmd=xcopy /s /c /d /e /h /i /r /y

set hour=%time:~0,2%

if "%hour:~0,1%"==" "  set hour=0%time:~1,1%

set folder=%date:~10,4%_%date:~4,2%_%date:~7,2%_%hour%_%time:~3,2%

echo ### Backing up your data

%backupcmd% "C:\PATHTODATA" "%drive%\%folder%\%Username"



the reason I asked if you are in a domain earlier in this was you will need a username and password to mount the windows computer in /etc/fstab. if you have a domain you can just use the domain admin account for each one.

---

### Post by CharlesA on 2011-12-27
The xcopy script would probably work.

I use robocopy for backing up windows machines to a samba share, but that's me. :p

---

### Post by collisionystm on 2011-12-27
> **CharlesA said:**
> The xcopy script would probably work.

I use robocopy for backing up windows machines to a samba share, but that's me. :p



I have an old optiplex a.k.a my 'backup server' lol.
It has a Buffalo  Raid 10 usb storage attached via usb with 2TB of space.
The box runs rsnapshot
My 2 windows boxes are mounted in /etc/fstab
and the others are all linux

The server stores 2 weeks of backups and performs a backup nightly

Really comes in handy when backing up a common samba share because you can put back files that someone deletes. Well all know what a pain the @$$ samba shares are when it comes to deleting files.

---

### Post by daedalo on 2011-12-27
Joo,

Thanks man, your example just shed some light for me, i must confess that i know very little about RAID technology (i know how it work, but never had the chance to mess with it), any advice of how to get that part up to speed ? Any tutorials that you may have used to learn about it?

collisionystm,

All the machines are in one domain but i´m not the network admin and i don´t have permissions to do almost nothing , we are part of a very large Windows network, but we have a lot of issues with backups and very little space on the server for our office... we have another network that i want to use, the problem with this network is that we may only access it wireless ... right now, my idea is to set up the backup server and try my luck doing the backup wireless (sound´s slow, but the alternative it´s not doing backups at all :P). Thanks for the info!

---

### Post by CharlesA on 2011-12-27
> **collisionystm said:**
> 
Really comes in handy when backing up a common samba share because you can put back files that someone deletes. Well all know what a pain the @$$ samba shares are when it comes to deleting files.

Know that well.

There is a "recycle bin" feature of Samba, but I've never used it.

[http://www.samba.org/samba/docs/man/manpages-3/vfs_recycle.8.html](http://www.samba.org/samba/docs/man/manpages-3/vfs_recycle.8.html)

---

### Post by jchung on 2011-12-27
> **daedalo said:**
> Joo,

Thanks man, your example just shed some light for me, i must confess that i know very little about RAID technology (i know how it work, but never had the chance to mess with it), any advice of how to get that part up to speed ? Any tutorials that you may have used to learn about it?

collisionystm,

All the machines are in one domain but i´m not the network admin and i don´t have permissions to do almost nothing , we are part of a very large Windows network, but we have a lot of issues with backups and very little space on the server for our office... we have another network that i want to use, the problem with this network is that we may only access it wireless ... right now, my idea is to set up the backup server and try my luck doing the backup wireless (sound´s slow, but the alternative it´s not doing backups at all :P). Thanks for the info!


I think you need to decide which route you want to go with your client backups:

1. Client / Server - like Bacula, Tivoli Storage Manager, Backup Exec, etc... Where you must setup an specific backup server software which the backup clients connect to and do their backups to.

2. Server less - i.e. Just backup to a directory/filesystem either local or via an SMB share.

#2 is simpler than #1. But #1 will probably provide a lot more features.


Once you decide that, you can start planning your fileserver:

1. How much space do you need?
2. How will the clients access the server?
3. What open source software do you need to install? (Samba, Bacula, etc...)
4. What accounts need to be created.

Now that you have this information, you can decide what level of protection you want? i.e. how many copies of the backups do you keep and what kind of hardware failure do you want to be able to survive?

1. I recommend you keep at least two copies of the backups. I've been bitten in the past by having only one backup copy.

2. I would recommend RAID 6 over RAID 5. I would recommend RAID 10 over RAID 6. Here is a rundown of the RAID levels
[INDENT]
RAID 0 - Stripe across all disks. Full disk capacity. Best performance. NO redundancy. 
RAID 1 - Mirror across two disks. Half disk capacity. Worst performance. Can withstand half the disks (i.e. 1 disk) failing.
RAID 10 - Mirror the disks in sets of two. Then Stripe across the mirrored disks. Half disk capacity. Moderate performance. Can withstand at least 1 disk failure and possibly up to half the disk. Depending on which disks
RAID 5 - Stripe across all disks. If N is the number if disks, the capacity is N-1. 1 disk used for parity data to recover from disk failure. Performance less than RAID 0, but with a good implementation, should be better than RAID 10. Can withstand 1 disk failure. 
RAID 6 - Stripe across all disks. If N is the number of disks, the capacity is N-2. 2 disks are used for parity data to recover from disk failure. Performance is slightly less than RAID 5 if you have a good imeplementation. Can withstand 2 disk failures.
[/INDENT]

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Which you choose depends on your budget and your aversion to risk.

3. I would recommend two file servers. One is the backup of your primary. Again. depends on budget and aversion to risk.


Regarding setting up a RAID:

[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)


Hope this helps.

Joo

---

### Post by rubylaser on 2011-12-27
> **jchung said:**
> I think you need to decide which route you want to go with your client backups:

1. Client / Server - like Bacula, Tivoli Storage Manager, Backup Exec, etc... Where you must setup an specific backup server software which the backup clients connect to and do their backups to.

2. Server less - i.e. Just backup to a directory/filesystem either local or via an SMB share.

#2 is simpler than #1. But #1 will probably provide a lot more features.


Once you decide that, you can start planning your fileserver:

1. How much space do you need?
2. How will the clients access the server?
3. What open source software do you need to install? (Samba, Bacula, etc...)
4. What accounts need to be created.

Now that you have this information, you can decide what level of protection you want? i.e. how many copies of the backups do you keep and what kind of hardware failure do you want to be able to survive?

1. I recommend you keep at least two copies of the backups. I've been bitten in the past by having only one backup copy.

2. I would recommend RAID 6 over RAID 5. I would recommend RAID 10 over RAID 6. Here is a rundown of the RAID levels
[INDENT]
RAID 0 - Stripe across all disks. Full disk capacity. Best performance. NO redundancy. 
RAID 1 - Mirror across two disks. Half disk capacity. Worst performance. Can withstand half the disks (i.e. 1 disk) failing.
RAID 10 - Mirror the disks in sets of two. Then Stripe across the mirrored disks. Half disk capacity. Moderate performance. Can withstand at least 1 disk failure and possibly up to half the disk. Depending on which disks
RAID 5 - Stripe across all disks. If N is the number if disks, the capacity is N-1. 1 disk used for parity data to recover from disk failure. Performance less than RAID 0, but with a good implementation, should be better than RAID 10. Can withstand 1 disk failure. 
RAID 6 - Stripe across all disks. If N is the number of disks, the capacity is N-2. 2 disks are used for parity data to recover from disk failure. Performance is slightly less than RAID 5 if you have a good imeplementation. Can withstand 2 disk failures.
[/INDENT]

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Which you choose depends on your budget and your aversion to risk.

3. I would recommend two file servers. One is the backup of your primary. Again. depends on budget and aversion to risk.


Regarding setting up a RAID:

[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)


Hope this helps.

Joo

These are good steps, and well laid out, except I'd go RAID6. For a backup server it's nice to maximize storage space and still have the guarantee that I could lose 2 disks and still be working.  In the RARE case that 2 disks fail in the same RAID10 mirror, you're hosed.  The only problem I see is that the OP mentioned this.

> **daedalo said:**
> All the machines are in one domain but i´m not the network admin and i don´t have permissions to do almost nothing , we are part of a very large Windows network, but we have a lot of issues with backups and very little space on the server for our office... we have another network that i want to use, the problem with this network is that we may only access it wireless ... right now, my idea is to set up the backup server and try my luck doing the backup wireless (sound´s slow, but the alternative it´s not doing backups at all ). Thanks for the info!

The first problem is that wireless is going to be painful even with a few users if you're creating a decent amount of data daily.  More importantly, it seems as if you're trying to work around the system, because backups don't currently work or work well. Since you're not the network Admin, I'd try to go through the proper channels and make a business case for providing a different backup solution, and the cost / benefit analysis of doing it.

Otherwise, you stand to get potentially burned if/when your personal backup system doesn't work as advertised and someone asks the Admin for further help.  He / She is likely to be very angry at you for not going through the proper channels.  And, depending on the severity of the data lost, could have very negative ramifications on your job.

Just my 2 cents.

---

### Post by CharlesA on 2011-12-27
> **rubylaser said:**
> These are good steps, and well laid out, except I'd go RAID6. For a backup server it's nice to maximize storage space and still have the guarantee that I could lose 2 disks and still be working.  In the RARE case that 2 disks fail in the same RAID10 mirror, you're hosed.  The only problem I see is that the OP mentioned this.

I'd definitely go with RAID 6 in this case. I run RAID 5 on my home machine, but I only have 3 disks and keep daily backups.

> Since you're not the network Admin, I'd try to go through the proper channels and make a business case for providing a different backup solution, and the cost / benefit analysis of doing it.

Otherwise, you stand to get potentially burned if/when your personal backup system doesn't work as advertised and someone asks the Admin for further help.  He / She is likely to be very angry at you for not going through the proper channels.  And, depending on the severity of the data lost, could have very negative ramifications on your job.

Huge +1 there. You don't want to step on toes. ;)

---

### Post by daedalo on 2011-12-27
Thanks for the reply´s everyone!

On side stepping the admins, i also think that it would be better to talk with them, but they don´t seem to care at all, which is the main reason of why i was hired... the order to get a local server comes from the top leadership of the office.

I have tried to contact the Network admins(they are on another location, in another country), but since i was hired to do the job they did´t wanted to do, i guess i´m the enemy for them.

Kind of a uneasy situation here.

---

### Post by collisionystm on 2011-12-27
> **daedalo said:**
> Thanks for the reply´s everyone!

On side stepping the admins, i also think that it would be better to talk with them, but they don´t seem to care at all, which is the main reason of why i was hired... the order to get a local server comes from the top leadership of the office.

I have tried to contact the Network admins(they are on another location, in another country), but since i was hired to do the job they did´t wanted to do, i guess i´m the enemy for them.

Kind of a uneasy situation here.


Okay

Well 2 things

First, on this backup server I will assume your users will not want to see each other's data.
if you decide an FTP method, you can use vsftpd and chroot the users so they cannot leave their own directory.

If you decide to use Samba and mount the windows shares, you will want to require user and pass for shares and build a user account for everyone on the server. As simple as, adduser NAME smbpasswd -a NAME  put a network map script locally on their machine to connect their shares every time they login so they are ready for backing up.
make a drivemap.bat file

make it say


NET USE F: \\Ubuntu/share /PERSISTENT:YES    

^ does not have to be F:

save it and place in the startup folder in their start menu.





Although to be honest this whole thing sounds a bit odd. You would think they might care a little more about what your doing on their network and ask to integrate something in with the existing password system

---

### Post by CharlesA on 2011-12-27
> **collisionystm said:**
> 
Although to be honest this whole thing sounds a bit odd. You would think they might care a little more about what your doing on their network and ask to integrate something in with the existing password system

Aye, it sounds extremely odd. At the very least I would expect using something like Samba and LDAP and having the users store their data on the server and backing up the server instead of each user's machine.

---

### Post by daedalo on 2011-12-27
> **collisionystm said:**
> 
Although to be honest this whole thing sounds a bit odd. You would think they might care a little more about what your doing on their network and ask to integrate something in with the existing password system

It´s odd actually, i can´t go into details, but originally i was hired to be their sysadmin... then i found that there was a team already for that... weird, i would love to tell you the whole history, but this is not the place, if anyone want to know more, send me a PM.

---

### Post by rubylaser on 2011-12-27
> **daedalo said:**
> It´s odd actually, i can´t go into details, but originally i was hired to be their sysadmin... then i found that there was a team already for that... weird, i would love to tell you the whole history, but this is not the place, if anyone want to know more, send me a PM.

Well, ultimately what you choose to do is up to you. You've been presented with a number of good ideas so you have some things to think about.  Personally, it sounds like you're venturing into a hornet's nest.  I'd get your superior to sign off on a document detailing the scope of work that they want you to complete.  That way you will either have proper coverage in the event of a problem, or your supervisor will reconsider and choose to go through the proper channels.

---

### Post by collisionystm on 2011-12-27
Sounds like you were hired to be the sysadmin, but they were out-sourcing their IT to someone else? Am I correct in saying that?
You need to speak with your boss and find out what the heck your supposed to be doing. If you are truly the sysadmin you need to be given all access rights to the servers, and if that interferes with an existing contract, well that is another battle in itself.

---

### Post by CharlesA on 2011-12-27
> **rubylaser said:**
> Well, ultimately what you choose to do is up to you. You've been presented with a number of good ideas so you have some things to think about.  Personally, it sounds like you're venturing into a hornet's nest.  I'd get your superior to sign off on a document detailing the scope of work that they want you to complete.  That way you will either have proper coverage in the event of a problem, or your supervisor will reconsider and choose to go through the proper channels.

Huge +1 to this. Better to cover your butt just in case something goes wrong.

> **collisionystm said:**
> Sounds like you were hired to be the sysadmin, but they were out-sourcing their IT to someone else? Am I correct in saying that?
You need to speak with your boss and find out what the heck your supposed to be doing. If you are truly the sysadmin you need to be given all access rights to the servers, and if that interferes with an existing contract, well that is another battle in itself.

Agreed. It sounds like a nasty predicament.

---

### Post by daedalo on 2011-12-28
> **collisionystm said:**
> Sounds like you were hired to be the sysadmin, but they were out-sourcing their IT to someone else? Am I correct in saying that?
You need to speak with your boss and find out what the heck your supposed to be doing. If you are truly the sysadmin you need to be given all access rights to the servers, and if that interferes with an existing contract, well that is another battle in itself.

Long read after this point...

We are an small office, a branch of a large company, this small office is located on a new market for the company, when i was hired i found that another team had already installed the network and in theory they were in charge of everything IT related, but due to excessive work or the distance, they were unable to help the users in this office... which has lead to a LOT of problems, after seeing this I thought that i was going to be the "bridge" between the IT team and the users here ... then i found that i was hired without the "blessing" of the IT team, and they were very very angry about it.

I tried to fix the relation and actually one of them ended being a good friend but sadly he resigned a month ago... my guess is that since there was no IT personal in this location and lots and lots of issues, they just hired someone to fix everything , even things that they were not cleared to handle, so... right now my bosses here expect me to fix and deploy all they need and my position is not acknowledged by the IT guys.

Messy situation if you ask me, as long as i know, i have managed to get things done and to avoid more hurt feelings.

On the options, thank you guys! I´m going to start testing, also thank you for your opinions about the odd situation, you have me thinking in other ways to approach to the IT team :/ .

---

### Post by CharlesA on 2011-12-28
Good luck with testing. It doesn't sound like a situation I would like to be in.

Too bad the other IT guys don't want to work with you, that would help immensely in getting a working solution in place - something that would work with the current network, etc.

---

