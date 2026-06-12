---
title: "How do I update a server install?"
date: 2007-08-09
forum: Server Platforms
---

### Post by Luft on 2007-08-09
I installed Ubuntu server so I have no GUI which is fine except that I don't know how to get security updates.  

Is there a way to automate the process so that when security updates come out they get downloaded and installed?

Thanks

---

### Post by ruibernardo on 2007-08-09
Hi Luft,

take a look at this page to make a task running time to time: [http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

---

### Post by regomodo on 2007-08-10
i guess you could set it up in cron with a script but to do it manually

$ sudo apt-get update
$ sudo apt-get upgrade

but that means you'll need to enter a password

---

### Post by ruibernardo on 2007-08-10
regomodo, he doesn't need to add a password, just edit crontab as sudo:

```
 sudo crontab -e
```

and add the apt-get commands with the times. Maybe a minute or two between them, just to make sure they don't run at the same time and depending on its internet capacity.

---

### Post by regomodo on 2007-08-10
> **epimeteo said:**
> regomodo, he doesn't need to add a password, just edit crontab as sudo:

```
 sudo crontab -e
```

and add the apt-get commands with the times. Maybe a minute or two between them, just to make sure they don't run at the same time and depending on its internet capacity.

ah. That makes sense. I couldn't remember how i set up rsnapshot in cron. That little tip will help

---

### Post by ruibernardo on 2007-08-10
Just a little note about "apt-get upgrade". 

There is a "-y" option in apt-get. From apt-get man page:

```
-y, --yes, --assume-yes

...assume "yes" as answer to all prompts and run non-interactively.
```

---

