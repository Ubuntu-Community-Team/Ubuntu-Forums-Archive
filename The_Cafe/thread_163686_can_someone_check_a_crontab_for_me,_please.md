---
title: "can someone check a crontab for me, please?"
date: 2006-04-21
forum: The Cafe
---

### Post by ice60 on 2006-04-21
hi, i've been trying to check this cron for a few days lol, i asked in Ubuntu 5.10 Support and a few IRC channels.

all i want to know is if it does what i want it to do. this is what i want it to do - run Mon and Tues at 16:55, 17:55 and 18:55.

this is the command, which i found on the Ubuntu Blog
```
find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```

and this is what i want to put in crontab -e
```
55 16-18  * * mon,tue find ~/.thumbnails -type f -atime +7 -exec rm {} \;
```

is this bit correct? 55 16-18  * * mon,tue


BTW, have you ever looked in ~/.thumbnails?

---

### Post by cgjones on 2006-04-21
That syntax for the run time certainly looks to be correct.

---

### Post by bswilson on 2006-04-21
Hmm, I didn't realize you could use the day abbreviation.  I thought you had to use a **numeral** to represent which day(s) you wanted...

```
*     *     *     *     *    command to be executed
-     -     -     -     -
|     |     |     |     |
|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
|     |     |     +------- month (1 - 12)
|     |     +--------- day of month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)
```

---

### Post by ice60 on 2006-04-21
[QUOTE=cgjones]That syntax for the run time certainly looks to be correct.[/QUOTE]
thanks, cgjones :)

the reason i'm running it more then once is because i don't leave my computer on all the time. the next thing i want to learn is anacrontab, for missed crons, so i can just run it once in anacrontab :D

---

### Post by ice60 on 2006-04-21
[QUOTE=bswilson]Hmm, I didn't realize you could use the day abbreviation.  I thought you had to use a **numeral** to represent which day(s) you wanted...

```
*     *     *     *     *    command to be executed
-     -     -     -     -
|     |     |     |     |
|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
|     |     |     +------- month (1 - 12)
|     |     +--------- day of month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)
```[/QUOTE]
hi, i've seen it written both ways, so i think you can use either :confused:

---

### Post by cgjones on 2006-04-21
Anacron isn't that much different then cron, once you get the hang of it. Glad I could help and good luck in the future.

---

### Post by ice60 on 2006-04-21
[QUOTE=cgjones]Anacron isn't that much different then cron, once you get the hang of it. Glad I could help and good luck in the future.[/QUOTE]
thanks, cgjones :)

---

