---
title: "Build a new server"
date: 2007-05-19
forum: Server Platforms
---

### Post by mikeyandmary on 2007-05-19
Hi all,

My current webserver is an old AMD Duron 750. I would like to build a faster server with more storage. The server will be used as a webserver and a fileserver. I plan to have the server online 24/7. I would like to setup a RAID to protect against data loss and want 250-500GB total capacity. For the record (and to help with spending recommendations) I live in Sydney, Australia.

So here are my questions...

Is SATA storage better than parallel ATA?

Intel or AMD for the processor? (I was thinking Core2Duo)

What is the best motherboard?

Are RAID/Enterprise drives better than consumer (cheaper) drives?

How much memory?

Should I just add more storage and RAM to my current machine and use software raid?

Will any "speed" upgrades be noticed when accessing over the internet? (I have Bigpond cable which I think is 128k upload)

Thank you, thank you, thank you for your help :KS

---

### Post by craigp84 on 2007-05-20
> I would like to setup a RAID to protect against data loss 

Common misconception, backups help mitigate the risk of data loss. RAID just helps reduce downtime. e.g. raid wont protect your data if you accidentally do rm -rf wrong_folder/

Invest in a good backup strategy before RAID, although RAID's a nice to have if you've got the backup & recovery plan nailed.

> want 250-500GB total capacity.

The larger the RAID volume, the longer it takes to recover in case of a disk failure, but that's by the by if this is a home server, you can just leave it turned on for a day or so to recover.

> Is SATA storage better than parallel ATA?

Just purely because you no longer have to deal with those bloody wide PATA cables, hell yeah, it;s a shed load better!

> Intel or AMD for the processor? (I was thinking Core2Duo)

I read all the hype about the intel stuff being soooo much better than the AMD stuff nowadays. But you know what, that's not my experience. Maybe those intel chips are technically better in some mathematical benchmark tests, but the AMD stuff just "feels" faster.

So like clicking on an icon on the desktop, just opens the app slightly faster under AMD chips than similarly priced intel chips.

Also on the server i've been able to verify this a bit more, with similar priced chips, the AMD stuff will be faster compute (i look after a compute grid in my day job of a couple of thousand servers).

I've been try to work out why this may be, but the only thing i've turned up is that AMD contribute to GCC (the software compiler - the thing used to build all your programs & linux kernels etc.,), and that they ensure GCC takes full advantage of the hardware, whereas intel do not, so code genereated by gcc for intel is not as optimised.

Maybe someone else can help me out with this, it's really been puzzling me for quite a while.

> Are RAID/Enterprise drives better than consumer (cheaper) drives?

Nope. And unless you're going to spend a good few hundred on a hardware RAID card, just use software raid. The cheaper raid cards are *not* better than software raid (except for RAID0 - which you prob wouldn't use anyway, linux LVM offers too many advantages).

Its the old story about the RAM, buy as much as you can afford, linux will use it sensibly.

Hope this helps,

Craig

---

### Post by regomodo on 2007-06-01
There's a lot of information here

[http://www.smallnetbuilder.com/](http://www.smallnetbuilder.com/)

I'm looking to build a raid5 file server. Mainly because to prevent data loss from a failing HDD (i've experienced that unpleasantness) and to keep my files separate from my Linux experiment shenanigans (i've just totaled a drive because of that).

I was going to raid5 in my comp, but as the poster above says, that won't keep you from losing your data due to a cockup

---

### Post by craigp84 on 2007-06-01
A fairly effective way to do backups for the average low value file server, is to do "poor man's raid". The concept is simple - thankfully so is the application :)

Let's say you have 2 x 500Gb drives. You could RAID1 them. This will ensure that if one drive goes south, the other lives on, and you get no downtime.

You could choose to run with only 1 drive, then schedule a cron job to copy the contents of disk 1 onto disk 2, say every 4 hours.

At this point what you have is nearly RAID1 - except, it resynchs every 4 hours instead of immediately. The down side at this point is it takes a while to copy all of disk 1 to disk 2. Also, it's only one backup, not much history. You'd really be better with RAID1 at this point, but stick with it...

Now, if you use something smarter than just a copy, like rsync, you drop the copy time too maybe a few mins. Go one step further and use the excellent "rsnapshot" - which is really just some wrapper scripts around rsync and cp - and you get weekly, daily and hourly backups which take minutes to perform.

But it's still not a great backup, if you issue an rm -rf / - you're probably going to manage to blitz the live disk, and the copy disk.

So, you arrange to have the copy disk mounted read -only at all times, except when making backups to it (you also probably arrange to mount it with the "sync" option, see man fstab). You'll find there's an option in rsnapshot's config to issue a command before and after a backup.

Let's say /data is your data disk, and /backup is your backup disk, then the fstab for /backup looks something like:

```
/dev/sda2    /backup    ext3    defaults,ro,sync    0 0
```

And the command to have issued before backup is:

```
mount -w -o remount /backup
```

And afterwards to set it read only again:

```
mount -r -o remount /backup
```

Now what you have is a fairly effective, cheap backup solution. It's clearly not the best solution in the world (what if the building goes on fire, there's no offsite backup) - but it's only cost you an hour or so to setup and you're in a much better situation should you rm -rf /data. Whereas is /data was a raid array (and so there was no /backup) you'd be up sh1t creek without a paddle as they say.

Obviously you're trading in uptime / resiliency to failure for the backups, so for this to make sense, you have to accept down time in case of a drive failure. For most home users / small setups, that's not an issue when they know their data's still safe :-)

Hope this helps,

-c

---

### Post by regomodo on 2007-06-01
craig. You make a good point.

I had thought about it as my RAID idea would mean i would have 500GB sata lying about. My plan b was to get another 500GB drive but keep it out of the fstab (unmounted) and somehow copy data from the main drive to the backup through a script.

I don't know what i'll do. I'll probably get that extra drive (~£60) and it should do for know, then think about  a fileserver later. I just get a little carried away and excited when i think of  a new project to do.

---

### Post by obrient on 2007-06-01
> Will any "speed" upgrades be noticed when accessing over the internet? (I have Bigpond cable which I think is 128k upload)

Unfortunately you could have all of the things that others mentioned above but with 128K upload you will not see a major difference in speeds. You will be limited to the 128K speeds since that is all your network connection will allow. 

However for the data storage  within your own network I would bet you might notice a difference in speed between an older machine and a new machine. This will be especially noticable if you went to Gigabit networking within your network.

---

