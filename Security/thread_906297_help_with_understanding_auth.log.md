---
title: "help with understanding auth.log"
date: 2008-08-31
forum: Security
---

### Post by ub newb on 2008-08-31
Hi, 

I tried to get help on the absolute beginners forum, so if this is a beginner question, I apologize. I haven't got an answer over there yet.
 
Please point me to an area that can help me decipher these auth log entries? xyzzz is my user name masked, and I was wondering why there would be any root activity on my account when I wasn't doin it around 2AM in the morning? 


Aug 25 02:16:55 MDdesktop sudo: root : TTY=unknown ; PWD=/ ; USER=xyzzz ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Aug 25 02:16:55 MDdesktop sudo: pam_unix(sudo:session): session opened for user xyzzz by (uid=0)
Aug 25 02:16:55 MDdesktop sudo: pam_unix(sudo:session): session closed for user xyzzz
Aug 25 02:16:56 MDdesktop sudo: root : TTY=unknown ; PWD=/ ; USER=xyzzz ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Aug 25 02:16:56 MDdesktop sudo: pam_unix(sudo:session): session opened for user xyzzz by (uid=0)
Aug 25 02:16:56 MDdesktop sudo: pam_unix(sudo:session): session closed for user xyzzz
Aug 25 02:16:57 MDdesktop sudo: root : TTY=unknown ; PWD=/ ; USER=xyzzz ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Aug 25 02:16:57 MDdesktop sudo: pam_unix(sudo:session): session opened for user xyzzz by (uid=0)
Aug 25 02:16:57 MDdesktop sudo: pam_unix(sudo:session): session closed for user xyzzz

Thanks

---

### Post by rogeriopvl on 2008-08-31
is xyzzz your username? Or do you have a user with that username?

---

### Post by ub newb on 2008-08-31
xyzzz is what I substituted for my user name for the purposes of posting this log,  my real user name is in the original log.

---

### Post by rogeriopvl on 2008-08-31
> **ub newb said:**
> xyzzz is what I substituted for my user name for the purposes of posting this log,  my real user name is in the original log.

Ok, then you have no problem. It's normal to have those entries in auth.log mentioning the root user. It's only system "routines".

---

### Post by sot3 on 2008-09-16
Okay, but what "system routines"?

I've discovered these same lines in my auth.log in the past few days, but they weren't there before my upgrade to hardy over the weekend.  

Since mine occur at 07:35 every day, I took a peek at the likely source:
```
$ grep gconftool /etc/cron.daily/*
/etc/cron.daily/apt:if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
/etc/cron.daily/apt:    use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy)
/etc/cron.daily/apt:    host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
/etc/cron.daily/apt:    port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)

```

I'm not sure what this does or why it's necessary now when it wasn't before, but this is the code block in question:
```
# set the proxy based on the admin users gconf settings
admin_user=$(getent group admin|cut -d: -f4|cut -d, -f1)
if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
        use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy)
        host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
        port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)
        if [ "$use" = "true" ] && [ -n "$host" ] && [ -n "$port" ]; then
                export http_proxy="http://$host:$port/"
        fi
fi

```

---

### Post by bsh on 2009-06-08
hi
i have the same, at 7:35 every day.
i am not sure, but i think this is the update-notifier or something like that, that checks for available updates every day.

---

