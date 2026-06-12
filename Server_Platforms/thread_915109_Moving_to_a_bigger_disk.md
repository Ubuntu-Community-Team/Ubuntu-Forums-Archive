---
title: "Moving to a bigger disk"
date: 2008-09-09
forum: Server Platforms
---

### Post by Vegan on 2008-09-09
After searching, I best ask. My server has a smallish 30GB disk and while the phpBB will take a while to fill it, eventually it will become stuffed with content.

Now I realize I can paste a disk into the system easy enough, but I wanted ideas to back up the SQL database and just do a fresh install of everything with a new larger disk.

The web site is a simple FTP copy.

---

### Post by schettj on 2008-09-09
mysql? phpmyadmin will dump/restore it, or you could just google for the correct sql commands to dump it. Something like dump database should do it. ([http://yoursql.ludit.it/Help/sqldumps.html](http://yoursql.ludit.it/Help/sqldumps.html)) 

You'll still need to note and re-create the users/permissions (or at least I did last time I did this using phpmyadmin)

Seriously tho, just add a big disk and mount it on whatever dir your database is using --- or more accurately
- mount new disk in temp path
- stop the database
- mv database files to new disk
- unmount disk
- mount disk onto dir database uses
- restart database
- Enjoy

And where did you find a 30 gig disk? Those are so 2000

(fun/interesting page about disk capacity here [http://www.alts.net/ns1625/winchest.html](http://www.alts.net/ns1625/winchest.html)) - I just recently got a 1GB sata for $100. Wild.

---

### Post by Vegan on 2008-09-09
I am using an old machine right now, an old IBM 300 GL with a 30 Gb disk. I plan to replace the machine eventually and wanted to move the site to a whole new platform lock stock and bbl.

---

