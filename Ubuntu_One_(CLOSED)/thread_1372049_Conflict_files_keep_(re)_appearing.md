---
title: "Conflict files keep (re) appearing"
date: 2010-01-04
forum: Ubuntu One (CLOSED)
---

### Post by candtalan on 2010-01-04
I have a bunch of .u1conflict files, and I removed the files having incomplete content and renamed some conflict files to remove the extension. However, the conflict files recur.

What should I do?

---

### Post by joshuahoover on 2010-01-15
> **candtalan said:**
> I have a bunch of .u1conflict files, and I removed the files having incomplete content and renamed some conflict files to remove the extension. However, the conflict files recur.

What should I do?

First, are you synchronizing content with two or more computers? If so, it's possible the conflicts are resulting from changes being synced from one and conflicts resulting on the other. If you are not synchronizing two or more computers and you aren't uploading files via the web, then this is a bug. If this is the case, please do the following:

1) Quit the Ubuntu One client
2) Open (or create if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf  
    Add the following 2 lines to this file and save: 
[__main__][FONT=monospace]
[/FONT]log_level = DEBUG

3) Restart the Ubuntu One client  
4) Attempt to synchronize files as you have been and try to get the conflicts
5) File a new bug by right-clicking on the Ubuntu One Client and select "Report a Problem"
6) In the bug report, attach the following file: ~/.cache/ubuntuone/log/syncdaemon.log
7) Mark the bug report as private by clicking on the yellow pencil icon next to the "This report is public" in the upper right hand corner of the page and select "This bug should be private"

We'll review this bug and follow up with you in the bug report.

Thank you,

Joshua

---

