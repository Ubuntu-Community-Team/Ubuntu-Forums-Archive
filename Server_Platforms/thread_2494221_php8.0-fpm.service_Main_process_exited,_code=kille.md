---
title: "php8.0-fpm.service: Main process exited, code=killed, status=9/KILL"
date: 2024-01-09
forum: Server Platforms
---

### Post by matiajelo on 2024-01-09
Hi..

I've been experiencing issues with my Ubuntu server in the last few days, Like the title I created. Suddenly, the php-fpm service died with a very random timing.
Here, I'll display the logs a few moments before its php-fpm service down. I don't know the cause of this service suddenly shutting down

Jan  8 16:46:44 myserver.jabikha.com crontab[165669]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165671]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165672]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165674]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165675]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165677]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165678]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165680]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165682]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165684]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165685]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165687]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165689]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165691]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165692]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165694]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165697]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165699]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165701]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165703]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165707]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165709]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165714]: (ftpuser) LIST (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com crontab[165716]: (ftpuser) REPLACE (ftpuser)
Jan  8 16:46:44 myserver.jabikha.com systemd[1]: php8.0-fpm.service: Main process exited, code=killed, status=9/KILL
Jan  8 16:46:44 myserver.jabikha.com systemd[1]: php8.0-fpm.service: Failed with result 'signal'.
Jan  8 16:46:44 myserver.jabikha.com systemd[1]: php8.0-fpm.service: Consumed 2.277s CPU time.
Jan  8 16:47:01 myserver.jabikha.com cron[846]: (ftpuser) RELOAD (crontabs/ftpuser)

If there are additional logs that need to be displayed for further analysis, I am willing. Please provide the command I should use to retrieve them




I ask for help in finding a solution to the issues occurring on my server
Thks

---

