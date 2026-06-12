---
title: "Anybody have suggestions on how to setup my own mini-cloud storage system?"
date: 2010-01-26
forum: Server Platforms
---

### Post by Jekshadow on 2010-01-26
I have collected a number of computers over the years, and now I would like to put them to good use. I considered UEC, but many do not support hardware virtualization and all I really need is storage. Over all the machines, I estimate that I have 4-5 terabytes of storage, all going to waste because each one has relatively low storage space. Is there any way I could setup a redundant storage solution that utilities these machines in a networked system?

---

### Post by quixote on 2010-01-28
I haven't plowed through this whole [Linux Journal article]("http://www.linuxjournal.com/article/8590"), but maybe it'll give you some ideas.  I'm sure what you want to do is entirely possible.  If nothing else, you could put together  a system using [Rubel's scripts]("http://www.mikerubel.org/computers/rsync_snapshots/").  Also some interesting stuff at [this link]("http://blog.interlinked.org/tutorials/rsync_time_machine.html") although I haven't used it.

But what I really wanted to say was that if you make your network accessible from the web, don't use anything less than ssh with passwordless login via public - private key authentication.  I found out the hard way when I was in the process of setting up my system and figured it would be okay to have a root password for a while until I got comfortable with using it.  The password was cracked one day, and the only way to regain control of the system was to pull the plug.  Then I had to reinstall, change all my passwords, get new credit cards, yadda, yadda, yadda.  So be careful!  Don't do what I have done.:redface:

---

### Post by Jekshadow on 2010-01-28
> **quixote said:**
> I haven't plowed through this whole [Linux Journal article]("http://www.linuxjournal.com/article/8590"), but maybe it'll give you some ideas.  I'm sure what you want to do is entirely possible.  If nothing else, you could put together  a system using [Rubel's scripts]("http://www.mikerubel.org/computers/rsync_snapshots/").  Also some interesting stuff at [this link]("http://blog.interlinked.org/tutorials/rsync_time_machine.html") although I haven't used it.

But what I really wanted to say was that if you make your network accessible from the web, don't use anything less than ssh with passwordless login via public - private key authentication.  I found out the hard way when I was in the process of setting up my system and figured it would be okay to have a root password for a while until I got comfortable with using it.  The password was cracked one day, and the only way to regain control of the system was to pull the plug.  Then I had to reinstall, change all my passwords, get new credit cards, yadda, yadda, yadda.  So be careful!  Don't do what I have done.:redface:

Thanks for the info.

I already use public/private key auth on my servers accessible from the internet, so that will not be a problem.

---

### Post by FakeOutdoorsman on 2010-01-29
You could use [rdiff-backup](http://www.nongnu.org/rdiff-backup/).  It's in the repository.  It allows you to create incremental backups.

I currently use Duplicity as a cronjob to create daily incremental and encrypted backups to a third-party cloud storage service.  Duplicity is by the same author and is similar to rdiff-backup but additionally encrypts the backup files.  rdiff-backup is a little easier to use and good if you don't require encrypted backups.

---

### Post by idlemind324 on 2010-01-29
I know this is off-topic but FreeNAS mixed with compiling your various hard-drives into a single machine to present larger LUN's might be in your benefit.

For example you could take 2-3 of your computers and fill them to the top w/drives and use volume management and software to present that as a single volume then utilize FreeNAS to present that to your virtual installation as an iSCSI or NFS LUN / volume.

In that situation you will have more than one point for your storage but it might be easier to configure / manage in the end. Also you should look at how much power you will be using by have 10 computers with 100GB storage shared each vs. say 2-3 servers with 300-400 GB each. (numbers are arbitrary as I have no clue what you actually have). The power difference on expense could actually make it cheaper to buy an expansion card to allow more disks in one machine or maybe a RAID expansion card and a few large drives in a single device.

There are a lot of options to look at with what you are trying to do.

---

