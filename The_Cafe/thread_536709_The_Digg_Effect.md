---
title: "The Digg Effect"
date: 2007-08-28
forum: The Cafe
---

### Post by Beamerboy on 2007-08-28
I have been trying to figure out why awstats hangs when I try and process the weblogs from yesterday and now I know why.

Awstats last ran successfully at 14:10 GMT on Monday 27th August, at which point there were 13449 lines in the log file as can been seen here:

```

Create/Update database for config "/etc/awstats/awstats.conf" by AWStats version 6.6 (build 1.887)
From data in log file "/var/log/apache2/blog.paladine.org.uk-access.log"...
Phase 1 : First bypass old records, searching new record...
Direct access after last parsed record (after line 13449)

```

So why isn't awstats working? here is why:

```

wc -l /var/log/apache2/blog.paladine.org.uk-access.log
375037 /var/log/apache2/blog.paladine.org.uk-access.log

```

As you can see, apache served around 362 000 requests between 14:10 yesterday and now (07:47).  The resulting log file is somewhat large:

```

ls -al /var/log/apache2/blog.paladine.org.uk-access.log
-rw-r----- 1 root adm 95918588 2007-08-28 07:37 /var/log/apache2/blog.paladine.org.uk-access.log

```

Anyone able to think of a way to get awstats to process those logs?  I have tried starting it with nice -19 and I have also started itnormally and tried to renice -19 PID but neither have worked.  I left the process running for about 2 hours last night and it still never completed.

If I just leave awstats running is it likely to finish eventually or am I S.O.L. on this one?

Thanks in advance.

Paladine

---

### Post by Princess on 2007-08-28
does this involve getting a shovel?

---

### Post by Andrewie on 2007-08-28
if you can't handle the digg effect don't submit it to digg rofl, another poor server pwned by digg.

I got my shovel, lets get to work :lolflag:

---

