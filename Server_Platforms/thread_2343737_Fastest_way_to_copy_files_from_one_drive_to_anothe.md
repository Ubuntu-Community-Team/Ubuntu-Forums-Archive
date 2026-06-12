---
title: "Fastest way to copy files from one drive to another on a Ubuntu server machine!"
date: 2016-11-18
forum: Server Platforms
---

### Post by agarwaldvk on 2016-11-18
Hi All


This is a hypothetical scenario in preparation to run backup jobs for my data on the server run at predetermined frequency.

The intent is to run one or more script files residing on my Windows PC - the command to run the script file would also be initiated from from my windows PC.

Just wondering if it would be any faster if I were to copy data from one internal physical drive to another, both on my Ubuntu server machine, if the copy command were issued from the server machine locally or remotely from a Windows PC using SSH at the puTTy command line? Or it wouldn't matter as the transfer is internal and not through the network per se?


Best regards


Deepak

---

### Post by darkod on 2016-11-18
If you use ssh session the command will run locally on the server, not the windows pc. So, it would be same... And that's the fastest way.

But if you want commands to be scheduled you would usually use cron jobs, which run on the server itself and not through a ssh session. In fact, if the copy is long and you close the session the command that you ran remotely will usually stop.

There is a way around for that with a program called screen. That allows opening screen, running a command and detaching screen so that it runs in the background allowing you to close your ssh session without stopping the running process.

---

### Post by agarwaldvk on 2016-11-18
Hi darkod


Thanks for your response. Seriously, mate, how much do you know?

I don't know what you do for a living but has to be something very very clever.

I will look in to these cron jobs things that you have mentioned. Also about screen. I will ask more details about these later when I am actually ready for it - at the moment, as you already know, I am only copy/pasting data to be able reformat the other drive to ext4 format. So I am long way from this activity but I am hopeful that I would be able to get there sooner than later!

A question though for you - if I am doing a very long copy long and as long as the ssh session can be maintained to be 'on' that shouldn't be an issue then, would it? Can these ssh sessions get closed on their own?

One more - if this is the case, then  how is it that it is copying at the rate of about 50 gb/hr, that is about 15 MB/sec - when I do a copy/paste on my windows pc (its a much faster processor) it does it at around 35 MB/s copying to a powered usb external drive and at arond 70MB/s on an internal hdd. So, howcome this is so slow - is it to do with the processor as this (my Ubuntu server) has 8 gb RAM - I can provide you with the machine details if you can tell me how to get it out from terminal.



Best regards


Deepak

---

### Post by darkod on 2016-11-18
Hmmm the copy speed depends on many factors, mostly on file number and size. Bunch of smaller files will always copy slower than one big file. In general between internal HDDs it should be faster though...

As long as your ssh session doesn't fail it should be ok. In situations when moving lots of data it's better to use rsync instead of cp command. Because if it gets interrupted, rsync can then continue the sync between the two folders, while cp can't know what is already copied and what not.

As for screen, few tips:
1. When you log into ssh session just type:
```
screen
```

It will look like standard terminal but you will be inside screen now. In there start the process that you plan to start. Then to detach the screen hit Ctrl+A, then D.

You will get a message you detached screen. After that you can close your ssh session as normal.

Next time you log in, to attach your scrren running in the background do:
```
screen -r
```

You can view a list of screens (you can open more than one) with:
```
screen -ls
```

They will start with 4-digit number. You can select which one to attach to:
```
screen -r <number>
```

You always detach with the Ctrl+A, then D.

Once you finish your task in the screen session, you do the standard 'exit' and you will close it permanently like that and go back to the ssh session.

It's very good program for when you want to leave things running and log off. I have left rsync jobs running for 2 days like that...

---

### Post by 1clue on 2016-11-18
With absolutely no disrespect to darkod, your questions have more to do with experience and experimentation than with knowledge.

Generally speaking, copying from one drive to another on a single physical system is faster, because *generally speaking* network cards have lower throughput than disk interfaces.  That said, there are network cards with better throughput than most disk interfaces, and there are disks (e.g. a really old usb stick) that could be slower than a modern typical network card. Both these examples could cause a network transfer to be faster.

Generally speaking, transferring a bunch of small files is slower than transferring one big one, but transferring a huge file could take longer if a data or network error is encountered, since you'd need to start all over again. So using a segmented archive large enough that the overhead of switching files is small compared to the wire transfer speed but small enough that an error doesn't set you way back might be a good idea.

Generally speaking, when you involve encryption on typical desktop/laptop hardware your entire process will slow down.  That said there are systems out there which have hardware encryption support which can make the difference there too. This same idea works with hardware compression support.

If you're on a trusted network and your information is not sensitive, then you might choose a network transfer mode which does not involve encryption in order to gain some speed.

If you're on a slow network (wireless n or lower, 10/100 ethernet, etc) and have a relatively fast cpu at the source system then you may want to use compression as it may speed up the transfer overall.

In any case it makes sense to combine files with something like tar, and possibly break them up into manageable chunks for transfer.

Finally, the trick Darko mentioned about screen is a good one. Another alternative for that app is tmux. I started on screen but switched to tmux later. I pretty much live on the command line and use ssh to access remote systems. I have configuration files on each host such that I run tmux and a whole lot of 'tabs' are automatically created with certain apps running or changed to certain directories, depending on my circumstances.  This allows me to start multiple lengthy processes, follow multiple logs and then disconnect to return later, without getting anything confused with another task.  I've found tmux to be more capable of complicated configurations than screen is. Both apps are very similar and based on your needs or preferences either could be a good choice.

---

### Post by SeijiSensei on 2016-11-18
> **1clue said:**
> but transferring a huge file could take longer if a data or network error is encountered, since you'd need to start all over again.
With all due respect, that's not true if you use rsync. It recpvers the incomplete image and picks up from where the transfer was interrupted.

> Generally speaking, when you involve encryption on typical desktop/laptop hardware your entire process will slow down. 
Rsync runs over ssh. The entire transaction is encrypted from end-to-end. The loss in performance is negligible especially compared to the speeds of the devices involved.

> In any case it makes sense to combine files with something like tar, and possibly break them up into manageable chunks for transfer.
Perhaps.  Rsync only sends diffs which considerably improves transfer speeds.  If everything is already archived with tar, then changes to individual files in the archive can require the entire archive to be uploaded. If the upstream target is a mirror of the source, then only the differences between individual files are transferred by rsync.

The author of rsync, Andrew Tridgell, is a really smart guy.  I believe the original version of rsync was written for his graduate thesis, though he's even better known for Samba.  Rsync is a remarkably well-designed tool for file transfers.  It's efficient, reliable, and highly configurable. I can't really imagine using anything else.

> Finally, the trick Darko mentioned about screen is a good one. Another alternative for that app is tmux.
I just use Dolphin in Kubuntu with lots of tabs, many pointing to the same machine, and sometimes multiple instances on separate desktops.

---

