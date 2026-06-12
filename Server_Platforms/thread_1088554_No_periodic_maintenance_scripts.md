---
title: "No periodic maintenance scripts?"
date: 2009-03-06
forum: Server Platforms
---

### Post by chowse on 2009-03-06
Hi,
I installed 8.10-server-i386 using "Install a minimal system", and went to configure the daily, weekly, and monthly maintenance scripts that I thought lived in /etc/periodic, and found that directory doesn't exist.

Have we outgrown them, do they live somewhere else, or do I need to install them?

Thanks,
Charles

---

### Post by gombadi on 2009-03-06
I have never seen or heard of /etc/periodic.

Are you meaning cron?

Have a look in -

```

human@dave:~$ ls -1 -d /etc/cron*
/etc/cron.d
/etc/cron.daily
/etc/cron.hourly
/etc/cron.monthly
/etc/crontab
/etc/cron.weekly

```

---

### Post by chowse on 2009-03-06
I'm actually referring to this:

<http://www.digipedia.pl/man/periodic.8.html>

---

### Post by gombadi on 2009-03-06
If you have a look in /etc/crontab you will see it uses run-parts

```

01 *	* * *	root    cd / && run-parts --report /etc/cron.hourly

```

Will that do what you want?

You may have to create the /etc/periodic directory structure yourself and add some lines to /etc/crontab to run the scripts in each sub-directory when you want.

Looks like periodic itself may not have been ported from FreeBSD to Linux/Ubuntu.

---

### Post by chowse on 2009-03-06
YES!!
That's what I've been looking for.
Thanks for the pointer!

---

