---
title: "Cron issue with 6.06LTS Server ?"
date: 2008-05-21
forum: Server Platforms
---

### Post by jbjoret on 2008-05-21
Hi,

I hope someone can help me, I am a switcher from SuSE and quite new to the Ubuntu Server. I have cron running.
~# ps aux | grep cron
root      9722  0.0  0.0   2056   860 ?        Ss   May16   0:00 /usr/sbin/cron
root     13537  0.0  0.0   2804   792 pts/0    S+   13:23   0:00 grep cron

And I have a cronjob in the /etc/cron.daily directory. It looks like this job never gets called. if I call "crontab -l" it tells me "no crontab for root", I can't find any cron.log anywhere as well. How can I verify that it is ok ? My script does nothing else than date >> cron_call_list.txt but the file don't exist. 

Thx.

---

