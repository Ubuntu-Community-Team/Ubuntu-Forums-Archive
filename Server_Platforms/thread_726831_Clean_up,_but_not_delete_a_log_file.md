---
title: "Clean up, but not delete a log file"
date: 2008-03-17
forum: Server Platforms
---

### Post by w1z4rd on 2008-03-17
Hi

I have a large log file I use often to get stats from but I would like to remove certain entries from it. For example, say the log file is access.log and the domain fubar.com is in there a lot of times. How do I remove all fubar.com entries without deleting the whole log?

Regards

---

### Post by lloyd_b on 2008-03-17
> **w1z4rd said:**
> Hi

I have a large log file I use often to get stats from but I would like to remove certain entries from it. For example, say the log file is access.log and the domain fubar.com is in there a lot of times. How do I remove all fubar.com entries without deleting the whole log?

Regards

In a terminal window:
```
grep -v "fubar.com" logfile.txt > logfile.2
```
This will output only those lines that don't contain "fubar.com" to logfile.2.

Once this is complete, you can potentially copy "logfile.2" back over "logfile.txt" (though I would question whether this is safe or not to do while the application writing the log is still running).

Under no circumstances should you have the "grep" command redirected back to the original file - this will destroy the data you're trying to preserve!

It should also be possible to do the same thing via the "sed" command, but I'm not skilled enough with "sed" to tell you the exact syntax for "delete any line containing fubar.com".

Lloyd B.

---

### Post by w1z4rd on 2008-03-17
Thanks it worked!

---

