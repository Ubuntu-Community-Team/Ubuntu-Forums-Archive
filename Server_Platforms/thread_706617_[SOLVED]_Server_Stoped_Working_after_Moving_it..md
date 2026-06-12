---
title: "[SOLVED] Server Stoped Working after Moving it."
date: 2008-02-24
forum: Server Platforms
---

### Post by dethredic on 2008-02-24
Ok, previously my server was under my bed, but I moved it onto my desk. In the process I turned it off, unpluged the internet and power, moved it, put the connections back in and booted up.

My internet works while on my server, but my site is down.

Can someone help me with this? I am not sure what I have to try in order to narrow things down.

---

### Post by astrotech226 on 2008-02-24
When you say your site is down, do you mean that you are running a web server from your house?

If that's the case, be sure Apache is running.  The other thing is that do you get your address dynamically?  If you turned power off for a period of time, your address might have changed.  What address do you go to on the internet to access your site?

---

### Post by k_grdn on 2008-02-24
Hi,

First thing check if apache is running.

pidof apache2 or  ps auxwww|grep apache

Regards,

k_grdn

---

### Post by dethredic on 2008-02-24
yes this server is @ my house. It is just for a couple of smaller sites.

[QUOTE]
root@server1:/home/phil# /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                          5851
                                                                         [ OK ]

---

### Post by dethredic on 2008-02-24
Ok, it has to be something with my DNS.

24.57.219.152 works, but [www.hatchseadgroup.com](www.hatchseadgroup.com) does not. 

Any ideas what it could be?

root@server1:/home/phil# 
root@server1:/home/phil# pidof apache2 or ps auxwww|grep apache
root@server1:/home/phil# 

[/QUOTE]


EDIT: It is defiantly bind9

> 
root@server1:/home/phil# /etc/init.d/bind9 start
 * Starting domain name service... bind                                  [fail] 
root@server1:/home/phil# 


Any ideas of what to try now?

---

### Post by astrotech226 on 2008-02-24
Looks like your dns servers are down.  Whois shows these are your servers.

```
ns1.hatchseadgroup.com
ns2.hatchseadgroup.com
```

Dig times out attempting to resolve [www.hatchseadgroup.com](www.hatchseadgroup.com).  Are you running dns on your server you shut off?  Maybe that service needs started.  Don't know your setup, but maybe:

```
/etc/init.d/bind9 start
```

---

### Post by k_grdn on 2008-02-24
Check /var/log/syslog for bind errors.

---

### Post by astrotech226 on 2008-02-24
After you try to start bind and it fails, what's at the bottom of your /var/log/syslog file?

---

### Post by dethredic on 2008-02-24
well there is like 10000000 lines since an hour ago. I just tried to start bind 9 again, and here is the only line written in the last 5 mins:

> Feb 24 17:09:01 server1 /USR/SBIN/CRON[7153]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

I have no idea what this means

---

### Post by astrotech226 on 2008-02-24
That's odd there's nothing in the log.  Maybe there's already a process running for it.  Try to stop the service and see if any processes are hanging around for it:

```
ps -ef | grep named
```

If there are, I'd try the nasty kill:

```
killall -9 named
```

Then try to start it again.

---

### Post by dethredic on 2008-02-24
Great that worked

> 
root@server1:/home/phil# ps -ef | grep named
bind      4850     1  0 16:23 ?        00:00:00 /usr/sbin/named -u bind
syslog    6867     1  0 17:01 ?        00:00:00 /sbin/syslogd -a /var/lib/named/dev/log -u syslog
root      7182  7169  0 17:20 pts/0    00:00:00 grep named
root@server1:/home/phil# killall -9 named
root@server1:/home/phil# /etc/init.d/bind9 start
 * Starting domain name service... bind                                  [ OK ] 
root@server1:/home/phil# 


will this happen more often, or is it a one time onnly thing?

---

### Post by astrotech226 on 2008-02-24
> will this happen more often, or is it a one time onnly thing?

That's hard to say.  It would be interesting to see if the logs had anything in them from startup that showed why it wrecked in the first place.  Now you know what it is, if you get a time where you can reboot it you could do some good tests.

---

