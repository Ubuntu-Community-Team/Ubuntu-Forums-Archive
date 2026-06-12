---
title: "Is there a way to NOT delete old log files with logrotate?"
date: 2015-04-17
forum: Server Platforms
---

### Post by Raner on 2015-04-17
I want to use logrotate to rotate old log files to a new folder, but I do NOT want to delete them. What options should I specify in a logrotate.conf file in /etc/logrotate.d to do this?

I found that "rotate 0" deletes logs immediately, and then setting any number past that just rotates it after that many rotation periods.

I thought maybe not specifying a rotate parameter in the logrotate.conf would work, but since I don't want to risk data loss, I don't want to leave it to chance. I couldn't figure this out from the man page.

---

### Post by CharlesA on 2015-04-17
Not natively it seems.

See here:
[http://serverfault.com/questions/437841/how-can-i-rotate-many-log-files-into-a-different-subdirectory-per-rotation](http://serverfault.com/questions/437841/how-can-i-rotate-many-log-files-into-a-different-subdirectory-per-rotation)

---

### Post by Raner on 2015-04-17
Thanks. 

Would you happen to know what happens if you leave out the "rotate" parameter all together? This was my first guess, but I can't find it documented what the default is if this is left unassigned. (I do specify rotation by size and date. (monthly, size 100kb)).

---

### Post by CharlesA on 2015-04-17
It should be in the man page.
[http://linuxcommand.org/man_pages/logrotate8.html](http://linuxcommand.org/man_pages/logrotate8.html)

---

### Post by Raner on 2015-04-18
Thanks. Unfortunately the man page did not say. I expect it either defaults to something, or if I am lucky, doesn't put a cap the rotation, but I am completely unsure.

>  **rotate** *count*
              Log files are rotated <count>  times  before  being  removed  or
              mailed to the address specified in a **mail** directive. If *count* is
              0, old versions are removed rather then rotated.

---

### Post by CharlesA on 2015-04-18
Probably defaults to deleting the log files if it's not specified, but I don't know for sure.

Would probably have to look at the source code to find out for sure.

---

### Post by SeijiSensei on 2015-04-18
If you use "weekly" or "monthly" and set the rotate parameter to a large number it will be the equivalent of not deleting anything at all.  For instance, "weekly" plus "rotate 53" would give you a complete year's worth of logs.  I'm not certain there's much value in holding stuff beyond a year or two unless you are required to do so by law.  I suggest also using the "compress" option if you're logging this much.

---

### Post by Raner on 2015-04-18
Thanks for the help. Setting the rotate option to a very large number is what I ended up doing.

---

