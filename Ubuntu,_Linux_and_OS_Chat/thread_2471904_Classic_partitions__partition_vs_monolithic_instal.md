---
title: "Classic partitions  partition vs monolithic install"
date: 2022-02-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Draciron on 2022-02-12
This topic has probably been raised before, Things have changed since.  20.04 LTS makes it such a pain to do /home on a separate partition that I wound up with a monolithic partition as I was in a bit of a hurry when I installed. and rather frustrated while attempting to do my normal partitioning. I'm sure it's possible, or why have the custom feature at all? 

I strongly feel that the default should be /home on it's own partition. This saves a lot of potential problems. Some examples. I just had an update go bad and clobber my system. So when I reinstall I'm just formatting / and leaving /home untouched. If logs and other files run amock on either / or /home it doesn't interfere with the other. So for example if your MySQL server set to high verbosity decides to eat /, you can still save the document you are working on before attending to the problem with / being full, or if code you are working on gets in an endless loop and you fill up /home, your system purrs on without a hitch except for programs that need to write to /home.  More so, once or twice I've had HDs go bad, corrupted in a way that / was unreadable, but I could still mount /home and retrieve the data from it.  

I often have a /data partition as well if I have multiple HDs, or for servers a partition specific to the server. For example if I'm building a MySQL server, I give MySQL it's own partition. That way if it fills up the drive with logs gone mad, MySQL crashes and nothing else. Usually takes me a few mines to think to check free space, but it's a really quick and easy fix once I do. That sure beats having to log in as root, just to get into the server. Something Ubuntu intentionally makes difficult. One of the reasons I tend to avoid Ubuntu for servers. There's eventually some idiot that sets verbosity to high on logs and then doesn't tell anybody so we can clean up the logs on a regular basis or I'll forget I turned it on high at a developers request and a couple weeks later I've got a crashed server and if I didn't set a root password I'm having to boot from USB to get in. On other distros I can just SSH in as root, clear the logs, logout and be done with it. If I have /home on it's own partition, I just SSH in as me, sudo to root and clean up the logs.  A monolithic partition just makes things unnecessarily difficult and degrades performance with the dynamic swap drive which in a hard hit server might by itself lose the ability to swap. This can cause some really odd errors that make it difficult to troubleshoot. Linux is relatively graceful about running out of RAM compared to other OS's but that grace can also obscure why things are crashing.  A fixed /swap ensures you always have some swap space and being formatted to /swap makes it faster theoretically. I haven't tested it, but I'd assume the whole reason for a /swap format option is that it improves swap performance. 

Another partition I often create when I'm setting up dual boots for people is a common partition formatted with FAT or NTFS that both Windoze and Linux can mount and see. I feel this is a really important partition. NTFS drivers are so so on Linux as M$ keeps changing things just to change them. Windows struggles to mount EXT partitions at best. Having a common partition both OS's can use is invaluable. It allows people to pass files back and forth easily without installing special drivers and potentially corrupting an important file system. If you corrupt /common, theoretically you have all the important files triplicated or at least  a copy on one of the native partitions, plus backups.  If you have a monolithic Linux partition, and monolithic windows partition and something gets corrupted you are looking at a wipe and load for one or maybe both OS's.  By default if there are 2 HDs, one for Linux, on for Windoze is another good idea. 

Another partition I always create is a swap partition. Since my machines never have bountiful RAM and I multitask heavily, I use the swap drive heavily. Having it partitioned as swap really helps system performance in my opinion. Even with a 100 gig / partition on this machine, I'm using 40 gigs of it and not running any severs especially hard. I have a MySQL, Postgres and NGIX servers up for some light DBA and web sork. They are lightly used and the logs are less than 50 megs for all of them combined. 

The monolithic partition I guess is for windoze users first trying Ubuntu. Though having /home mounted on it's own partition is transparent to them.  So I'm not sure what is gained by a monolithic partition.   If they click on default and it's a classic 3 partition set up, they won't know any different typically. Maybe it makes them use an extra couple clicks if they erase the Linux partition, but most of them would just do a wipe and load and erase the whole HD anyway. 

