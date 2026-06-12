---
title: "can't get telak to work ?"
date: 2010-09-21
forum: The Cafe
---

### Post by nourathar on 2010-09-21
Hi all,

I was looking for a solution to have a picture from a remote server put on my desktop and refreshed every hour or so, and I found telak. It is exactly what I need, nothing more, except that I can't get it to work.
It is parsing its config file ok, it says it is downloading from what seems the right location, but then I get:

~/.telak/cache/e9903daa1d41203a4fbfe24a25b339bc unable to stat() file: No such file or directory

I explicitly specify the location of the telak cache, and the adress is correct, but it doesn't seem to save anything. Does anybody know how to get this to work or whether there is another script or application out there that could do the same thing ?

many thanks,

Joost.

---

### Post by Cuddles McKitten on 2010-09-21
The easiest way would probably just to make an hourly cron job that uses wget to download the picture.  Then you don't have to figure out how to use "telak."

---

### Post by nourathar on 2010-09-23
Yes, I'm still quite new to Linux, but after having a look at the man  page of crontab that looks like the way to go, a nice excercise !

thanks,

Joost.

---

