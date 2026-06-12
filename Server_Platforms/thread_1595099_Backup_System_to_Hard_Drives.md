---
title: "Backup System to Hard Drives"
date: 2010-10-12
forum: Server Platforms
---

### Post by DocLove on 2010-10-12
[SIZE=3][FONT=Calibri]            Hello, I have a problem that I hope that someone has a solution to.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]I currently have an Ubuntu 10.04 Server with 10 – 2TB hard drives (Hot Swappable). I discovered that having a software raid over 16TB is not supported, so I split the drives into 2 sections and have 2 Software Raid arrays storing my movies, audio, pictures, and other software. The total current usage is around 7TB. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Since backing the files up to DVD’s or even BlueRay is laughable, I am going to backup the system to 2TB hard drives probably 4 of them, the problem becomes that I can only hook one backup drive at a time into the system using a hot swap tray. Now I know that I can do this manually by copying the files one at a time to the drive until it is full, switching the drive out and repeating this, but I am hoping for an automated solution,  Start backup, plug first drive in, system fills up drive, swap and repeat. Also it would be nice if the system remembered what had already been backed up so when I add files to the system, I only need to attach the last drive and not start the process over.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I hope this makes sense, please ask questions if I haven’t been clear.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The Doc.[/SIZE][/FONT]

---

### Post by brettg on 2010-10-12
I'm not going to go into any details but if I were going to attempt to do this I would look at using [AMANDA]("www.amanda.org")

Normally you would use it to backup to tapes but you can also configure "virtual tapes" which are essentially files on a disk.

However, I think the first stumbling block you will come across is that you will need an enormous dump drive for the intermediate steps of the process.

General instructions on how to get amanda working [can be found here]("http://tuxnetworks.blogspot.com/2009/07/backing-up-with-amanda.html"); 

Good luck

---

### Post by Carlbc18 on 2010-10-13
I too have a similar issue to The Doc. I have a 2-2TB Software RAID 1 setup on my server (drives no hotswapable that i'm aware of). I am looking for a backup solution just in the off chance both disks fail.  

Would AMANDA still be the recommended software? Or is rsync a better option?

---

### Post by brettg on 2010-10-13
Firstly, you need to be aware that syncing drives is not a proper backup solution. It is OK for guarding against drive failure but it will not protect you from file corruption or accidental deletion (unless you notice and restore before the next sync runs)

Having said that, I currently have a 4x1TB RAID where I store my stuff and I currently rsync that to an external USB drive. 

In my case I am only using half the 4TB I have available so it all fits on a single 2TB external but I am just about to hit the capacity limit on that drive and am having to modify my arrangement.

There is no easy solution.

In my case I am going for a interim solution and simply rsyncing the largest directory (videos) on to the 2TB drive and everything else on to another drive. I'm hoping that this will remain viable until the time that 4TB single hard drives become available but I have my doubts because 3TB drives are only just coming online. Anyway, I will cross that bridge when I get to it.

Sync frequency is something you need to consider. Lots of people will tell you to "sync every hour" but in my opinion this is a stupid idea. Firstly, I don't add stuff all that often to my main media storage so it is unnecessary. Secondly, when I do make changes then that is the time where my fat fingers are most likely to cause a major oopsie. The last thing I want is to accidently delete a bunch of stuff and a few minutes later have the sync run and wipe out my bloody backups too. 

Personally I like to run mine daily. That gives me enough time to realise when I've made a mistake (hopefully) and then rectify it.

If I add a whole bunch of new files to the store and I am *sure* I haven't fubared anything I can always kick the sync off manually.

For user documents however rsync is not a good solution. It is trivially easy to accidently delete, modify or somehow corrupt a document and not realise for quite some time. Once you sync your primary to the "backup" you will wipe out the only good copy you have. 

So for user docs I use amanda with a 14 day virtual tape cycle.

---

### Post by DocLove on 2011-11-18
Well It's been over a year and my collection has grown. I still haven't found a good solution my backup problem. I found an external ESATA hard drive mount so I can drop drives in and out easier, but I am forced to copy files in groups till the backup drive is full and then swap it out and repeat until I have backed up everything. 

Can anybody recommend an application that would allow me to say "Back this up" and it would fill up the drive, ask me to swap it out, and then keep going? manually doing this is a pain and I don't backup my files as often as I should. It would also be nice if it would do incremental backups, copy all files to a set of hard drives, and then only copy new files to the currently plugged in drive.

Thank You
    The Doc

---

### Post by brettg on 2011-11-18
Take a look at rsnapshot

[http://rsnapshot.org/](http://rsnapshot.org/)

---