My suggestion is having these options.  **Monolithic**, **Classic** (3 partitions / /home and /swap),  Default to twice RAM present for /swap,  20% of the drive for / up to 100 gigs no less than 20 gigs, and the rest in /home. **Dual Boot **option  auto detect the windoze partition. Split the HD in half by default, allowing for user to interactively shift space between Windows and Linux partitions with a min partition space for each. With 20.04  10 gigs would likely be the min space.  . No idea how much space Windoze takes up any more. With XP and Win 7 I always allowed a min of 20 gigs for the windoze partition, usually 100 as most of the time the person I was setting it up for just wanted windoze to play games and they tend to eat up a lot of space. . The[ dual boot option would create by default the / for Linux as a monolithic partition, a /common that is formatted in FAT or NTFS, auto install of NTFS drivers to mount the windoze partition would be nice but probably steps on too many toes downline to be realistic.  Then a **custom** option that doesn't make custom partitions such a pain, but does warn users this option should only be used by advanced users. 

This will make installations easier, especially for novice users. The easier it is to install the more people are likely to actually go through with the install and give Linux a serious look.  A monolithic partition is only easy in writing the code for the setup. It saves a few lines of code.. The novice Linux user won't know the difference. They only know at some point Linux crashed and they do not know what went wrong when say .xsession-errors suddenly fills up their drive and things are wiggy from there.  I used .xesession-errors specifically because I've had that happen to me 3 times over the years. Once on a monolithic partition and it caused all sorts of weird errors. One of the reasons I stopped using monolithic partitions.  I've had logs fill up HDs on countless servers over the years. MySQL is the worst, though Postgres and Apache can be really bad about it and these are installed by default on most installs. So much software uses these apps. Most backup software for example use MySQL by default. 

Side gripe, the install should force a password to be set up when installing things like Postgres & MySQL. I can't count how many times I've caught default passwords in use on dev servers and workstations during security audits. Half the time the user was unaware they had even installed and set up the server as it was a dependency for something they installed.  It's a major security issue. 

If it's somehow a manpower issue I'd be happy to write the code and maintain it. It's not that much code or testing realistically.  A blind guess would be 100-150 lines of code, not having looked at the code.

---

### Post by howefield on 2022-02-12
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum as not a support request.

---

### Post by SeijiSensei on 2022-02-12
To mount my separate /home partition, I just choose "manual" at the disk layout stage, pick the appropriate filesystem, and tell the installer to make it /home. Really not hard at all.

---

### Post by grahammechanical on 2022-02-12
To have the installer automatically create both a root partition and a home partition would raise the question of what default sizes the partitions should be. And people would criticise the sizes decided upon.

Regards

---

### Post by Draciron on 2022-02-12
> **SeijiSensei said:**
> To mount my separate /home partition, I just choose "manual" at the disk layout stage, pick the appropriate filesystem, and tell the installer to make it /home. Really not hard at all.

With versions prior to 20.04 that was the case. In 20.04 something changed. 

It doesn't change the core point that monolithic partitions for most instances are not best policy and it's a rather trivial  change to save time and improve the way Linux is thought of in the general community.  

Monolithic partitions with inexperienced users are just a problem looking to happen in my opinion. Telling them RTFM isn't a solution, it's a cop out that hurts Linux and why Linux is only 2% of the desktops in the world.  A separate /home partition isn't earth shattering but would probably keep hundreds using Linux each year. Those hundreds will convert others. Over time it makes a big difference and saves a lot of hassle for people like us since companies will need to support Linux or at least release driver source to Linux driver developers if we get as much as 10% of the desktop share.  We can call tech support and not have them flee in terror when we say we use Linux or have to lie and pretend to use Windows and do the silly reboots and other idiocy when we KNOW the problem is on their side not ours. 

The first time a novice user runs out of space on / they'll likely just think Linux is buggy and give up. A monolithic partition makes that much more likely.

---

### Post by Draciron on 2022-02-12
> **grahammechanical said:**
> To have the installer automatically create both a root partition and a home partition would raise the question of what default sizes the partitions should be. And people would criticise the sizes decided upon.

Regards

We are Linux users, we'll argue over the proper way to rm  -r * from ./.   No matter what you do, there will be comments as Linux is the do it YOUR way OS rather than a 1 size fits all solution thrown at you by Windoze and OS X. 

The defaults in my opinion would be as stated in original post. 20% up to 100 gigs for / with a min of 20 gigs. Double the RAM for /swap and rest to /home.  Those defaults would be a good topic of debate. There may be a better setup than that. That's just my personal experience since I tend to install a lot of software. So I use a lot of space on /. On this machine I'm using 40 gigs and that's without any hard hit servers. I have a MySQL and Postgress and NGIX set up on here, but rarely use them. I just keep them around for quick tests and backup software I'm using is set up to use MySQL.   So for me 100 gigs is a good default size for /.   Others may find that excessively large and decide 50 gigs is a better default.  

Drives in PCs and laptops are getting decidedly smaller nowadays. For a time the default was all the way up to a terrabye, but lately the drives have been mostly 500, 400 and even as small as 200 gigs. Those with SSD drives are often less than 100 gigs.   That's why I suggest a min size, as a 64 gig SSD drive would only be a 12 gig / and that's not enough for anything but a minimal install and maybe not for even that. 

At worst this I think will be an interesting convo about how everyone partitions their machines. I find it hard to believe many experienced users use the monolithic partition. Especially on LTS releases. 

It also is a potential big time saver when somebody is doing mass installs. 

A slider like what is used already when you repartition could allow for a quick and easy resizing if you prefer a bigger or smaller swap, or root or home partition. A checkbox can allow you to bypass the swap partition with a click.  So for example somebody setting up a lab from scratch could save hours with this option.  Think about setting up all those partitions manually through custom install on 20-50 machines. 

A server install option that puts the logs and DBs on a separate partition would also be a huge time saver.  If you allow FTP  and don't have user file limitations I would also put the web server root on it's own partition. I've seen people upload some gigantic files to servers. Often personal files. Then wonder why you deleted it and griped them out for uploading their movie collection to a work server.  It being immediately obvious when they filled up the root partition uploading all that garbage, thus knocking out a production server so I'm getting a call at 4am, that the web server is down. 

What about the guy who decides to try Linux for a web sever for their small office. Then has that happen to them? The error msgs are cryptic when that happens. They might be there all night before they figure it out. We want to ENCOURAGE people to use Linux. Make it easier for them while keeping Linux as flexible and powerful as possible for experienced users.

---

