---
title: "PHP segfault"
date: 2011-03-07
forum: Server Platforms
---

### Post by kristjans on 2011-03-07
Hello! I had a strange issue today at 20:40, my server crashed and was down for 30 minutes until restarting Apache. I am not sure what is going on, and how to make sure this won't happen again. After checking through syslogs, I found two interesting lines around time of the event:

```
Mar  7 20:40:03 phenom CRON[27466]: (root) CMD (php /cron/moving_matrix.php)
Mar  7 20:40:03 phenom CRON[27467]: (root) CMD (php /cron/error_logger.php)
Mar  7 20:40:03 phenom CRON[27468]: (root) CMD (php /cron/secondgrade.php)
Mar  7 20:40:03 phenom CRON[27469]: (root) CMD (php /cron/error_watcher.php)
[B]Mar  7 20:40:39 phenom kernel: [2877577.638248] php[27490]: segfault at 40c6 ip 00000000000040c6 sp 00007fff179cb940 error 14 in php5[400000+70d000]
Mar  7 20:40:50 phenom kernel: [2877588.302771] php[27471]: segfault at 233c ip 00007fd65a7de242 sp 00007fff59853758 error 4 in ld-2.11.1.so[7fd65a7c6000+20000][/B]
Mar  7 20:41:03 phenom CRON[29593]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  7 20:41:03 phenom CRON[29594]: (root) CMD (php /cron/moving_matrix.php)
Mar  7 20:42:04 phenom CRON[29612]: (root) CMD (php /cron/secondgrade.php)
Mar  7 20:42:04 phenom CRON[29613]: (root) CMD (php /cron/moving_matrix.php)
Mar  7 20:43:01 phenom CRON[29645]: (root) CMD (php /cron/moving_matrix.php)
Mar  7 20:44:01 phenom CRON[29662]: (root) CMD (php /cron/secondgrade.php)
```

```

kristjan@phenom:/var/log$ php --version
PHP 5.3.2-1ubuntu4.7 with Suhosin-Patch (cli) (built: Jan 12 2011 18:36:55)
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

```

```

kristjan@phenom:/var/log$ cat /etc/issue
Ubuntu 10.04.2 LTS \n \l

```

Please advise what to do. Thank you!

---

### Post by Vegan on 2011-03-07
Reboot the server with a cron job so it will not have problems.

I also suggest checking your memory with memtest to see if there is a dodgy stick

---

### Post by wongo888 on 2011-03-08
You really should try to track this down. 

Rebooting every night or every week doesn't solve your underlying problem. UNIX machines routinely run for months or years without stopping or rebooting.

Check to see if this is reproducible in some way. Your logs might show evidence of a failing drive. You might also try reinstalling php5.

---

