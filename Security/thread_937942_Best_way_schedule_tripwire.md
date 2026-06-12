---
title: "Best way schedule tripwire"
date: 2008-10-04
forum: Security
---

### Post by Shwick2 on 2008-10-04
Ubuntu 8.04

Does tripwire have a config file that can schedule integrity checks, or do I have to do it from a cron job?

---

### Post by cariboo on 2008-10-04
Have a look at this howto:

[http://www.alwanza.com/howto/linux/tripwire.html](http://www.alwanza.com/howto/linux/tripwire.html)

It should answer your questions.

JIm

---

### Post by Shwick2 on 2008-10-04
Thanks but it only tells me to "Perform updates regularly (determine your schedule)".

 I'm just trying to determine if there is some tripwire setting that does this, or if you need a cronjob.  It seems like they would have build something like this into tripwire.

---

### Post by cariboo on 2008-10-04
There is a cron job installed when you install tripwire, at least the 64bit version. Look in /etc/cron.daily
there should be a file called tripwire, it is set to run daily and email you the results.

Jim

---

### Post by Shwick2 on 2008-10-05
Yes you are correct.  I was reading tripwire's email strategy and it said it send one email for every rule that was broken.  I'd rather have one email sent with the full report, so I'll make a script for that.

---

### Post by Shwick2 on 2008-10-05
I built this off of the tripwire daily cron script.  I'm trying to check the number of violations.

There's a problem when $tripResult is instantiated with the tripwire report- it doesn't have any newline characters.

This causes grep to not get the line with the number of violations, it just gets the entire report.



#!/bin/sh -e

tripwire=/usr/sbin/tripwire

[ -x $tripwire ] || exit 0

umask 027

tripResult=$($tripwire --check --quiet)

tripViolations=$(echo $tripResult | grep "Total violations found" | awk '{print $4}')

exit 0

---

### Post by Shwick2 on 2008-10-07
I learned that shell variables always remove redundant white space, but is there any way to make them accept the original string without removing redundant white space?

---

