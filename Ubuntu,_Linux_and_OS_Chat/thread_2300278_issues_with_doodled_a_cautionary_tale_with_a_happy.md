---
title: "issues with doodled: a cautionary tale with a happy ending"
date: 2015-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by ray field on 2015-10-24
just wanted to put something up here so it shows up in the archive in case anyone has this problem in the future: I believe most users should consider avoiding doodled.

"doodle" can be used to index and search metadata in files -- very useful if you have media files in a number of places, or with confusing names. it's quite old (~2008?) but works very nicely. installed it yesterday and was sufficiently pleased with it to shortcut some batch search capabilities in my .bashrc.

"doodled" is a daemon designed to monitor directories and index them when they've changed -- when I was installing it, I did see some references to problems with accessing HDD partitions of a more recent design. didn't think much about it.

this morning I needed to reboot, and found I couldn't access my main Ubuntu installation -- after the initial logo, the screen would go black -- couldn't even get to the login screen. I kind of got the cold sweats, figuring now I was going to have to spend a day trying to diagnose the problem (bad power supply?), which would likely frustrate me enough that I'd just decide to replace the whole system for who knows how much money.

an hour and a half later, continuing my efforts to recover from the boot console, I finally took the trouble to read through the agate type; there at the top, before the various failures and kernel panics, was "doodled daemon starting." I booted to the root prompt, un/re-mounted the drive r/w, removed doodled -- and rebooted successfully, thankfully.

the moral: remember what you did, and pay attention.

---

### Post by QDR06VV9 on 2015-10-24
Glad things worked out for you!
In testing I often forget changes made to my system, So I decided to keep voice memos or notes or instructions to myself.LOL
The Older I get the better I was.
Thanks for the share.
Regards

---

### Post by tgalati4 on 2015-10-24
Did doodled lock up your system, or was it so busy indexing, that it looked like a freeze?  This is common behavior with indexers.  Try again, but let it run for a while.

---

### Post by Bucky Ball on 2015-10-25
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request, but thanks for sharing.

---

### Post by ray field on 2015-10-25
apparently I didn't make it clear enough (?) -- doodled made it impossible to boot *at all*.

---

