---
title: "Windows XP problem - won't boot from hard drive"
date: 2007-07-11
forum: Windows
---

### Post by epimer on 2007-07-11
I'm trying to help a friend out with his Windows XP, and I've hit the limits of my knowledge on the matter (didn't take long!). The problem is that his laptop won't boot off the hard drive. I used the INSERT LiveCD to have a looksee, and it booted fine, and the hard drive could be mounted with no problems (data looked intact, etc.).

So what do I do know? The ideal solution would obviously be to get the drive bootable again without having to format/reinstall etc. - but I don't know how!

---

### Post by loserboy on 2007-07-11
what does it say when you just try to do a normal boot?  the boot record may be corrupted

---

### Post by smoker on 2007-07-11
hi, does it try to boot, or just nothing? any error messages? any abnormal sounds coming from the hard drive?

if you have the xp install disc you could boot from it, go into the recovery console and do a 'chkdsk /f /r ' and see if that will help. you could also, from the recovery console, try the 'fixmbr' and 'fixboot' commands (all without quotes), if none of those do any good, you could try a 'repair' install, which won't overwrite apps and data (still best to have a backup, though).

to check the integrity of the hard drive incase of mechanical failure, download and burn a bootable copy of 'drive fitness test'
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

best of luck

---

### Post by LaRoza on 2007-07-12
You could restore the MBR with the Super Grub Disk.

Even if the MBR is not the problem, using it will cause no harm.

---

