---
title: "LAMP/File Server with RAID; changing default directories"
date: 2006-06-12
forum: Server Platforms
---

### Post by timbellomo on 2006-06-12
Hey Everyone,

OK, here's the scoop.  I performed a LAMP install, and then followed most of the "Perfect Setup" from ISPConfig's website (i'm basically just running it to host my own hobby sites - if you have a better recommendation, let me know).  Everything's working just fine.  So, of course, now I've got to take it to the next level.

I configured a software **RAID 5 on a 4x250GB** array (IDE).  I formatted as ext2 (Just a guess...)

**Question 1**. Should I be using a **different filesystem?**  FYI, I'm going to be setting up Samba to be able to use this as a file backup server on a network with Windows machines.

**Question 2**. Now that everything is set up, how can I **change the default web folder in apache2 and the default database location in mySQL**.  Basically, I want all of my data to reside on this RAID; if things hit the fan, I want to know that my data is safe (don't worry, I'll be making DVD backups as well).  I figure that it would be easier to manage if my sites could be "hosted" directly from the RAID.

Any advice would be greatly appreciated.

I'm new(er) to Linux, but I'm becoming a huge proponent of Ubuntu because the community is **so **great.  Thank you all so much for the help you've given me in the past (as a lurker).

-Tim

---

### Post by Soleil-Raid on 2006-06-12
[QUOTE=timbellomo]Hey Everyone,
I configured a software **RAID 5 on a 4x250GB** array (IDE).  I formatted as ext2 (Just a guess...)

**Question 1**. Should I be using a **different filesystem?**  FYI, I'm going to be setting up Samba to be able to use this as a file backup server on a network with Windows machines.
[/QUOTE]

While there's nothing 'wrong' per se with ext2, there are much better filesystems out there. I'd use ext3 as a bare minimum, but really, you'd want to use XFS or JFS. These have things like ACL (access control lists), journalling (you want this, trust me) and the ability to grow the volume size. If you're going to have really big files that you change a lot, go with XFS, otherwise, I'd reccomend JFS. Avoid reiserfs. (explanation at the bottom).

If you intend to stick more hard drives in at some point, look into installing LVM on top of the RAID5 array, then XFS or JFS on top of that.

> 
**Question 2**. Now that everything is set up, how can I **change the default web folder in apache2 and the default database location in mySQL**.  Basically, I want all of my data to reside on this RAID; if things hit the fan, I want to know that my data is safe (don't worry, I'll be making DVD backups as well).  I figure that it would be easier to manage if my sites could be "hosted" directly from the RAID.


For apache, edit the document root of your various websites, and for mysql, a symlink to the right location will do it. If you're RAID5 is on /RAID, then something like the following would be in order.

sudo /etc/init.d/mysql stop
sudo mv /var/lib/mysql /RAID/
sudo ln -s /RAID/mysql /var/lib/mysql
sudo /etc/init.d/mysql start

This shuts down the mysql server, moves the MySQL directory to the RAID volume, makes a link from where MySQL expects to find the MySQL folder to it's real location, and restarts the MySQL server.


Filesystem stuff:
In the even of a system crash, or power failure, Journaling speeds up the process of fixing up in the broken files. Ext2 is not journalled, Ext3 is ext2 with an effective (but slow) journal built on top of ext2. If you have Ext2, and the power fails, you could literally be waiting hours (perhaps longer on a big array) before the system is usable again as the system goes through and checks every single node on the disk.

Further explanation: [http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

Reiserfs, XFS, and JFS all have Journaling built in.

I personally reccomend against Reiserfs, because my experiances and anecdotal evidence from other sys-admins has led me to believe that it likes to corrupt data after a while.

JFS was made by IBM, and XFS was made by SGI. This is reflected in their focus. My understanding is that JFS is geared towards to having lots and lots of little files on big arrays (think workgroup/email server), where as XFS is geared to having lots of big files on gigantic arrays (think video editing). You probably want JFS.

Hope this is helpful.

---

### Post by timbellomo on 2006-06-12
Sounds good; I'll look into LVM and probably end up with JFS.

I do have a question about Apache still, though; is there a global place to make this change?  Or do I have to change it in every website individually?

A side note about symlinks:
So just to make sure I understand this correctly -- a symlink will make the system think that files exist somewhere, but it's really just a pointer to another folder?  Since this will be my file server as well, I'll be storing all of my photos on it, in say /RAID5/photos.  Will a symlink allow me to tell Gallery (or some other photo gallery software) to look for images in the website's directory (say... /RAID5/www/site1/photos) and have that just be a symlink to /RAID5/photos?  Are there permission issues that I have to address?  Was that even a coherent question?

Thanks!

---

### Post by Soleil-Raid on 2006-06-12
[QUOTE=timbellomo]Sounds good; I'll look into LVM and probably end up with JFS.

I do have a question about Apache still, though; is there a global place to make this change?  Or do I have to change it in every website individually?

A side note about symlinks:
So just to make sure I understand this correctly -- a symlink will make the system think that files exist somewhere, but it's really just a pointer to another folder?  Since this will be my file server as well, I'll be storing all of my photos on it, in say /RAID5/photos.  Will a symlink allow me to tell Gallery (or some other photo gallery software) to look for images in the website's directory (say... /RAID5/www/site1/photos) and have that just be a symlink to /RAID5/photos?  Are there permission issues that I have to address?  Was that even a coherent question?

Thanks![/QUOTE]

The apache question... If you set a DocumentRoot, then anything under that DocumentRoot location on the filesystem will work. If you have Virtual servers, then you'll need to do those seperatly.

With symlinks, these are transperantly followed by all applications, but if you want to see if a given file is a symlink, you can. Apache by default (I think) has it's Options set to not follow symlinks for security reasons, although this can be overriden.
See: [http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

---

### Post by timbellomo on 2006-06-13
NOTE:  The moving of mysql was catastrophic for me.  It stopped being able to start (problem finding mysqld.sock).  I removed, purged and reinstalled.  Now I'm stuck with Access not granted errors to root@localhost (even though I tried new and old passwords.)

I'm going to be reinstalling Dapper; starting fresh.  Don't worry, there was nothing important in it yet; just time.

-Tim

---

### Post by Soleil-Raid on 2006-06-13
[QUOTE=timbellomo]NOTE:  The moving of mysql was catastrophic for me.  It stopped being able to start (problem finding mysqld.sock).  I removed, purged and reinstalled.  Now I'm stuck with Access not granted errors to root@localhost (even though I tried new and old passwords.)

I'm going to be reinstalling Dapper; starting fresh.  Don't worry, there was nothing important in it yet; just time.

-Tim[/QUOTE]

Darn. That worked for me...
It's really odd that mysqld.sock should have issues with that, given that mysqld.sock is found in /var/run/mysqld/
Where the permissions okay for mysqld to access the directory the RAID was mounted on, and did mysql actually stop?

---

### Post by timbellomo on 2006-06-13
I wouldn't know where to begin... I'm unfamiliar with these things... a bit over my head as usual; but a catastophic event (relatively) forces me to learn more.  But thanks for your help anyway.  I'm sure I just messed something up... I think I restarted mysql before changing some reference to the directory in my.cnf -- but I couldn't tell you for sure.

-Tim

---

### Post by LordHunter317 on 2006-06-13
[QUOTE=Soleil-Raid]If you're going to have really big files that you change a lot, go with XFS, otherwise, I'd reccomend JFS. Avoid reiserfs. (explanation at the bottom).[/quote]Uhh, XFS performs as well, if not better than JFS, in virtually all access categories in real benchmarks.

> If you intend to stick more hard drives in at some point, look into installing LVM on top of the RAID5 array, then XFS or JFS on top of that.That really won't help him.  There's no completely safe way to resize a software RAID in Linux.  

> 
I personally reccomend against Reiserfs, because my experiances and anecdotal evidence from other sys-admins has led me to believe that it likes to corrupt data after a while.Reiser did have corruption issues, back in early 2.4 (.8-.16 or so).  It doesn't now.  However, reiser v3 still has massive performance problems on full filesystems, and the recovery tools are still the worse of the lot.

But hey, XFS had some corruptions issues from about 2.6.8-2.6.12 or so, so if you're worried about driver bugs, use ext3.

> This is reflected in their focus. My understanding is that JFS is geared towards to having lots and lots of little files on big arrays (think workgroup/email server), where as XFS is geared to having lots of big files on gigantic arrays (think video editing). You probably want JFS.No, both do small and large files equally well.

[quote=timbellomo]I do have a question about Apache still, though; is there a global place to make this change? Or do I have to change it in every website individually?[/quote]Ulimately, DocumentRoot can be set at the VirtualHost level, so yes, you'll be changing it at this level.  There's no way to enforce a global DocumentRoot.  Even if you could, you can use Alias to bring in whatever you want from the filesystem.

---

