---
title: "Syncdaemon taking 100% cpu"
date: 2011-07-26
forum: Ubuntu One (CLOSED)
---

### Post by rickbeton on 2011-07-26
Hi,

I know other threads have raised similar issues to mine but I haven't been able to find in them a solution to my problem...

My laptop cannot complete its Ubuntu One sync - the syncdaemon never stops running at 100%.  After a few hours, I give up and kill it off.

It writes large amounts to .cache/ubuntuone/log/syncdaemon.log for a while but then stops writing anything, even though it continues running at 100%.

Whilst it is working so hard (doing nothing?), the file manager is virtually unusable.

The problem started when I (a) installed Magicicada and (b) added another 700Mb folder to my synced folders.

My desktop PC doesn't have this problem. They are both very similar Ubuntu installations except it has a conventional hard disk whereas the problem laptop has SSD.

Any suggestions?

Rick

---

### Post by cbennett926 on 2011-08-02
What does the Magicicada program do?

---

### Post by duanedesign on 2011-08-04
@rickbenton - Does anything get written to .cache/ubuntuone/log/syncdaemon-exceptions.log

@cbennett926 - Magicicada is a GUI for the syncdaemon. It is usefull for showing you more information about ubuntu one is doing. You can get the same info using the command line tool u1sdtool but Magicicada puts the info in a nice GUI.

---

