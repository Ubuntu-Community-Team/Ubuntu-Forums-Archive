---
title: "Random Reboots"
date: 2009-09-18
forum: Server Platforms
---

### Post by tjhart85 on 2009-09-18
Hi,

I just set up my Ubuntu Server 9.04.

It has SSH installed.  It is my File server & Torrent downloader with RUtorrent webui.  I have a software RAID5 with 4 1TB drives with jfs file system.  The system is on a seperate 10GB drive that I ran badblocks on, which showed no problems.

NOW, for what it's doing:  It randomly restarts.  I have no idea why!  Are there any logs that I can check that would give me some explanation of what it was doing when it restarted?

---

### Post by hessiess on 2009-09-18
Clean it out, restarting/powering off sugests that its overheating.

---

### Post by tjhart85 on 2009-09-18
I'll do that & add a couple more fans while I'm at it.

I guess 5 hard drives total can easily heat the system up quite a bit.

Are there any logs that show why it turns off though?

---

### Post by hessiess on 2009-09-18
> **tjhart85 said:**
> I'll do that & add a couple more fans while I'm at it.

I guess 5 hard drives total can easily heat the system up quite a bit.

Are there any logs that show why it turns off though?

/var/log/kern.log maby. Though if its just shutting off due to overheating its unlickly to be logged as that's a hardware protection feature.

---

