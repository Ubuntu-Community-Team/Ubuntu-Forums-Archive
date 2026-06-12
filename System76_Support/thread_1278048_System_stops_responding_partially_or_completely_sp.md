---
title: "System stops responding partially or completely sporadically."
date: 2009-09-29
forum: System76 Support
---

### Post by Trevor Bramble on 2009-09-29
I'm occasionally get severe freezing on my system.  I hadn't pinned it down until catching this in the messages log:

> Sep 28 23:13:13 wayfarer kernel: [36940.300992] ata3.00: configured for UDMA/133
Sep 28 23:13:13 wayfarer kernel: [36940.301016] ata3: EH complete
Sep 28 23:13:16 wayfarer kernel: [36943.325504] ata3.00: configured for UDMA/133
Sep 28 23:13:16 wayfarer kernel: [36943.325536] ata3: EH complete
Sep 28 23:13:19 wayfarer kernel: [36946.357092] ata3.00: configured for UDMA/133
Sep 28 23:13:19 wayfarer kernel: [36946.357122] ata3: EH complete
Sep 28 23:13:22 wayfarer kernel: [36949.581118] ata3.00: configured for UDMA/133
Sep 28 23:13:22 wayfarer kernel: [36949.581148] ata3: EH complete
Sep 28 23:13:27 wayfarer kernel: [36954.745493] ata3.00: configured for UDMA/133
Sep 28 23:13:27 wayfarer kernel: [36954.745517] ata3: EH complete
Sep 28 23:13:30 wayfarer kernel: [36957.969560] ata3.00: configured for UDMA/133
Sep 28 23:13:30 wayfarer kernel: [36957.969592] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Sep 28 23:13:30 wayfarer kernel: [36957.969600] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Sep 28 23:13:30 wayfarer kernel: [36957.969610] Descriptor sense data with sense descriptors (in hex):
Sep 28 23:13:30 wayfarer kernel: [36957.969614]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 28 23:13:30 wayfarer kernel: [36957.969635]         1a 69 24 e8 
Sep 28 23:13:30 wayfarer kernel: [36957.969643] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Sep 28 23:13:30 wayfarer kernel: [36957.969695] ata3: EH complete
Sep 28 23:13:30 wayfarer kernel: [36957.975606] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Sep 28 23:13:30 wayfarer kernel: [36957.975655] sd 2:0:0:0: [sda] Write Protect is off
Sep 28 23:13:30 wayfarer kernel: [36957.975721] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 23:13:30 wayfarer kernel: [36957.975791] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Sep 28 23:13:30 wayfarer kernel: [36957.975827] sd 2:0:0:0: [sda] Write Protect is off
Sep 28 23:13:30 wayfarer kernel: [36957.975888] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

A Google search didn't turn up much except some scary talk about filesystem corruption.

What can I do to examine my filesystem for disrepair?  What else may be causing this trouble?

Thanks in advance!

---

### Post by thomasaaron on 2009-09-29
*After* the next freeze, please restart your computer and go *immediately* to System > Admin > System76 Driver and click the Support tab and the Create button.

It'll create a logs.tar archive in your home directory. Please attach that archive to this thread.

Also, please include information in your next post about which System76 Model you have, what software is running during the freeze, etc...

The more info the better.

---

### Post by Trevor Bramble on 2009-09-29
This is a Serval Pro v3. I'll dump a process list in the next one.  It won't show any smoking gun of course, because the resources will already have been released and the system will be usable again.

I *was* blaming Eclipse, but the above event happened after I'd swapped in Komodo IDE.  Eclipse uses ~500MB of memory per instance (I'll sometimes run 2) and I'll often have SQL Developer up at the same time (another few hundred megs of Java).

But it looks like Eclipse was often the first app to stop responding just because it was using the most resources and it had focus more often than any others (usually Rhythmbox, Thunderbird, Chromium, and ~2 Firefox instances/profiles).

Requested log dump and process list coming on the next freeze.

Thanks, Tom!

---

### Post by Trevor Bramble on 2009-10-09
I keep experiencing this when I don't have time to do anything about it.  But I managed to restart and generate the logs as requested a couple of days ago.  (See attached.)

Software running at the time can be any combination of common programs I run.  I touched on some of them earlier.  Here are some more: apache, mysql, jungledisk (installed after this started), firestarter, Urban Terror, XChat... the list could go on for awhile; I'm pretty active on the system.

I haven't been able to pin down software that has to be running for this to occur, if any actually exists.

---

### Post by thomasaaron on 2009-10-09
> Oct  7 00:01:15 wayfarer kernel: [76585.075296] compiz.real[22266]: segfault at 8 ip 0000003ccbed7973 sp 00007fffd1a54f10 error 4 in libGLcore.so.180.44[3ccb400000+da2000]

This looks like it's probably to blame. A compiz segfault.

The only place I see that particular error message online is in this thread, and the person is running Jaunty inside a VM...

[http://forums.somethingawful.com/showthread.php?threadid=3123824&pagenumber=4](http://forums.somethingawful.com/showthread.php?threadid=3123824&pagenumber=4)

Could be one of your compiz plugins conflicting with something you're running, though. My first guess would be Urban Terror.

---

### Post by Trevor Bramble on 2009-10-09
> **thomasaaron said:**
> This looks like it's probably to blame. A compiz segfault.

The only place I see that particular error message online is in this thread, and the person is running Jaunty inside a VM...

[http://forums.somethingawful.com/showthread.php?threadid=3123824&pagenumber=4](http://forums.somethingawful.com/showthread.php?threadid=3123824&pagenumber=4)

Could be one of your compiz plugins conflicting with something you're running, though. My first guess would be Urban Terror.

A fair guess, though on reflection I don't think it's happened while I was in a game, which is surprising because I play often.

I think I have noticed a pattern though, with JungleDisk running every morning, it is triggered during the backup.  So it seems storage-related to me.  I think the segfault may be unrelated (I was toying with conky around that time, maybe the culprit?)

PS. Something Awful forums?  *shudder*

---

### Post by thomasaaron on 2009-10-09
Just looked back through your logs.

There are some hard drive related erros, but they are a good 30 minutes before your crash.

Could be multiple issues too.

---

### Post by Trevor Bramble on 2009-10-12
A clue!

This seems to happen every half hour, HH:20 and HH:50.  I checked crontab for my account and for root and I only have my nightly backintime job in there.  Tracker indexing is disabled.  Update Manager is configured to check only daily as well.

Rhythmbox was configured to check hourly for podcast updates, but I only listen to two of those, so I set that to manual, at least for now.

Thunderbird is checking for mail constantly w/ IMAP so that can't be it.

JungleDisk wasn't even installed when this started, so it's not that.

I've attached a process list.  Would you mind trying to identify anything suspicious?  This is a more or less typical snapshot of what's going on with my system at any given time.  So if there's some background process amping up every half hour, and not something that fires up, make me unhappy, then dies, it will hopefully be visible to the trained eye....

---

### Post by Trevor Bramble on 2009-10-13
The half-hour schedule appears to be based on the time the system is booted or brought out of suspension.

---

### Post by Trevor Bramble on 2009-11-10
For the record:

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/426556](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/426556)

I think that's the culprit.  It rarely happens without having suspended, but when I have awakened the computer from suspension, it happens like clockwork.

---

