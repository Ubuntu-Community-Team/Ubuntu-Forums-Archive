---
title: "Cron Job"
date: 2006-09-05
forum: Server Platforms
---

### Post by emptycs on 2006-09-05
What is the cron command so it runs

./hlds ??

---

### Post by amo-ej1 on 2006-09-05
How do you mean ? The cron daemon itself ? 

```

root@lap:/# /etc/init.d/cron
 * Usage: /etc/init.d/cron start|stop|restart|reload|force-reload

```
So /etc/init.d/cron restart.

Or to run the commands which are cron'ed ?

---

### Post by emptycs on 2006-09-05
I want to add a command to the cron job so it can run hlds/./hlds_run or something near that. Or a way for me to run that

---

### Post by amo-ej1 on 2006-09-05
Ah, in that case you will be more intested in the 'crontab' command. You can edit your cron settings (for your current user) with 'crontab -e' and list them with 'crontab -l'. As root you can specify the -u <user> flag to examine a given users crontab. The exact format of the crontab file is describe in 'man 5 crontab' while 'man 1 crontab' will give you an explanation about the crontab command itself. 
The following crontab entry will run the script /my/script.sh every day at midnight. 
```

0 0 * * * /my/script.sh

```

---

### Post by emptycs on 2006-09-05
Cool thanks

---

