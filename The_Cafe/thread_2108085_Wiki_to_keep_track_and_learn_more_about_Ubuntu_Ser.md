---
title: "Wiki to keep track and learn more about Ubuntu Server"
date: 2013-01-23
forum: The Cafe
---

### Post by donniezazen on 2013-01-23
Hello,

I have been running a dedicated Ubuntu Server for almost a year now. I want to expand it make it more useful with a full fledged backup machine, VPN, and other security and media related stuff.

How do you keep track of all the things you want to do with your server? None of this can be achieved in one sitting and it's hard to keep track of what you have done and what needs to be done. I am thinking about setting up a personal wiki page (attach all config files etc. ) to begin with and may be later publish it for all. This will be a good learning experience. Or may be use Github. What is your process?

Thanks.

---

### Post by TheFu on 2013-01-23
When I did this for work, I had a nobook with tabs for every server. Inside I wrote down notes after I'd figured out exactly how to set something up. I'd try to create a script to do it quicker the next time.

These days, I avoid anything that isn't **apt-get install**. If there is something more needed, I create a {my-initials}-README file in the same directory as the programs or data, then place my notes inside there.

The wiki has been tried, but it is usually too cumbersome to edit. We have a wikipedia instance.  When our servers died, that wiki didn't do any good. You really want this sort of data in a place that you can easily access when all your infrastructure is gone.

I use something like textile markdown for my notes.  It is completely 2nd nature to me and running it through a perl filter creates HTML.

Backup, backup, backup.  Restore.  rinse and repeat.  Be absolutely certain that your backups can be restored at 3am after a night of drinking. That is when something bad will happen, not at 2pm on Tuesday (though that is bad and can happen too).

How do I keep track of what I need to do?
I've used text files, todo.sh, spreadsheets, todo programs, online programs and in the end, I'm back to using a text file with different sections for IT, Home, Company1, Company2, Company3, Android and Personal.  It isn't fancy, but if I can't use it on every platform easily + copy/paste into the list easily, FORGET IT.

Consistent use is more important than being fancy.

Find something that works for you. If you make it a month, you've probably found the right answer for your needs.

Did I mention that having backups is critical?

---

### Post by CharlesA on 2013-01-23
Pretty much what TheFu said.

I have most of the stuff I've done to my server in my head, but I also did have a "reinstall script" a long while ago that I should probably update.

If my server takes a dump, I can throw the OS drive and drive array in another box and be up "soonish" if it is a hardware problem.

Software problem might take 6-8 hours to get functionality back, but at the bare minimum, I would need to compile the RAID drivers, mount the array and install samba and ssh. I can deal with the rest of the stuff later because access to files on a *file server* is pretty important.

---

### Post by donniezazen on 2013-01-23
So a combination of text files and some way of uploading config files like on Github/Gitlab would be nice way to begin. Script would be the second step. I know a little bit of bash that I have picked up off internet. I do need to look into it.

Thanks.

---

### Post by castrojo on 2013-01-23
Consider installing and using `etckeeper`, it keeps /etc in version control (bzr or git) that you can then push somewhere. 

And it has apt integration so if you install something new it'll stick those files in version control too.

---

### Post by donniezazen on 2013-01-24
> **castrojo said:**
> Consider installing and using `etckeeper`, it keeps /etc in version control (bzr or git) that you can then push somewhere. 

And it has apt integration so if you install something new it'll stick those files in version control too.

Thanks for suggesting etckeeper. I sounds great.

---

### Post by Cheesemill on 2013-01-24
I set up a wiki at work for all of our network documentation, with it I can rebuild any of our servers from scratch pretty quickly. It's useful being able to look at the revision history to see what changes were made by who and why.

As part of the backup routine it gets converted into a pdf and emailed to a couple of free email accounts every night so I can still access all of the information if there is a major incident that takes down the server room completely.

I also use exactly the same setup for my home servers.

---

### Post by TheFu on 2013-01-24
> **donniezazen said:**
> Thanks for suggesting etckeeper. I sounds great.

Having multiple versions of files in /etc is an important thing, but unless you are a software developer, perhaps you would like to use more standard, administrative tools ---- like backups with versioning?  

