---
title: "bind custom logging not working as expected"
date: 2011-04-02
forum: Server Platforms
---

### Post by dbv on 2011-04-02
I want to prevent bind from filling up the syslog by defining its own logging facility (local7). Here's a part of named.conf.options:

```
logging {
    channel "mysyslog" {
        syslog local7;
        print-category  yes;
    };

    category default { mysyslog; };
    category lame-servers { null; };
};
```

This is the bit from from rsyslog.conf that pushes local7 into its own file:

```
*.*;auth,authpriv.none,cron.none,local7.none        -/var/log/syslog
local7.*            /var/log/named.log
```

But now it's logging to both syslog and named.log. How do I stop it from logging to syslog? Is it using another (default) facility and how do I disable it? Thanks.

---

### Post by Doug S on 2011-04-02
Try this in you rsyslog.conf:
 
```
 
*.*;auth,authpriv.none;cron.none;local7.none        -/var/log/syslog
local7.*            /var/log/named.log

```
(I have replaced two commas with semicolons.)
 
Also check /etc/rsyslog.d/50-default.conf for a possible conflict (if you have it, I have a 10.10 server and your info shows 10.04. I don't know if they are different).

---

### Post by dbv on 2011-04-02
Sorry, that configuration was from 50-default.conf, not from rsyslog.conf.

I replaced the commas with semicolons, did a 'kill -HUP' on rsyslogd and it's still the same.

---

### Post by dfreer on 2011-04-02
```
_*.*;_auth,authpriv.none,cron.none,**local7.none**        -/var/log/syslog
local7.*            /var/log/named.log
```
Perhaps remove the local7.none entirely from that line? Also what's up with the *.*?

---

### Post by Doug S on 2011-04-02
Here is an interesting reference: [http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)
I think that you are asking logging to go to both syslog and your other file in your named.conf file. I think you want to delete "syslog" from your named.conf file. They also have a good example in the above link, where the 50-default.conf file wouldn't have to be modified at all as everything is done in the named.conf file.

---

### Post by dbv on 2011-04-03
> **dfreer said:**
> ```
_*.*;_auth,authpriv.none,cron.none,**local7.none**        -/var/log/syslog
local7.*            /var/log/named.log
```
Perhaps remove the local7.none entirely from that line? Also what's up with the *.*?

As I understand it, *.* is a catch-all. The local7.none means exclude any severity (none) from syslog which effectively means not to log it. That setup works fine for cron. There's a cron.none there and another cron.* /var/log/cron.log on another line. There is nothing in syslog from cron, everything is in cron.log.

---

### Post by dbv on 2011-04-03
> **Doug S said:**
> Here is an interesting reference: [http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)
I think that you are asking logging to go to both syslog and your other file in your named.conf file. I think you want to delete "syslog" from your named.conf file. They also have a good example in the above link, where the 50-default.conf file wouldn't have to be modified at all as everything is done in the named.conf file.

I used that originally and yes, it works fine. Except that the output doesn't have 'named' in it so logwatch ignores it. That's why I went back to syslog.

---

### Post by Doug S on 2011-04-03
I agree with you. What you are trying to do should be working. It should only be logging to the desired log file and not also syslog, at least as far as I have been able to figure out both by reading and by experimenting.

---

### Post by dbv on 2011-04-03
OK, it is actually working. The only thing that ends up the syslog are the ~30 lines of startup messages from bind:


Apr  3 04:28:11 gw named[20570]: adjusted limit on open files from 1024 to 1048576
Apr  3 04:28:11 gw named[20570]: found 4 CPUs, using 4 worker threads
Apr  3 04:28:11 gw named[20570]: using up to 4096 sockets
Apr  3 04:28:11 gw named[20570]: loading configuration from '/etc/bind/named.conf'
Apr  3 04:28:11 gw named[20570]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Apr  3 04:28:11 gw named[20570]: using default UDP/IPv4 port range: [1024, 65535]
Apr  3 04:28:11 gw named[20570]: using default UDP/IPv6 port range: [1024, 65535]
...

But all the rest now goes to /var/log/named.log. But logwatch is still ignoring it :)

Thanks for trying to help Doug.

---

### Post by dbv on 2011-04-03
OK, logwatch just needed a /etc/logwatch/conf/services/named.conf (to tell it which log files to use, in my case syslog and named.log) and /etc/logwatch/conf/logfiles/named.conf (to tell it where named.log is) defined and everything is good.

I suppose at this point I can go back and have named log to file instead of syslog since I know how to configure logwatch. I suppose I should edit the Ubuntu logwatch page since it's lacking.

---

### Post by Doug S on 2011-04-03
Thanks for the follow ups. I was wondering exactly what you said in your last post.

---

