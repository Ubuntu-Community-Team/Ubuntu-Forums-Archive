---
title: "HELP! Apache Lock Up?"
date: 2006-10-24
forum: Server Platforms
---

### Post by brownrl on 2006-10-24
This is a weird one that I get lately with Ubuntu Server and Apache...

Whenever I go to reload the apache or restart this is what I get if the apache has been running for longer than 15 minutes...


```

root@lounge:~# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... (98)Address already in use: make_sock: could not bind to address [::]:443
no listening sockets available, shutting down
Unable to open logs                                         [fail]

```

So its one of the SSL children not shutting down?

Then I do a ps aux and this is not good either...

```

root@lounge:~# ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1568   532 ?        S    Aug31   0:02 init [2]
root         2  0.0  0.0      0     0 ?        S    Aug31   0:02 [migration/0]
...
...
...
www-data 27640 69.0  0.2   4924  2908 ?        R    04:12 149:22 /usr/sbin/httpd
www-data 27646 69.1  0.2   4928  2912 ?        R    04:12 149:28 /usr/sbin/httpd
...
...
...
www-data 30302 34.1  0.1   5068  2372 ?        R    07:45   0:59 /usr/sbin/httpd
www-data 30304 33.8  0.1   5064  2364 ?        R    07:45   0:58 /usr/sbin/httpd

```

So 4 apache procs using nearly 100% CPU!!!

Yikes! what is this, I don't really need ssl at the moment but I don't like the idea that I need to be on standby incase apache does not work.

Thanks for any pointers...

---

### Post by bswilson on 2006-10-24
Regarding your SSL port binding question, I think you can fix that by creating the **/var/www/log** directory.  See [this post]("http://www.ubuntuforums.org/showthread.php?t=237170") for a guy who had the same problem.

---

### Post by brownrl on 2006-10-25
Thanks a ton... That seems to do the trick.

Created log dir in the /var/www/log then did restart of apache and it seems to be in order.

Again thanks for your help.

---

### Post by brownrl on 2006-10-30
Actually, this did not work. I created a /var/www/log and it did not work.

I do think it is something with the log files and it takes a long time to let them go in shutting down.

I removed all the ssl stuff from my apache and now it happens on the 80 port... and in the end I try to restart apache one apache process hangs for very long trying to stop doing something...

```

/etc/init.d/apache stop
/etc/init.d/apache start

 * Starting apache 2.0 web server...                                            (98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

ps aux | grep www-data
www-data  4340  4.3  0.2   4828  2792 ?        S    14:26   2:26 -bash

```

---

### Post by brownrl on 2006-10-30
The above happens anytime that I let apache run for more than 30 minutes.

log files show nothing except.

```

[Mon Oct 30 15:22:26 2006] [notice] caught SIGTERM, shutting down
[Mon Oct 30 15:22:59 2006] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Mon Oct 30 15:22:59 2006] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Mon Oct 30 15:23:00 2006] [notice] Apache/2.0.55 (Ubuntu) mod_python/3.1.4 Python/2.4.3 PHP/5.1.2 configured -- resuming normal operations

```

---

