---
title: "Command to search log file and delete lines that contain a specific string of text?"
date: 2019-12-11
forum: Server Platforms
---

### Post by Robert_Boutin on 2019-12-11
Not trying to do anything shady.  I have a Nextcloud installation on Ubuntu 18.04 Server that I upgraded and my nextcloud.log exploded and consumed nearly my entire hard drive.  I corrected the problem that was causing the log entries and I want to delete those entries from the log file but keep everything else.  Problem is that there is an entry every second since October for this particular warning so deleting line by line isn't really an option.

I've been searching online and I can find how to search a file for a string of text but haven't found something that explains how to actually delete the full line of text from the file.

Can anyone help point me in the right direction?  Thanks

EDIT:  Found a solution using **sed**, just needed to search harder.

---

