---
title: "Storing MySql on a Separate Drive"
date: 2007-07-26
forum: Server Platforms
---

### Post by josh.b on 2007-07-26
Hey All,

I'm a brand new Ubuntu user, I'm setting up a server environment to host my own sites.

I'm wondering if anyone can help me out with this, on my Dapper Server box I have a 200 G Hard drive (where the system is installed) and a 320 G spare drive that until now I've always used for storage.

What I'd like to do is store my database there so it will have plenty of room to grow.

Anyone that can get me started with the process, I would certainly appreciate it.

Josh

---

### Post by kidders on 2007-07-28
Hi there,

Doing this might take a little planning, because you'll have to shut down your MySQL server ... which would presumably break lots of services you're hosting. The process itself is simple enough, really...[LIST=1]
[*]Do some reading, and choose a suitable filesystem type for your MySQL database. Since your new filesystem will contain nothing else, you have an opportunity to tailor it precisely to your SQL server's needs, in terms of performance, storage efficiency & reliability ... things that some filesystems are better at than others.
[*]Become root, and use a good, reliable tool (eg **cfdisk**) to erase your spare disk's partition scheme, and re-create it to suit it's new purpose in life. Don't allocate space to your databases unnecessarily ... ie if 200GB is enough for your foreseeable needs, then feel free to leave 120GB unallocated.
[*]Run **partprobe** to re-scan your partition tables without having to reboot. (Do not skip this step.)
[*]Use the appropriate **mkfs** tool to create your chosen filesystem. If (for the sake of argument) you use mkfs.xfs, check out it's man page for how to set a filesystem label. These can be really useful, but not all "mkfs" utilities do it the same way. Take the opportunity to examine some of your other advanced choices, such as filesystem block sizes, etc.
[*]Mount your new filesystem somewhere (eg /mnt/database).
[*]Do an **ls -ld /var/lib/mysql** and use **chmod** and **chown** to match your new filesystem root's permissions & ownership exactly to those of your current /var/lib/mysql. Inconsistencies will either wreak havoc with your database server, or open security vulnerabilities.
[*]Shut down your MySQL database server. (Do not skip this step either!) If you like, do an additional **lsof | grep /var/lib/mysql** to double-check that nothing on your system is still using any of the files that make up your database.
[*]Do a **cp -dpR /var/lib/mysql/* /mnt/database**
[*]Now, move your original database to one side (rather than deleting it), until you've had a chance to be 100% sure nothing has gone wrong. I suggest something like **mv /var/lib/mysql /var/lib/mysql.old**
[*]Recreate /var/lib/mysql.
[*]Touch a file called something like "/var/lib/mysql/.DONOTSTART". I'll get back to this.
[*]Unmount /mnt/database, and modify your /etc/fstab to have that filesystem mounted at /var/lib/mysql.
[*]Do a **mount -a** and check that your databases are where they should be. Pay particular attention to the permissions. It is critically important that you not restart your database server unless everything is *exactly* as it should be.
[*]Restart your MySQL server, keeping a close eye on your system logs, to make sure your server had no reason to complain about anything.[/LIST]Off the top of my head, I don't *think* I've forgotten anything ... this list certainly got a bit long-winded (lol), but I'm not altogether sure how much step-by-step detail you need. It sure feels like a long time since I wrote "The process itself is simple enough" hehe!! If you're an experienced user, the following rough outline would probably be sufficient. If not, perhaps it'll help you make some sense of what I wrote...[LIST=1]
[*]Create somewhere to put your database.
[*]Shut down your database server & copy its data to the new location.
[*]Move your original data to one side.
[*]Alter /etc/fstab and mount your new database in the right place.
[*]Double-check everything is as it should be.
[*]Restart your MySQL server.[/LIST]After a day or two, once you're sure you won't ever need it again, remove the backup copy of your database. In the meantime, should anything go wrong with the switch-over to your new database storage, you can use it to quickly bounce back to the way things looked originally, so your users don't have to do without their MySQL server for any more than about 60 seconds at a time.


The only additional comment I would make has to do with my suggested creation of a dummy dot-file "under" your databases' mount point. The reason for doing it is that you can now...[LIST]
[*]Alter your system so your MySQL database refuses to start unless its filesystem is mounted. That way, you can be sure that nothing that *depends* on your MySQL server will start either.
[*]Have yourself notified (perhaps by email) should this happen.[/LIST]Things like this are really only important if your database server is at a remote location, so you can be made aware that there is a problem. In general, this sort of procedure covers most "live" storage space manipulations (ie moving critical parts of your system around, while your booted into it). MySQL servers however are a little delicate, and easy to upset, so be sure not to begin until you're clear on what you will do should something not seem quite right at any stage.

The critical points to be aware of, when doing anything like this (eg setting up a new /home partition) are:
[LIST=1]
[*]Don't do anything major until you're sure nothing is trying to access what you're about to move. Linux is expert at retaining access to files ... even after they've been deleted ... and the last thing you want is for your system to have open file handles to the wrong copies!
[*]Be sure there is no net change. To your applications, your filesystem must at least *appear* to be identical, before and after your switch-over. Linux will crucify you for making permissions-related errors, for example.[/LIST]I hope this helps. Once you've done this sort of thing once or twice, it very quickly becomes "simple enough". :-)

---

