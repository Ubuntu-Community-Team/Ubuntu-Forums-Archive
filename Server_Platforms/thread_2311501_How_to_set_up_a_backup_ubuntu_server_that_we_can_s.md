---
title: "How to set up a backup ubuntu server that we can switch to in an emergency"
date: 2016-01-27
forum: Server Platforms
---

### Post by Stephen_White on 2016-01-27
Hi,

I'm a programmer at a small start-up company (12 employees).  About 6 months ago I set up an Ubuntu server using a Lenovo ThinkServer (3.2 GHz Intel Xeon, 4GB DDR3) with a raid 5 set-up using four 4 TB SATA drives (WD40EFRX), so we have about 12 TB of useable space.  We're using the Ubuntu server predominantly as a file server, but we also use it for other things such as a wiki (MediaWiki) and messaging (jabber/XMPP).

My boss has ordered an identical hardware set-up with the intent that the new server will function as an emergency backup in case our original server has a catastrophic failure.  So in an ideal scenario if our current server had some serious issue we could switch to the backup server while repairing the original server and the backup server would have a fairly recent copy of all data of the original server such that people could keep working with only a minor disruption and loss of data.  For example, it would be great if the backup server was sync'd to match the original server nightly or at least weekly.

Can some one point me to instructions on how I could go about automating slaving a backup server to be synchronized to our original server?  I'm hoping there is some relatively straight way of automating this.

I've heard that it can be difficult to do full back-ups without taking down the server being backed up (i.e., unmounting drives).  I'd rather have the server being backed up remain functional during the backup; however, this is not a requirement as long as the backup process can be automatable and done in 3 hours or less in the middle of the night.

Another hope I had was that the back-up server could synchronize with the original server and then I could take the back-up server down periodically as necessary and do a full volume-wise backup of the back-up server to an external HDD that can then be stored off-site.  I'm currently using rdiff-backup and a cron job to back up most directories to an external HDD that is then stored off-site, but it would be a nightmarish amount of work for me if our Ubuntu server died and I had to rebuild it (i.e., reinstall Ubuntu) and restore everything directory by directory.

Any and all help IS GREATLY APPRECIATED!!! THANKS!

- Stephen White

---

### Post by TheFu on 2016-01-28
Use this opportunity to fix your backups. Backups that haven't been tested to restore on bare metal aren't really backups. They are "hope", they are not "a plan." Businesses need "a plan" that works and has been well-tested.  

So - when the new server arrives, use the existing backups to restore the system to the new hardware.  Backups should be both local and remote. There should be at least 3 copies of the data on 3 different physical storage systems.  Offsite needs to be far enough away so that any large natural disaster doesn't impact it.  Where I worked before, 200 miles was the limit. Anything closer than that wasn't considered "off-site."  Think about what happens if there is a hurricane, flooding or earthquake in the area.

rdiff-backup is the tool I use to backup 20-30 systems here nightly. Most are virtual machines, which makes testing backups and restores really easy. Virtualization is how most companies handle their servers these days. It abstracts the physical hardware from the server.  For example, your physical server is overkill for those things for a small company. The RAM and CPU are probably 10x what is needed.  From a security design standpoint, I'd split the file server and wiki apart into different VMs.  I'd use LVM on the physical server with separate LVs assigned to each VM.  That way you can take snapshots through LVM and perform all the backups using that. Zero downtime.  If you want a little more redundancy and better remote backup support, check out ZFS. You'll want to add 2 more HDDs - total of 6 - ZFS likes 6 HDDs.  Then you can do zsend to backup the storage from one system to another.  I'm not saying that rdiff-backup isn't a good tool, just that there are options and using different tools for different purposes is smart.

Of course, there are 50 other ways to accomplish the same goals and only you can decide which is desired for your specific situation.  At 5am, after a failure, YOU will be the guy doing the restore work, not me.

Oh - and be certain to practice the restores onto bare-metal as many times as is required until you can do it and hand over the restore-notes to someone who is **unfamiliar** with the system(s), but knowledgeable about Linux administration, in a general way. After all, anyone can be killed crossing a street. The restore process shouldn't be dependent on 1 person.  If they can't follow the restore instructions, then it isn't done.

I wrote 5 posts over the last 2 weeks here about good backups and the techniques for someone else. Please look that up. Data corruption during backups was the main thing I was trying to get the other person to understand.  For example, mediawiki uses mysql/mariaDB, so either the DB must be dumped to a file before each backup or the wiki system AND DBMS need to be shutdown to avoid data corruption in the backups.

