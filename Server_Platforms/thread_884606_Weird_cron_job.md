---
title: "Weird cron job"
date: 2008-08-09
forum: Server Platforms
---

### Post by WeyOh on 2008-08-09
Hi,

I have a server with webmin and php5 (amongst other things), and I recently noticed that my syslog consist mostly of entries regarding a cron job which I don't remeber configuring. Does someone have an idea of what this does? And is there a way to make it run in a quiet way?

```
Aug  9 14:09:02 server /USR/SBIN/CRON[13550]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

```

Thanks,

Sam

---

### Post by windependence on 2008-08-09
Please explain what you mean by "in a quiet way".

-Tim

---

### Post by WeyOh on 2008-08-09
> **windependence said:**
> Please explain what you mean by "in a quiet way".

-Tim

Hi Tim,

By "quiet way", I meant that it doesn't output this line to the syslog.

---

### Post by windependence on 2008-08-09
Seems like it starts with testing if the directory /var/lib/php5 exists
That is what
[ -d /var/lib/php5 ]
is doing

and if so executes the find command afterwards which looks for files only where
the cmin age is greater than $(/usr/lib/php5/maxlifetime)

then it deletes them.

Looks like simple housekeeping.

You could take a look at the /usr/lib/php5/maxlifetime script and see if you could comment out the log location. Really though this is just normal PHP maintenance.

-Tim

---

### Post by WeyOh on 2008-08-09
> **windependence said:**
> 

You could take a look at the /usr/lib/php5/maxlifetime script and see if you could comment out the log location. Really though this is just normal PHP maintenance.


Below is the script
 ```
#!/bin/sh -e

max=1440

for ini in /etc/php5/*/php.ini; do
        cur=$(sed -n -e 's/^[[:space:]]*session.gc_maxlifetime[[:space:]]*=[[:space:]]*\([0-9]\+\).*$/\1/p' $ini 2>/dev/null || true);
        [ -z "$cur" ] && cur=0
        [ "$cur" -gt "$max" ] && max=$cur
done

echo $(($max/60))

exit 0

```

but the log doesn't appear mentioned at any point. Is the line output elsewhere? What does the -e parameter do?

---

### Post by MJN on 2008-08-10
All cron executions are recorded in Syslog hence if you want to remove the logging from this particular execution then your only option is to stop it happening - i.e. delete /etc/cron.d/php5

However, as Tim says, this cron job is PHP doing some housekeeping (purging expired sessions) hence I suggest you leave it be.

Mathew

---

