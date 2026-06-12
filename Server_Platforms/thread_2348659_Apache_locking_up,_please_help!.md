---
title: "Apache locking up, please help!"
date: 2017-01-06
forum: Server Platforms
---

### Post by joelbarnard on 2017-01-06
Hello everyone!

I am having an issue I cannot resolve, I am running Ubuntu Server 16.04, a fresh install, running LAMP, my install went perfectly and for the first few days had no issues. But now I am getting these strange lockups where my http side just shows a white page and I have to restart apache to bring it back up again, strangely, the https side does not go down, can someone please advise me?

Here is the error log pulled around the time of one of these crashes...

```
[Wed Jan 04 08:08:49.432784 2017] [mpm_prefork:notice] [pid 4668] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 08:08:49.432822 2017] [core:notice] [pid 4668] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 09:07:29.975447 2017] [core:notice] [pid 4668] AH00051: child pid 4777 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 09:07:29.975554 2017] [mpm_prefork:notice] [pid 4668] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 09:07:30.832906 2017] [mpm_prefork:notice] [pid 4954] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 09:07:30.832956 2017] [core:notice] [pid 4954] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 10:09:53.165320 2017] [core:notice] [pid 4954] AH00051: child pid 4960 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:09:53.165?4 2017] [mpm_prefork:notice] [pid 4954] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 10:09:54.180140 2017] [mpm_prefork:notice] [pid 5261] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 10:09:54.180186 2017] [core:notice] [pid 5261] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 10:40:58.711018 2017] [core:notice] [pid 5261] AH00051: child pid 5264 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:40:58.711515 2017] [mpm_prefork:notice] [pid 5261] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 10:40:59.556511 2017] [mpm_prefork:notice] [pid 5756] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 10:40:59.556555 2017] [core:notice] [pid 5756] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 10:41:54.347067 2017] [core:notice] [pid 5756] AH00051: child pid 5776 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:41:54.3471? 2017] [mpm_prefork:notice] [pid 5756] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 10:41:55.180517 2017] [mpm_prefork:notice] [pid 5844] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 10:41:55.180561 2017] [core:notice] [pid 5844] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 10:45:40.722289 2017] [core:notice] [pid 5844] AH00051: child pid 5855 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:45:40.722395 2017] [mpm_prefork:notice] [pid 5844] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 10:45:41.587378 2017] [mpm_prefork:notice] [pid 5?2] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 10:45:41.587426 2017] [core:notice] [pid 5?2] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 10:51:49.395434 2017] [core:notice] [pid 5?2] AH00051: child pid 5924 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:51:49.395536 2017] [mpm_prefork:notice] [pid 5?2] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 10:51:50.233842 2017] [mpm_prefork:notice] [pid 5980] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 10:51:50.233879 2017] [core:notice] [pid 5980] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
[Wed Jan 04 10:55:35.105970 2017] [:error] [pid 5996] [client 70.209.198.19:1600] script &#8216;/var/www/html/data/public/e12ebd.php&#8217; not found or unable to stat
[Wed Jan 04 10:55:55.793137 2017] [core:notice] [pid 5980] AH00051: child pid 5983 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:55:55.793214 2017] [core:notice] [pid 5980] AH00051: child pid 5985 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:55:55.793247 2017] [core:notice] [pid 5980] AH00051: child pid 5994 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:55:55.793269 2017] [core:notice] [pid 5980] AH00051: child pid 5995 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:55:55.793292 2017] [core:notice] [pid 5980] AH00051: child pid 5996 exit signal Segmentation fault (11), possible coredump in /etc/apache2
[Wed Jan 04 10:55:55.793343 2017] [mpm_prefork:notice] [pid 5980] AH00169: caught SIGTERM, shutting down
[Wed Jan 04 10:55:56.678525 2017] [mpm_prefork:notice] [pid 6052] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured &#8212; resuming normal operations
[Wed Jan 04 10:55:56.678563 2017] [core:notice] [pid 6052] AH00094: Command line: &#8216;/usr/sbin/apache2&#8217;
```

Apache 2.4.18
PHP 7.0.8-0ubuntu0.16.04.3

---

### Post by ajgreeny on 2017-01-06
*Thread moved to **Server Platforms**.* which is more appropriate for the problem and should be a better fit.

---

### Post by joelbarnard on 2017-01-06
Can anyone help me?

---

### Post by wildmanne39 on 2017-01-06
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

You can bump your post once every 12 hour to keep it in view of the community.

Hopefully someone that can help will reply soon.

---

### Post by joelbarnard on 2017-01-16
@wildmanne39 I am still having this issue and have not received any support, do you know of any services by which I may pay a guru to take a look at this for me? I'm not sure what else to do. Thank you.

---

### Post by wildmanne39 on 2017-01-16
No we do not allow anyone to get paid to help but if you bump your thread once every twelve hours that will keep it on the front page so people can see it.

You can get paid support at Canonical but I would wait and see if bumping it helps.
[https://www.ubuntu.com/support/plans-and-pricing](https://www.ubuntu.com/support/plans-and-pricing)

---

### Post by SeijiSensei on 2017-01-16
I'd start by tracking down the error referenced here:

```

[Wed Jan 04 10:55:35.105970 2017] [:error] [pid 5996] [client 70.209.198.19:1600] script &#8216;/var/www/html/data/public/e12ebd.php&#8217; not found or unable to stat
[Wed Jan 04 10:55:55.793137 2017] [core:notice] [pid 5980] AH00051: child pid 5983 exit signal Segmentation fault (11), possible coredump in /etc/apache2

```

Does e12ebd.php exist?  

Did you run a full dist-upgrade after installation?  If not, run
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and see if that helps.

How much memory do you have?

---