For simple data mirroring, use **rsync**. Be certain the source and target storage areas are not in-use during this operation.  The first time will take awhile, but after that, should be just a few minutes. Might make sense to rework the way backups are done.  Let the mirrored server be used for backups, that way the main production system doesn't need to be offline waiting for the backups to finish.  I take my main email server offline during backups and make the email-gateway box hold mail during this period nightly.  The email systems both run inside virtual machines.  If I need to move to different hardware or add more CPU/RAM to the VM, it is pretty trivial.  I use rsync to mirror OSes to new physical storage, but for backups, which require versioning, rdiff-backup is my tool.

Take a look at devops methods for system management. Completely recommended.  We use **ansible** here. Every new box gets an ansible playbook to build and maintain it. After we think we're all done, we create a new VM with our base server (only ssh), then run the ansible playbook. If we don't end up with the box we need doing that, then we've failed and go back to tweak the ansible tasks, roles and playbook until it works perfectly.  Editing settings on-the-production system is something we don't do anymore. New stuff is added to the tasks, roles, and playbooks, then re-run against the server. All this may seem like a waste of effort, but it is called "infrastructure as code" - software developer-types love that idea. 

And keep doing rdiff-backups even after you have these things mirrored.  Replication and backups are different tasks with different tools.

---

### Post by Stephen_White on 2016-01-29
Wow!  Thank you sooooo much for the lengthy reply!  There's a lot of information in your reply that I will need to digest and investigate further.  I will also read your other posts.

I realize there are many, many ways of handling backups, which is both a blessing and a curse.  Ultimately my goals break down to:

1.  Our server either doesn't go down during the backups or only goes down for a short time in the middle of the night.

2.  The backed up data is sufficient that we can switch very rapidly to the backup machine, allowing work to continue while I would work on repairing the original machine.

3.  That any lost data would be limited to the time of the last backup (i.e., the backup in the middle of the night).

Maybe those are unrealistic goals?

I could set up rdiff-backup to run as a cron job to update files on the backup machine, but as you mentioned with the Mediawiki db issue it doesn't seem to me like using rdiff-backup to back-up specific directories would be reliable as an accurate snap shot of the original machine.  I could see switching to the backup machine and having Mediawiki failing.  Or the backup machine missing important issues related to installed packages on the original machine.  Or files currently open for writing, or started during the rsync-backup, being missed.

I was hoping there was some easily automatable way to snap shot one machine onto the other each night, with the machine being snap shot either not going down or only going down for a few hours.  The idea being that the backup machine would then be a completely useable snap shot of the original machine.  Also, I'm not familiar with how I can automate the master machine being taken down into a dormant state (i.e., no file I/O) where it could be snap shotted, and then re-activated after the snap shot has finished.  Maybe there is some software that does that nicely?  Maybe people set up rsync to constantly back up all changes to the master machine to other partitions on the master machine, then use a cron job to unmount the backed up partitions on the master machine and snap shot that?  Although, as with rdiff-backup, I don't understand how that would work unless you could guarantee that all file I/O had finished before taking the snap shot.

Forgive my ignorance, and thanks again for your great response.

---

### Post by TheFu on 2016-01-29
All of this can be automated. It is trivial for a jr. linux admin to accomplish with scripting.  If your scripting-fu isn't upto the task, work on that.

