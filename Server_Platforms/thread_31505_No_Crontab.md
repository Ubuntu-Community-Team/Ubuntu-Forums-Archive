---
title: "No Crontab"
date: 2005-05-03
forum: Server Platforms
---

### Post by dallypost on 2005-05-03
I am setting up my first server. The server is hosting [www.dallypost.com](www.dallypost.com).

I have written scripts to back up my web site and to dump mysql. Both scripts work. I now want to run these scripts daily via cron. Cron is installed and running. When I do sudo crontab -l, I get No crontab for root. I also tried this for non-root users and get the same thing.

Thanks,

Lance Earl ](*,)

---

### Post by Professor X on 2005-05-03
Try ```
sudo crontab -e
```.  The -e flag is used to edit your crontab, the -l is used for listing cron jobs.

---

