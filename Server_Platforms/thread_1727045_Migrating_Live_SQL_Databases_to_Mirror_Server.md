---
title: "Migrating Live SQL Databases to Mirror Server"
date: 2011-04-12
forum: Server Platforms
---

### Post by honeytech on 2011-04-12
Hello,

First and foremost, I would like to say that these forums have been a god-sent for me as I've recently setup a system of 4 Ubuntu servers to eventually (soon) run at a production level.  And I cannot say where I would be now without the extensive resources found here via all of the extremely helpful users.   

My setup is as follows

Location 1:

Server1a - responsible for handling all website requests & ftp (apache2, pure-ftpd)

Server1b - handles dns records, databases, and email (howtoforge ISPConfig setup)


Location 2:

Server2a - A mirror of Server1a.  Using crontab and rsync, I have Server2a copy website data, pure-ftpd virtual users, system users & corresponding information.

Server2b - Is a mirror of Server1b, Email is 'rsync'ed. DNS records & Email users are manually copied over (which is ok with me for the time being)

After some research, I've managed to find some tutorials that say you can 'dump' a database and transfer it over with rsync, but I don't know what that is, what it actually does, and I'm basically just curious if this simpler solution will work, as I do not yet know a whole lot when it comes to databases.

All four Ubuntu versions are the same, and all administrative users and corresponding sensitive info is also the same (and well protected), as far as SQL root user, system users, etc are also the same on each server.  Also, all of the servers run the same software and have the same configurations..  So, my question is, can I just copy the primary databases over to the mirror servers as is, or is there some other determining factor that would stop the databases from being usable once copied over?

I sincerely thank anyone who takes the time to read all this and try to help me out here.  Mirroring my databases is essentially the final step before I can go live, but I really don't know what to do here.

---

### Post by BkkBonanza on 2011-04-12
The SQL databases can be just copied or rsync'd. It's not the best way as data can be invalid this way especially if you use transactions or record updates that must be atomic (ie. all changes need to be in sync).

The ideal way to keep a mirror in sync is to use "mysql replication". This is fairly easy to setup. You define the master to have a given server id value in it's conf. Use a different id in the slave conf. Define also which datbases should be replicated (if not all). Then start the slave replication process and it will keep the slave in sync within seconds of the master. There are several good tutorials around on setting this up.

Keep in mind if the link between your servers is over public networks then you should either enable ssl for the replication or alternately start an ssh tunnel first, and then run the replication via that tunnel. The replication itself does not encrypt data. I find using the ssh tunnel easier but either way works.

When you use replication in it's simplest form you can share database reads between your servers but insert/update queries need to go to the master only. If you want to use both web servers actively then the second one has to redirect POST requests (that may update sql data) to the master server. If only your master server is active then this isn't an issue.

---

### Post by honeytech on 2011-04-12
Awesome

Thank you so much for the thorough reply!

For the record, I've set up ssh tunnels.  In an effort to secure the system as much as possible, the tunnels are set up only in the necessary directions and with the necessary users to perform rsync functionality and maintenance.  I don't see a need for any users besides myself to have shell access.  SSL is also a potential option, as I do have a cert set up, but haven't really explored that option.

I will definitely look into mysql replication.

But it is also definitely good to know that db's can be copied directly if needed.

Thanks again

---

### Post by BkkBonanza on 2011-04-12
If you do use rsync then try to use "double rsync". That is, make two passes - first catches the bulk of changes, and the second catches any changes during the first rsync, thus cutting down possible sync issues to a minimum.

Using mysqldump is generally considered a better way to dump and restore a database for transfer to other servers. But rsync will work when data doesn't change too quickly and transaction sync isn't critical.

---

