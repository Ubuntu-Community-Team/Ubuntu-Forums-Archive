---
title: "rdiff-backup removals"
date: 2020-11-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2020-11-27
Cannot find a definitive answer.  rdiff-backup offers the removal of backed up version 'older -than' - lets say 30days.  In the scenario where a machine is not use for 3 months and has a backup perform on day 98 (compared to the last backup) what happens?  I assume all the previous version backups are deleted and there is only one backed up version saved.

---

### Post by TheFu on 2020-11-27
Any single backup over 30 days old is removed, unless you don't use the --force option and multiple backups were made on the same date OR you didn't run the cleanup daily.  Easily tested.  And to me, the manpage was clear about this.
```

       --remove-older-than time_spec
              Remove  the incremental backup information in the destina&#8208;
              tion directory that has been around longer than the  given
              time.   time_spec  can  be  either  an absolute time, like
              "2002-01-04", or a time interval.  The time interval is an
              integer  followed by the character s, m, h, D, W, M, or Y,
              indicating seconds, minutes, hours, days,  weeks,  months,
              or  years respectively, or a number of these concatenated.
              For example, 32m means 32 minutes, and 3W2D10h7s  means  3
              weeks,  2 days, 10 hours, and 7 seconds.  In this context,
              a month means 30 days, a year is 365 days, and  a  day  is
              always 86400 seconds.
...
              By default, rdiff-backup will only delete information from
              one  session at a time.  [B]To remove two or more sessions at
              the same time, supply  the  --force  option [/B] (rdiff-backup
              will tell you if --force is required).
```

Use the --force option and it always works the same way.

---

