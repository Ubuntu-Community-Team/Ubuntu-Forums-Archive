---
title: "Help please, is this normal?"
date: 2009-02-02
forum: Security
---

### Post by nacho87 on 2009-02-02
Im getting this from syslog and i don't know whar does it means:
```
Feb  2 21:09:01 nacho-netbook /USR/SBIN/CRON[14550]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

and this:

```
Feb  2 21:17:01 nacho-netbook /USR/SBIN/CRON[14637]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

and this one from auth.log frecuently:

```
Feb  2 21:17:01 nacho-netbook CRON[14630]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb  2 21:17:01 nacho-netbook CRON[14630]: pam_unix(cron:session): session closed for user root
```

also i get this from daemon.log every 2 minuts:
```
Feb  2 21:20:52 nacho-netbook NetworkManager: <debug> [1233606052.116828] periodic_update(): Roamed from BSSID 00:17:3F:80:03:C0 (belkin54g) to (none) ((none)) 
Feb  2 21:20:58 nacho-netbook NetworkManager: <debug> [1233606058.124822] periodic_update(): Roamed from BSSID (none) ((none)) to 00:17:3F:80:03:C0 (belkin54g) 
```

Yesterday it apeared a proxy in my system and i can't disable it, set in 127.0.0.1:8008

I hope you can help me, and sorry about my bad english!
thanks!

---

### Post by cjacobsen on 2009-02-02
> **nacho87 said:**
> Im getting this from syslog and i don't know whar does it means:
```
Feb  2 21:09:01 nacho-netbook /USR/SBIN/CRON[14550]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

and this:

```
Feb  2 21:17:01 nacho-netbook /USR/SBIN/CRON[14637]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

and this one from auth.log frecuently:

```
Feb  2 21:17:01 nacho-netbook CRON[14630]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb  2 21:17:01 nacho-netbook CRON[14630]: pam_unix(cron:session): session closed for user root
```

At least these messages seems normal. However, I've got little experience on proxy's.

---

### Post by nacho87 on 2009-02-02
thanks for the answer. after changing some things and restarting the proxy is off.

---

### Post by hyper_ch on 2009-02-04
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

