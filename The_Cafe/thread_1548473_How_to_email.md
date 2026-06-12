---
title: "How to email"
date: 2010-08-08
forum: The Cafe
---

### Post by LowSky on 2010-08-08
Maybe someone can help me with this.

I want my PC to email the results of running a command like lsusb every 24 hours. How would I go setting this up?

TIA

---

### Post by Bachstelze on 2010-08-08
```
command | mail -s Subject foo@bar.org
```

Put that in a cron job, either directly or in a shell script if you want to so something more complex.

---

### Post by LowSky on 2010-08-08
Thanks Bachstelze I'm going to try that out

---

### Post by Bachstelze on 2010-08-08
> **LowSky said:**
> Thanks Bachstelze I'm going to try that out

Your system must be properly configured to send email, though.  If you want a quick and easy way, use ssmtp and configure it to use the SMTP server of your ISP.

---

### Post by LowSky on 2010-08-08
Very cool! I got it to work! Thanks for tips

Installed ssmtp, then created a simple cron job that looks like this

```
MAILTO=xxxxxxx@gmail.com
00 10 * * * mythtv-status
```


Now I get an email that will tell me what is being recorded for the day.

---

