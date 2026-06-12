---
title: "Input/Output error"
date: 2008-10-26
forum: Server Platforms
---

### Post by youaredoome0 on 2008-10-26
My server has been responding to various commands such as sudo and shutdown with "-bash: /usr/bin/sudo: Input/output error". I picked this system up off the street and installed a 7-year old hard drive I got for free in it. It's recently been making hard drive noise without the HD light flashing.

---

### Post by cariboo on 2008-10-26
You may want to go to your hard drive manufacturers web site and download their diagnostic tools and check you hard drive, it sounds like it is failing.

Jim

---

### Post by lykwydchykyn on 2008-10-27
You can also check dmesg for disk I/O errors, and run badblocks to try to diagnose it.  Your post seems to make a good case for it being HDD problems, though, so I'd guess you just need to go ahead and swap it out, then test the old on at your leisure.

---

### Post by youaredoome0 on 2008-11-01
Both badblocks and fsck are giving me an Input/Output error. I also notice frequent failures when attempting to access files over SFTP.

---

### Post by lykwydchykyn on 2008-11-02
I'd say it's toast.  Have you tried to reboot?  It probably won't come back up.

---

