---
title: "Server with lots of sleeping processes"
date: 2014-05-08
forum: Server Platforms
---

### Post by ashutosh5 on 2014-05-08
Hello Community Members,


We are running ubuntu 12.04. There are 103 PHP applications running on the same server. One application executes a command line php script for all the 103 applications. We saw a weird behavior, on the server we have 15GB ram out of which 14 GB was consumed by the apache  user www-data. When our application user got active the server was very slow, almost unavailable. the htop shows that there are 637 processes for www-data in sleep mode. Further we restarted the cron server and killed all the www-data processes and the memory usage went to 705MB to 903MB. 

we have checked syslog the oom killer woke up and tried to kill processes a lot of times.

Is there any way to find why all the processes was in sleep mode, what exactly was the process for which server was putting other process to sleep mode?

---

### Post by tgalati4 on 2014-05-09
Check the apache log files in /var/log/apache.  It sounds like a PHP process fails then gets restarted.  It's possible that you don't have enough memory set for each PHP process-- check your php.ini settings.

---

### Post by ashutosh5 on 2014-05-12
Thanks for your reply, the memory for php is allocated 4GB. still there are certain processes in sleep mode. After checking the apache logs we traced an error related to MaxClient. 

The question remains same why there are alot of sleeping processes with user www-data ?

---

### Post by tgalati4 on 2014-05-12
Set your PHP to development environment and look through the logs:  [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

Go through the status of your PHP installation when RAM fills up:  [https://help.ubuntu.com/community/ApacheMySQLPHP#Status](https://help.ubuntu.com/community/ApacheMySQLPHP#Status)

---

