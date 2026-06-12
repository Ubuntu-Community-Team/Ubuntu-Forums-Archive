---
title: "Scheduled copying of data"
date: 2008-07-03
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-07-03
I have my test Ubuntu 8.04 server now running with Webmin and SSH access.
The aim of this project is to find an alternative to the current Win2K3 server platform which we are running at the moment.

The current functions of the Win2k3 server need to be replicated in some way but I'm not sure where to begin.

Currently we have:
1 - RAID 5 for the company data files (hereby called COMPDATA)
2 - Nightly copies of COMPDATA from Server1 to Server2 (backup server with identical config)
3 - Weekly backup of COMPDATA to 4mm DAT drive connected to the Server1

1 - I assume that the RAID functionality will work the same with Linux as it does with Windows as it's built into the RAID controller of the server. Right or Wrong?

2 - How do I map to a network drive on another machine and schedule data copies to it?

3 - Is there a module for doing tape backups?

Thanks

Paul

---

### Post by amenszer on 2008-07-03
I'm not sure what you're hardware setup is...but I have several Hp Proliant servers using p400 and p600 raid controllers, and they all run Ubuntu. I have yet to run into any problems with Raid configurations and Ubuntu.

As far as backups...

There's a program that comes with ubuntu called cron. There's a cron.daily directory for daily backups and a cron.weekly directory for weekly backups. Basically, all you need to do is write a backup script (usually employing rsync) and throw it into one of the two directories above, and it will be run automatically daily or weekly at a specified time. The time can be altered in /etc/crontab.
Rsync is a program that will sync two locations to mirror each other. In daemon mode, it can also share out backup locations or locations that need to be backed up on servers. For all of my servers that have files or directories that need to be backed up...I simply share them out, and make them only accessible (outside of the machine) to the server that is doing the backups...and then once every 2 hours (that is our backup schedule), the backup server automatically rsyncs with the shared out locations.

One thing that may interest you is rsync snapshot backups. I just recently converted my company's backup system to employ this method. Here is a link explaining it:
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

The idea for the above method is to save space and backup time. I can attest that it has saved us a ton of space and time...as it only really stores new files and file differences.

As far as the tape backups go...I'm not really sure. I don't have any experience employing tape hardware in an ubuntu environment. I'm sure you can find something though if you do some googling or search this forum.

If you need more detailed information about anything I mentioned above...I'll be glad to give assistance.

---

### Post by Titan8990 on 2008-07-03
1 - It will not matter if you are using a discrete card. If you are using softRAID or fakeRAID then it will matter but it highly recommeneded you use a discrete hardware controller.

2 - rsync via SSH: [http://ubuntuforums.org/showthread.php?t=639979&highlight=rsync](http://ubuntuforums.org/showthread.php?t=639979&highlight=rsync)

3 - [http://www.amanda.org/](http://www.amanda.org/)

---

### Post by G1ZmO65 on 2008-07-03
Thanks to you both for your input.

We will be using hardware raid. Whether its a Compaq/HP server or a Dell just depends on what hardware we have available at the time.

Just now I have Ubuntu server on a pc to get to grips with it and see whats what.

I'll have a look at the stuff you've suggested and let you know how I get on.

This project (replacement of the Win2k3 servers) is probably going to take place next year but I'd like to get my teeth into Linux long before then 
1/ to make sure that I'm irreplaceable lol
2/ to boost my CV for the future (just in case) :P
3/ MS annoys me :)

Cheers
Paul

---

