---
title: "How to backup data form ubuntu server trough network.."
date: 2007-05-28
forum: Server Platforms
---

### Post by cas_merican on 2007-05-28
**I need help...show me step by step how to conduct backup data from ubuntu server trough **remote.:popcorn:

---

### Post by turinglabs on 2007-05-28
There are many ways to backup data on a network. 

It would help if you would clarify your question  - what type of network (LAN, WAN?), what or how much are you backing up (text or data files, raw disk partitions?), what media are you backing up to on the target system (disk, tape?), do you need full backups every time or periodic, partial backups of just what has changed since the last backup (incremental)?

---

### Post by cas_merican on 2007-05-29
i gonna use lan..i will remote using other pc...backup the whole partitions.i am kindda new with this ubuntu server...

---

### Post by Wim Sturkenboom on 2007-05-29
Your question is still not clear.

Do you use the remote connection only to access the server or do you want to pull files over to another machine?
Do you access your server over the internet or just on a local network?

---

### Post by cas_merican on 2007-05-29
i use putty and trough internet...where i can access the server..from that,i would to make backup and store to my pc..could it be done?

---

### Post by shibu on 2007-05-29
1.First create backup

tar -cvzf  filename.tar.gz  DIR-TO-BACKUP

replace DIR-TO-BACKUP  with the dir that you would like to backup.

2.Copy filename.tar.gz to web access folder and download the backup created to your pc.

or if you are using Linux as both server and your desktop with static IP then try this from the sever.

rsync -avz --exclude=/proc -e ssh / root@backup-pc-ip-address:/root/

---

### Post by cas_merican on 2007-05-29
this will back up all the partion of the hardisk?am i right..i just follow the step...

---

### Post by cas_merican on 2007-05-29
actually how can i make backup for all partation?i mean the code for it..

---

### Post by Chayak on 2007-05-29
[Linux Reality Backup episode]("http://media.libsyn.com/media/linuxreality/linuxreality063.ogg")

Take a listen to this podcast.  He covers backups in this one.

---

### Post by shibu on 2007-05-29
To backup your entire server to another linux server run this as root on your server.


rsync -avz --exclude=/proc -e ssh  /   root@backup-pc-ip-address:/root/

replace  /root with the directory where you would like place the backup. Check up backup providers such as bqbackup, let me know if this works for you   ?

---

### Post by Brazen on 2007-05-29
Did you use LVM for your for your partitioning?  Your backups will be a lot more reliable if you quiesce your disks and take a snapshot to back up.  You'll need LVM for the snapshot and XFS can quiesce the file system.  I'm not sure if there is a way to quiesce an EXT3 file system, but with EXT3's journaling, it may not be quite as necesary.  Also, if your server includes a MySQL database, you'll want to do a mysqldump to dump the databases to a file that is suitable for backing up.

---

### Post by Brazen on 2007-05-29
Also, if you installed it in a VMWare virtual machine, the VMWare server has tools for snapshotting the virtual machine from the command line which would make very reliable and very easy-to-restore backups.

---

