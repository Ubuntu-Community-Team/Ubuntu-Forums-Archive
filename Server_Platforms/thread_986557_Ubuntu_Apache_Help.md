---
title: "Ubuntu Apache Help"
date: 2008-11-18
forum: Server Platforms
---

### Post by IceburgIV on 2008-11-18
I have an Ubuntu server that I have set up that my load average are constantly over 30.  I have ran through all the documents online and I can't seem to make a difference.  If I run top, I see that the apache seems to be the culprit.

```

root@zaphod:~# ps -ef | grep -c "apache"
37

```

A snapshot from top shows:

```

17119 www-data  20   0 99.0m  13m 3448 R  7.9  0.9   0:38.61 apache2
18308 www-data  20   0 83568  60m 3024 R  7.9  4.0   0:15.62 apache2
 4757 www-data  20   0  105m  52m 3452 R  5.9  3.4  14:46.99 apache2
 6222 www-data  20   0 34272  14m 3480 R  5.9  1.0   8:53.42 apache2
 7984 www-data  20   0  100m  17m 3564 R  5.9  1.2   9:19.96 apache2
10295 www-data  20   0  107m  34m 3484 R  5.9  2.3   9:34.79 apache2
10303 www-data  20   0  102m  21m 3620 R  5.9  1.4   5:50.44 apache2
12770 www-data  20   0 93152  31m 3708 R  5.9  2.1   6:13.88 apache2
12771 www-data  20   0 92364  29m 3568 R  5.9  1.9   7:23.33 apache2
12772 www-data  20   0  104m  31m 3524 R  5.9  2.1   5:43.97 apache2
13949 www-data  20   0  106m  32m 3460 R  5.9  2.1   5:54.75 apache2
17414 www-data  20   0 85384  14m 3284 R  5.9  0.9   0:45.32 apache2
18314 www-data  20   0 99468  76m 3020 R  5.9  5.1   0:17.32 apache2
31044 www-data  20   0 89288  22m 3564 R  5.9  1.5  18:13.54 apache2
 4273 mysql     20   0  275m  71m 2788 S  3.9  4.7 246:18.88 mysqld
12778 www-data  20   0 91084  53m 3588 R  3.9  3.5   4:40.27 apache2
13948 www-data  20   0 87752  18m 3576 R  3.9  1.2   4:15.26 apache2

```

My apache2.conf file shows (without the commented out parts)

```

LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 60
KeepAlive Off
MaxKeepAliveRequests 100
KeepAliveTimeout 4

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
# Was 150 SAW 20080921
    MaxClients          50
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


HostNameLookups off
etc (log conf's, format's other...)

```

Cpu(s): 94.9%us,  0.8%sy,  1.2%ni,  2.4%id,  0.4%wa,  0.1%hi,  0.2%si,  0.0%st
Mem:   1555000k total,   845332k used,   709668k free,     3428k buffers
Swap:  3229024k total,   869096k used,  2359928k free,   142656k cached

The virtual hosts that I have are:

A Pligg site ([www.neweasyrecipe.com](www.neweasyrecipe.com)) which only gets 100 hits / day.  But the site is very intensive.

An internal picture site.  Only my friends have access, and its only 1-2 hits per day.

An internal stats page.  Only active on Sunday's when football is on.  

An internal jinzora page.  I only use it for listening to music at work.

An internal munin page for monitoring / stats of the server.

I think NewEasyRecipe has to be the issue.  I can't figure out how or what to do though, or where do go.  Can anyone help?

---

### Post by oneloveamaru on 2008-11-18
install "htop" it's a little bit nicer than top. Watch what process keeps popping up on top. If apache seems to be the problem, shut it down and wait a bit to see if the load goes down. /etc/init.d/apache2 stop

---

### Post by IceburgIV on 2008-11-19
I installed htop, and have attached a screen shot.  

The weird thing is that if I opened another SSH window, stop apache2, the apache processes never drop out of the top or htop process list.  The webpage aren't being served any more, but the top 8 processes are apache2 -k start still.

The screenshot is while apache is running.  I stopped it shortly after this for about 3 minutes, before restarting it.

---

### Post by IceburgIV on 2008-11-20
No one?

---

### Post by JDiss on 2008-11-23
Without getting into technicalities, I'd probably advise you to check out your error and access logs to see if there's anything there.  I did notice that htop was reporting a load average more around 16 than 30, but it's still fairly high considering what you say the traffic is like.

Are you using worker or prefork?

---

