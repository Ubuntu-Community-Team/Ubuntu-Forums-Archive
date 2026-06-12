---
title: "Screenshot utility with webserver upload?"
date: 2006-07-16
forum: The Cafe
---

### Post by howbag on 2006-07-16
Hey! I was wondering if theres a program for my dapper to contineously take screenshots and publish them to my server? the server is on the same machine.
So I can remotely see what's happening? :D

Thanks for replies!

---

### Post by henriquemaia on 2006-07-16
I don't know if this is what you want, but you can achieve that with a simple command line.

```
import -window root /path/to/your/server/folder/screenshot.png
```

---

### Post by henriquemaia on 2006-07-16
One thing I forgot to mention: 

To use this you need** imagemagick**.

ps:it's in the repositories.

---

### Post by howbag on 2006-07-16
Wow. That was pretty simple :D Thanks!

Is it possible to make it go contineously? make a simple script executing that cmd every 10th minute or something?

---

### Post by henriquemaia on 2006-07-16
> **howbag said:**
> Wow. That was pretty simple :D Thanks!

Is it possible to make it go contineously? make a simple script executing that cmd every 10th minute or something?

Yes. Put that on crontab. It will take care of it. Don't know how to use crontab? look here:

[http://ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://ubuntuforums.org/showthread.php?t=102626&highlight=cron)

---

### Post by howbag on 2006-07-16
hm, crontab doesnt seem to start.
my crontab file: 5,10,15,20,25,30,35,40,45,50,55 * * * * -window root /var/www/screenshot.png

it shows no error on the exit, and I did save. But nothing happens, no new screenshots are made :(

---

### Post by jasay on 2006-07-16
I tried this so I wouldn't have to wait 5 minutes and it seems to work
> * * * * * export DISPLAY=:0 && import -window root /var/www/screenshot.jpg

---

### Post by howbag on 2006-07-16
For some reason everything worked after I replaced mine with that line of yours jasay! Thanks :D

---

### Post by henriquemaia on 2006-07-16
The reason is that you have to export DISPLAY=:0, otherwise import from cron won't get the screenshot.

My bad, because I have written a HowTo on this and forget to mention it, :D

[http://ubuntuforums.org/showthread.php?t=185993&highlight=crontab](http://ubuntuforums.org/showthread.php?t=185993&highlight=crontab)

---

