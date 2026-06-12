---
title: "Will the low-latency kernal guard against rsync high CPU usage?"
date: 2016-07-09
forum: Ubuntu Studio
---

### Post by Zorrokan Zenovka on 2016-07-09
Hi

I'm writing some rsync scripts to automate backup.

Now I could simply use cron to run the jobs on schedule, but my concern is that even with the low-latency kernal, rsync might chew up a lot of CPU cycles and cause glitches if recording when a backup starts.  

So I'm interested to know if the low-latency kernel would guard against this, always prioritising audio or if i need to run nice against the cron job, for example:

0 6 * * *   /usr/bin/nice -n 19 /root/scripts/backup.sh > /dev/null 2>&1

If not that, I could use batch to run the backup script whenever it detects system resource using has been low for sometime, indicating that no one is using the computer to record anything.

Any advice would be gladly received


A

---

