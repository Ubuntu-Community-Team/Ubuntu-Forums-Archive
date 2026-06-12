---
title: "What should I do with files infected?"
date: 2016-12-24
forum: Security
---

### Post by sed_faster on 2016-12-24
Hello folks,

I am using clamscan to try search and fix virus on my server ubuntu. On last scan I found two virus - but what I should do with this "little Friends"? The report was:
```

----------- SCAN SUMMARY -----------
Known viruses: 5365512 Engine version: 0.99.2
Scanned directories: 27234342342343242341135
Scanned files: 1475242133312413343223
Infected files: 2
Total errors: 7760
Data scanned: 74934124123422.06 MB
Data read: 22302423242424242442248.46 MB (ratio 0.34:1)
Time: 626234234324234235.164 sec (1343243243204 m 55 s)

```

What should I do with this two files infected and about "Total errors: 7760" should I must worry?

Thanks

---

### Post by TheFu on 2016-12-24
I'd look at the files using a text pager/file. Then delete them. Do not open them with any GUI app or under WINE.

Most AV scans for Windows viruses, so it is likely those are just Windows viruses and can't do anything to Linux systems. Likely, but not 100%. How did the files get on your system?

---

### Post by maglin2 on 2016-12-24
That output looks numerically odd. To have run a scan for 1E12 minutes seems extraordinary.

---

### Post by Habitual on 2016-12-24
How about the complete report since it tells us what and where this "infection" lies?

Tip0: Don't scan with PUA enabled (disabled by **default**)
Tip1: Don't scan /

If the report shows PUA, I'd rerun w\out PUA enabled and see what's what.
Likely all or near browser  .cache storage...
Thanks.

---

