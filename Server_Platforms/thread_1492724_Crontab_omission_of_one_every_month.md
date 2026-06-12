---
title: "Crontab omission of one every month"
date: 2010-05-25
forum: Server Platforms
---

### Post by redelek on 2010-05-25
Hey  everyone,

I set a backup copy of your home computer.
I have a problem.
A copy of the full exercise once a month
```
15 22 1 * * /  root / scripts / bcsys.sh full
```incremental and  would like to do on a daily basis since 22, but aside 1 day each  month when it comes to full

```
00 22 * * * /  root / scripts / bcsys.sh incremental
```How can this be set and whether there is a possibility?

Best regards
Redelek

---

### Post by Groodles on 2010-05-25
> **redelek said:**
> Hey  everyone,

I set a backup copy of your home computer.
I have a problem.
A copy of the full exercise once a month
```
15 22 1 * * /  root / scripts / bcsys.sh full
```incremental and  would like to do on a daily basis since 22, but aside 1 day each  month when it comes to full

```
00 22 * * * /  root / scripts / bcsys.sh incremental
```How can this be set and whether there is a possibility?

Best regards
Redelek

So if I understand correctly, you want to do;

1)  A full backup at 22:15 on the 1st day of every month.
2)  An incremental backup at 22:00 on every day EXCEPT the 1st of the month.

The Full backup:
```
15 22 1 * * /path/to/full/backup/command
```The incremental backup:
```
00 22 2-31 * * /path/to/full/incremental/command
```By using the range "2-31" for the day of the month you specify all days except the 1st day.  Check out "man crontab".

---

