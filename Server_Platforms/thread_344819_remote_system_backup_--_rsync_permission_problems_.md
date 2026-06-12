---
title: "remote system backup -- rsync permission problems / dirvish / dd"
date: 2007-01-23
forum: Server Platforms
---

### Post by irlkersten on 2007-01-23
Hello everyone!

I've been trying to create a backup solution for a small server I have since about 2 days solid and have come to a dead end. It's server running edgy that I have only remote access to and I wanted to backup the entire system to another server, so in the case of a harddisk failure, the harddisk could be replaced and I could do my restore.

The backup server I am using is also a linux server, but not dedicated, and I do not have root access to it. I do, however have root access to my edgy server.

I have tried to create a backup using rsync(as root),with this comand:

> 
rsync --progress -catlrpAogDzH --delete --devices --exclude=/proc --exclude=/var/cache/apt/archives/*.deb -e ssh /  [email]backupuser@ backupserver .com:/home/backup/


It worked great and allowed for incremental backups, but because I don't have root access on the backup server, the file ownerships were all set to backupuser. Thus, when I tried to restore, it failed.

The next idea I had was to use dd to make an entire disk image, and pipe that over ssh to the backup server to a diskimage file. That also worked, but I realised that I cannot do this because data on the server is changing, and could mess up the image to easily.

I've thought of using SystemImager but that needs to be installed on the remote machine - so that's a no go. I've attempted to use dirvish on the dedicated server by mounting the remote server via fuse and sshfs, but the server seemed to have great difficulties with that, and transfer speeds were worse than dialup.

I managed to get dirvish working on the remote server, but that would have would have meant that I needed to enable remote root login, and that didn't seem like an option to me.

I also looked into creating snapshots of the filesystem so that I could use the above dd solution, but didn't have much luck. I only came across this:

[http://linuxdevices.com/articles/AT8994481913.html](http://linuxdevices.com/articles/AT8994481913.html)

It basically says that snapfs would have worked, but only exists for the 2.2 kernel, and that their solution was experimental. The only way for me to do it would be via LVM, and I can't do that because I the server is partitioned already. The rescue system ( a live cd of some sort) will only allow me to reinstall the server image, so I can't change the partition / filesystem types. hda1 - ext3 and hda2 - swap.

I would really appreciate any ideas or comments you may have to the above attempts. Of course if any you have any suggestions on a solution, you'd make me the happiest ubuntu server (wannabe) admin! :-P

Regards,

Tim (irlkersten)

EDIT: I also found this, but figured it's not much use to me: [http://www.ubuntuforums.org/showpost.php?p=943177&postcount=11](http://www.ubuntuforums.org/showpost.php?p=943177&postcount=11)

---

### Post by dannyboy79 on 2007-01-23
my signature may have your answer. partimage can backup entire partitions to an image over a network. a question I have is, you stated that your rsync files were all owned by backupuser, why don't you simply add this user to your admin group or just give him the correct permissions on your machine? i use sbackup for my backups.

---

### Post by irlkersten on 2007-01-23
Thanks! I'll check out partimage.

The backupuser is the username I use to get access to the backup server. I don't have any other access... so I can't add that user to the admin group -- this is my big problem -- not being able to have admin access to the backup server also means I can't install any programs on it... I can only run software that doesn't require installing, or is pre-installed.

Maybe there is some sort of way to install programs as a normal user in a chroot or something - I don't know anything about this and should probably look into it :-)

I would use another dedicated or VPS, but as a backup solution that's too expensive for me because I'm a student in college and am only learning at present.

---

### Post by irlkersten on 2007-01-23
Ok, I've taken a brief glance at partimage and it looks nice, but I don't have physical access to my server, and in order to use partimage over the network, the backupserver needs to have partimage-server installed, and once again, I don't have admin permissions :-(

---

### Post by irlkersten on 2007-01-23
Do you think it's possible to make rsync use an archive on the backup server? (I.E. many files on the client server => single archive on backup server). That way the permissions would still be preserved, as they would be inside the archive. Does that even make sense???

Or is it possible to pipe a tar file to rsync? That way, a single file will be rsynced and the permissions inside the tar archive would not be lost on the backup server. I understand that I could make a tar archive of the entire file system and then rsync that tar file, but I don't have enough space on the server to do this. Hence it must be piped so that it can go straight over the network to the backup server.

I have searched for all kinds of solutions and can't seem to find any. If I'm looking in the wrong direction, please let me know so that I might make more use out of my time.

My last attempt was to setup the server with LVM and use it's snapshot feature, but since I don't have physical access to it, this proved rather hard. I managed to partition the hard disk, with a /boot partition and an lvm partition, a volume group and logical volume, but could not figure out how to install ubuntu onto it. This was all done in rescue mode which is no more than a live cd that I have ssh access to...
[http://rescuecd.sourceforge.net/](http://rescuecd.sourceforge.net/)

The cd supports ext2/3, jfs and reiserfs. To the best of my knowledgy, ext3 does not support snapshots without LVM. I failed to find if jfs or reiserfs have snapshot capabilities.

I'm hopelessly stuck and have run out of ideas :-( 

Help?

---

### Post by dannyboy79 on 2007-01-24
> **irlkersten said:**
> Ok, I've taken a brief glance at partimage and it looks nice, but I don't have physical access to my server, and in order to use partimage over the network, the backupserver needs to have partimage-server installed, and once again, I don't have admin permissions :-(

partimage doesn't require you to install anything. you would download knoppix or whatever has partimage on it. boot YOUR computer using that disc, than run partimage and backup your partition as an image to the backupserver. 

what I said about adding backupuser to the admin group, I meant on you machine! if your files reside on the server which you don't have access to as the user backupuser, than can't you simply create that user on YOUR machine and add him to the admin group. What exactly is happening when you try to restore files from the server??? What is the error you are getting???? Maybe that's why I am not understanding what you issue is?

---

### Post by MJN on 2007-01-24
The problem is simply that if he's backing up a file owned by, say, root on machine 1 then when rsync plonks a copy on machine 2 it tries to also make it owned by root but fails given that rsync doesn't have the permission to make files owned by root on machine 2!

To put it bluntly, the only way rsync can preserve ownerships etc is if it's run as a super user.

I'm not sure of the way round it to be honest, other than perhaps to use a different backup strategy than rsync. Of course, with rsync gain advantage from it only transferring files that have changed, however any solution that packaged files up beforehand (e.g. tar the whole drive on machine 1) would not be able do anything like this.

I'm not sure of your exact circumstances but can you make the backup to a machine that you *do* have SU access to? Your own for example?

Mathew

---

### Post by irlkersten on 2007-01-24
First of all, thank you both for replying!! It makes such a huge difference getting some feedback after struggeling for so long :-)   I truely appreciate it!

> The problem is simply that if he's backing up a file owned by, say, root on machine 1 then when rsync plonks a copy on machine 2 it tries to also make it owned by root but fails given that rsync doesn't have the permission to make files owned by root on machine 2!

This is exactly it.

I was thinking of making a backup to a computer at home (that I have SU access to) but my network connections are terribly slow and it would take forever. Also I am keen on making it an automated solution. For now, I will use the following solution:

Mirror the entire filesystem with rsync to a "BACKUP_SNAPSHOT" folder on the same drive. This means that when I backup files to that folder, it will be fairly fast -- something like a true filesystem snapshot. This is because I'm worried that if the backup takes too long, the files will be semi-changed before they are backed up as the system is still live.
I know it's not a true snapshot, but I'm hoping it comes close.
I will then pipe the "BACKUP_SNAPSHOT" folder through tar/gzip and across ssh to the backup server. In this way the permissions will be kept as they are now inside an archive. I know this is bandwidth intensive, but that doesn't matter much in my case.

The main disadvantage of this method for me is the fact that the filesystem is mirrored and I have limited space. I guess I will have to make do though. What would be very cool would be a compressed folder as the backup_snapshot folder, but I can't find anything on it. I was thinking along the lines of fuse and encfs, except for compressing instead of encrypting. I've heard of cramfs, but got the impression that one would need a seperate partition for it.

> partimage doesn't require you to install anything. you would download knoppix or whatever has partimage on it. boot YOUR computer using that disc, than run partimage and backup your partition as an image to the backupserver.

I probably misread that information when I first looked it up. I had thought that a partimage-server was needed on a remote machine in order to backup the image over a network. My bad. I still can't use it as a solution though, as it requires me shutting down the server, and since it's a webserver, I don't want to do that. I'm looking for a backup method that will provide me with daily backups of the live system.

---

### Post by MJN on 2007-01-25
Sounds like you're on to as good a solution as you can expect to get in the circumstances.
 
Just a quick note on your limited bandwidth home (I know you said it's got other drawbacks such as lack of automation) but remember that rsync not only just transfers files that have changed but also just the *parts* of those files that have changed.
 
In my case I have around 60GB of data (the majority are from digital photos hence it soon racks up) to backup and given the sentimental nature I back these up locally as well as off-site to my brothers machine. Upload speed is, as always, somewhat limited (384bkps compared with 8mbps down!) however in practice it works very well given that only the changes are transferred and, on a day-to-day basis, this isn't all that much. Of course it helps that my machine is always on hence it is all done automatically and doesn't really matter how long it takes.
 
You mentioned about long backups potentially missing out on some changed files - this does happen, quite often in fact, for me. Rsync mentions at the end of its run that some files had changed (or even disappeared) between doing the first 'scan for changes' and actually transferring them over. However I've never had any trouble with this - indeed I consider the warning as more advisory/info as I don't believe it could have any detrimental effect. In the majority of cases I suspect it is logfiles as I can't think of much else that might change so rapidly (the only other rapid-changing aspect to the server is users' mail but as I use Maildir each message is stored in a seperate file so again it wouldn't matter here).
 
Do let us know how you get on in practice, as I'm sure this particular issue (no root access) comes up from time-to-time.
 
Mathew

---

### Post by irlkersten on 2007-01-25
Having a machine that's always on at home is a good idea, and I've been meaning to do it in a long time. It's just a matter of time before I do get it. I'm glad it's so efficient with rsync. I may need to look into it further. For now I will try what I explained above, but I'll let you know in due time how will this works for me. I have aleady done an entire restore, wiped the hdd, booted into rescue mode, and restored the files and it worked flawlessly, so I'm happy for the moment. I'm glad that missing files don't seem to be a problem. :-)
I'm going to ask my backup host nicely if they'll run an rsync cron job for me as root, and I'll give them scp access (no shell). That would solve it completely :-P

Anyways, like I said, I'll keep you posted, and thank you for all the help!!

Tim

---

### Post by MJN on 2007-01-25
> **irlkersten said:**
> I'm going to ask my backup host nicely if they'll run an rsync cron job for me as root, and I'll give them scp access (no shell). That would solve it completely :-P
 
That'd be good.
 
However, they'll need shell access in order to run rsync - it runs over ssh and not scp (you could always run rsync as a daemon however you're better off not). Worry not though - you can restrict their shell access to running *just* rsync using the **forced-commands-only** SSHD option (i.e. they can't just login and do anything). There is a good guide on how to do this at [http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html).
 
Mathew

---

### Post by dannyboy79 on 2007-01-25
> **MJN said:**
> The problem is simply that if he's backing up a file owned by, say, root on machine 1 then when rsync plonks a copy on machine 2 it tries to also make it owned by root but fails given that rsync doesn't have the permission to make files owned by root on machine 2!

To put it bluntly, the only way rsync can preserve ownerships etc is if it's run as a super user.

 

Well than his first thread is completely written incorrectly!! He specifically states that he is able to back-up his server, it's just that the files are owned by backupuser on the remote non-dedicated, non-being able to run any program as root server. So when you want to restore the files why can't you just restore them???? if you add backupuser to your system and add hiim in the admin group you'll be able to rrestore them wouldn't you?? So there is obviously poor communication here as you have explained your problem differently to different people. If my above idea isn't valid (please explain why it's not) than sbackup works awesome, that's what I use and you don't need root access to the remote server. it backs everything up into a nice litttle tar file. it can be run on a running system. you can chose exactly what you want backed up with a gui. it's really a great program!  

for your problem, at least you have the files backed up correct???? despite them being owned by backupuser. couldn't you restore them and just chown and chgrp them? i guess I don't know how rsync works. when you want to retrieve your files from a remote server, does rsync have to be running on the remote server? if so, are you saying that it has to be running as root? this sounds like a silly solution than to use for backing up to a server you can't run sudo on!!!! why would you do this then????? can't rsync pull files from a server, rsync would still be running as root on YOUR machine wouldn't it? I guess I can't help with rsync.

---

### Post by MJN on 2007-01-25
> **dannyboy79 said:**
> Well than his first thread is completely written incorrectly!!
 
No it wasn't - I understood what he meant. Admittedly it's a complex issue but no need to get worked up about it! :)
 
> He specifically states that he is able to back-up his server, it's just that the files are owned by backupuser on the remote non-dedicated, non-being able to run any program as root server. So when you want to restore the files why can't you just restore them???? if you add backupuser to your system and add hiim in the admin group you'll be able to rrestore them wouldn't you??
 
As he stated it's not so much the backup stage that highlights the problem - sure the files are tucked away nicely on the backup server. However, and this is the gotcha that tends to only manifest itself come restoration time, the backed up files no longer have their correct ownership permissions set - they're all owned by whatever the user was that rsync ran as (unless it was root, which it can't be as discussed, in which case the owners would all be untouched).
 
Hence, when the system is restored the ownership permission are not correct - more specifically they are not the same as the original state hence this falls foul of backup rule #1. Perhaps this isn't so bad for a bunch of photos, but for the security of system files it is unacceptable.
 
> If my above idea isn't valid (please explain why it's not) than sbackup works awesome, that's what I use and you don't need root access to the remote server.
 
Relax. Noone said your idea wasn't valid - indeed I didn't comment at all on the proposal, I just explained what the problem was in direct response to your final question '*Maybe that's why I'm not understanding what your issue is?'*
 
> for your problem, at least you have the files backed up correct???? despite them being owned by backupuser. couldn't you restore them and just chown and chgrp them?
 
In theory, yes, you could. But in practice how does he know what the proper ownership details are for every file, all 100,000 of them?
 
Again, your sbackup idea may be the ideal solution but that wasn't what I was discussing.
 
Mathew

---