Doing something 1-off is fine for a hobby system. Bringing in a 1-off tool for a company is asking for trouble unless you are the owner.  I cannot imagine anything that** etckeeper** does that versioned backups don't do as well.  OTOH, if you aren't doing system backups to restore later, then definitely do use something to keep your /etc and other settings backed up and versioned.  

I use** rdiff-backup** and have restored entire machines with it.  I tested about 10 different solutions before deciding on that tool. For me, it was the right mix of capabilities and ease of use.  I can easily retain 30 or 90 days of all system changes for very little more storage than a mirror.  I think 30 days of backups are 1.2x the source size.  So if the source system is 10G, then all 30 days of backups is 12G.  That was true the last time I checked.  There are always other, little files, tweaks, and settings that are not in /etc on a system. Backups are the only way to capture those consistently.  We all have to do backups anyway, why have 2 tools for the same purpose?

I'm curious about **rdiff-backup** efficiency now.  Last night, most backups took under 2 minutes per server, though email was 7 minutes.  The more data that changes, the more time it requires and the more storage is needed.  Here's that data for our small company email server (Zimbra):
```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Jan 24 02:57:18 2013         10.8 GB           10.8 GB   (current mirror)
Wed Jan 23 02:56:50 2013         12.7 MB           10.8 GB
Tue Jan 22 02:56:57 2013         14.8 MB           10.8 GB
Mon Jan 21 02:56:59 2013         13.9 MB           10.8 GB
Sun Jan 20 02:56:55 2013         18.1 MB           10.8 GB
Sat Jan 19 02:56:49 2013         12.5 MB           10.8 GB
Fri Jan 18 02:56:55 2013         24.9 MB           10.9 GB
Thu Jan 17 02:56:58 2013         16.4 MB           10.9 GB
Wed Jan 16 02:57:08 2013         11.1 MB           10.9 GB
Tue Jan 15 02:57:32 2013         13.9 MB           10.9 GB
Mon Jan 14 02:57:43 2013         9.67 MB           10.9 GB
Sun Jan 13 02:57:39 2013         18.8 MB           10.9 GB
Sat Jan 12 02:57:21 2013         29.8 MB           11.0 GB
Fri Jan 11 02:56:55 2013         9.04 MB           11.0 GB
Thu Jan 10 02:56:48 2013         11.2 MB           11.0 GB
Wed Jan  9 02:56:51 2013         9.21 MB           11.0 GB
Tue Jan  8 02:56:50 2013         70.8 MB           11.1 GB
Mon Jan  7 02:56:58 2013          125 MB           11.2 GB
Sun Jan  6 02:56:57 2013         16.5 MB           11.2 GB
Sat Jan  5 02:57:22 2013         10.3 MB           11.2 GB
Fri Jan  4 02:56:52 2013         17.6 MB           11.2 GB
Thu Jan  3 02:56:51 2013         10.6 MB           11.2 GB
Wed Jan  2 02:56:47 2013         10.5 MB           11.2 GB
Tue Jan  1 02:56:45 2013         10.0 MB           11.3 GB
Mon Dec 31 02:58:48 2012         13.2 MB           11.3 GB
Sun Dec 30 02:57:17 2012         18.2 MB           11.3 GB
Sat Dec 29 02:56:46 2012         10.9 MB           11.3 GB
Fri Dec 28 02:57:18 2012         10.5 MB           11.3 GB
Thu Dec 27 02:57:23 2012         10.9 MB           11.3 GB
Wed Dec 26 02:57:20 2012         13.6 MB           11.3 GB
```
How is that for storage efficiency of 30 days? About 1.1x and I can restore the server as of any of those dates.

**Automatic, versioned, backups completely rock.  **BTW, I do get /etc in those backups too, but I also get crontabs, server monitoring data, and all those other little nook and cranny locations (/usr/local) on the server too.

---

### Post by CharlesA on 2013-01-24
I think I've looked into rdiff-backup before, but haven't messed with anything because I've already got a backup setup with rsync + cp -al, so it is basically a full backup with version control. I've looked at switching backups methods, but so far, it has worked fine and I don't really feel like rewriting scripts to mess with something that is working fine.

---

### Post by Cheesemill on 2013-01-24
I use [rsnapshot]("http://www.rsnapshot.org/") on my /etc and user data folders, it's trivial to set up and handles backup rotation for you. Using a combination of rsync and hard links it gives me a set of full backups that don't take up much more room than a single backup plus incrementals.

