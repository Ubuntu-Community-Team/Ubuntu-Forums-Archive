---
title: "Case of the missing GB [SOLVED!]"
date: 2008-03-10
forum: The Cafe
---

### Post by LaRoza on 2008-03-10
**Post edited to point out the useful information on getting space back on Vista**

It all started on a rather normal day, checking e-mails, browsing the forum, writing code, and so on. It occured to me, as it does every so often, that I hadn't booted into Windows for a while. This task is getting rarer, but I use Windows for testing web sites, so it has its own partition, an ample size of about 35 GB. It uses less than half, and since I don't install anything, it should be enough forever. You see, I store all data on other drives and partitions, and the C: and \ partitions (of Windows and Ubuntu) are ever used for storing any files that I create or download.

I booted into Windows, which is painless enough after its initial disk thrashing. It is Windows Vista, but I have it configured to be efficient and least memory intensive. It has worked for me, and although I dislike it, it does what I want and I am happy with our arrangement.

After doing a clean of the system, with CCleaner, and checking the registry, I went to do a defrag. I had uninstalled a lot of software recently, so it may be fragmented. I started up [Auslogics Disk Defrag]("http://www.auslogics.com/en/software/disk-defrag/download"), a reliable program that I recommend, and it shocked me with its visual representation of my disk. All but 1.5 GB were used! A defrag is impossible with that amount, but I was more concerned with the missing space.

The hunt began. I checked the size of each directory in the root of the partition, the totals didn't add up to over 30 GB. I found prefetch had taken the liberty of trying to load my applications at start up, which results in hard drive thrashing when ever I log in. I disabled that and deleted all the prefetch records. It freed less than a GB.

I disabled hibernation, which should have freed some space (up to 2.5 GB, which is how much RAM I have). The command to do so is:

```

powercfg -h off

```

Because Vista has no GUI method of doing that task. That didn't free any space.

So I thought to check the pagefile, which I thought I disabled. It was small, but I disabled it anyway, as I don't come close to using all of my RAM.

[color="blue"]My final stop was the System Restore feature. This feature is something I am trying to make for Linux, and I know how restore points build up. Still, my program would have to be run more times than I could realistically do to use even 1 GB. I disabled system restore (which deletes restore points) and checked with the defragger again. 

It freed 24 GB, and the 12 GB's were for my system, just like I left it. Case solved.[/color]

Given that I use Vista rarely, and that it was able to use twice as much space for restore points than for the actual system, I no wonder why TB drives are being developed. Anyone using Vista daily will need that space for the restore points it creates behind the scenes.

---

### Post by NightwishFan on 2008-03-10
My vista partition is 70 gb and I have nothing installed already 30gb are used. T_T

I have it because I have some friends that play some starcraft some time and I am too poor to buy a copy of xp and too lazy too pirate it.

Vista is trash.

---

### Post by LaRoza on 2008-03-10
> **NightwishFan said:**
> My vista partition is 70 gb and I have nothing installed already 30gb are used. T_T

I have it because I have some friends that play some starcraft some time and I am too poor to buy a copy of xp and too lazy too pirate it.

Vista is trash.

Well, disable System Restore to free that space if that is what is using it. It seem to create restore points every time you do something (install/uninstall). It does this because the registry is to fragile...

Disabling SuperFetch seems to speed things up as well (delete all the fetch records if you do that, in C:\Windows\prefetch I think.

---

### Post by scragar on 2008-03-10
w0w, I knew some people complained that vista consumed far more space than ever before, but to make 2 full sized back-ups on a rather small space sounds very outragious...

my only counter argument about there being no back-up the entire system on ubuntu is that it generaly doesn't need one (most things can be recovered using the command line, and in the event that the command line fails then there was no hope for recovery anyway).

---

### Post by p_quarles on 2008-03-10
I killed my Vista partition a while back, but this explains something that had been confusing me back then.

I know you, LaRoza, have already seen [this](http://xkcd.com/394/), but I've been looking for a good (read any) excuse to link to it.

---

### Post by LaRoza on 2008-03-10
> **scragar said:**
> w0w, I knew some people complained that vista consumed far more space than ever before, but to make 2 full sized back-ups on a rather small space sounds very outragious...

my only counter argument about there being no back-up the entire system on ubuntu is that it generaly doesn't need one (most things can be recovered using the command line, and in the event that the command line fails then there was no hope for recovery anyway).

It isn't a full system backup, it is many restore points. 

The system restore feature on Windows is mainly a registy countermeasure, my system restore program (that I am writing, finished it, but not tested) just backs up (and can restore) essential files and directories which may be changed.

Not really rocket science, but it may make undoing system changes easier.

(My other program does the same for packages, it is able to record packages and restore them later)

---

### Post by Freddy on 2008-03-10
Thanks dude! I just did what you did some days ago, never went hunting for the reason behind why almost all of my disk space was gone though, now I guess I know why.

When I had XP installed I could at least have a 3-4 games installed on that OS but since I installed Vista Half-Life2 is all I get and maybe 4gb left. 

/thanks :).

---

### Post by LaRoza on 2008-03-10
> **p_quarles said:**
> I killed my Vista partition a while back, but this explains something that had been confusing me back then.

I know you, LaRoza, have already seen [this](http://xkcd.com/394/), but I've been looking for a good (read any) excuse to link to it.

Links to xkcd are always good (even if we know them all, like I do...)

Maybe we need an automatice xkcd subforum, where the posts are just the xkcd cartoons.

---

