---
title: "mdadm vs. evms"
date: 2006-07-18
forum: Server Platforms
---

### Post by rmjb on 2006-07-18
Hi, I used evms to "reactivate" a software RAID-1 I had on my PC before I installed Ubuntu and it worked great, just as expected.

Then I used it to create a software RAID-5 as /dev/emvs/raid5 that maps to /dev/md0. That worked fine, but evms did not indicate that the RAID-5 was rebuilding.

Anyhow, it took almost 24 hours to rebuild all the while I'm waiting impatiently on it. I then rebooted the server to change an IDE cable for better performance, and wouldn't you know it, it started to rebuild AGAIN!

This time it took almost 12 hours, but again I was impatient and I wanted to test if it had to rebuild on each reboot (I know it shouldn't have to) so before it was finished rebuilding I tried to mount /dev/md0 but got an error that the device was busy... okay... so I try to mount /dev/evms/raid5 and it mounts, and I can use it. I stored files made folders and so on.

So how can evms enable that access to a rebuilding device when md won't even do it?

Oh, and after the second test reboot, it didn't have to rebuild again, though the Xubuntu screen paused for a long time at the "Mounting root filesystem" line.

- rmjb

---

