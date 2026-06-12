---
title: "rsync"
date: 2008-11-05
forum: Server Platforms
---

### Post by baudday on 2008-11-05
Hi,

I came across this article-- [http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/](http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/) -- about how to set up rsync to back up a windows pc. I'm just wondering if rsync is a good option for this. Thanks.

---

### Post by MJN on 2008-11-05
Sure - I used to use it regularly to backup Windows PC's over the Internet. Admittedly I chose it mainly because I was already using rsync extensively in my Linux environment and hence an already-proven solution was of real benefit.

I used the [cwrsync]("http://www.itefix.no/i2/node/10650") Rsync/cygwin package installed as a client on the Windows PC's.

Incidentally, unlike the guide you linked to I run rsync over SSH as opposed to a service daemon as these machines already had shell access (and hence the native security requirements were already satisfied).

Mathew

---

### Post by oblivian on 2008-11-05
Hi,

Well, yes and no.

We backup up approx. 25 WinXX/Vista/Linux/OSX machines using Ubuntu and BackupPC. Either using SMB or DeltaCopy (Rsync). It works very well, except DeltaCopy can't backup open files on WinXX clients. Still, I whole-heartedly recommend this solution. Rsync is wonderful, especially when backing up remote clients over SSH.

BackupPC is a very mature backup/management/solution. It lacks a dedicated Win client that support shadow copy, like Bacula, but apart from that it kicks ***.

Or just use the Rsync Daemon of course... With DeltaCopy you can schedule each client to contact and backup to the Rsync daemon/server, while BackupPC works the other way around and contacts each client at a set of schedules. DeltaCopy support rsync over SSH.

BackupPC:
sudo apt-get install backuppc

DeltaCopy: (Win)
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

Alternatively: (Win)
[http://mobassh.mobatek.net/en/](http://mobassh.mobatek.net/en/)
(Backup using Rsync and SSH over a remote Internet connection)

Or use the CygWin option. Both DeltaCopy and MobaSSH is built on CygWin, but containing just the stuff you need.


Cheers,

Obi

---

### Post by MJN on 2008-11-05
Ooh I like the sound of the DeltaCopy client tool. One problem I always faced was the inevitable user-unfriendliness of a command-line rsync running in cygwin as many users were not comfortable customising the backup scripts if file/schedule changes were ever required (I invariably did it for them - admittedly this was beneficial for many cases) but DeltaCopy could well prove valuable should I ever need to do this again.

Mathew

---

### Post by baudday on 2008-11-05
I'm a bit confused, I don't know all the terminology.

I know a daemon is something that constantly runs, so are there two different ways you can use rsync? (daemon or ssh)

Is DeltaCopy used on the server side or the client side? I'm sorry if I seem like I have no idea what's going on, I kind of don't with this...

I guess if you could just answer how a setup using Rsync and DeltaCopy would work exactly. What would I install where and how would it work?

---

### Post by baudday on 2008-11-06
Can anyone help me out?

---

### Post by oblivian on 2008-11-06
Well, Rsync is both a "server" and a client. You can use rsync to sync local directories to a remote rsync server (daemon) and vice versa.

Same with DeltaCopy which basically is rsync ported to Windows. You can either run it as a server (daemon) or as a client, depending on what suite your needs best.

---

### Post by baudday on 2008-11-06
So it would make sense to run Rsync on my server and DeltaCopy on the windows computer?

---

### Post by koenn on 2008-11-06
deleted

---

### Post by koenn on 2008-11-06
> **baudday said:**
> So it would make sense to run Rsync on my server and DeltaCopy on the windows computer?

yes.
The easiest is to 
- run rsync as daemon on the server
- use DeltaCopy on the Windows computers to send files to the server
When you install Deltacopy, it installs both a server (daemon) you use only the client in this scenario.


Alternatives:
1/
In stead of rsync in daemon mode you can use ssh to let DeltaCopy send files to the server, but this requires you set up ssh with public key authentication. Password authentication won't work.

2/
You might run DeltaCopy server on the Windows machines and let rsync on the server pull the backups. I think it's at least theoretically possible, but I haven't tried it.
 This is probably more manageable (all schedules can be managed centrally) but it's harder to set up or to secure : you need DeltaCopy server running on every machine you want to back up, while you don't want any rogue rsync user being able of copying files at will from the machines in question.

---

### Post by oblivian on 2008-11-06
> **koenn said:**
> 
2/ You might run DeltaCopy server on the Windows machines and let rsync on the server pull the backups. I think it's at least theoretically possible, but I haven't tried it.
 This is probably more manageable (all schedules can be managed centrally) but it's harder to set up or to secure : you need DeltaCopy server running on every machine you want to back up, while you don't want any rogue rsync user being able of copying files at will from the machines in question.
Yes, this is possible. In fact this is what we do at our data center. Each Windows client has DeltaCopy installed running in server mode, while an Ubuntu server centrally polling data from each client at certain scheduled times. As mentioned earlier we use BackupPC on the Ubuntu server to manage the backups. BackupPC support rsync, rsyncd, tar and SMB to transfer/poll data. The great thing with BackupPC is that it uses a pooling/compressing system to store files.

# A clever pooling scheme minimizes disk storage and disk I/O. Identical files across multiple backups of the same or different PCs are stored only once resulting in substantial savings in disk storage and disk I/O.
# One example of disk use: 95 latops with each full backup averaging 3.6GB each, and each incremental averaging about 0.3GB. Storing three weekly full backups and six incremental backups per laptop is around 1200GB of raw data, but because of pooling and compression only 150GB is needed. 

[http://backuppc.sourceforge.net/info.html](http://backuppc.sourceforge.net/info.html)

---

### Post by happyhacker on 2009-01-06
I tried using backuppc smb but it would never connect to windows. So I am downloading cygwin. It seems a huge file (taking a long time to download it's files. Should I be using DeltaCopy instead?

---

### Post by oblivian on 2009-01-06
If it is rsync for Windows you are after, you just need DeltaCopy. CygWin is so much much more...

[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp]("http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp")

---

### Post by happyhacker on 2009-01-07
Does this integrate with backuppc (using the backuppc rsync option) and/or standalone? I have rsync running on the server so this looks a good idea. I also have synctoy backing up to ubuntu.

Can DeltaCopy be invoked from the rsync on the server?

---

### Post by oblivian on 2009-01-07
Use BackupPC to poll from the Windows Client.

On the Windows client, set up DeltaCopy in server mode (Rsync daemon) and set BackupPC to poll from the Windows client via rsyncd in transfer mode setup in BackupPC.

Note: In paths in BackupPC, don't have a forward slash (/) when backing up from Windows client. Just the the rsync share name. I.e If you share the C:\ disk with rsync, in BackupPC the path is simply: c (or what ever you name the share).

As opposed to rsync via SSH where you have to enter the complete system path.

Regards,

Oblivian

---

