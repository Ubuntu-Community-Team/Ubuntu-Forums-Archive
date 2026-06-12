---
title: "Sun Netra T1 105 UltraSparc Crash"
date: 2006-11-28
forum: Sun Sparc Users
---

### Post by redman5087 on 2006-11-28
Hello,
I have a Sun Netra T1 105 ultrasparc with Linux (Ubuntu Server) installed.
Every night the machine stops working. I don't know what just happens. Is it a crash? Is it a network problem? When this happens, I can access the computer with the "lom" and I can get the "ok" prompt but I can not access the system itself anymore(the operating system)! Also the secure shell doesn't work anymore. And the apache server is not reachable anymore. I have to reboot the system to get it working.
I have checked the logs but nothings interesting shows up.

Can anyone help me,

Kind regards,

---

### Post by timcredible on 2006-11-28
if dmesg doesn't have anything, maybe check to see what cron jobs are kicking off at night.

---

### Post by redman5087 on 2006-11-28
> **timcredible said:**
> if dmesg doesn't have anything, maybe check to see what cron jobs are kicking off at night.

Dmesg doesn't show up anything interesting. I will check the cron jobs.
That I can access the "OK" prompt and the "lom" prompt but not the operating system does that mean that it is crashed?

---

### Post by redman5087 on 2006-11-28
> **timcredible said:**
> if dmesg doesn't have anything, maybe check to see what cron jobs are kicking off at night.

I think I don't have any cronjobs running.

---

### Post by redman5087 on 2006-11-29
After further analyses, I think the machine stops because of inactivity.
WHen I stay logged in by SSH or by the "lom" it doesn't happen.
Could this be something with the power management.

---

### Post by redman5087 on 2006-12-04
Any help would be appreciated.

---

### Post by yonderway on 2006-12-31
I am having a hell of a time just getting Edgy to install on my Netra T1 105.

The guided partitioning works ok, but online resizing of ext3 doesn't work so I'd rather use ReiserFS or XFS.  What a pain.

And just when you think you have it all set, the scsi driver loses track of the disk and /dev/sda disappears.

Linux on sparc is still very immature.  Aurora Linux is supposed to be one of the most mature sparc distros and I had to rip it off all my machines because rpm was forgetting about packages it installed.

This experience has been maddening enough to just about drive me back to OpenBSD.

---