For example I have 1 weeks worth of backups every other hour, 2 months worth of daily backups, and 1 years worth of weekly backups all taken care of automatically.

It also allows users to restore there own backups without having to involve IT staff (everyone has a read-only backup folder in their home folder that's a link to their full backup tree).

---

### Post by TheFu on 2013-01-24
I like KISS. 

How do you handle uid/gid collisions?

How do you handle when file permissions change over time?  Aren't the permissions connected to the target file?  That is how it works here.

rdiff-backup stores uid/gid and permissions in metadata with the backup.  If that isn't important for restores, than rbackup and rsync with cp -rl are great solutions.

---

### Post by CharlesA on 2013-01-24
> **TheFu said:**
> I like KISS. 

How do you handle uid/gid collisions?

How do you handle when file permissions change over time?  Aren't the permissions connected to the target file?  That is how it works here.

rdiff-backup stores uid/gid and permissions in metadata with the backup.  If that isn't important for restores, than rbackup and rsync with cp -rl are great solutions.

Good point. I've got my permissions set so they are pretty much set in stone even if I reinstall the box and it's only serving 4 or 5 users, so it's not too bad. rdiff-backup sounds really handy though. I might look into it just cuz and see if it offers anything that I could use that my current solution doesn't offer.

---

### Post by donniezazen on 2013-01-24
> **Cheesemill said:**
> I set up a wiki at work for all of our network documentation, with it I can rebuild any of our servers from scratch pretty quickly. It's useful being able to look at the revision history to see what changes were made by who and why.

As part of the backup routine it gets converted into a pdf and emailed to a couple of free email accounts every night so I can still access all of the information if there is a major incident that takes down the server room completely.

I also use exactly the same setup for my home servers.

What software did you use for wiki?

> **TheFu said:**
> Having multiple versions of files in /etc is an important thing, but unless you are a software developer, perhaps you would like to use more standard, administrative tools ---- like backups with versioning?  

Doing something 1-off is fine for a hobby system. Bringing in a 1-off tool for a company is asking for trouble unless you are the owner.  I cannot imagine anything that** etckeeper** does that versioned backups don't do as well.  OTOH, if you aren't doing system backups to restore later, then definitely do use something to keep your /etc and other settings backed up and versioned.  

I use** rdiff-backup** and have restored entire machines with it.  I tested about 10 different solutions before deciding on that tool. For me, it was the right mix of capabilities and ease of use.  I can easily retain 30 or 90 days of all system changes for very little more storage than a mirror.  I think 30 days of backups are 1.2x the source size.  So if the source system is 10G, then all 30 days of backups is 12G.  That was true the last time I checked.  There are always other, little files, tweaks, and settings that are not in /etc on a system. Backups are the only way to capture those consistently.  We all have to do backups anyway, why have 2 tools for the same purpose?

I'm curious about **rdiff-backup** efficiency now.  Last night, most backups took under 2 minutes per server, though email was 7 minutes.  The more data that changes, the more time it requires and the more storage is needed.  Here's that data for our small company email server (Zimbra):

How is that for storage efficiency of 30 days? About 1.1x and I can restore the server as of any of those dates.

**Automatic, versioned, backups completely rock.  **BTW, I do get /etc in those backups too, but I also get crontabs, server monitoring data, and all those other little nook and cranny locations (/usr/local) on the server too.

The server that I am using falls somewhere between test and productive machine. It's an old laptop hooked to an external USB hard drive. I want to expand it and in future get a better machine with multiple SATA drives. It's currently running Transmission, Plex Media Server, Subsonic, ddclient, stores my deja-dup backup, webmin, cups and I am thinking about beefing up security and setting up a VPN.  It's more like install and modify once and then forget about it.

I want to be able to easily keep track of commands I run, link the commands to webpages where I found them, and ideally store versions of both packages and config files. You are right. Some software like Crashplan install themselves in /usr/local/crashplan. It could be changed though. Do you backup through rdiff-backup to a different machine? Does rdiff-backup do versioning?

Thanks.

---

### Post by CharlesA on 2013-01-24
> **donniezazen said:**
> What software did you use for wiki?

Probably MediaWiki. I use one at work.

---

