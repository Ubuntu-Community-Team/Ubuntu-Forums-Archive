---
title: "script issue"
date: 2010-10-28
forum: Server Platforms
---

### Post by Vegan on 2010-10-28
I use a bash script to backup my server files, lock stock and barrel. No problem.

So here is the question:

if I name the script as backup.sh it will not run, but if I drop the .sh it works fine. :confused:

What gives? :confused:

---

### Post by CharlesA on 2010-10-28
Are you using cron to run them?

I seem to remember a thread you created about this sorta thing earlier.

Oh [here]("http://ubuntuforums.org/showthread.php?t=1585733") it is.

---

### Post by SeijiSensei on 2010-10-28
[We just had this conversation a few weeks ago]("http://ubuntuforums.org/showpost.php?p=9918251&postcount=10").  So, to coin a phrase, what gives?

---

### Post by Vegan on 2010-10-28
That is true but with my new server I am using a fresh install so I see the problem as reproducible.

What can't I use the .sh as it makes no sense whatsoever

Should I use .bash instead??

---

### Post by CharlesA on 2010-10-28
How are you wanting to run the script?

The same way you were doing it in the other thread?

Like I said in the other thread, I just throw my scripts in a regular crontab, not in cron.daily|monthly|weekly, and they run fine.

---

### Post by Vegan on 2010-10-28
```
sudo ln backup /etc/cron.daily
```

just like before

I changed my script a bit, to make it more clean looking and not as messy as it started off as.

I now have it clean looking and it does what I want so far.

But I have to wait 3 months for the rotation module

---

### Post by CharlesA on 2010-10-28
So, what's the point of the thread?

The reason why it doesn't run if it has an extension was stated in the other thread.

---

### Post by Vegan on 2010-10-29
I was hoping the new 10.10 would cure that nuisance.

I though that Linux was nominally agnostic to the file name, all it cares is if its executable

---

### Post by CharlesA on 2010-10-29
It's something that has to be fixed upstream first, if it bothers you that much, file a bug report with Debian.

Also see here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=68561](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=68561)

---

### Post by Vegan on 2010-10-29
I will just leave it as backup with no extension as that is all that is liked.

---

