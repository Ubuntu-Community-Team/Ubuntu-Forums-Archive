---
title: "check use of mounted share"
date: 2010-12-29
forum: Server Platforms
---

### Post by radiognome on 2010-12-29
Nearing the end of 2010 I found time to fix-up my cronjob backupscripts. There is one thing I want to make better, but don't know how, so I hope to find someone with a clever suggestion for my problem.

My backups go to a shared NAS (running Windows XP embedded).
In the shellscript I basically follow the next procedure:

1: Check mtab if the share is mounted. If not, mount.
2: Set a variable if this script mounted the share or not.
3: pg_dump or whatever needs to be done to the share
4: If this script mounted the share, umount it, else leave it.

I hoped to solve issues with the share being mounted double with this. I have to put a mount somewhere, as the NAS is somewhat flakey due to its OS.
This goes well for one long job running, and a short one being started during this.
All goes wrong when 
Job A mounts the share
Job B starts, finds it mounted
Job A finishes and (tries to) umount it (-l option)
Job B can't finish as suddenly the target is no longer present.

Is there a way to automatically check if another script / process / is running using this share so I can mount / unmount depending of the share being used currently?
Could I perhaps make multiple mountpoints for the same share, one for every cronjob I have? 
Anyone have a clever idea?

Thanks for reading and a happy 2011,

Martin

---

### Post by kidders on 2010-12-30
Hi there,

What you're describing could be achieved by tracking the PIDs of running backups. For example, every backup could begin by running **touch /var/run/nas/MY_PID_HERE**, and finish by removing the file again. At any one time, there would be three possibilities ...

[LIST]
[*]The /var/run/nas directory might be empty - No backups running.
[*]/var/run/nas might have files in it whose names correspond to known PIDs - One or more backups is in progress.
[*]/var/run/nas might have files in it whose names *don't* correspond to running processes - One or more backups failed half way through, and are no longer using the NAS.
[/LIST]

The problem with this type of thing is that it really only moves your problem, rather than solving it ...[LIST]
[*]Job A finishes, checks for running backups & finds none.
[*]Job B starts a backup.
[*]Job A unmounts the NAS.
[*]Job B gets upset.
[/LIST]

One solution is to implement a locking mechanism. Suppose all your backup scripts included another script with a pair of function in it to mount/unmount your NAS. Individual backup scripts would start and end by calling the shared mount & unmount functions.

**Function: acquireNAS**
[LIST=1]
[*]Wait a random amount of time (eg 0.3 - 2.5 seconds).
[*]Check if a lock file (eg /var/run/nas.lock) exists and contains the PID of a running process. If it does, wait until one of these conditions is no longer the case.
[*]Write the script's PID to /var/run/nas.lock.
[*]Check for files in /var/run/nas with names that match the PID of a running process. If there are any, a backup is in progress, and mounting your NAS should be unnecessary. Otherwise, mount your NAS.
[*]Create an empty file in /var/run/nas whose name is the PID of your script.
[*]Remove /var/run/nas.lock
[/LIST]

**Function: releaseNAS**
[LIST=1]
[*]Again, wait until /var/run/nas.lock does not exist, or at least contains a number that is *not* the PID of a running process.
[*]Write the script's PID to /var/run/nas.lock again. Like before, this reduces the likelihood of a race condition (eg two scripts competing to both mount and unmount the NAS).
[*]Remove the file in /var/run/nas corresponding to the running script.
[*]Check for files in /var/run/nas with names that match the PID of a running process. If there are any, a backup is in progress, and unmounting your NAS would interrupt it. Otherwise, unmount your NAS.
[*]Remove /var/run/nas.lock
[/LIST]

Basically, the idea is that multiple backup scripts may run in parallel, but only one may be manipulating the NAS's mount point at any one time. Each script knows how many others are running, so they won't try to yank the NAS away from one another. The first one to start mounts it, and the last one to finish unmounts it.

As you may already know, my suggestion isn't *completely* bulletproof, but it should be quite reliable in practice.

Alternative (simpler) options include ...[LIST]
[*]Making backup scripts wait for each other to finish (ie a queueing system).
[*]Serialising your backups by rolling them all into one master script that executes them one after the other, perhaps with lowered CPU & I/O priority.
[/LIST]

I hope that helps.

---

### Post by radiognome on 2010-12-30
Thanks for this creative thinking.

Gives me some clues to dive deeper into using Linux. I like the one with checking a lock-file. I don't know (yet) how to obtain the PID of the script from within itself, but finding things like that is how I learn more about my favorite workhorse-OS day by day.

The idea of communicating between scripts by means of a common file is great thinking.

The scripts are too diverse to merge into one. Some things have to be done daily, some monthly, some preserve half a years versions, some none (and some in between....).

Kind regards,

Martin

---

### Post by kidders on 2010-12-30
No problem.

> **radiognome said:**
> I don't know (yet) how to obtain the PID of the script from within itselfFor a shell script ...

```
#!/bin/bash
echo My PID is $$
```I can imagine "$$" being tricky to google lol.

---

