---
title: "Help with Snort Script"
date: 2009-08-30
forum: Security
---

### Post by TuckLive on 2009-08-30
I’m having a problem with my snort script stopping anytime I log into my server. When my server boots, the script loads and runs fine until I log on to update or whatever as my normal user. When I try to log off I always get the message "There are stopped jobs" and BASE will no longer show alerts. Snort is still collecting data, because when I restart the server I see the alerts after it went down. Here is my script:

```
#!/bin/bash
/sbin/ifconfig eth1 up
/usr/local/bin/snort -Dq -u snort -g snort -c \
/etc/snort/snort.conf -i eth1
/usr/local/bin/barnyard -c /etc/snort/barnyard.conf -g \
/etc/snort/gen-msg.map -s /etc/snort/sid-msg.map -d \
/var/log/snort -f snort.unified -w /etc/snort/bylog.waldo &
```

---

### Post by TuckLive on 2009-08-31
Ok I must have had something else running, because my script keeps running when I first log out.  I guess now I just need to find the command to keep a program running after I close my SSH session.  I regularly log in and stop Snort and I need it to keep running when I start it back up and log out.

---

### Post by bodhi.zazen on 2009-08-31
To keep an application running use screen.

If you wish to detach a program from a terminal, use nohup

nohup snort >/dev/null &

---

### Post by unspawn on 2009-09-01
> **TuckLive said:**
> I&#8217;m having a problem with my snort script stopping anytime I log into my server. (..) Here is my script
...in addition to what's said already, if this is a structural addition to the system (not a one shot process), then it might come in handy to follow distribution standards and use a proper daemon startup script. If the package doesn't come with one then maybe take some ideas from [http://vrt-sourcefire.blogspot.com/2008/09/snort-startup-script-for-ubuntu.html](http://vrt-sourcefire.blogspot.com/2008/09/snort-startup-script-for-ubuntu.html) ?

---

