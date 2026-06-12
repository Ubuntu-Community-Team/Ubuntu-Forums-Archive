---
title: "/usr/sbin/sendmail-msp: not found"
date: 2007-09-08
forum: Server Platforms
---

### Post by robinbillings on 2007-09-08
I'm running Feisty Fawn with postfix, courier imap and squirrelmail.  I keep getting messages about every 20 minutes from Cron:

/usr/share/sendmail/sendmail: 1176: /usr/sbin/sendmail-msp: not found

Any idea on how to fix this?

Robin Billings

---

### Post by robinbillings on 2007-09-08
This may not have been the best solution, but I edited the /etc/crod.d/sendmail file and commented out the line:

*/20 *    *    *    *          smmsp   test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp

Of note, the following line is, by default, commented out:

#*/10 *    *    *    *          root    test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-mta

This fixed the Cron message to root problem.  Mail seems to come and go just fine.  Anyone see a problem with this?

Robin Billings

---

### Post by sparklyprgs on 2007-09-13
worked fine for me too...  :)
but i changed it via webmin using: System / Scheduled Cron Jobs/ deactivate smmsp

---

