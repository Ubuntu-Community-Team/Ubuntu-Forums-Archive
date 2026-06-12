---
title: "(LUKS encrypted LVM) Ubuntu 11.10 running FSCK on every boot."
date: 2011-12-29
forum: Security
---

### Post by CoolBreeze47 on 2011-12-29
Hi folks

Using the Ubuntu 11.10 alternate CD, I set up a LUKS encrypted LVM with the home and swap folders encrypted as well. I've done this many times and never had any issues.

However, with the last 4-5 installs I've found it necessary to run sudo touch /forcefsck due to the system freezing during an update. I just wanted to force a system check on the next reboot to make sure everything was ok since I had to shut my PC down manually.

In doing this however, now each time I boot, the system runs an FSCK (rather than every 30 days like it's supposed to).

Is there any relatively easy way I can resolve this?.

Thanks so much for any help, CB

---

### Post by CoolBreeze47 on 2011-12-29
Couldn't find a way to move this thread to the "General Help" forum where I think it would have a larger audience and perhaps fit in better (since it's really not a post about security but rather, a question about booting, etc).

Oh well...I'll just repost. Please delete this one and accept my apology :P

- CB

---

