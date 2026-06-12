---
title: "how to run command that needs root privilages in cron?"
date: 2009-03-12
forum: Server Platforms
---

### Post by three_jeeps on 2009-03-12
I have a job that I want to run in cron that requires root privilege.  Specifically:
/usr/lib/cgi-bin/awstats.pl -config=my_domain -update>/dev/null

I entered it with the proper time values in crontab but it does not run.  I run it at the cl using sudo and it runs fine.

On most unix systems one could prefix the command with root or su and it will run.  What do I need to do in Ubuntu?

I have searched and found many discussions about the philosophy of ubuntu's approach of protecting root privilege for security reasons, but no mention of how to do what I want.
thanks
J

---

### Post by hyper_ch on 2009-03-12
you add it to root cron

I do it like this:

(1) create a cron.txt file
(2) add the cronjobs there
(3) add it to root cron
```

sudo crontab cron.txt

```
(4) verfiy that it was added
```

sudo crontab -l -u root

```
(5) enjoy

---

### Post by three_jeeps on 2009-03-12
> **hyper_ch said:**
> you add it to root cron

I do it like this:

(1) create a cron.txt file
(2) add the cronjobs there
(3) add it to root cron
```

sudo crontab cron.txt

```
(4) verfiy that it was added
```

sudo crontab -l -u root

```
(5) enjoy

and just to be complete: sudo /etc/init.d/cron restart
(for me, cron did not automatically restart when updating crontab)

Thank you!

---

### Post by hyper_ch on 2009-03-12
I never done a cron restart... hmm...

---

