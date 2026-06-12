---
title: "How to set schedule on Server"
date: 2012-03-23
forum: Server Platforms
---

### Post by Rainersxd on 2012-03-23
Hellow agen !
 This time I have problem with server...
 I have a Ubuntu Server, but I still thinking how to set schedule on this system.
 Please help.

---

### Post by jerome1232 on 2012-03-23
erm, huh? Set a schedule for what? Clarification please, although my gut tells me you want something like this [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Rainersxd on 2012-03-23
Thanks you answered my question, but I will mark this as [solved] when I will get results...

---

### Post by Rainersxd on 2012-03-31
I'm sorry, but I think I need something els.
 I need something that will automatically hibernate my computer in 23:00 o'clock (after *Latvian time).
*Latvia is in Europe.

---

### Post by Lars Noodén on 2012-03-31
As mentioned by jerome1232 above, [cron](https://help.ubuntu.com/community/CronHowto) should do that for you.
```

00 23 * * * /usr/sbin/pm-hibernate

```

Note that [pm-hibernate](http://manpages.ubuntu.com/manpages/oneiric/en/man8/pm-hibernate.8.html) must be run as root, so your cron job must be done as root.

---

### Post by Rainersxd on 2012-03-31
Sorry, I didn't understand. how that command looks like ?
I tepid > sudo cron 00 23 * * * /usr/sbin/pm-hibernate And he say: cron: can't lock /var/run/crond/pid, otherpid may be 672: Resource temporarily unavailable
Did I did something wrong or I need change those numbers in that file ?

---

### Post by 2F4U on 2012-03-31
I guess you need a bit more information about cron and how to use it:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[http://manpages.ubuntu.com/manpages/oneiric/man1/crontab.1.html](http://manpages.ubuntu.com/manpages/oneiric/man1/crontab.1.html)

This may also be of help. Instead of shutdown put your desired command in:
[http://ubuntuforums.org/showthread.php?t=925450](http://ubuntuforums.org/showthread.php?t=925450)

---

### Post by Lars Noodén on 2012-03-31
> **Rainersxd said:**
> Sorry, I didn't understand. how that command looks like ?

Look at the links that 2F4U and others have supplied.  cron is controlled by editing a configuration file.  The example I provided was what you could have in the configuration file.  You can edit the configuration for cron using [crontab](http://manpages.ubuntu.com/manpages/oneiric/en/man1/crontab.1.html)

```

sudo crontab -e

```

---

### Post by Rainersxd on 2012-04-08
Sorry for holding this to long, but this is my first experience with server edition.
So what was the file what I need to edit ?

---

### Post by Lars Noodén on 2012-04-08
There's a program called [crontab](http://manpages.ubuntu.com/manpages/oneiric/en/man1/crontab.1posix.html) (see #8 above) which is used to edit the [configuration file for cron](http://manpages.ubuntu.com/manpages/oneiric/en/man5/crontab.5.html) (see #2 above)

---

### Post by eric_1982 on 2012-04-11
If you are looking have this happen just one time you could use the "at" command. This is similar to crontab but the job is scheduled just once instead of repeated at a defined period. 

An example on using the "at" command could be found at: 
[http://mixeduperic.com/ubuntu/how-to-schedule-a-one-time-restart-on-your-ubuntu-system-using-the-at-command.html](http://mixeduperic.com/ubuntu/how-to-schedule-a-one-time-restart-on-your-ubuntu-system-using-the-at-command.html)

You would just need to modify it to your needs.

---

