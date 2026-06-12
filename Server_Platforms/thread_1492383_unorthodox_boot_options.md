---
title: "unorthodox boot options"
date: 2010-05-24
forum: Server Platforms
---

### Post by Vegan on 2010-05-24
OK I have this pathetic machine I am using for the web server while I put together the replacement.

It has a disk limitation. I put a VIA USB2 card on the machine and now I can mount no problem.

So how about reinstall to the USB storage and simply put a loader on the small obsolete hard disk?

Any ideas on making that work?

---

### Post by arrrghhh on 2010-05-24
I'm guessing the problem is the BIOS won't boot from USB?

---

### Post by volkswagner on 2010-05-24
You could start by installing "/boot" on the internal (provided it has at least 100MB avail space it should be sufficient) drive and "/" on the USB drive.  If you have boot issues, you may have a little debugging to get the USB to automount.

---