* Disaster Recovery requirements begin with RTO/RPO requirements.  Wikipedia has descriptions of those terms. Basically, 24 hrs is pretty easy and normal backups can be used for DR needs for $0 more.  Shorter times for either means doing something more expensive than normal backups.
* Unix automation is handled via cron. It has been around 35+ yrs - perhaps since 1973. anacron added some new ideas - like @reboot which some people find handy. [http://blog.jdpfu.com/2010/06/05/5-cron-tips](http://blog.jdpfu.com/2010/06/05/5-cron-tips)
* Shell scripting has been around since the beginning. It is common to create backup scripts for each system using bash.  Once you make 1 script, all the others fall into place.  I assume you know about **ssh** and remote scripting. [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) Setting up ssh-keys is the first thing I do on every new server to make remote access a) secure and b) trivial.  Never use passwords for remote access. My ssh - jump point: [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)
* rdiff-backup is for versioned backups. The backup area shouldn't be modified by any other tool. It is fine to use rsync or cp or scp or {other file copy methods} to copy **FROM** the rdiff-backup area **TO** some other location for full or limited restore needs. Do not modify ANYTHING in the rdiff-backup area. It will be bad.
* rsync is good for mirroring and some old-timers use it for versioned backups using hard-linking to manage the daily versions. There are pros/cons with this method. 
* mysql backups: [http://blog.jdpfu.com/2009/12/13/cold-backup-for-alfresco](http://blog.jdpfu.com/2009/12/13/cold-backup-for-alfresco)
* 1st Five Minutes on a New Server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

An old script for rdiff-backup: [http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) - I'm NOT following scripting best practices. It does show how to get a list of installed packages, crontabs, everything in /etc/ and selected other places depending on what each system does, and I capture system data so you know what needs to be mirrored when a new box shows up - stuff like that. You would need to add or call a DB backup script before doing the rdiff-backup command that shutsdown the DB, dumps it, restarts it, then does the rdiff-backup stuff.  I would use "pull" backups, not "push" for security reasons. After, being hacked **Is** a real good reason to use versioned backups.  Generally, I have 60 days of daily backups - sometimes less and sometimes 120 days. It just depends on the risk factors for the system involved.  I don't do "mirror" backups.  I backup enough to be able to recreate the system as it was at the time of the backup. So I do not backup the OS, just the settings and a list of installed packages.  I avoid installing anything outside a package manager, but if I do, then that stuff is part of the backups too (/usr/local/).  

Oh - and don't get hung up on "no file I/O" - a DBMS should guaranty atomic commits, plus by dumping the DB to a text file and backing that up, it doesn't matter what the DBMS files are doing, does it?

Found a simple mysqldump script:```

#!/bin/bash
DB_NAME=redmine_default
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`cat ~root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/${DB_NAME}_`date +%Y%m%d`.gz
find  $BACKDIR -type f -name $DB_NAME\* -atime 60 -exec rm {} \;
``` 
The last line could/should use the -delete option to find instead of the -exec rm stuff. Live and learn.

Hope that helps.  Most DBs take seconds to dump.  Be certain you practice restoring a dumped DB, just like you practice doing the restore for the entire system backups too. Get so these things are easy - probably 10 times - and take good notes.  Do not put those notes into the system that needs to be restored. Avoid the chicken-egg problem.

Anyway, you can see that I've jotted down a bunch of thoughts on my blog. Hope they help.  Sorry that the block software screws up scripts so copy/paste doesn't work and quotes and comments and extra lines get inserted. I've been meaning to fix that, but it has been an issue for ... er ... 5 yrs, so don't hold your breath.

Hopefully, someone else will highlight my mistakes above. There isn't just 1 way to do this and professional admins with decades of experience will probably use lvm snapshots for their backups.  I'm looking at that now, but don't expect to change for many months, if this year.  Why not? Most of my system backups take 1-5 minutes (most are 1-2 min), so if it isn't broke, don't fix it.  I only have 1 system that started causing backup time issues. It was working great for 7 yrs and took only 4-7 minutes, then I migrated the version of the primary software on that box and upgraded the OS through 2 LTS releases. The upgrade/migration required 6 different software installations and I practiced it 5 times inside a VM to ensure the enterprise impact was minimal.  Backup times changed from 5 min to 45-75 minutes now.  I don't know why or what changed to cause that added time. Still don't.  LVM snapshots would reduce that time to about 3 minutes of downtime. I'm just not comfortable enough to change that yet.  Devil I know vs the devil I don't know. Plus life keeps getting in the way. ;)

---

### Post by Stephen_White on 2016-01-29
THANKS again for the great response!

I'd definitely consider myself a very junior Linux admin (first time for me as administrator), but I've written plenty of bash scripts and cron jobs before.

Sounds like as you mentioned with the SQL example that I'll need to write specific script(s) to shut down specific things, back them up, and start them up again, which I can certainly do.  As opposed to somehow automating volume dumping from one machine to another.

Sounds like I'll also need to put in some ways to guard against people try to make changes to things while I'm backing things up.

Thanks again for your excellent help!

---

### Post by TheFu on 2016-01-29
> **Stephen_White said:**
> Sounds like I'll also need to put in some ways to guard against people try to make changes to things while I'm backing things up.

Thanks again for your excellent help!

If you don't allow local accounts, that is easy. Shut off the service.
Also, publicize when system maintenance periods happen.  I got
* 2am-3am daily backups
* 5am-11am Saturdays

That set the expectations clearly and I was pretty clear that if they could access the system, it should be fine to use, but during those periods, data loss wasn't my problem.  Once in awhile, I'd be caught overseas and be impacted by these time periods (I like to travel) - or even have access blocked when in less-friendly countries either by the local government overlords or by my firewall blocking entire countries deemed to be too much hassle to selectively filter, so I just blocked all subnets known to be from there.  Not that big of a hassle, since I have systems in a few different countries and could hop to one in a nicer place, then to my main network.  ssh rocks!

I think we've covered more than I know now. Bye.

---

