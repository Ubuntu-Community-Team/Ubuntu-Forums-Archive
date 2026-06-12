---
title: "etc/printcap on printer-less server?"
date: 2008-08-06
forum: Server Platforms
---

### Post by Carleas on 2008-08-06
For some reason, the cron daemon emails me every day telling me that it cannot find printcap:  
```
/etc/cron.daily/lprng:
. . . Read_file_list: cannot stat required or included file '//etc/printcap' - No such file or directory
```
I don't have any printers, so I don't have a printcap file.  Shouldn't cron stop looking for printers if this file doesn't exist?

---

