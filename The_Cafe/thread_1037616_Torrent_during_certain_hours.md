---
title: "Torrent during certain hours"
date: 2009-01-11
forum: The Cafe
---

### Post by PurposeOfReason on 2009-01-11
Is there a torrent application that I can limit to only run on certain hours? I ask because I'm at uni and there is a ~7 hour window when people can get away with it and I'd like to be able to not have to physically monitor it.

---

### Post by ithanium on 2009-01-11
You can use **cron** and **at** for what you want
Read:
> man at
man cron

---

### Post by $USER on 2009-01-11
ktorrent allows scheduling if thats what you want

settings > configure ktorrent > plugins > bandwidth scheduler plugins > have fun

---

### Post by ghindo on 2009-01-12
I'm pretty sure that almost any torrent client can be set up to only run during certain hours.  What client are you using?

---

### Post by PurposeOfReason on 2009-01-12
Deluge is what I'm most partial too though I can get the best one for the job as long as it is gtk.

---

### Post by PurposeOfReason on 2009-01-12
I like the at command best but when I run it like so:
at -f /usr/bin/deluge -v 9:59pm today

Nothing happens at the time I put.

---

### Post by Polygon on 2009-01-12
the old deluge had a scheduler plugin, but i have not used it in a while so i am not sure if it has been ported to the 1.0 branch

---

### Post by LookTJ on 2009-01-12
> **PurposeOfReason said:**
> I like the at command best but when I run it like so:
at -f /usr/bin/deluge -v 9:59pm today

Nothing happens at the time I put.Have you tried putting the time in a 24 hour format? 

at -f /usr/bin/deluge -v 21:59 today or something?

***EDIT***
[quote=from man at]
      At allows fairly complex time  specifications,  extending  the  POSIX.2
       standard.   It  accepts  times of the form HH:MM to run a job at a spe&#8208;
       cific time of day.  (If that time is already  past,  the  next  day  is
       assumed.)   You  may  also specify midnight, noon, or teatime (4pm) and
       you can have a time-of-day suffixed with AM or PM for  running  in  the
       morning or the evening.  You can also say what day the job will be run,
       by giving a date in the form month-name day with an optional  year,  or
       giving a date of the form MMDDYY or MM/DD/YY or DD.MM.YY.  The specifi&#8208;
       cation of a date must follow the specification of the time of day.  You
       can  also  give times like now + count time-units, where the time-units
       can be minutes, hours, days, or weeks and you can tell at  to  run  the
       job  today by suffixing the time with today and to run the job tomorrow
       by suffixing the time with tomorrow.[/quote]

HH:MM is 24 hour format.

---

